# TredIN Oracle Always-Free deployment

1. Create an Oracle Cloud Always Free ARM A1 VM.
2. Copy this ZIP/project to the VM and extract it.
3. Copy `.env.oracle.example` to `.env.oracle` and set strong secrets plus TrueData credentials.
4. Keep `ORDER_EXECUTION_ENABLED=false` until a real authorised broker adapter is connected.
5. Start:
   docker compose -f docker-compose.oracle.yml up -d --build
6. Initialize database:
   docker compose -f docker-compose.oracle.yml run --rm core node src/init-db.js
   docker compose -f docker-compose.oracle.yml run --rm core node src/seed-instruments.js
   docker compose -f docker-compose.oracle.yml run --rm core node src/provision-admin.js
7. Open the VM public IP in a browser.

Do not commit `.env.oracle` or real credentials to GitHub.

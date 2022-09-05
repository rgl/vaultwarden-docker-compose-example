Start it up:

```bash
docker compose up
```

Register the `alice@example.com` account at:

http://localhost:8080/#/register?email=alice@example.com

Login with the created credentials.

Under the `VERIFY EMAIL` widget, click the `Send Email` button.

Read (and respond) the confirmation email at:

http://localhost:8025

Repeat the process and register the `bob@example.com` account.

Create the `Example` organization with the `example-org@example.com` email at:

http://localhost:8080/#/create-organization

Add the `alice@example.com` to the `Example` organization.

After Alice responds to the email confirming she want to join the organization,
Bob must still confirm this in the `Organization` `Manage` `People` page, e.g., at:

http://localhost:8080/#/organizations/225036f6-7089-4ad0-9668-cec2990ea94e/manage/people

Poke the database:

```bash
docker compose exec --user postgres postgres psql vaultwarden
```
```sql
-- show tables.
\d
-- show users.
select * from users;
```

Destroy everything:

```bash
docker compose down --volumes --remove-orphans --timeout=0
```

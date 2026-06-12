---
title: "postgresql with python"
date: 2010-08-08
forum: General Help
---

### Post by sgsawant on 2010-08-08
I am stuck:

**postgresql**
- For the most part I referred:
[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)
- I installed postgres by using the command 'sudo apt-get install postgresql'
- Since I want to use postgres on the same machine I tried:
```

shashank@shashank-laptop:~$ sudo -u postgres createuser --superuser $USER
shashank@shashank-laptop:~$ sudo -u postgres psql
psql (8.4.4)
Type "help" for help.

postgres=# \password $USER
Enter new password: 
Enter it again: 
ERROR:  role "$user" does not exist

```

[B]pgadmin3
[/B]- Undaunted by the previous failure, I installed pgadmin3
- There I am not able to connect anywhere and the error I receive is: "password authentication failure.

[B]python3, py-postgresql & postgres
[/B]- Undaunted by even that I installed python3 on my Ubuntu.
- Then I installed py-postgresql
- Then I tried:
>>> import postgresql    #This worked, it's just a simple import
>>> db = postgresql.open("pq://localhost/postgres") #This did not work :(

Here's the error:
```

>>> db = postgresql.open("pq://localhost/postgres")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python3.1/dist-packages/postgresql/__init__.py", line 88, in open
    c.connect()
  File "/usr/local/lib/python3.1/dist-packages/postgresql/driver/pq3.py", line 2484, in connect
    self.typio.raise_client_error(could_not_connect, creator = self, cause = exc)
  File "/usr/local/lib/python3.1/dist-packages/postgresql/driver/pq3.py", line 444, in raise_client_error
    raise client_error
postgresql.exceptions.ClientCannotConnectError: could not establish connection to server
  CODE: 08001
  LOCATION: CLIENT
CONNECTION: [failed]
  failures[0]:
    SSL socket('::1', 5432)
    postgresql.exceptions.AuthenticationSpecificationError: password authentication failed for user "shashank"
      CODE: 28000
      LOCATION: File 'auth.c', line 273, in auth_failed from SERVER
  failures[1]:
    socket('::1', 5432)
    postgresql.exceptions.AuthenticationSpecificationError: password authentication failed for user "shashank"
      CODE: 28000
      LOCATION: File 'auth.c', line 273, in auth_failed from SERVER
  failures[2]:
    SSL socket('127.0.0.1', 5432)
    postgresql.exceptions.AuthenticationSpecificationError: password authentication failed for user "shashank"
      CODE: 28000
      LOCATION: File 'auth.c', line 273, in auth_failed from SERVER
  failures[3]:
    socket('127.0.0.1', 5432)
    postgresql.exceptions.AuthenticationSpecificationError: password authentication failed for user "shashank"
      CODE: 28000
      LOCATION: File 'auth.c', line 273, in auth_failed from SERVER
CONNECTOR: [Host] pq://shashank@localhost:5432/postgres
  category: None
DRIVER: postgresql.driver.pq3.Driver

```

Of course I didn't expect most of the things to work, after getting an error at the first step.
But can someone point me in the right direction?
The way I see it, is that, using postgres I create a local database.
But I am not able to go ahead due to password authentication failures.
I have used a constant username and a constant password so that I don't 
jumble it up. But I still keep receiving password authentication error.



Please let me know.

Regards,

-sgsawant

---

### Post by sgsawant on 2010-08-08
Request repeat.

---

### Post by zenonChochem on 2011-03-03
Hi, this may be late but who knows. I just had the same problem and found out that: the connections to the postgresql server are controlled by: pg_hba.conf, and by default are restrictive. You just have to find the file pg_hba.conf on your postgres account and set the last columns to 'trust'.
For more info look for configuring pg_hba.conf on google, they seems to be minor differences between versions of postgresql.

---


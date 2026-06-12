---
title: "db_connect problem!"
date: 2011-07-19
forum: General Help
---

### Post by Libra- on 2011-07-19
Hey guys!

I'm having problems to connect the MySQL to the metasploit.
When I try to use db_connect I get the following error:

[B][-] Error while running command db_connect: Failed to connect to the database: uninitialized constant MysqlCompat::MysqlRes

Call stack:[/B] [B]
/opt/framework-3.7.2/msf3/lib/msf/ui/console/command_dispatcher/db.rb:1844:in `db_connect_mysql'
/opt/framework-3.7.2/msf3/lib/msf/ui/console/command_dispatcher/db.rb:1727:in `cmd_db_connect'
/opt/framework-3.7.2/msf3/lib/rex/ui/text/dispatcher_shell.rb:376:in `run_command'
/opt/framework-3.7.2/msf3/lib/rex/ui/text/dispatcher_shell.rb:338:in `block in run_single'
/opt/framework-3.7.2/msf3/lib/rex/ui/text/dispatcher_shell.rb:332:in `each'
/opt/framework-3.7.2/msf3/lib/rex/ui/text/dispatcher_shell.rb:332:in `run_single'
/opt/framework-3.7.2/msf3/lib/rex/ui/text/shell.rb:143:in `run'
/opt/framework-3.7.2/msf3/msfconsole:130:in `<main>'[/B]

Ubuntu Version: 11.04
Metasploit Framework Version: 3.8.0-dev.13016

PS: I'm new at ubuntu.

Thanks ! Have a nice day.

---

### Post by Libra- on 2011-07-19
Someone?

---

### Post by Libra- on 2011-07-20
up

---

### Post by Habitual on 2011-07-21
```
sudo gem install --no-rdoc --no-ri -v=2.7 mysql -- --with-mysql-dir=/usr/local/mysql --with-mysql-config=/usr/bin/mysql_config
```

is the fix so says [https://baber.wordpress.com/2011/01/08/fixing-mysql-gem-errors-in-bt4/](https://baber.wordpress.com/2011/01/08/fixing-mysql-gem-errors-in-bt4/)

---


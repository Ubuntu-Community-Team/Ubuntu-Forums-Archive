---
title: "installing the innodb plugin 1.0.4 for MySQL 5.1.37"
date: 2010-02-02
forum: General Help
---

### Post by meonkeys on 2010-02-02
I'm using MySQL 5.1.37 (I just installed whatever came with Ubuntu 9.10). I'm interested trying the ["InnoDB plugin" version 1.0.4]("http://www.innodb.com/wp/2009/08/11/innodb-plugin-104-released/") to see if it performs better. Anyone know if this plugin is some kind of beta that might eventually make it into MySQL that comes with Ubuntu? Or is this just a different version of the InnoDB engine?

If folks have used this plugin, could you share what directory you installed it into? I read the README that comes in the tarball, but I couldn't find the plugins directory on my disk.

I should probably also head on over to one of the MySQL forums to ask these same questions.

---

### Post by meonkeys on 2010-02-03
The [MySQL 5.1.43 announcement]("http://forums.mysql.com/read.php?3,315946,315946#msg-315946") indicates the InnoDB plugin version is 1.0.6.

I got the InnoDB plugin version 1.0.4 working with MySQL 5.1.37 on Ubuntu 9.10 desktop to work as follows:
[LIST]
[*]created /usr/lib/mysql/plugin
[*]installed the InnoDB plugin 1.0.4 in that directory
[*]modified /etc/mysql/my.cnf as specified in the README in the tarball from innobase (innodb_plugin-1.0.4-linux-i686-glibc23.tar.gz)
[*]added apparmor rules (below) to allow mysqld to use the plugin
[*]reloaded apparmor rules (sudo /etc/init.d/apparmor reload)
[*]restarted mysql (sudo /etc/init.d/mysql restart)
[/LIST]

new apparmor rules added to /etc/apparmor.d/usr.sbin.mysqld
```

/usr/lib/mysql/plugin/ r,
/usr/lib/mysql/plugin/* mr,

```

[More on AppArmor rules]("http://en.opensuse.org/AppArmor_Geeks#Anatomy_of_a_Profile").

---


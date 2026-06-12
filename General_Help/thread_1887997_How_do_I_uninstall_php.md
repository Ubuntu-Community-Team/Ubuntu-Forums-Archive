---
title: "How do I uninstall php?"
date: 2011-11-28
forum: General Help
---

### Post by 0n_a_mission on 2011-11-28
[from [http://ubuntuforums.org/showthread.php?t=1207665](http://ubuntuforums.org/showthread.php?t=1207665)]

OK, I think I have a clue to what might be going on, but I have no idea  how to fix it.  What I have found is that from a command line I get  this:
     ```
dev@dev-desktop:~$ php -info |more
phpinfo()
PHP Version => 5.2.17

System => Linux dev-desktop 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011 i686
Build Date => Sep 22 2011 16:26:24 
```
But from a browser I get this:[INDENT] **PHP Version 5.3.2-1ubuntu4.10**
**System** Linux dev-desktop 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011 i686 
**Build Date** Oct 14 2011 23:57:47
[/INDENT]What this tells me is that I have two different PHP  instances running and, so, when I try to add pdo-oci to my install by  the command line it goes to the wrong instance.

Does this make sense?

If not, what does?

If so, how do I "uninstall" the older one and get only one version on my machine? I have tried extensive searches on this forum and general Google searches and can not seem to find anything of help.  Maybe I am just using the wrong search terms -- "Uninstall php" and "remove php" and "purge php" with and without keywords "Ubuntu" , "linux", etc

Please help.

Thanks,
Tim 
- Ubuntu 10.04.3 LTS
- Oracle 9 & 10
- PHP 5.2.17 **& 5.3.2**
- InstantClient 11.2.0.2.0

---

### Post by okmat on 2011-11-28
sudo apt-get remove php5

---

### Post by 0n_a_mission on 2011-11-28
> **okmat said:**
> sudo apt-get remove php5

THanks, okmat, but which instance will that get rid of?  

OK, I answered that myself -- it removed the one I wanted to keep.  No problem, I can reinstall it, but how do I get rid of the other one?

Thanks,
Tim 
- Ubuntu 10.04.3 LTS
- Oracle 9 & 10
- PHP 5.2.17 
- InstantClient 11.2.0.2.0

---

### Post by 0n_a_mission on 2011-11-28
Actually, it doesn't seem to have removed either.  I still get the exact same thing:

From the command line:
```
dev@dev-desktop:~$ php --info|more
phpinfo()
PHP Version => 5.2.17

System => Linux dev-desktop 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011 i686
Build Date => Sep 22 2011 16:26:24

```

and from the phpinfo() web page:

[INDENT]PHP Version 5.3.2-1ubuntu4.10


System    Linux dev-desktop 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011 i686
Build Date    Oct 14 2011 23:57:47

[/INDENT]I have no idea what to do next.

---

### Post by okmat on 2011-11-28
I'd suggest to backup your databases and www dir, then completely remove php mysql, phpmyadmin and apache with 

```
sudo apt-get remove --purge apache2 php5 mysql-server-5.0 phpmyadmin
```

...and reinstall everything from scratch

```
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

```

and 

```
sudo apt-get install phpmyadmin

```

Hope that helps

---

### Post by 0n_a_mission on 2011-11-28
[okmat]("http://ubuntuforums.org/member.php?u=628668"), your time and advise were greatly appreciated.  I have worked out my issue by starting completely from scratch -- a new install of Ubuntu and that way I know I only have the one instance of php and it has all of the drivers that I want.

---


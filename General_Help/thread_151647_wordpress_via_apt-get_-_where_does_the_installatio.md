---
title: "wordpress via apt-get - where does the installation go?"
date: 2006-03-28
forum: General Help
---

### Post by bnj on 2006-03-28
Hello,
I am trying to install wordpress on my Ubuntu server.
apache, php, mysql and phpmyadmin are working fine. So I did apt-get install wordpress, and here is what I have got:

```

prompt:~$ sudo apt-get install wordpress
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  wordpress
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/304kB of archives.
After unpacking 1630kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package wordpress.
(Reading database ... 77809 files and directories currently installed.)
Unpacking wordpress (from .../wordpress_1.5.2-1_all.deb) ...
Setting up wordpress (1.5.2-1) ...
prompt:~$ 

```

But then I cannot find where wordpress has been installed. There is a directory wordpress in /etc/, but it is empty. And it does not appear in /var/www/.
I also looked in my public_html, just in case, but nothing there.
Anybody has an idea?

Thank you.

---

### Post by localzuk on 2006-03-28
Well, to find anything it is easiest to run 
```
sudo updatedb
locate filename
```

So in this case, replace filename with wordpress and you find that it is installed in /usr/share/wordpress.

---

### Post by localzuk on 2006-03-28
Further to this, you now need to configure it and enable it via your apache configuration files.

---


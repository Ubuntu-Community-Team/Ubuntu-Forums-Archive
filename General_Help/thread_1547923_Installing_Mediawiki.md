---
title: "Installing Mediawiki"
date: 2010-08-07
forum: General Help
---

### Post by Silvernail on 2010-08-07
Installing 'Mediawiki' and using the instructions found at this website.
[https://help.ubuntu.com/community/MediaWiki](https://help.ubuntu.com/community/MediaWiki)

I get this error during installation.
>  dave@dave:~$ sudo apt-get install mediawiki
...............
......................

(Reading database ... 321919 files and directories currently installed.)
Unpacking mediawiki (from .../mediawiki_1%3a1.15.1-1ubuntu2.1_all.deb) ...
Setting up mediawiki (1:1.15.1-1ubuntu2.1) ...
 * Reloading web server config apache2                                          [Sat Aug 07 12:06:32 2010] **[warn] NameVirtualHost *:80 has no VirtualHosts**
                                                                         [ OK ]

dave@dave:~$ 
Then this one which I presume is because 'VirtualHosts' is missing.
> dave@dave:~$  sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                [Sat Aug 07 12:13:15 2010] [warn] The Alias directive in /etc/apache2/sites-enabled/gforge at line 15 will probably never match because it overlaps an earlier Alias.
[Sat Aug 07 12:13:15 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Sat Aug 07 12:13:16 2010] [warn] The Alias directive in /etc/apache2/sites-enabled/gforge at line 15 will probably never match because it overlaps an earlier Alias.
[Sat Aug 07 12:13:16 2010] **[warn] NameVirtualHost *:80 has no VirtualHosts**
                                                                         [ OK ]
dave@dave:~$ 

How do I establish/create/initialize 'VirtualHosts'?

---

### Post by Silvernail on 2010-08-07
I am trying to install on my computer not a server.

---


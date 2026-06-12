---
title: "Squid ?"
date: 2009-08-27
forum: General Help
---

### Post by elliotbeken on 2009-08-27
hi all i know how to install squid..

but i want to install 2.6 becase i am using webmin which only supports 2.6

how do i install 2.6 ?

thanks

---

### Post by bboston7 on 2009-08-27
From terminal
```
sudo apt-get install squid
```

From webmin
1. click "System"
2. Click "Software Packages"
3. Click "Package from APT"
4. Type "squid" without the quotes
5. Click the "Install" button
6. Refresh webmin after the install finishes.

---

### Post by elliotbeken on 2009-08-27
Thanks for the quick reply but the steps you showed still install 2.7 

"Your version of Squid is not supported by Webmin. Only versions from 1.1 to 2.6 are supported by this module."

---

### Post by scouser73 on 2009-08-27
Does this help at all? [[COLOR="Red"]**Squid 2.6 Tutorial**[/COLOR]]("https://help.ubuntu.com/7.04/server/C/squid.html").

---

### Post by elliotbeken on 2009-08-28
:) i will try and explain again..

i need to install squid 2.6 not any other version.... i can intall version 2.7 and 3.0 but they are no good i need 2.6 only

---

### Post by IkeLewis on 2009-12-29
**Bump bump!**

---

### Post by Strongman332 on 2009-12-29
you could google squid.deb 2.6 to see if you get anything

---

### Post by wallaroo on 2009-12-29
You can get 2.6 from the Debian archives here :

[http://packages.debian.org/search?keywords=squid&searchon=names&suite=oldstable&section=all](http://packages.debian.org/search?keywords=squid&searchon=names&suite=oldstable&section=all)

You'll need to uninstall 2.7 before installing 2.6.

---


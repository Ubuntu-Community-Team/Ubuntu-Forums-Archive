---
title: "nmap 4.00 on breezy"
date: 2006-02-01
forum: General Help
---

### Post by yanik on 2006-02-01
Hi everyone,

I just finished compiling the latest nmap, the great network scanning tool.  Here is what I had to do in order to compile it.

First, get a real root account (I tried with sudo and about 50 gnome-terminal windows appeared asking my password...):
```

$sudo passwd
```
Now install auto-apt and update it.  If it ask to install other packages (and it will), just say yes:
```
#apt-get install auto-apt
#auto-apt update
#auto-apt updatedb
#auto-apt update-local
#auto-apt run ./configure
```
Then do the real ./configure:
```

#./configure
```
Fianlly, make a debian package (.deb) and then install it.
```

#apt-get install checkinstall
#checkinstall -D make install
```

Hope this helps.  I don't know if these generated packages are good enough to wok on another ubuntu install, I'll make mine available for a couple of days right here: [http://www.libera.ca/nmap-4.00_4.00-1_i386.deb](http://www.libera.ca/nmap-4.00_4.00-1_i386.deb) (right-click save as)


Yanik

---

### Post by noigeaR on 2006-02-01
thanks for the how-to!

i hope nmap 4.00 will hit dapper soon so we can get an official backport to breezy. dapper is still at 3.95 right now :roll:

---

### Post by LordBug on 2006-02-01
> First, get a real root account

Did you try "sudo -s" first?

---

### Post by yanik on 2006-02-02
no, I didn't even knew about that switch.

---


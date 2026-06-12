---
title: "cups configuration stuck"
date: 2012-07-20
forum: General Help
---

### Post by marianoa on 2012-07-20
Hi everybody,

I'm having a problem trying to update the cups package. The setting up was taking
a long time so I killed the process. Now if I give 
```
sudo dpkg --configure -a
```it gets to 
```
Setting up cups (1.5.3-0ubuntu1)...
Updating PPD files for cups ...
Updating PPD files for hpijs ...

```and it stays there, I waited for more than an hour now.

Any idea? Thanks

---

### Post by TheFu on 2012-07-20
I'd try a reinstall first.

$ sudo apt-get --reinstall install cups

If that failed, I'd force a purge and a new install. If that fails, then it is time to force the install 

$ sudo apt-get -f install cups 

If that fails, then the last resort, which is never a good idea and can be dangerous is to dig into the APT cache files and remove all knowledge of cups. I've seen 20 threads here with that method. I hope the issue gets solved before you get here.

---

### Post by marianoa on 2012-07-20
Hi TheFu,

I tried your suggestions but all of them fail since the package manager complains that dpkg
has been stopped and I have to execute
```
 
sudo dpkg --configure -a

```
before doing anything else.
Any other suggestion? I'd really like to avoid messing up with the apt cache by hand

---

### Post by marianoa on 2012-07-21
An update on my problem.
I found out that the problem was related to the script

/var/lib/dpkg/info/cups.postinst

and since it processed one by one the files in

/usr/share/cups/ppd-updaters/

I decided to move in a different folder the file "printer-driver-hpijs" which was the
one on which the script got stuck. This made the setting up run fine and now I'm able
to use the package manager again.

---


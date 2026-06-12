---
title: "NEED help with root password"
date: 2010-05-13
forum: General Help
---

### Post by blksilver on 2010-05-13
Trying to install printer and system is asking for root password

---

### Post by John Bean on 2010-05-13
There is no root password. Use yours :-)

---

### Post by blksilver on 2010-05-13
doesnt work

---

### Post by John Bean on 2010-05-13
You'll need to tell us exactly what you're trying to do and how. As a starter, what command did you type that caused it to ask for the root password?

---

### Post by KeyserSoze93 on 2010-05-14
If you set a root password, it may ask for that instead. If you don't know it, you can reset it by running:

```

sudo passwd root

```

It will ask for your own password for sudo, and then ask for a new password for root (and confirm it.)

---

### Post by cdenley on 2010-05-14
> **KeyserSoze93 said:**
> If you set a root password, it may ask for that instead. If you don't know it, you can reset it by running:

```

sudo passwd root

```

It will ask for your own password for sudo, and then ask for a new password for root (and confirm it.)

Setting a root password is strongly discouraged, and posting that command isn't allowed on this forum.
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

To unset your root password:
```

sudo usermod -p ! root

```

You shouldn't need a root password for installing a printer or doing anything in ubuntu.

---

### Post by cloyd on 2010-05-14
Lexmark x2600 printers driver from Lexmark demands a real root account and root password. I set one up. I know the password; it is not my sudo password, and since I installed the Lexmark printer, I have never used it. As a matter of fact, immediately after I installed the printer, I shut the machine rebooted the machine, because I wanted to be sure I was not working as root. But for some strange reason, some lexmark printers demand root passwords.


EDIT
I just read

quote
Setting a root password is strongly discouraged, and posting that command isn't allowed on this forum.
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
Unquote

I did not realize that posting the command was against forum policy. I did recognize the dangers of logging in as root. I've tried to help some others on with lexmark printers with this information. I think it would be helpful if some moderators or others more knowledgeable than I would look at the drivers on the lexmark site and tell some of us how to accomplish the install w/o the root account. I beat my head against a wall until I make a root account.  

"Get rid of your lexmark printer and buy  an HP" may be good advice for the long run, but frequently, it is not very helpful for the immediate problem in the here and now,

---

### Post by QIII on 2010-05-14
Is that driver not available as a selection when you attempt to add the printer in the normal way through Ubuntu?

---

### Post by cdenley on 2010-05-14
```

wget http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip
unzip lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip
chmod a+rx lexmark-inkjet-08-driver-1.0-1.i386.deb.sh
sudo ./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh

```

---

### Post by lisati on 2010-05-14
Speaking of "root" passwords & privileges, take a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cloyd on 2010-05-14
> **QIII said:**
> Is that driver not available as a selection when you attempt to add the printer in the normal way through Ubuntu?
   
The short answer is no. The long answer is that lexmark is poorly supported (let's say that differently  . . . lexmark supports linux poorly!).  Many lexmark printers won't work at all with linux, and many of those that do apparently demand a root account.

---

### Post by cdenley on 2010-05-14
> **cloyd said:**
> The short answer is no. The long answer is that lexmark is poorly supported (let's say that differently  . . . lexmark supports linux poorly!).  Many lexmark printers won't work at all with linux, and many of those that do apparently demand a root account.

They don't require a root password. The installer requires root privileges. That is what sudo is for!

---

### Post by cloyd on 2010-05-14
> **cdenley said:**
> They don't require a root password. The installer requires root privileges. That is what sudo is for!

I don't want to be argumentative, but what a few of us are trying to tell some others is this:  with the many of the drivers that lexmark supplies, _sudo does not work._  I know sudo is supposed to be safer than root. I don't want to log in as root. Sudo _should_ work.  But in this situation, sudo does not work.

---

### Post by QIII on 2010-05-14
Thanks for the solution cdenley.  I'll put that in my black book as an example for the next time I see something like this.

As for OEM support for Linux, after breaking it with large, heavy objects I'd personally throw out anything that required me to log in as root to use it.  That's just me.

---

### Post by lisati on 2010-05-14
If sudo doesn't work for some reason, the three most likely causes are either a bug, a PEBKAC error (or some such problem), or the need to use a different driver/installer/etc.

---

### Post by jerome1232 on 2010-05-14
It's probably something as simple as their installation script using su to get root privileges and not even attempting to use sudo or checking to see if it has root privileges already.

Crappy OEM support is crappy, Lexmark is something to avoid at all costs.

---

### Post by cloyd on 2010-05-14
Ok,  I just learned something, too.  Sudo may work. I looked back on this thread, on which I had posted, and hadn't gotten back to until today. Others have posted solutions which may have worked for me.  Others may want to look here:
[http://ubuntuforums.org/showthread.php?t=1122702&highlight=password](http://ubuntuforums.org/showthread.php?t=1122702&highlight=password)

---

### Post by cdenley on 2010-05-14
The installer itself won't use sudo to escalate privileges, but if you escalate to root privileges before running the installer using sudo, then you are not prompted for a root password.

---

### Post by cdenley on 2010-05-14
> **cloyd said:**
> Ok,  I just learned something, too.  Sudo may work. I looked back on this thread, on which I had posted, and hadn't gotten back to until today. Others have posted solutions which may have worked for me.  Others may want to look here:
[http://ubuntuforums.org/showthread.php?t=1122702&highlight=password](http://ubuntuforums.org/showthread.php?t=1122702&highlight=password)

Sometimes I get the feeling my posts are invisible.
[http://ubuntuforums.org/showpost.php?p=9299734&postcount=9](http://ubuntuforums.org/showpost.php?p=9299734&postcount=9)

---

### Post by dabl on 2010-05-14
If you are using the CUPS browser interface, try entering "root" as the user, and then give it your password.  No need to really set up root as a user on the system, it's just the name CUPS is looking for.

Not that the Lexmark is necessarily going to have a driver available ....  :-({|=

---

### Post by cdenley on 2010-05-14
By the way, unrelated to root privileges, the driver will only install on 32-bit systems. I figured out how to force it to install on 64-bit systems, but I don't know if it actually works. I got to the point where it asks you to connect the printer to the USB port, but I don't actually have a lexmark printer to test with.

```

sudo apt-get install ia32-libs
echo -e '#!/bin/sh\n/usr/bin/dpkg --force-architecture $@'|sudo tee /usr/local/bin/dpkg
sudo chmod a+rx /usr/local/bin/dpkg
sudo ./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh
sudo rm /usr/local/bin/dpkg

```

---

### Post by cloyd on 2010-05-14
> **cdenley said:**
> Sometimes I get the feeling my posts are invisible.
[http://ubuntuforums.org/showpost.php?p=9299734&postcount=9](http://ubuntuforums.org/showpost.php?p=9299734&postcount=9)


My apologies for not listening.

---


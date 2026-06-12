---
title: "Avast Anti Virus"
date: 2010-03-29
forum: General Help
---

### Post by St Nabi on 2010-03-29
Hi there all, 

I just installed Avast on my Ubuntu 9.10 OS 32 bit, when I try to open Avast, I get the following message :- 
"An error occured in avast! engine: Invalid argument"

Firstly what does this mean and secondly how do I access Avast?

Looking forward to your replies.

Thanks & Regards

St Nabi

---

### Post by desnaike on 2010-03-29
This happened to me yesterday after upgrading the virus database I went into home .avast folder deleted vps file and it worked so maybe the update is somehow broken.

---

### Post by St Nabi on 2010-03-29
Hi there, 

My problem is that I can't get into the Home.avast folder in the first place. Avast simply wont open.

---

### Post by 2hot6ft2 on 2010-03-29
> **St Nabi said:**
> Hi there, 

My problem is that I can't get into the Home.avast folder in the first place. Avast simply wont open.
Opening avast has nothing to do with getting into its folder. Go to
Places > Home Folder
click on View then check the box by Show Hidden Files.
Then you can see and open the folder .avast
When you're done click on View and un-check the box.

---

### Post by St Nabi on 2010-03-30
Hi and thanks for your assistance. 

I opened the .avast folder and deleted the vps file as mentioned by dsnaike it initially opened but when I tried to update, it gave the following message, "avast! engine failed to reinitialize after database upgrade.The application will terminate now"

I also got the previous message too, "An error occured in avast! engine: Invalid argument".

Any suggestions

---

### Post by inpxfx on 2010-03-30
i actually was having trouble with the deb file on the website using gdebi to install would give me errors about the upsteam data not being readable i finally got a good copy after trying over and over again. seems to be a problem with my computer reading tar.bz files most are all corrupted was happening with updating ubuntu also. 


same errors as most when it wont start up go into your home and delete avastrc 400vps and lockfile and itll start up again 
avastrc has your license key in it so just rename it to something else to stay away from the hassle of looking for it all over again

also i noticed the preference only  open and not crash with certain themes wild1.1 works others dont. 

this is bitdefender until avast works im screwing with this one 

[http://www.wilderssecurity.com/showthread.php?p=1649471](http://www.wilderssecurity.com/showthread.php?p=1649471)
 everyone is having issues it seems with updating 
i just miss using nautilus actions to quick scan a file
oh well hopefully itll be fixed sooner or later

---

### Post by mthei on 2010-04-02
This is a problem with the Linux version of Avast. [There is a way to get around it.](http://forum.avast.com/index.php?PHPSESSID=9cba7077ccb4b141cbb74cf64a2db104&topic=57775.0)

---

### Post by mike4ubuntu on 2010-09-08
what starup script is best to put this in, so that it is applied automatically when system starts up?  Might be some problems with this in /etc/init.d/rcS

---

### Post by Dragynn on 2010-09-08
I have Avast in Lucid 10.04, had the same problem, lotsa workarounds out there, but I have found after experimenting with 3 different computers and several versions of Linux, that all you need to do is edit /etc/sysctl.conf by adding this:

kernel.shmmax = 128000000

save, close, and re-boot. You don't have to delete 400.vps. This workaround is working in Ubuntu 10.04, Puppy Linux 5.1 and several other Puppy-based distros. I do it right after installing Avast, and prior to doing an update.

Good Luck!

---

### Post by tonewheelkev on 2011-01-14
> **Dragynn said:**
> .......... all you need to do is edit /etc/sysctl.conf by adding this:

kernel.shmmax = 128000000

save, close, and re-boot. ..........

Any chance of going over this again.......PLEASE

---

### Post by tonewheelkev on 2011-01-14
> **Dragynn said:**
> .......... all you need to do is edit /etc/sysctl.conf by adding this:

kernel.shmmax = 128000000

save, close, and re-boot. ..........

Any chance of going over this again.......PLEASE

---

### Post by tonewheelkev on 2011-01-14
> **Dragynn said:**
> .......... all you need to do is edit /etc/sysctl.conf by adding this:

kernel.shmmax = 128000000

save, close, and re-boot. ..........

Any chance of going over this again.......PLEASE

---

### Post by mike4ubuntu on 2011-01-21
Nobody's probably looking at this thread too much anymore.  In Lucid, it was necessary to set a dynamic kernel parameter to get Avast Anti Virus to work reliably in the 64 bit kernel version.

kernel.shmmax = 128000000

putting this setting in the /etc/sysctl.conf guaranteed it would be set automatically upon a reboot.

---

### Post by VinDSL on 2011-02-04
> **tonewheelkev said:**
> Any chance of going over this again.......PLEASEProblem(s)...

[LIST=1]
[*]By default, the maximum size of the kernel.shmmax block is set too tight (in bytes).


[*]And, the Avast AV Database has grown so large that it exceeds this limit.
[/LIST]

Fix...

All you have to do is set this SHM block to a more reasonable value.

Personally, I've found that 100000000 allows Avast to load/run just fine.


Here's how my SHM blocks look...
```

vindsl@Zuul:~$ sudo sysctl -a | grep shm
[sudo] password for vindsl: 
**[COLOR="Red"]kernel.shmmax = 100000000[/COLOR]**
kernel.shmall = 2097152
kernel.shmmni = 4096

```

If you want to temporarily reset the offending block, run this command from CLI (console)...
```

sudo sysctl -w kernel.shmmax=100000000

```

Avast should now start and run.

You can do this every time you want to run Avast, or...

You can add it to your ~/etc/sysctl.conf file, and forget about it.

Edit your ~/etc/sysctl.conf (as root).
```
$ sudo gedit ../../etc/sysctl.conf

```

At the bottom of this file, add a blank line, followed by a line containing...
```

kernel.shmmax=100000000

```

...save, and reboot.

That's it!  ;)


Here's a screenie of Avast running on my desktop...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-avast-4-feb-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-avast-4-feb-2011.png")[/INDENT]

---


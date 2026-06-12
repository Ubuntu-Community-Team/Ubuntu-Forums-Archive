---
title: "HP Color Laserjet 2605dn"
date: 2010-11-09
forum: General Help
---

### Post by oldironman64 on 2010-11-09
Hi,

Being relatively new to LINUX, folks, I would need some help.

I have a color laserjet 2605dn on my router and it works (almost perfectly) under Windows.
Now I am trying to get it to running under Ubuntu 9.01:
I defined the printer, I installed the HPLIP driver. (I also tried the other drivers on the DB list)
I included it in CUPS and I can also ping on the IP address.
When I print a TEST page,  it says first that it has started to print, then print job is completed, which is OK.
No error message whatsoever.:P

The only problem is, that it doesn't print at all. The print queue shows the job while printing, then it is emptied.
Log shows that there were some 20 print job printed.:confused:

Does anybody have any idea what I am doing wrong?

---

### Post by kanishkdudeja on 2010-11-09
refer to this thread..

[http://ubuntuforums.org/showthread.php?t=1377343](http://ubuntuforums.org/showthread.php?t=1377343)

---

### Post by kanishkdudeja on 2010-11-09
during installing hplip did it tell u to plug in ur printer ? and hplip requires internet access during installation..if ur internet was not on that time..hplip would show it installed successfully but it would not..

---

### Post by oldironman64 on 2010-11-09
> **kanishkdudeja said:**
> during installing hplip did it tell u to plug in ur printer ? and hplip requires internet access during installation..if ur internet was not on that time..hplip would show it installed successfully but it would not..

Thank you for the ideas.

When I installed hplip internet was active. Actually I had to download first a .run file, then sh it in a terminal window according to instructions.

The system log shows however that connection failed because of port 9100 being probably closed.
I put port forwarding on 9100 but it didn't help. The port test shows only 80(http), 139 (netbios) and 515 (print) being open.

Still trying:guitar:

---

### Post by kanishkdudeja on 2010-11-09
yeah v hav to install by first downloading a run file and then executing it in the terminal..

try install it by:

```
sudo apt-get install hplip
```

---

### Post by oldironman64 on 2010-11-09
I reinstalled HPLIP first then I found the error log with this msg:

"[cups-polld 192.168.1.102:631] Unable to connect to 192.168.1.102 on port 631: Connection refused"

It looks that  cups is trying to access the printer on port 631. Now port 631 on localhost is CUPS management but on the printer this port is not open. Does it supposed to mean "shared"?

---

### Post by kanishkdudeja on 2010-11-09
umm..no idea..

i would suggest either wait for sumbody else to solve this problem..

or install ubuntu 10.10..

hplip and cups are installed by default in it..

the minute u plug in ur printer it will ask you whether you want to install the pulgin..

click on yes and it will automatically install..

---

### Post by kanishkdudeja on 2010-11-09
how did u check this port is not open on the printer ?

---

### Post by kanishkdudeja on 2010-11-09
i did some googling for u..

check if these links help u..

[https://answers.launchpad.net/ubuntu/+source/cupsys/+question/7880](https://answers.launchpad.net/ubuntu/+source/cupsys/+question/7880)

[http://www.linuxquestions.org/questions/linux-general-1/cups-unable-to-connect-to-server-184088/](http://www.linuxquestions.org/questions/linux-general-1/cups-unable-to-connect-to-server-184088/)

[http://www.linuxforums.org/forum/red-hat-fedora-linux/143709-cups-printer-config.html](http://www.linuxforums.org/forum/red-hat-fedora-linux/143709-cups-printer-config.html)

[http://forums.opensuse.org/english/get-help-here/network-internet/401359-unable-connect-cups-server-localhost.html](http://forums.opensuse.org/english/get-help-here/network-internet/401359-unable-connect-cups-server-localhost.html)

[http://techtouch.ca/blog/2010/01/03/unable-to-connect-to-cups-server-localhost631-connection-refused/](http://techtouch.ca/blog/2010/01/03/unable-to-connect-to-cups-server-localhost631-connection-refused/)

---


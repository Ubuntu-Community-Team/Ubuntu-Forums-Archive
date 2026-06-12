---
title: "Modem Detection on the LiveCD"
date: 2005-02-27
forum: General Help
---

### Post by Trexx on 2005-02-27
The liveCD doesn't seem to be detecting my modem, is there a way for me to fix this? If not, will it do it with the actual installed version when I install it? Thanks for the help!!!

---

### Post by alastair on 2005-02-27
If this is not the latest "hoary" liveCD, then try that.

If it is - then I believe that it is essentially the same as the install CD, so the problem will probably be present on a real install. This might be fixable still though.

What sort of modem? Check logs :

/var/log/syslog (or type : dmesg)

Perhaps :

lspci

Has it worked on a different linux dist?

---

### Post by Trexx on 2005-02-27
[QUOTE=alastair]If this is not the latest "hoary" liveCD, then try that.

If it is - then I believe that it is essentially the same as the install CD, so the problem will probably be present on a real install. This might be fixable still though.

What sort of modem? Check logs :

/var/log/syslog (or type : dmesg)

Perhaps :

lspci

Has it worked on a different linux dist?[/QUOTE]
 This is my first time using a Linux distro.

It is a SmartLink modem, unfortunately I cannot find the model number. 


Edit:
I've run the dmsg and lspci, but I can't seem to get the modem to detect. I started it in expert mode, and I saw that it said my modem on the list, but after that, it freezes on me (where it says to type something in).  So I dunno what to do. :( I'll try to look for some documentation on it.

---

### Post by alastair on 2005-02-28
I have a smartlink in my laptop (a thinkpad). You have to download a special driver - and perhaps compile from source e.g. perhaps only :

1) apt-get install sl-modem-daemon

But perhaps :

2) apt-get install sl-modem-source

and compile.

Try 1) first.

---

### Post by Trexx on 2005-03-01
How would I compile? Thanks for the info! I'll try to driver thingy.

EDIT:
I did both, I got the same error on both. They were:

> 
E: Could not open lock file /var/lib/dpkg/lock
E: Unable to lock the administration directory (/var/lib/dpkg/) Are you root?


Is that because it's on the liveCD? 

Also, if it won't detect my modem, how is it supposed to install the drivers? J/w, thanks for the help!

---

### Post by alastair on 2005-03-04
Ooops ... I forgot you are on a Live CD. So you would need to keep any files you need on a persistent medium e.g. USB disk/key. Makes things a little more complex but ... you could still have a "build" directory (or .deb package + README/steps) on the USB disk.

As for the errors - try putting "sudo" in front of any commands you use to install things i.e.

sudo apt-get install sl-modem-daemon

---

### Post by Trexx on 2005-03-05
[QUOTE=alastair]Ooops ... I forgot you are on a Live CD. So you would need to keep any files you need on a persistent medium e.g. USB disk/key. Makes things a little more complex but ... you could still have a "build" directory (or .deb package + README/steps) on the USB disk.

As for the errors - try putting "sudo" in front of any commands you use to install things i.e.

sudo apt-get install sl-modem-daemon[/QUOTE]
 Thanks, I'll check that out in a while. Thanks for the help!

---


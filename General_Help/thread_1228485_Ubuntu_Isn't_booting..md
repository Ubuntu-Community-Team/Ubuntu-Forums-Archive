---
title: "Ubuntu Isn't booting."
date: 2009-08-01
forum: General Help
---

### Post by Raiju on 2009-08-01
i had a program hang in ubuntu(ndiswrapper), so i restarted the computer. while the computer was shutting down, it just stopped.(as the bar was loading)

so i had to hold my power button to cut my computer off.

when i tried to load ubuntu again, it would boot up.the screen with the status bar loads, then a prompt with text comes up. some text comes up but then it stops after this is said...

 *Enabling additional executable binary formats binfmt-support 
WANRING: all config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a furture release.
                                                                             [ok]
* checking battery state... [ok]
 

then it stops after that.

i can log in using recovery mode but i have no gui and i'm new to linux :(

any idea on how to get ubuntu up and running again?

---

### Post by ecmatter on 2009-08-01
If you type **startx** at the command line in recovery mode, you should get your gui back.

---

### Post by MaxIBoy on 2009-08-01
Boot into recovery mode. You should be given a menu. Try the options to "repair" the system.

If those don't work, boot up into recovery mode again. Then, try "apt-get install --reinstall initscripts" and then reboot, see if that works.

---

### Post by Raiju on 2009-08-01
> **MaxIBoy said:**
> Boot into recovery mode. You should be given a menu. Try the options to "repair" the system.

If those don't work, boot up into recovery mode again. Then, try "apt-get install --reinstall initscripts" and then reboot, see if that works.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package iniscripts
------
it didnt work

> **ecmatter said:**
> If you type **startx** at the command line in recovery mode, you should get your gui back.
  
startx didnt work :<

---

### Post by Raiju on 2009-08-01
BUMP!@


i am using a wireless card to connect to the internet, not sure if ubuntu connects when trying to download those packages in recovery mode

---

### Post by Bucky Ball on 2009-08-01
Try plugging in an ethernet cable if you can.

---

### Post by zkriesse on 2009-08-01
If you're having problems like that you need to stick the disk in and re-load the OS...sorry man

---

### Post by Buce on 2009-08-01
> E: Couldn't find package iniscripts

Note that 'initscripts' is the package you want, not 'iniscripts'.

If you're not sure whether you're connected to the internet or not, try:

```
ping google.com
```

If you get an 'unknown host' error, you're not connected.

---


---
title: "LightDM doesn't start automatically."
date: 2012-08-28
forum: General Help
---

### Post by Splooshie123 on 2012-08-28
When I booted into Ubuntu, it got stuck at the splash screen. However, I was able to the console, meaning the system had started, but lightdm had not. Had I not started lightdm manually from the console, it would have been stuck at the splash screen forever.

This is my /var/log/boot.log:
```
fsck from util-linux 2.20.1 
Ubuntu: clean, 379898/6553600 files, 10754588/26214400 blocks 
modem-manager[1093]: <info>  ModemManager (version 0.5.2.0) starting... 
  
modem-manager[1093]: <info>  Loaded plugin Sierra 
  
modem-manager[1093]: <info>  Loaded plugin Linktop 
  
modem-manager[1093]: <info>  Loaded plugin MotoC 
  
modem-manager[1093]: <info>  Loaded plugin Novatel 
  
modem-manager[1093]: <info>  Loaded plugin Samsung 
  
modem-manager[1093]: <info>  Loaded plugin Option 
  
modem-manager[1093]: <info>  Loaded plugin Option High-Speed 
  
modem-manager[1093]: <info>  Loaded plugin X22X 
  
modem-manager[1093]: <info>  Loaded plugin Generic 
  
modem-manager[1093]: <info>  Loaded plugin Ericsson MBM 
  
modem-manager[1093]: <info>  Loaded plugin Longcheer 
  
modem-manager[1093]: <info>  Loaded plugin Huawei 
  
modem-manager[1093]: <info>  Loaded plugin ZTE 
  
modem-manager[1093]: <info>  Loaded plugin Wavecom 
  
modem-manager[1093]: <info>  Loaded plugin Gobi 
  
modem-manager[1093]: <info>  Loaded plugin SimTech 
  
modem-manager[1093]: <info>  Loaded plugin Nokia 
  
modem-manager[1093]: <info>  Loaded plugin AnyData 
  
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd 
 * Starting mDNS/DNS-SD daemon[74G[ OK ] 
 * Stopping Mount filesystems on boot[74G[ OK ] 
 * Starting AppArmor profiles       [80G  [74G[ OK ] 
Rather than invoking init scripts through /etc/init.d, use the service(8) 
utility, e.g. service S20lightdm start 
 * Stopping System V initialisation compatibility[74G[ OK ] 
 * Starting System V runlevel compatibility[74G[ OK ] 
 * Starting automatic crash report generation[74G[ OK ] 
 * Starting restore sound card(s') mixer state(s)[74G[ OK ] 
 * Starting ACPI daemon[74G[ OK ] 
 * Starting save kernel messages[74G[ OK ] 
 * Starting anac(h)ronistic cron[74G[ OK ] 
initctl: Unknown job: S20lightdm 
 
Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the start(8) utility, e.g. start S20lightdm 
 * Starting CPU interrupts balancing daemon[74G[ OK ] 
 * Starting crash report submission daemon[74G[ OK ] 
speech-dispatcher disabled; edit /etc/default/speech-dispatcher 
 * Starting deferred execution scheduler[74G[ OK ] 
 * Starting regular background program processing daemon[74G[ OK ] 
 * Starting VirtualBox kernel modules       [80G  [74G[ OK ] 
 * Stopping anac(h)ronistic cron[74G[ OK ] 
 * Stopping save kernel messages[74G[ OK ] 
 * Stopping restore sound card(s') mixer state(s)[74G[ OK ] 
 * Starting the Winbind daemon winbind       [80G  [74G[ OK ] 
saned disabled; edit /etc/default/saned 
 * Stopping cold plug devices[74G[ OK ] 
 * Stopping log initial device creation[74G[ OK ] 
 * Starting load fallback graphics devices[74G[ OK ] 
 * Starting configure virtual network devices[74G[ OK ] 
 * Stopping load fallback graphics devices[74G[ OK ] 
 * Stopping configure virtual network devices[74G[ OK ] 
 * Starting configure network device security[74G[ OK ] 
 * Starting GNOME Display Manager[74G[ OK ] 
 * Starting Userspace bootsplash[74G[ OK ] 
 * Starting anac(h)ronistic cron[74G[ OK ] 
 * Stopping anac(h)ronistic cron[74G[ OK ] 
 * Stopping GNOME Display Manager[74G[ OK ] 
[B] * Starting LightDM Display Manager[74G[ OK ] 
 * Stopping LightDM Display Manager[74G[ OK ] 
 * Stopping Userspace bootsplash[74G[ OK ] 
[/B] * Checking battery state...       [160G  [154G[ OK ] 
 * Stopping System V runlevel compatibility[74G[ OK ] 
 * Starting CUPS printing spooler/server[74G[ OK ] 
 * Starting Mount network filesystems[74G[ OK ] 
 * Stopping Mount network filesystems[74G[ OK ]
```The bold messages show lightdm starting but then stopping again. After that is says it's stopping the splash screen, which never happens.

Any ideas?

Don't remember why I looked, but I found out that all the lightdm scripts in /etc/rc*.d have the K20 prefix (which means "disabled", apparently). Maybe this has something to do with it?

---

### Post by Splooshie123 on 2012-08-30
Fixed it. I installed GDM a few days ago and after removing it, /etc/X11/default-display-manager contained lightdm instead of /usr/sbin/lightdm.

---

### Post by dcstar on 2012-09-19
> **Splooshie123 said:**
> Fixed it. I installed GDM a few days ago and after removing it, /etc/X11/default-display-manager contained lightdm instead of /usr/sbin/lightdm.

Then report it as a bug or it may **never** get fixed.

---

### Post by hussam_nasir on 2012-10-26
This worked for me too. Please do report this a a bug . Only then will this be resolved.

---

### Post by Cavsfan on 2013-01-19
> **Splooshie123 said:**
> Fixed it. I installed GDM a few days ago and after removing it, /etc/X11/default-display-manager contained lightdm instead of /usr/sbin/lightdm.

I guess it is still not fixed.
This saved me too!
I installed gdm on Precise and almost lost the ability to get back into it.
Found where **sudo dpkg-reconfigure lightdm** would make lightdm work except it didn't.
Since recovery is to a read only file system I could not do anything there until I found something **Paddy Landau** had posted on a bug about it.
He said this was a workaround and it worked:
Login to recovery and then enter:

```
mount --options remount,rw /
mount --all
```So, then I was successfully able to enter **sudo dpkg-reconfigure lightdm** without getting an error. I also purged gdm.
But, upon bootup all it would do was have a black screen with 4 dots that turned yellow and would not go past that.
I discovered I could press ALT+F2 and get the login prompt. Then I could enter **sudo service lightdm start** and it would finally allow me to login to Precise normally. 
I knew that lightdm was there but, wasn't starting upon bootup.
That is when I found this thread.
Editing **/etc/X11/default-display-manager** saved me! Whew!
Thank you **Splooshie123**!

---

### Post by Lennaron on 2013-01-30
Thank you, helped a lot after some months with starting lightdm by alternate console ;-)

---

### Post by firekage on 2013-01-31
Heh, i have to admit that i didn't know about this, and the cause of this. It happened to me also - i installed, just like you, gdm, and after that i could not start lightdm even when gdm was purged, also my system, if i was succesful in starting lightdm, was started in low graphic mode - don't know why.

---

### Post by Cavsfan on 2013-02-01
> **firekage said:**
> Heh, i have to admit that i didn't know about this, and the cause of this. It happened to me also - i installed, just like you, gdm, and after that i could not start lightdm even when gdm was purged, also my system, if i was succesful in starting lightdm, was started in low graphic mode - don't know why.

Did you edit **/etc/X11/default-display-manager**?

**gksudo gedit /etc/X11/default-display-manager**
and make sure it contained /usr/sbin/lightdm and not just lightdm?

If it gives you read only access enter:
```
mount --options remount,rw /
mount --all
```
before hand. I had to write this stuff down when I did it.

---

### Post by firekage on 2013-02-04
> **Cavsfan said:**
> Did you edit **/etc/X11/default-display-manager**?

**gksudo gedit /etc/X11/default-display-manager**
and make sure it contained /usr/sbin/lightdm and not just lightdm?

If it gives you read only access enter:
```
mount --options remount,rw /
mount --all
```before hand. I had to write this stuff down when I did it.

No, i just reinstalled gdm and i've been using it because i didn't know why lightdm doesen;t want to work at all. 

Now i know. Thanks.

---

### Post by henriquev162 on 2013-11-17
Hello guys, please help me I'm having the same problem but my /etc/X11/default-display-manager have this line /usr/sbin/lightdm and my lightdm stills not starting automatically... I haven't installed GDM, I think this started to happen after my qShutdown installation...

---


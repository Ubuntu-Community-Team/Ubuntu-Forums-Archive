---
title: "Difficulty starting Ubuntu 10.10"
date: 2010-12-24
forum: General Help
---

### Post by Robbyx on 2010-12-24
I had a computer crash. Started the computer and it would not proceed beyond:

Starting preload
  Checking battery status
  Starting TIMidity ++ ALSA mid emulation
*At this point it hangs.*

Ctrl ALT F1 does allow me to login, start gdm and proceed to run Ubuntu.

What can  I do so that ubuntu loads without hanging?

---

### Post by Robbyx on 2010-12-25
I would very much appreciate some guidance on this boot up problem.

---

### Post by wojox on 2010-12-25
Open a terminal and run:

```
sudo touch /forcefsck 
```

And reboot. This should force a file systems check.

---

### Post by Robbyx on 2010-12-25
Unfortunately, the file check has not cured the problem. 

I have tried supergrub and that too made no difference.

I am lucky that I have found a way of starting but it is not the way it should be. It is not longer automatic. I have to exit from the login procedure and run some command lines as mentioned above. 

Can you suggest another approach to the cure?

Would a reinstall of ubuntu help. I understand that it is possible to do a repair if there is an operating system there.

---

### Post by wojox on 2010-12-25
What was it doing when it crashed? Updates, web surfing...?

---

### Post by Robbyx on 2010-12-26
> **wojox said:**
> What was it doing when it crashed? Updates, web surfing...?

I have had two problems recently:

1. I was doing a kernel update and it ceased doing the update just as it reached the grub update point. I took advice in another posting and I thought it had been resolved.

2. In the last few days I was using a program under wine. The window kept flashing and would not close. I forced it to close.

Robin

---

### Post by NightwishFan on 2010-12-26
Start Ubuntu in Recovery Mode. To do this hold shift after your bios, but before grub, you should see a menu, pick recovery mode (should be the second option). When you get to the menu choose the option that repairs packages, when that finishes, choose "netroot" if you are plugged into ethernet, root otherwise. Then run this command:
```
apt-get -f install && dpkg --configure -a
```

Then type this to reboot:
```
reboot
```

When you reboot, if your system still does not work, boot back into recovery mode and see if you can boot using  the "Failsafe X". If so then your problem is graphics related.

---

### Post by Robbyx on 2010-12-26
I have been unable to bring up the menu which lets me choose recovery mode. Nothing happens when I hold the shift key, as instructed.

Is there a way into the recovery mode via a command line?

---

### Post by NightwishFan on 2010-12-26
Recovery mode is just an option in the normal boot menu, holding shift is supposed to force the menu to appear. Try holding shift either a bit later, or a bit earlier than you already are.

---

### Post by Robbyx on 2010-12-26
> **NightwishFan said:**
> Recovery mode is just an option in the normal boot menu, holding shift is supposed to force the menu to appear. Try holding shift either a bit later, or a bit earlier than you already are.

Thank you. That worked.

When I get to the second menu with the netroot option, I find I can not choose anything. The up/down keys do not work on it. The mouse has no effect. What should I do to move around that second menu?

Robin

---

### Post by NightwishFan on 2010-12-26
Try just the root option, also, this option boots you to a command line, which you should run the command I specified:
```
apt-get -f install && dpkg --configure -a
```

This should fix any package conflicts or incomplete installs if that was the problem. When finished, reboot, and if this gets you to a desktop, great, if not we can work it out.

---

### Post by Robbyx on 2010-12-26
> **NightwishFan said:**
> Try just the root option, also, this option boots you to a command line, which you should run the command I specified:
```
apt-get -f install && dpkg --configure -a
```

This should fix any package conflicts or incomplete installs if that was the problem. When finished, reboot, and if this gets you to a desktop, great, if not we can work it out.

I am very handicapped by what I can do at the recovery menu. It defaults to continue to normal boot. I can not choose any other options. 

As a workaround I have tried the following:

1. Stage 1
    Repair using recovery mode.
    Reboot.
2. Stage 2
    Boot normally and then fall into the command line via ctrl alt F1.
     sudo apt-get -f install
     sudo dpkg --configure -a
3. Stage 3
     Reboot again.

Following the above has not improved the position. I still have to manually go into the gdm. 

I do not understand why the recovery menu is unresponsive. I have tried the serial mouse, usb mouse and various arrow keys on the keyboard.

Robin

---

### Post by NightwishFan on 2010-12-26
I see, it is actually unresponsive, ok, just to make sure, lets make sure all the required packages for Ubuntu are installed, run:
```
sudo apt-get --reinstall --install-recommends install ubuntu-desktop
```

Also run:
```
sudo dpkg-reconfigure gdm
```

Then perhaps you should give us the /var/log/syslog here, if possible. Either copy to a flash drive, or grab it from a live cd by mounting your Ubuntu drive. To upload here, either put CODE tags around it, or make it a tar.gz file and upload as an attachment.

---

### Post by Robbyx on 2010-12-26
> **NightwishFan said:**
> I see, it is actually unresponsive, ok, just to make sure, lets make sure all the required packages for Ubuntu are installed, run:
```
sudo apt-get --reinstall --install-recommends install ubuntu-desktop
```

Also run:
```
sudo dpkg-reconfigure gdm
```

I did both of the above commands, from within gdm of ubuntu. On restarting I found they had made no difference to the start up problem. To remind you, when I boot Ubuntu it gets to the prechecks and then stops.

Is there an option that steps through the startup script so that  I can report where it is halting?

> Then perhaps you should give us the /var/log/syslog here, if possible. Either copy to a flash drive, or grab it from a live cd by mounting your Ubuntu drive. To upload here, either put CODE tags around it, or make it a tar.gz file and upload as an attachment.


I tried to access the syslog from within the GDM and found that gedit could not detect the character coding and would not open the file. Do I have to access it from outside of the gdm, in order to copy the contents?

---

### Post by NightwishFan on 2010-12-26
You might need to have a live CD available to do this, or try to copy it from a flash drive. It is key to figuring this out. You could also try opening the system log viewer as well. The command is gnome-system-log. GDM is an unprivileged user, so it might have trouble using certain apps.

Edit: I have to go, so I hope someone can help you until I return. *Though I have been useless too..*

---

### Post by wojox on 2010-12-26
You should be able to open a terminal and type:

```
cat /var/log/syslog
```

And copy and paste the contents up here.

---

### Post by Robbyx on 2010-12-26
```
Dec 26 19:17:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:17:25 robin kernel: [ 7607.726672] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:17:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:17:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:17:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:18:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:18:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:18:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:18:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:18:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:18:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:18:37 robin kernel: [ 7679.735340] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
Dec 26 19:18:55 robin kernel: [ 7697.373857] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=46 
Dec 26 19:18:55 robin kernel: [ 7697.378583] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=29 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=9 
Dec 26 19:19:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:19:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:19:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:19:18 robin kernel: [ 7720.727692] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
Dec 26 19:19:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:19:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:19:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:19:37 robin kernel: [ 7738.959989] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:20:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:20:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:20:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:20:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:20:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:20:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:21:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:21:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:21:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:21:03 robin kernel: [ 7825.338229] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
Dec 26 19:21:09 robin kernel: [ 7831.591254] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
Dec 26 19:21:30 robin kernel: [ 7852.747729] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
Dec 26 19:21:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:21:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:21:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:21:58 robin kernel: [ 7879.992340] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:22:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:22:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:22:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:22:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:22:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:22:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:23:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:23:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:23:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:23:18 robin kernel: [ 7960.720892] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=46 
Dec 26 19:23:18 robin kernel: [ 7960.726134] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=29 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=9 
Dec 26 19:23:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:23:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:23:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:24:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:24:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:24:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:24:24 robin kernel: [ 8026.239115] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=46 
Dec 26 19:24:24 robin kernel: [ 8026.241226] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=29 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=9 
Dec 26 19:24:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:24:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:24:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:25:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:25:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:25:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:25:23 robin kernel: [ 8084.974078] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
Dec 26 19:25:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:25:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:25:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:26:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:26:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:26:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:26:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:26:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:26:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:27:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:27:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:27:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:27:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:27:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:27:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:28:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:28:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:28:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:28:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:28:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:28:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:29:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:29:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:29:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:29:14 robin kernel: [ 8316.425083] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=49282 WINDOW=0 RES=0x00 RST URGP=0 
Dec 26 19:29:14 robin kernel: [ 8316.545103] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=49281 WINDOW=0 RES=0x00 RST URGP=0 
Dec 26 19:29:21 robin kernel: [ 8323.225633] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=49282 WINDOW=0 RES=0x00 RST URGP=0 
Dec 26 19:29:21 robin kernel: [ 8323.466532] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=49281 WINDOW=0 RES=0x00 RST URGP=0 
Dec 26 19:29:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:29:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:29:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:29:35 robin kernel: [ 8337.321942] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=49281 WINDOW=0 RES=0x00 RST URGP=0 
Dec 26 19:30:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:30:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:30:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:30:03 robin kernel: [ 8365.034852] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=49281 WINDOW=0 RES=0x00 RST URGP=0 
Dec 26 19:30:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:30:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:30:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:31:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:31:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:31:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:31:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:31:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:31:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:31:41 robin kernel: [ 8462.962458] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:32:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:32:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:32:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:32:04 robin kernel: [ 8486.142477] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=80.219.53.79 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=113 ID=22723 PROTO=UDP SPT=7150 DPT=7571 LEN=46 
Dec 26 19:32:04 robin kernel: [ 8486.142498] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=80.219.53.79 DST=192.168.1.64 LEN=29 TOS=0x00 PREC=0x00 TTL=113 ID=22724 DF PROTO=UDP SPT=7150 DPT=7571 LEN=9 
Dec 26 19:32:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:32:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:32:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:32:37 robin kernel: [ 8519.693459] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:32:40 robin kernel: [ 8522.371929] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:32:53 robin kernel: [ 8535.574910] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:33:01 robin kernel: [ 8543.761296] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:33:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:33:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:33:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:33:12 robin kernel: [ 8554.432543] usb 3-1: USB disconnect, address 2
Dec 26 19:33:12 robin kernel: [ 8554.432546] usb 3-1.1: USB disconnect, address 3
Dec 26 19:33:19 robin kernel: [ 8561.760017] usb 3-1: new full speed USB device using uhci_hcd and address 5
Dec 26 19:33:20 robin kernel: [ 8561.929593] pl2303 3-1:1.0: pl2303 converter detected
Dec 26 19:33:20 robin kernel: [ 8561.941889] usb 3-1: pl2303 converter now attached to ttyUSB0
Dec 26 19:33:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:33:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:33:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:33:39 robin kernel: [ 8581.772047] usb 5-2: new full speed USB device using uhci_hcd and address 2
Dec 26 19:33:40 robin kernel: [ 8581.957582] hub 5-2:1.0: USB hub found
Dec 26 19:33:40 robin kernel: [ 8581.959971] hub 5-2:1.0: 4 ports detected
Dec 26 19:33:40 robin kernel: [ 8582.241574] usb 5-2.1: new full speed USB device using uhci_hcd and address 3
Dec 26 19:33:40 robin kernel: [ 8582.488643] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
Dec 26 19:33:40 robin kernel: [ 8582.524687] input: UVC Camera (046d:0990) as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2.1/5-2.1:1.0/input/input9
Dec 26 19:33:41 robin rtkit-daemon[5053]: Successfully made thread 23299 of process 7949 (n/a) owned by '1001' RT at priority 5.
Dec 26 19:33:41 robin rtkit-daemon[5053]: Supervising 3 threads of 1 processes of 1 users.
Dec 26 19:33:42 robin kernel: [ 8584.312252] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
Dec 26 19:33:52 robin kernel: [ 8594.626123] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=80.219.53.79 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=113 ID=20579 PROTO=UDP SPT=7150 DPT=7571 LEN=46 
Dec 26 19:33:52 robin kernel: [ 8594.626144] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=80.219.53.79 DST=192.168.1.64 LEN=29 TOS=0x00 PREC=0x00 TTL=113 ID=20580 DF PROTO=UDP SPT=7150 DPT=7571 LEN=9 
Dec 26 19:33:59 robin kernel: [ 8600.931969] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
Dec 26 19:34:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:34:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:34:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:34:03 robin kernel: [ 8605.397171] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:34:13 robin kernel: [ 8615.305185] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:34:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:34:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:34:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:35:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:35:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:35:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:35:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:35:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:35:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:36:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:36:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:36:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:36:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:36:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:36:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:37:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:37:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:37:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:37:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:37:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:37:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:38:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:38:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:38:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:38:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:38:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:38:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:39:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:39:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:39:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:39:28 robin kernel: [ 8930.237725] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
Dec 26 19:39:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:39:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:39:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:39:33 robin kernel: [ 8935.431253] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:39:41 robin kernel: [ 8943.202427] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:40:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:40:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:40:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:40:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:40:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:40:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:41:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:41:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:41:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:41:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:41:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:41:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:42:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:42:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:42:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:42:31 robin kernel: [ 9113.573177] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:42:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:42:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:42:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:43:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:43:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:43:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:43:09 robin kernel: [ 9150.907041] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:43:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:43:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:43:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:43:36 robin kernel: [ 9178.078263] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:44:00 robin acpid: client connected from 12393[114:123]
Dec 26 19:44:00 robin acpid: 1 client rule loaded
Dec 26 19:44:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:44:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:44:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:44:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:44:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:44:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:44:35 robin kernel: [ 9237.657236] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
Dec 26 19:45:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:45:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:45:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:45:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:45:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:45:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:45:37 robin kernel: [ 9298.976351] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
Dec 26 19:45:43 robin kernel: [ 9305.371682] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
Dec 26 19:45:44 robin kernel: [ 9305.871274] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
Dec 26 19:45:44 robin kernel: [ 9306.371117] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
Dec 26 19:45:45 robin kernel: [ 9306.871676] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
Dec 26 19:45:45 robin kernel: [ 9307.374974] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
Dec 26 19:45:46 robin kernel: [ 9307.872535] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
Dec 26 19:45:46 robin kernel: [ 9308.373276] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
Dec 26 19:45:47 robin kernel: [ 9308.869063] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=192.168.1.254 DST=192.168.1.64 LEN=338 TOS=0x00 PREC=0x00 TTL=64 ID=24808 PROTO=UDP SPT=1900 DPT=1901 LEN=318 
Dec 26 19:46:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:46:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:46:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:46:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:46:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:46:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:46:39 robin kernel: [ 9361.372837] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
Dec 26 19:47:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:47:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:47:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:47:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:47:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:47:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:48:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:48:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:48:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:48:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:48:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:48:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:49:02 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:49:02 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:49:02 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
Dec 26 19:49:32 robin gammu-smsd[1278]: Starting phone communication...
Dec 26 19:49:32 robin gammu-smsd[1278]: Error at init connection: Error opening device, it doesn't exist. (DEVICENOTEXIST[4])
Dec 26 19:49:32 robin gammu-smsd[1278]: Going to 30 seconds sleep because of too much connection errors
 
```

---

### Post by NightwishFan on 2010-12-26
This output makes me think that your disk is either failing or you recently changed the disk layout somehow. You may just need to backup and reinstall if it is not.

Also @ using cat on the log... >_> I am tired for not mentioning that I use cat daily.

---

### Post by Robbyx on 2010-12-26
Is there a way of me checking the disk's stability?

---

### Post by Robbyx on 2010-12-26
> **NightwishFan said:**
> This output makes me think that your disk is either failing or you recently changed the disk layout somehow. You may just need to backup and reinstall if it is not.

Also @ using cat on the log... >_> I am tired for not mentioning that I use cat daily.

I thought most of the errors were directly related my attempts to access my mobile phone via a usb connection. Apart from them did you see other warning signs of impending failure?

---

### Post by Robbyx on 2010-12-26
Is it true that if I boot from the live cd and opt to install it will do a repair?

---

### Post by NightwishFan on 2010-12-26
No, the repair is done via recovery mode, and it is not automated. Also, my mistake, it appears smsd is not a device name but indeed the mobile phone. Strange, perhaps post the output of the command dmesg instead of the log, as this log seems to be incomplete, try this:
```
dmesg | less
```

---

### Post by Robbyx on 2010-12-26
```
0.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[ 4698.935066] r8169 0000:04:00.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100407)
[ 4698.935111] 3w-xxxx 0000:05:00.0: restoring config space at offset 0xf (was 0x90100, writing 0x9010a)
[ 4698.935123] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x6 (was 0x0, writing 0xfb000000)
[ 4698.935127] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x5 (was 0x0, writing 0xfbc00000)
[ 4698.935130] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xd001)
[ 4698.935134] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x2008)
[ 4698.935139] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00003)
[ 4698.935154] pci 0000:05:01.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 4698.935168] pci 0000:05:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xfb800000)
[ 4698.935172] pci 0000:05:01.0: restoring config space at offset 0x3 (was 0x0, writing 0x2008)
[ 4698.935177] pci 0000:05:01.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900007)
[ 4698.935235] PM: early resume of devices complete after 0.910 msecs
[ 4698.935395] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4698.935400] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 4698.935418] usb usb3: root hub lost power or was reset
[ 4698.935435] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 4698.935440] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 4698.935456] usb usb4: root hub lost power or was reset
[ 4698.935471] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 4698.935476] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[ 4698.935492] usb usb5: root hub lost power or was reset
[ 4698.935507] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 4698.935511] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 4698.935541] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 4698.935545] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 4698.935571] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[ 4698.935600] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 4698.935604] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 4698.935616] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 4698.935623] usb usb6: root hub lost power or was reset
[ 4698.935624] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 4698.935638] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 4698.935644] usb usb7: root hub lost power or was reset
[ 4698.935646] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 4698.935661] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 4698.935665] usb usb8: root hub lost power or was reset
[ 4698.935667] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 4698.935681] pci 0000:00:1e.0: setting latency timer to 64
[ 4698.935688] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 4698.935694] ata_piix 0000:00:1f.2: setting latency timer to 64
[ 4698.935698] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 4698.935701] ata_piix 0000:00:1f.5: setting latency timer to 64
[ 4698.935705] [drm] nouveau 0000:01:00.0: We're back, enabling device...
[ 4698.935709] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4698.935713] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 4698.935716] nouveau 0000:01:00.0: setting latency timer to 64
[ 4698.935718] [drm] nouveau 0000:01:00.0: POSTing device...
[ 4698.935720] pata_jmicron 0000:03:00.0: setting latency timer to 64
[ 4698.935722] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xDF5D
[ 4698.935734] pcieport 0000:00:1c.4: wake-up capability disabled by ACPI
[ 4698.935738] r8169 0000:04:00.0: PME# disabled
[ 4698.935743] 3w-xxxx 0000:05:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 4698.935793] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xE59E
[ 4698.935890] sd 3:0:0:0: [sda] Starting disk
[ 4698.938257] serial 00:07: activated
[ 4698.938823] parport_pc 00:08: activated
[ 4698.984031] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xECAF
[ 4698.984112] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xEE2F
[ 4699.008017] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xF01D
[ 4699.008020] [drm] nouveau 0000:01:00.0: Reinitialising engines...
[ 4699.008080] [drm] nouveau 0000:01:00.0: Restoring GPU objects...
[ 4699.022436] [drm] nouveau 0000:01:00.0: Restoring mode...
[ 4699.022479] [drm] nouveau 0000:01:00.0: 0xD359: Parsing digital output script table
[ 4699.076519] PM: resume of drv:usb dev:usb8 complete after 140.651 msecs
[ 4699.076526] PM: resume of drv:hub dev:8-0:1.0 complete after 140.646 msecs
[ 4699.076534] PM: resume of drv:usb dev:usb5 complete after 140.710 msecs
[ 4699.076539] PM: resume of drv:hub dev:5-0:1.0 complete after 140.713 msecs
[ 4699.076546] PM: resume of drv:usb dev:usb6 complete after 140.718 msecs
[ 4699.076563] PM: resume of drv:usb dev:usb7 complete after 140.718 msecs
[ 4699.076566] PM: resume of drv:hub dev:6-0:1.0 complete after 140.735 msecs
[ 4699.076571] PM: resume of drv:hub dev:7-0:1.0 complete after 140.714 msecs
[ 4699.076591] [drm] nouveau 0000:01:00.0: 0xD3A2: Parsing digital output script table
[ 4699.132859] [drm] nouveau 0000:01:00.0: Restoring CRTC_OWNER to 0.
[ 4699.139764] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[ 4699.139767] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[ 4699.139769] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 2)
[ 4699.139771] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 4)
[ 4699.159866] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
[ 4699.159868] [drm] nouveau 0000:01:00.0: 0xD359: Parsing digital output script table
[ 4699.180508] PM: resume of drv:usb dev:usb4 complete after 244.688 msecs
[ 4699.180516] PM: resume of drv:hub dev:4-0:1.0 complete after 244.692 msecs
[ 4699.180548] PM: resume of drv:usb dev:usb3 complete after 244.731 msecs
[ 4699.180554] PM: resume of drv:hub dev:3-0:1.0 complete after 244.735 msecs
[ 4699.180560] PM: resume of drv: dev:ep_81 complete after 192.530 msecs
[ 4699.212511] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
[ 4699.212514] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
[ 4699.212518] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 3)
[ 4699.232619] [drm] nouveau 0000:01:00.0: Output DVI-I-2 is running on CRTC 1 using output C
[ 4699.232621] [drm] nouveau 0000:01:00.0: 0xD3A2: Parsing digital output script table
[ 4699.270584] ata2: SATA link down (SStatus 4 SControl 300)
[ 4699.271292] ata3: SATA link down (SStatus 4 SControl 300)
[ 4699.281889] ata1: SATA link down (SStatus 4 SControl 300)
[ 4699.282431] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 4699.282433] ata5.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
[ 4699.288510] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 3)
[ 4699.288513] [drm] nouveau 0000:01:00.0: Output DVI-I-2 is running on CRTC 1 using output C
[ 4699.288518] PM: resume of drv:nouveau dev:0000:01:00.0 complete after 352.813 msecs
[ 4699.297058] ata5.00: configured for UDMA/66
[ 4699.440509] usb 4-2: reset low speed USB device using uhci_hcd and address 3
[ 4699.746938] psmouse serio1: ID: 10 00 64
[ 4699.807068] logips2pp: Detected unknown logitech mouse model 116
[ 4699.812585] PM: resume of drv:usb dev:4-2 complete after 876.616 msecs
[ 4699.812592] PM: resume of drv:usbhid dev:4-2:1.0 complete after 876.613 msecs
[ 4699.868508] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[ 4700.124509] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[ 4700.140605] PM: resume of drv:usb dev:4-1 complete after 1204.654 msecs
[ 4700.140611] PM: resume of drv:hub dev:4-1:1.0 complete after 1204.651 msecs
[ 4700.500008] PM: resume of drv:usb dev:3-1 complete after 1564.077 msecs
[ 4700.500017] PM: resume of drv:hub dev:3-1:1.0 complete after 1564.075 msecs
[ 4700.581620] usb 3-1.3: reset full speed USB device using uhci_hcd and address 4
[ 4700.699626] pl2303 3-1.3:1.0: no reset_resume for driver pl2303?
[ 4700.699705] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[ 4700.699720] pl2303 3-1.3:1.0: device disconnected
[ 4700.699725] PM: resume of drv:usb dev:3-1.3 complete after 1763.689 msecs
[ 4700.699731] PM: resume of drv:usb dev:3-1.3:1.0 complete after 1763.685 msecs
[ 4700.768631] usb 3-1.1: reset full speed USB device using uhci_hcd and address 3
[ 4701.016649] snd-usb-audio 3-1.1:1.2: no reset_resume for driver snd-usb-audio?
[ 4701.016652] snd-usb-audio 3-1.1:1.3: no reset_resume for driver snd-usb-audio?
[ 4701.016778] PM: resume of drv:usb dev:3-1.1 complete after 2080.791 msecs
[ 4701.016788] PM: resume of drv:uvcvideo dev:3-1.1:1.0 complete after 2080.791 msecs
[ 4701.016791] PM: resume of drv:usb dev:3-1.1:1.2 complete after 2080.773 msecs
[ 4701.016793] PM: resume of drv:uvcvideo dev:3-1.1:1.1 complete after 2080.787 msecs
[ 4701.016797] PM: resume of drv:usb dev:3-1.1:1.3 complete after 2080.771 msecs
[ 4704.464508] ata4: link is slow to respond, please be patient (ready=0)
[ 4706.816541] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 4706.840624] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[ 4706.840628] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[ 4706.840632] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 4706.856248] ata4.00: configured for UDMA/133
[ 4706.864304] PM: resume of drv:sd dev:3:0:0:0 complete after 7928.413 msecs
[ 4706.864312] PM: resume of drv:scsi_device dev:3:0:0:0 complete after 7928.395 msecs
[ 4706.864316] PM: resume of drv:scsi_disk dev:3:0:0:0 complete after 7683.684 msecs
[ 4706.864389] PM: resume of devices complete after 7929.126 msecs
[ 4706.864492] pl2303 3-1.3:1.0: pl2303 converter detected
[ 4706.876074] usb 3-1.3: pl2303 converter now attached to ttyUSB0
[ 4707.274289] PM: resume devices took 8.340 seconds
[ 4707.274323] PM: Finishing wakeup.
[ 4707.274324] Restarting tasks ... done.
[ 4707.520051] r8169 0000:04:00.0: eth0: link up
[ 4707.520058] r8169 0000:04:00.0: eth0: link up
[ 4708.306605] 3w-xxxx: scsi6: Unknown scsi opcode: 0x85
[ 4708.306624] 3w-xxxx: scsi6: Unknown scsi opcode: 0x85
[ 4715.595094] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=48364 WINDOW=0 RES=0x00 RST URGP=0 
[ 4715.757304] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=48363 WINDOW=0 RES=0x00 RST URGP=0 
[ 4717.381994] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 4717.880816] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 4718.304506] eth0: no IPv6 routers present
[ 4718.379415] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 4718.879828] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 4719.380342] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 4719.879688] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 4720.382577] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 4720.863927] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=192.168.1.254 DST=192.168.1.64 LEN=338 TOS=0x00 PREC=0x00 TTL=64 ID=23228 PROTO=UDP SPT=1900 DPT=1901 LEN=318 
[ 4722.395084] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=48364 WINDOW=0 RES=0x00 RST URGP=0 
[ 4722.681920] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=48363 WINDOW=0 RES=0x00 RST URGP=0 
[ 4736.554562] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=48363 WINDOW=0 RES=0x00 RST URGP=0 
[ 4740.988022] Corrupted low memory at c000e11c (e11c phys) = 00004000
[ 4740.988028] ------------[ cut here ]------------
[ 4740.988034] WARNING: at /build/buildd/linux-2.6.35/arch/x86/kernel/check.c:134 check_for_bios_corruption+0xcb/0xe0()
[ 4740.988036] Hardware name: EP35-DS3L
[ 4740.988037] Memory corruption detected in low memory
[ 4740.988039] Modules linked in: binfmt_misc vboxnetadp vboxnetflt vboxdrv reiserfs ipt_REJECT ipt_LOG xt_limit xt_tcpudp ipt_addrtype xt_state snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_usb_audio ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_nat nf_conntrack_ipv4 snd_hwdep snd_pcm nf_defrag_ipv4 snd_usbmidi_lib uvcvideo nf_conntrack_ftp videodev nf_conntrack snd_seq_midi v4l1_compat pl2303 snd_rawmidi ppdev nouveau ttm drm_kms_helper drm usbhid lp usbserial snd_seq_midi_event iptable_filter snd_seq snd_timer snd_seq_device intel_agp agpgart hid ip_tables x_tables psmouse parport_pc i2c_algo_bit parport serio_raw snd soundcore snd_page_alloc 3w_xxxx r8169 mii pata_jmicron
[ 4740.988084] Pid: 9, comm: events/0 Not tainted 2.6.35-24-generic-pae #42-Ubuntu
[ 4740.988086] Call Trace:
[ 4740.988091]  [<c0152862>] warn_slowpath_common+0x72/0xa0
[ 4740.988095]  [<c0133cdb>] ? check_for_bios_corruption+0xcb/0xe0
[ 4740.988097]  [<c0133cdb>] ? check_for_bios_corruption+0xcb/0xe0
[ 4740.988100]  [<c0152933>] warn_slowpath_fmt+0x33/0x40
[ 4740.988103]  [<c0133cdb>] check_for_bios_corruption+0xcb/0xe0
[ 4740.988105]  [<c0133cfd>] check_corruption+0xd/0x30
[ 4740.988109]  [<c0169dee>] run_workqueue+0x8e/0x150
[ 4740.988111]  [<c0133cf0>] ? check_corruption+0x0/0x30
[ 4740.988114]  [<c0169f34>] worker_thread+0x84/0xe0
[ 4740.988117]  [<c016e1b0>] ? autoremove_wake_function+0x0/0x50
[ 4740.988120]  [<c0169eb0>] ? worker_thread+0x0/0xe0
[ 4740.988122]  [<c016dd84>] kthread+0x74/0x80
[ 4740.988125]  [<c016dd10>] ? kthread+0x0/0x80
[ 4740.988127]  [<c010993e>] kernel_thread_helper+0x6/0x10
[ 4740.988129] ---[ end trace 7531e7880ab3c6da ]---
[ 4764.265653] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=48363 WINDOW=0 RES=0x00 RST URGP=0 
[ 4768.096534] sd 6:0:0:0: WARNING: Command (0x28) timed out, resetting card.
[ 5598.206155] Bluetooth: Core ver 2.15
[ 5598.206178] NET: Registered protocol family 31
[ 5598.206180] Bluetooth: HCI device and connection manager initialized
[ 5598.206183] Bluetooth: HCI socket layer initialized
[ 5607.102478] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=29 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=9 
[ 5705.385504] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 5705.885608] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 5706.386083] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 5706.888171] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 5707.385080] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 5707.886496] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 5708.384738] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 5708.869888] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=192.168.1.254 DST=192.168.1.64 LEN=338 TOS=0x00 PREC=0x00 TTL=64 ID=23804 PROTO=UDP SPT=1900 DPT=1901 LEN=318 
[ 5766.284324] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 5859.628532] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 6027.813771] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 6110.151329] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 6302.148344] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 6418.086529] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=80.129.144.58 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=115 ID=38248 PROTO=UDP SPT=7199 DPT=7571 LEN=46 
[ 6462.459622] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 6515.497491] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=38670 WINDOW=0 RES=0x00 RST URGP=0 
[ 6515.500288] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=38671 WINDOW=0 RES=0x00 RST URGP=0 
[ 6522.425755] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=38670 WINDOW=0 RES=0x00 RST URGP=0 
[ 6522.426874] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=38671 WINDOW=0 RES=0x00 RST URGP=0 
[ 6536.299593] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=38671 WINDOW=0 RES=0x00 RST URGP=0 
[ 6564.011461] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=38671 WINDOW=0 RES=0x00 RST URGP=0 
[ 6785.489582] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 7059.137669] usb 4-1.4: new full speed USB device using uhci_hcd and address 4
[ 7059.336674] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1.4/4-1.4:1.3/input/input5
[ 7059.336757] generic-usb 0003:0D8C:000C.0002: input,hidraw1: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1a.1-1.4/input3
[ 7059.479612] 4:1:1: usb_set_interface failed
[ 7059.480618] 4:1:1: usb_set_interface failed
[ 7059.481605] 4:1:1: usb_set_interface failed
[ 7059.482610] 4:1:1: usb_set_interface failed
[ 7059.483611] 4:1:1: usb_set_interface failed
[ 7059.484624] 4:1:1: usb_set_interface failed
[ 7059.485617] 4:1:1: usb_set_interface failed
[ 7059.486709] 4:1:1: usb_set_interface failed
[ 7059.487607] 4:1:1: usb_set_interface failed
[ 7059.488515] 4:1:1: usb_set_interface failed
[ 7059.492244] 4:1:1: usb_set_interface failed
[ 7059.493631] 4:1:1: usb_set_interface failed
[ 7059.494698] 4:1:1: usb_set_interface failed
[ 7059.495607] 4:1:1: usb_set_interface failed
[ 7059.496639] 4:1:1: usb_set_interface failed
[ 7059.498606] 4:1:1: usb_set_interface failed
[ 7059.499964] 4:1:1: usb_set_interface failed
[ 7059.500606] 4:1:1: usb_set_interface failed
[ 7059.501604] 4:1:1: usb_set_interface failed
[ 7059.502665] 4:1:1: usb_set_interface failed
[ 7059.503605] 4:1:1: usb_set_interface failed
[ 7059.504605] 4:1:1: usb_set_interface failed
[ 7059.505604] 4:1:1: usb_set_interface failed
[ 7059.506608] 4:1:1: usb_set_interface failed
[ 7059.507606] 4:1:1: usb_set_interface failed
[ 7059.508605] 4:1:1: usb_set_interface failed
[ 7059.509608] 4:1:1: usb_set_interface failed
[ 7059.510605] 4:1:1: usb_set_interface failed
[ 7059.512605] 4:1:1: usb_set_interface failed
[ 7059.513604] 4:1:1: usb_set_interface failed
[ 7059.514606] 4:1:1: usb_set_interface failed
[ 7059.515605] 4:1:1: usb_set_interface failed
[ 7059.516719] 4:1:1: usb_set_interface failed
[ 7059.517607] 4:1:1: usb_set_interface failed
[ 7059.518609] 4:1:1: usb_set_interface failed
[ 7059.521474] 4:1:1: usb_set_interface failed
[ 7059.522607] 4:1:1: usb_set_interface failed
[ 7059.523606] 4:1:1: usb_set_interface failed
[ 7059.524606] 4:1:1: usb_set_interface failed
[ 7059.525606] 4:1:1: usb_set_interface failed
[ 7059.526607] 4:1:1: usb_set_interface failed
[ 7059.527607] 4:1:1: usb_set_interface failed
[ 7059.528607] 4:1:1: usb_set_interface failed
[ 7059.529606] 4:1:1: usb_set_interface failed
[ 7059.530607] 4:1:1: usb_set_interface failed
[ 7059.531607] 4:1:1: usb_set_interface failed
[ 7059.532606] 4:1:1: usb_set_interface failed
[ 7059.533607] 4:1:1: usb_set_interface failed
[ 7059.534610] 4:1:1: usb_set_interface failed
[ 7059.535608] 4:1:1: usb_set_interface failed
[ 7059.536606] 4:1:1: usb_set_interface failed
[ 7059.537604] 4:1:1: usb_set_interface failed
[ 7059.538604] 4:1:1: usb_set_interface failed
[ 7059.539604] 4:1:1: usb_set_interface failed
[ 7059.540628] 4:1:1: usb_set_interface failed
[ 7059.541609] 4:1:1: usb_set_interface failed
[ 7059.542606] 4:1:1: usb_set_interface failed
[ 7059.543607] 4:1:1: usb_set_interface failed
[ 7059.544608] 4:1:1: usb_set_interface failed
[ 7059.545608] 4:1:1: usb_set_interface failed
[ 7059.546682] 4:1:1: usb_set_interface failed
[ 7059.547606] 4:1:1: usb_set_interface failed
[ 7059.548607] 4:1:1: usb_set_interface failed
[ 7059.549606] 4:1:1: usb_set_interface failed
[ 7059.550619] 4:1:1: usb_set_interface failed
[ 7059.551614] 4:1:1: usb_set_interface failed
[ 7059.552612] 4:1:1: usb_set_interface failed
[ 7059.553610] usb 4-1.4: USB disconnect, address 4
[ 7059.553614] 4:1:1: usb_set_interface failed
[ 7059.553800] 4:1:1: usb_set_interface failed
[ 7059.553990] 4:1:1: usb_set_interface failed
[ 7059.554545] 4:1:1: usb_set_interface failed
[ 7059.554575] 4:1:1: usb_set_interface failed
[ 7059.554659] 4:1:1: usb_set_interface failed
[ 7059.554871] 4:1:1: usb_set_interface failed
[ 7059.555102] 4:1:1: usb_set_interface failed
[ 7059.555807] 4:1:1: usb_set_interface failed
[ 7059.555838] 4:1:1: usb_set_interface failed
[ 7059.555922] 4:1:1: usb_set_interface failed
[ 7059.556160] 4:1:1: usb_set_interface failed
[ 7059.556403] 4:1:1: usb_set_interface failed
[ 7059.556854] 4:1:1: usb_set_interface failed
[ 7059.556871] 4:1:1: usb_set_interface failed
[ 7059.556894] 4:1:1: usb_set_interface failed
[ 7059.557068] 4:1:1: usb_set_interface failed
[ 7059.557267] 4:1:1: usb_set_interface failed
[ 7059.557706] 4:1:1: usb_set_interface failed
[ 7059.557722] 4:1:1: usb_set_interface failed
[ 7059.557747] 4:1:1: usb_set_interface failed
[ 7059.557915] 4:1:1: usb_set_interface failed
[ 7059.558101] 4:1:1: usb_set_interface failed
[ 7059.558626] 4:1:1: usb_set_interface failed
[ 7059.558657] 4:1:1: usb_set_interface failed
[ 7059.558734] 4:1:1: usb_set_interface failed
[ 7059.558946] 4:1:1: usb_set_interface failed
[ 7059.559177] 4:1:1: usb_set_interface failed
[ 7059.559877] 4:1:1: usb_set_interface failed
[ 7059.559909] 4:1:1: usb_set_interface failed
[ 7059.559992] 4:1:1: usb_set_interface failed
[ 7060.282657] usb 4-1.4: new full speed USB device using uhci_hcd and address 5
[ 7060.385660] usb 4-1.4: device descriptor read/64, error -71
[ 7060.589675] usb 4-1.4: device descriptor read/64, error -71
[ 7060.781687] usb 4-1.4: new full speed USB device using uhci_hcd and address 6
[ 7060.982527] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1.4/4-1.4:1.3/input/input6
[ 7060.982604] generic-usb 0003:0D8C:000C.0003: input,hidraw1: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1a.1-1.4/input3
[ 7061.472721] usb 4-1.4: USB disconnect, address 6
[ 7061.473739] cannot submit datapipe for urb 0, error -19: no device
[ 7061.476015] cannot submit datapipe for urb 0, error -19: no device
[ 7062.013754] usb 4-1.4: new full speed USB device using uhci_hcd and address 7
[ 7062.208817] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1.4/4-1.4:1.3/input/input7
[ 7062.208875] generic-usb 0003:0D8C:000C.0004: input,hidraw1: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1a.1-1.4/input3
[ 7078.755711] usb 4-1.4: USB disconnect, address 7
[ 7078.989725] usb 4-1.4: new full speed USB device using uhci_hcd and address 8
[ 7079.184807] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1.4/4-1.4:1.3/input/input8
[ 7079.184885] generic-usb 0003:0D8C:000C.0005: input,hidraw1: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1a.1-1.4/input3
[ 7102.636215] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 7137.294053] usb 3-1.3: USB disconnect, address 4
[ 7137.294181] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[ 7137.294198] pl2303 3-1.3:1.0: device disconnected
[ 7214.994070] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=46 
[ 7214.997690] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=29 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=9 
[ 7218.435665] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 7262.001346] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 7302.242548] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 7332.515583] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 7505.373449] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 7505.871751] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 7506.372128] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 7506.872154] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 7507.372637] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 7507.873090] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 7508.372215] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 7508.854451] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=192.168.1.254 DST=192.168.1.64 LEN=338 TOS=0x00 PREC=0x00 TTL=64 ID=24084 PROTO=UDP SPT=1900 DPT=1901 LEN=318 
[ 7510.800691] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 7572.269175] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 7607.726672] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 7679.735340] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 7697.373857] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=46 
[ 7697.378583] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=29 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=9 
[ 7720.727692] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 7738.959989] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 7825.338229] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 7831.591254] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 7852.747729] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 7879.992340] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 7960.720892] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=46 
[ 7960.726134] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=29 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=9 
[ 8026.239115] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=46 
[ 8026.241226] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=174.95.245.43 DST=192.168.1.64 LEN=29 TOS=0x00 PREC=0x20 TTL=53 ID=0 PROTO=UDP SPT=7178 DPT=7571 LEN=9 
[ 8084.974078] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 8316.425083] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=49282 WINDOW=0 RES=0x00 RST URGP=0 
[ 8316.545103] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=49281 WINDOW=0 RES=0x00 RST URGP=0 
[ 8323.225633] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=49282 WINDOW=0 RES=0x00 RST URGP=0 
[ 8323.466532] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=49281 WINDOW=0 RES=0x00 RST URGP=0 
[ 8337.321942] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=49281 WINDOW=0 RES=0x00 RST URGP=0 
[ 8365.034852] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=49281 WINDOW=0 RES=0x00 RST URGP=0 
[ 8462.962458] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 8486.142477] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=80.219.53.79 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=113 ID=22723 PROTO=UDP SPT=7150 DPT=7571 LEN=46 
[ 8486.142498] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=80.219.53.79 DST=192.168.1.64 LEN=29 TOS=0x00 PREC=0x00 TTL=113 ID=22724 DF PROTO=UDP SPT=7150 DPT=7571 LEN=9 
[ 8519.693459] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 8522.371929] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 8535.574910] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 8543.761296] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 8554.432543] usb 3-1: USB disconnect, address 2
[ 8554.432546] usb 3-1.1: USB disconnect, address 3
[ 8561.760017] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 8561.929593] pl2303 3-1:1.0: pl2303 converter detected
[ 8561.941889] usb 3-1: pl2303 converter now attached to ttyUSB0
[ 8581.772047] usb 5-2: new full speed USB device using uhci_hcd and address 2
[ 8581.957582] hub 5-2:1.0: USB hub found
[ 8581.959971] hub 5-2:1.0: 4 ports detected
[ 8582.241574] usb 5-2.1: new full speed USB device using uhci_hcd and address 3
[ 8582.488643] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
[ 8582.524687] input: UVC Camera (046d:0990) as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2.1/5-2.1:1.0/input/input9
[ 8584.312252] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 8594.626123] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=80.219.53.79 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=113 ID=20579 PROTO=UDP SPT=7150 DPT=7571 LEN=46 
[ 8594.626144] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=80.219.53.79 DST=192.168.1.64 LEN=29 TOS=0x00 PREC=0x00 TTL=113 ID=20580 DF PROTO=UDP SPT=7150 DPT=7571 LEN=9 
[ 8600.931969] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 8605.397171] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 8615.305185] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 8930.237725] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 8935.431253] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 8943.202427] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 9113.573177] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 9150.907041] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 9178.078263] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 9237.657236] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 9298.976351] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 9305.371682] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 9305.871274] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 9306.371117] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 9306.871676] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 9307.374974] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 9307.872535] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 9308.373276] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[ 9308.869063] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=192.168.1.254 DST=192.168.1.64 LEN=338 TOS=0x00 PREC=0x00 TTL=64 ID=24808 PROTO=UDP SPT=1900 DPT=1901 LEN=318 
[ 9361.372837] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 9578.135879] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[ 9645.657375] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[ 9673.899358] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=209.85.229.97 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=38989 PROTO=TCP SPT=443 DPT=41534 WINDOW=0 RES=0x00 RST URGP=0 
[ 9674.660461] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.67 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=53874 WINDOW=0 RES=0x00 RST URGP=0 
[ 9674.661514] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.83 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=44676 WINDOW=0 RES=0x00 RST URGP=0 
[ 9674.807084] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=209.85.229.97 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=38990 PROTO=TCP SPT=443 DPT=41534 WINDOW=0 RES=0x00 RST URGP=0 
[ 9675.036560] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=184.73.226.70 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=TCP SPT=80 DPT=34796 WINDOW=0 RES=0x00 RST URGP=0 
[ 9676.329386] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.67 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=53874 WINDOW=0 RES=0x00 RST URGP=0 
[ 9676.330382] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.83 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=44676 WINDOW=0 RES=0x00 RST URGP=0 
[ 9676.634950] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=209.85.229.97 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=38991 PROTO=TCP SPT=443 DPT=41534 WINDOW=0 RES=0x00 RST URGP=0 
[ 9677.383209] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=184.73.226.70 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=TCP SPT=80 DPT=34796 WINDOW=0 RES=0x00 RST URGP=0 
[ 9679.669314] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.67 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=53874 WINDOW=0 RES=0x00 RST URGP=0 
[ 9699.692743] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.83 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=44676 WINDOW=0 RES=0x00 RST URGP=0 
[ 9726.478187] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.83 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=44676 WINDOW=0 RES=0x00 RST URGP=0 
[ 9818.672693] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[10117.416955] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=33077 WINDOW=0 RES=0x00 RST URGP=0 
[10117.547489] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=33076 WINDOW=0 RES=0x00 RST URGP=0 
[10124.218119] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=33077 WINDOW=0 RES=0x00 RST URGP=0 
[10124.474282] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=33076 WINDOW=0 RES=0x00 RST URGP=0 
[10138.345071] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=33076 WINDOW=0 RES=0x00 RST URGP=0 
[10166.057179] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=33076 WINDOW=0 RES=0x00 RST URGP=0 
[10188.153737] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=209.85.229.109 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=2133 PROTO=TCP SPT=995 DPT=54231 WINDOW=0 RES=0x00 RST URGP=0 
[10223.763983] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[10302.578799] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[10318.321072] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[10377.392440] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[10411.464079] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[10486.398253] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[10920.993379] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[10937.526334] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[11040.386428] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[11062.094750] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[11105.373256] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[11105.871373] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[11106.371175] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[11106.871118] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[11107.371437] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[11107.873836] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[11108.371877] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[11108.859119] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=192.168.1.254 DST=192.168.1.64 LEN=338 TOS=0x00 PREC=0x00 TTL=64 ID=25502 PROTO=UDP SPT=1900 DPT=1901 LEN=318 
[11393.943249] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[11396.775196] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[11486.325249] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[11560.341440] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[11713.742866] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[11918.425503] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=57083 WINDOW=0 RES=0x00 RST URGP=0 
[11918.426479] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=57084 WINDOW=0 RES=0x00 RST URGP=0 
[11920.900866] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=209.85.229.109 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=24507 PROTO=TCP SPT=995 DPT=39705 WINDOW=0 RES=0x00 RST URGP=0 
[11920.901937] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=209.85.229.109 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=24508 PROTO=TCP SPT=995 DPT=39705 WINDOW=0 RES=0x00 RST URGP=0 
[11925.228839] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=57083 WINDOW=0 RES=0x00 RST URGP=0 
[11925.229811] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=57084 WINDOW=0 RES=0x00 RST URGP=0 
[11938.826999] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=57084 WINDOW=0 RES=0x00 RST URGP=0 
[11966.058809] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=57084 WINDOW=0 RES=0x00 RST URGP=0 
[12005.213545] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[12017.652747] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[12171.409071] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[12335.311102] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[12621.698622] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[12663.057324] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[12721.167751] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[12905.375236] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[12905.872965] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[12906.374445] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[12906.872690] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[12907.373374] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[12907.873196] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[12908.374720] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[12908.855196] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=192.168.1.254 DST=192.168.1.64 LEN=338 TOS=0x00 PREC=0x00 TTL=64 ID=25738 PROTO=UDP SPT=1900 DPT=1901 LEN=318 
[12951.078763] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[13173.102006] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[13183.544783] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[13381.495075] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=85.5.184.230 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=115 ID=44941 PROTO=UDP SPT=7197 DPT=7571 LEN=46 
[13432.137411] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=85.5.184.230 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=115 ID=48518 PROTO=UDP SPT=7197 DPT=7571 LEN=46 
[13433.731137] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[13433.741073] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 3)
[13502.956430] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[13514.867855] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[13719.321140] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=51561 WINDOW=0 RES=0x00 RST URGP=0 
[13719.448841] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=51560 WINDOW=0 RES=0x00 RST URGP=0 
[13726.122488] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=51561 WINDOW=0 RES=0x00 RST URGP=0 
[13726.378139] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=51560 WINDOW=0 RES=0x00 RST URGP=0 
[13740.234118] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=51560 WINDOW=0 RES=0x00 RST URGP=0 
[13742.625005] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[13745.273074] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[13761.157329] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[13767.913587] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=51560 WINDOW=0 RES=0x00 RST URGP=0 
[13785.445727] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[13910.920723] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[13965.868860] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[13986.840701] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[14006.624534] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[14114.033228] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[14147.382559] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[14167.730482] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[14335.547368] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[14346.290932] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[14424.434880] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[14429.971637] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[14474.830793] 3w-xxxx: scsi6: Unknown scsi opcode: 0x85
[14474.830815] 3w-xxxx: scsi6: Unknown scsi opcode: 0x85
[14476.684877] PM: Syncing filesystems ... done.
[14476.724569] PM: Preparing system for mem sleep
[14476.734547] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
[14476.744479] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 3)
[14476.844854] Freezing user space processes ... (elapsed 0.01 seconds) done.
[14476.860015] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[14476.876014] PM: Entering mem sleep
[14476.876025] Suspending console(s) (use no_console_suspend to debug)
[14476.876420] sd 6:0:0:0: [sdb] Synchronizing SCSI cache
[14476.876474] sd 3:0:0:0: [sda] Synchronizing SCSI cache
[14476.876902] sd 3:0:0:0: [sda] Stopping disk
[14476.887942] ACPI handle has no context!
[14476.888101] parport_pc 00:08: disabled
[14476.888231] serial 00:07: disabled
[14476.888691] [drm] nouveau 0000:01:00.0: Disabling fbcon acceleration...
[14476.888693] [drm] nouveau 0000:01:00.0: Unpinning framebuffer(s)...
[14476.888710] [drm] nouveau 0000:01:00.0: Evicting buffers...
[14476.888744] pata_jmicron 0000:03:00.0: PCI INT A disabled
[14476.888818] ata_piix 0000:00:1f.2: PCI INT B disabled
[14476.892039] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[14476.892047] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[14476.892055] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[14476.892061] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[14476.892526] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[14476.892625] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[14476.907889] [drm] nouveau 0000:01:00.0: Idling channels...
[14476.908332] [drm] nouveau 0000:01:00.0: Suspending GPU objects...
[14476.908529] uhci_hcd 0000:00:1a.2: PCI INT C disabled
[14476.912529] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[14476.980015] PM: suspend of drv:sd dev:6:0:0:0 complete after 103.604 msecs
[14476.980022] PM: suspend of drv:scsi dev:target6:0:0 complete after 103.603 msecs
[14476.980027] PM: suspend of drv:scsi dev:host6 complete after 103.602 msecs
[14476.980035] 3w-xxxx 0000:05:00.0: PCI INT A disabled
[14476.996593] HDA Intel 0000:00:1b.0: PCI INT A disabled
[14477.012507] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 120.424 msecs
[14477.223166] [drm] nouveau 0000:01:00.0: And we're gone!
[14477.223187] nouveau 0000:01:00.0: PCI INT A disabled
[14477.236014] PM: suspend of drv:nouveau dev:0000:01:00.0 complete after 347.350 msecs
[14477.236023] PM: suspend of drv:pcieport dev:0000:00:01.0 complete after 343.393 msecs
[14477.299848] PM: suspend of drv:sd dev:3:0:0:0 complete after 423.378 msecs
[14477.299855] PM: suspend of drv:scsi dev:target3:0:0 complete after 423.381 msecs
[14477.299861] PM: suspend of drv:scsi dev:host3 complete after 411.231 msecs
[14477.299932] ata_piix 0000:00:1f.5: PCI INT B disabled
[14477.312009] PM: suspend of drv:ata_piix dev:0000:00:1f.5 complete after 423.334 msecs
[14477.312016] PM: suspend of drv: dev:pci0000:00 complete after 419.372 msecs
[14477.312022] PM: suspend of devices complete after 435.732 msecs
[14477.312025] PM: suspend devices took 0.436 seconds
[14477.312191] r8169 0000:04:00.0: PME# enabled
[14477.312197] pcieport 0000:00:1c.4: wake-up capability enabled by ACPI
[14477.360101] PM: late suspend of devices complete after 48.073 msecs
[14477.360945] ACPI: Preparing to enter system sleep state S3
[14477.363521] PM: Saving platform NVS memory
[14477.363800] Disabling non-boot CPUs ...
[14477.364638] Broke affinity for irq 18
[14477.468008] CPU 1 is now offline
[14477.468011] SMP alternatives: switching to UP code
[14477.474299] Back to C!
[14477.474299] PM: Restoring platform NVS memory
[14477.474299] Enabling non-boot CPUs ...
[14477.474299] SMP alternatives: switching to SMP code
[14477.480318] Booting Node 0 Processor 1 APIC 0x1
[14477.474014] Initializing CPU#1
[14477.612365] CPU1 is up
[14477.613160] ACPI: Waking up from system sleep state S3
[14477.614473] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x103)
[14477.614485] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0xfc000004)
[14477.614489] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[14477.614493] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
[14477.614512] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[14477.614519] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xfc41fc31)
[14477.614523] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xfc20fc10)
[14477.614526] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x20009090)
[14477.614532] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810008)
[14477.614536] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[14477.614563] pcieport 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x40b)
[14477.614570] pcieport 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xfc61fc51)
[14477.614574] pcieport 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xf7f0f700)
[14477.614577] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0xf0f0, writing 0xb0b0)
[14477.614583] pcieport 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810008)
[14477.614587] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[14477.614613] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x100, writing 0x105)
[14477.614620] pcieport 0000:00:1c.4: restoring config space at offset 0x9 (was 0x10001, writing 0xfc81fc71)
[14477.614624] pcieport 0000:00:1c.4: restoring config space at offset 0x8 (was 0x0, writing 0xf9f0f800)
[14477.614627] pcieport 0000:00:1c.4: restoring config space at offset 0x7 (was 0xf0f0, writing 0xc0c0)
[14477.614633] pcieport 0000:00:1c.4: restoring config space at offset 0x3 (was 0x810000, writing 0x810008)
[14477.614637] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[14477.614856] ata_piix 0000:00:1f.5: restoring config space at offset 0x1 (was 0x2b00003, writing 0x2b00007)
[14477.614873] nouveau 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[14477.614879] nouveau 0000:01:00.0: restoring config space at offset 0x9 (was 0x1, writing 0xa001)
[14477.614883] nouveau 0000:01:00.0: restoring config space at offset 0x7 (was 0x4, writing 0xf5000004)
[14477.614887] nouveau 0000:01:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xe000000c)
[14477.614890] nouveau 0000:01:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xf4000000)
[14477.614894] nouveau 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[14477.614897] nouveau 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x20100007)
[14477.614930] pata_jmicron 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[14477.614944] pata_jmicron 0000:03:00.0: restoring config space at offset 0x8 (was 0x1, writing 0xb401)
[14477.614949] pata_jmicron 0000:03:00.0: restoring config space at offset 0x7 (was 0x1, writing 0xb301)
[14477.614954] pata_jmicron 0000:03:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xb201)
[14477.614959] pata_jmicron 0000:03:00.0: restoring config space at offset 0x5 (was 0x1, writing 0xb101)
[14477.614964] pata_jmicron 0000:03:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xb001)
[14477.614969] pata_jmicron 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[14477.614976] pata_jmicron 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[14477.615026] r8169 0000:04:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[14477.615043] r8169 0000:04:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xf9000004)
[14477.615049] r8169 0000:04:00.0: restoring config space at offset 0x4 (was 0xfc01, writing 0xc001)
[14477.615054] r8169 0000:04:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[14477.615060] r8169 0000:04:00.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100407)
[14477.615105] 3w-xxxx 0000:05:00.0: restoring config space at offset 0xf (was 0x90100, writing 0x9010a)
[14477.615117] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x6 (was 0x0, writing 0xfb000000)
[14477.615121] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x5 (was 0x0, writing 0xfbc00000)
[14477.615125] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xd001)
[14477.615129] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x2008)
[14477.615134] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00003)
[14477.615149] pci 0000:05:01.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[14477.615163] pci 0000:05:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xfb800000)
[14477.615167] pci 0000:05:01.0: restoring config space at offset 0x3 (was 0x0, writing 0x2008)
[14477.615172] pci 0000:05:01.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900007)
[14477.615233] PM: early resume of devices complete after 0.917 msecs
[14477.615496] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[14477.615501] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[14477.615519] usb usb3: root hub lost power or was reset
[14477.615535] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[14477.615540] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[14477.615556] usb usb4: root hub lost power or was reset
[14477.615571] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[14477.615576] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[14477.615592] usb usb5: root hub lost power or was reset
[14477.615607] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[14477.615612] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[14477.615642] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[14477.615646] HDA Intel 0000:00:1b.0: setting latency timer to 64
[14477.615672] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[14477.615700] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[14477.615705] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[14477.615722] usb usb6: root hub lost power or was reset
[14477.615736] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[14477.615740] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[14477.615757] usb usb7: root hub lost power or was reset
[14477.615771] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[14477.615775] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[14477.615792] usb usb8: root hub lost power or was reset
[14477.615806] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[14477.615811] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[14477.615838] pci 0000:00:1e.0: setting latency timer to 64
[14477.615845] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[14477.615849] ata_piix 0000:00:1f.2: setting latency timer to 64
[14477.615851] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[14477.615855] ata_piix 0000:00:1f.5: setting latency timer to 64
[14477.615860] [drm] nouveau 0000:01:00.0: We're back, enabling device...
[14477.615863] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[14477.615867] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[14477.615869] nouveau 0000:01:00.0: setting latency timer to 64
[14477.615871] [drm] nouveau 0000:01:00.0: POSTing device...
[14477.615873] pata_jmicron 0000:03:00.0: setting latency timer to 64
[14477.615875] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xDF5D
[14477.615887] pcieport 0000:00:1c.4: wake-up capability disabled by ACPI
[14477.615891] r8169 0000:04:00.0: PME# disabled
[14477.615896] 3w-xxxx 0000:05:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[14477.615949] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xE59E
[14477.615960] sd 3:0:0:0: [sda] Starting disk
[14477.618415] serial 00:07: activated
[14477.618980] parport_pc 00:08: activated
[14477.668072] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xECAF
[14477.668157] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xEE2F
[14477.692015] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xF01D
[14477.692017] [drm] nouveau 0000:01:00.0: Reinitialising engines...
[14477.692078] [drm] nouveau 0000:01:00.0: Restoring GPU objects...
[14477.706443] [drm] nouveau 0000:01:00.0: Restoring mode...
[14477.706535] [drm] nouveau 0000:01:00.0: 0xD359: Parsing digital output script table
[14477.756517] PM: resume of drv:usb dev:usb8 complete after 140.561 msecs
[14477.756523] PM: resume of drv:hub dev:8-0:1.0 complete after 140.565 msecs
[14477.756549] PM: resume of drv:usb dev:usb7 complete after 140.614 msecs
[14477.756557] PM: resume of drv:usb dev:usb6 complete after 140.625 msecs
[14477.756564] PM: resume of drv:hub dev:6-0:1.0 complete after 140.630 msecs
[14477.756570] PM: resume of drv:hub dev:7-0:1.0 complete after 140.633 msecs
[14477.764009] [drm] nouveau 0000:01:00.0: 0xD3A2: Parsing digital output script table
[14477.820356] [drm] nouveau 0000:01:00.0: Restoring CRTC_OWNER to 0.
[14477.827277] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[14477.827280] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[14477.827282] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 2)
[14477.827284] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 4)
[14477.847380] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
[14477.847382] [drm] nouveau 0000:01:00.0: 0xD359: Parsing digital output script table
[14477.860508] PM: resume of drv:usb dev:usb5 complete after 244.581 msecs
[14477.860515] PM: resume of drv:hub dev:5-0:1.0 complete after 244.584 msecs
[14477.860528] PM: resume of drv:usb dev:usb4 complete after 244.604 msecs
[14477.860535] PM: resume of drv:usb dev:usb3 complete after 244.614 msecs
[14477.860538] PM: resume of drv:hub dev:4-0:1.0 complete after 244.610 msecs
[14477.860542] PM: resume of drv:hub dev:3-0:1.0 complete after 244.620 msecs
[14477.860548] PM: resume of drv: dev:ep_81 complete after 192.490 msecs
[14477.904007] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
[14477.904010] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
[14477.904015] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 3)
[14477.924117] [drm] nouveau 0000:01:00.0: Output DVI-I-2 is running on CRTC 1 using output C
[14477.924119] [drm] nouveau 0000:01:00.0: 0xD3A2: Parsing digital output script table
[14477.947065] ata1: SATA link down (SStatus 4 SControl 300)
[14477.957679] ata3: SATA link down (SStatus 4 SControl 300)
[14477.957848] ata2: SATA link down (SStatus 4 SControl 300)
[14477.958511] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[14477.958513] ata5.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
[14477.972509] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[14477.976547] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 3)
[14477.976549] [drm] nouveau 0000:01:00.0: Output DVI-I-2 is running on CRTC 1 using output C
[14477.976553] PM: resume of drv:nouveau dev:0000:01:00.0 complete after 360.693 msecs
[14477.976569] ata5.00: configured for UDMA/66
[14478.224510] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[14478.346092] PM: resume of drv:usb dev:5-2 complete after 730.082 msecs
[14478.346100] PM: resume of drv:hub dev:5-2:1.0 complete after 730.089 msecs
[14478.425618] psmouse serio1: ID: 10 00 64
[14478.485494] logips2pp: Detected unknown logitech mouse model 116
[14478.596008] PM: resume of drv:usb dev:4-1 complete after 980.024 msecs
[14478.596015] PM: resume of drv:hub dev:4-1:1.0 complete after 980.030 msecs
[14478.620509] usb 4-2: reset low speed USB device using uhci_hcd and address 3
[14478.990108] PM: resume of drv:usb dev:4-2 complete after 1374.123 msecs
[14478.990115] PM: resume of drv:usbhid dev:4-2:1.0 complete after 1374.128 msecs
[14479.052508] usb 3-1: reset full speed USB device using uhci_hcd and address 5
[14479.195109] usb 3-1: device firmware changed
[14479.195120] PM: resume of drv:usb dev:3-1 complete after 1579.112 msecs
[14479.195126] PM: resume of drv:pl2303 dev:3-1:1.0 complete after 1579.116 msecs
[14479.269132] usb 5-2.1: reset full speed USB device using uhci_hcd and address 3
[14479.489138] usb 4-1.4: reset full speed USB device using uhci_hcd and address 8
[14479.519146] snd-usb-audio 5-2.1:1.2: no reset_resume for driver snd-usb-audio?
[14479.519149] snd-usb-audio 5-2.1:1.3: no reset_resume for driver snd-usb-audio?
[14479.519311] PM: resume of drv:usb dev:5-2.1 complete after 1903.299 msecs
[14479.519320] PM: resume of drv:uvcvideo dev:5-2.1:1.0 complete after 1903.308 msecs
[14479.519323] PM: resume of drv:usb dev:5-2.1:1.3 complete after 1902.997 msecs
[14479.519325] PM: resume of drv:uvcvideo dev:5-2.1:1.1 complete after 1903.312 msecs
[14479.519327] PM: resume of drv:usb dev:5-2.1:1.2 complete after 1903.313 msecs
[14479.627143] snd-usb-audio 4-1.4:1.0: no reset_resume for driver snd-usb-audio?
[14479.627145] snd-usb-audio 4-1.4:1.1: no reset_resume for driver snd-usb-audio?
[14479.627147] snd-usb-audio 4-1.4:1.2: no reset_resume for driver snd-usb-audio?
[14479.628266] PM: resume of drv:usb dev:4-1.4 complete after 2012.275 msecs
[14479.628275] PM: resume of drv:usb dev:4-1.4:1.0 complete after 2012.270 msecs
[14479.628277] PM: resume of drv:usb dev:4-1.4:1.2 complete after 2012.270 msecs
[14479.628280] PM: resume of drv:usb dev:4-1.4:1.1 complete after 2012.274 msecs
[14479.628284] PM: resume of drv:usbhid dev:4-1.4:1.3 complete after 2012.277 msecs
[14483.152007] ata4: link is slow to respond, please be patient (ready=0)
[14485.448041] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[14485.472126] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[14485.472129] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[14485.472133] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[14485.488247] ata4.00: configured for UDMA/133
[14485.490708] PM: resume of drv:sd dev:3:0:0:0 complete after 7874.747 msecs
[14485.490717] PM: resume of drv:scsi_device dev:3:0:0:0 complete after 7874.738 msecs
[14485.490721] PM: resume of drv:scsi_disk dev:3:0:0:0 complete after 7630.102 msecs
[14485.490800] PM: resume of devices complete after 7875.540 msecs
[14485.941833] PM: resume devices took 8.328 seconds
[14485.941868] PM: Finishing wakeup.
[14485.941869] Restarting tasks ... done.
[14485.942294] usb 3-1: USB disconnect, address 5
[14485.942366] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[14485.942378] pl2303 3-1:1.0: device disconnected
[14486.052034] usb 3-1: new full speed USB device using uhci_hcd and address 6
[14486.083460] r8169 0000:04:00.0: eth0: link up
[14486.083465] r8169 0000:04:00.0: eth0: link up
[14486.213578] pl2303 3-1:1.0: pl2303 converter detected
[14486.225598] usb 3-1: pl2303 converter now attached to ttyUSB0
[14486.689506] 3w-xxxx: scsi6: Unknown scsi opcode: 0x85
[14486.689525] 3w-xxxx: scsi6: Unknown scsi opcode: 0x85
[14494.160063] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=55373 WINDOW=0 RES=0x00 RST URGP=0 
[14494.313017] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=55372 WINDOW=0 RES=0x00 RST URGP=0 
[14496.160006] eth0: no IPv6 routers present
[14497.043932] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14497.543833] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14498.044045] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14498.544233] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14499.045287] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14499.545517] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14500.043005] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14500.525222] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=192.168.1.254 DST=192.168.1.64 LEN=338 TOS=0x00 PREC=0x00 TTL=64 ID=25906 PROTO=UDP SPT=1900 DPT=1901 LEN=318 
[14500.969401] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=55373 WINDOW=0 RES=0x00 RST URGP=0 
[14501.241062] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=55372 WINDOW=0 RES=0x00 RST URGP=0 
[14515.113084] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=55372 WINDOW=0 RES=0x00 RST URGP=0 
[14521.000051] Corrupted low memory at c000e11c (e11c phys) = 00004000
[14542.825356] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=55372 WINDOW=0 RES=0x00 RST URGP=0 
[14547.168609] sd 6:0:0:0: WARNING: Command (0x28) timed out, resetting card.
[14705.376511] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14705.873894] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14706.375067] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14706.874054] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14707.374488] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14707.873778] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14708.377800] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[14708.868850] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=192.168.1.254 DST=192.168.1.64 LEN=338 TOS=0x00 PREC=0x00 TTL=64 ID=25928 PROTO=UDP SPT=1900 DPT=1901 LEN=318 
[14818.458234] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[14853.352594] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[14864.048114] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[15008.273490] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[15081.055309] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[15177.777522] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[15329.960213] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[15331.295173] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[15532.540493] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[15774.832150] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[15786.795407] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[15823.630694] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[15991.528185] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.110.196.145 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=120 ID=28741 PROTO=UDP SPT=7598 DPT=7571 LEN=46 
[16184.676125] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[16252.206438] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[16254.818731] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[16294.579056] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[16294.969148] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=60947 WINDOW=0 RES=0x00 RST URGP=0 
[16294.970123] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=60948 WINDOW=0 RES=0x00 RST URGP=0 
[16301.771522] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=60947 WINDOW=0 RES=0x00 RST URGP=0 
[16301.772574] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=60948 WINDOW=0 RES=0x00 RST URGP=0 
[16315.371524] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=60948 WINDOW=0 RES=0x00 RST URGP=0 
[16342.572648] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=60948 WINDOW=0 RES=0x00 RST URGP=0 
[16401.170267] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[16412.448409] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[16505.379623] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[16505.875939] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[16506.373857] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[16506.874168] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[16507.373974] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[16507.874372] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[16508.374991] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[16508.856233] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=192.168.1.254 DST=192.168.1.64 LEN=338 TOS=0x00 PREC=0x00 TTL=64 ID=27007 PROTO=UDP SPT=1900 DPT=1901 LEN=318 
[16792.629520] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[16830.617935] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[16851.529724] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[16872.366139] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[16875.656156] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[16909.706638] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[17009.684620] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=98.217.116.148 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=116 ID=9723 PROTO=UDP SPT=7344 DPT=7571 LEN=46 
[17012.425414] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[17030.317971] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[17050.245087] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[17058.373696] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[17144.428722] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[17851.804679] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[17960.280741] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[17960.291542] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 3)
[17999.152414] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[18095.849489] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=37551 WINDOW=0 RES=0x00 RST URGP=0 
[18095.969298] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=37552 WINDOW=0 RES=0x00 RST URGP=0 
[18102.521943] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=37551 WINDOW=0 RES=0x00 RST URGP=0 
[18102.762659] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=37552 WINDOW=0 RES=0x00 RST URGP=0 
[18116.361643] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=37552 WINDOW=0 RES=0x00 RST URGP=0 
[18143.593225] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=37552 WINDOW=0 RES=0x00 RST URGP=0 
[18305.034282] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[18305.375872] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[18305.874623] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[18306.374897] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[18306.873880] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[18307.374766] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[18307.876146] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[18308.374576] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[18308.855811] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=192.168.1.254 DST=192.168.1.64 LEN=338 TOS=0x00 PREC=0x00 TTL=64 ID=28011 PROTO=UDP SPT=1900 DPT=1901 LEN=318 
[18353.457797] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[18502.607920] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[18676.264716] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[18736.097527] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[18833.988868] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[19077.006342] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[19081.366779] 3w-xxxx: scsi6: Unknown scsi opcode: 0x85
[19081.366800] 3w-xxxx: scsi6: Unknown scsi opcode: 0x85
[19083.164689] PM: Syncing filesystems ... done.
[19083.248728] PM: Preparing system for mem sleep
[19083.259389] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
[19083.269869] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 3)
[19083.376302] Freezing user space processes ... (elapsed 0.01 seconds) done.
[19083.392514] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[19083.408013] PM: Entering mem sleep
[19083.408024] Suspending console(s) (use no_console_suspend to debug)
[19083.408432] sd 6:0:0:0: [sdb] Synchronizing SCSI cache
[19083.408511] sd 3:0:0:0: [sda] Synchronizing SCSI cache
[19083.420608] ACPI handle has no context!
[19083.420764] parport_pc 00:08: disabled
[19083.420894] serial 00:07: disabled
[19083.421041] [drm] nouveau 0000:01:00.0: Disabling fbcon acceleration...
[19083.421043] [drm] nouveau 0000:01:00.0: Unpinning framebuffer(s)...
[19083.421071] [drm] nouveau 0000:01:00.0: Evicting buffers...
[19083.421256] ata_piix 0000:00:1f.2: PCI INT B disabled
[19083.421285] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[19083.421295] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[19083.421303] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[19083.421312] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[19083.421835] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[19083.422021] pata_jmicron 0000:03:00.0: PCI INT A disabled
[19083.424535] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[19083.437443] sd 3:0:0:0: [sda] Stopping disk
[19083.438349] [drm] nouveau 0000:01:00.0: Idling channels...
[19083.438792] [drm] nouveau 0000:01:00.0: Suspending GPU objects...
[19083.444046] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[19083.444075] uhci_hcd 0000:00:1a.2: PCI INT C disabled
[19083.486990] 3w-xxxx 0000:05:00.0: PCI INT A disabled
[19083.528085] HDA Intel 0000:00:1b.0: PCI INT A disabled
[19083.544006] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 122.683 msecs
[19083.752616] [drm] nouveau 0000:01:00.0: And we're gone!
[19083.752637] nouveau 0000:01:00.0: PCI INT A disabled
[19083.768014] PM: suspend of drv:nouveau dev:0000:01:00.0 complete after 346.973 msecs
[19083.768024] PM: suspend of drv:pcieport dev:0000:00:01.0 complete after 346.170 msecs
[19083.891338] PM: suspend of drv:sd dev:3:0:0:0 complete after 482.838 msecs
[19083.891346] PM: suspend of drv:scsi dev:target3:0:0 complete after 482.843 msecs
[19083.891353] PM: suspend of drv:scsi dev:host3 complete after 471.036 msecs
[19083.891429] ata_piix 0000:00:1f.5: PCI INT B disabled
[19083.904009] PM: suspend of drv:ata_piix dev:0000:00:1f.5 complete after 482.943 msecs
[19083.904017] PM: suspend of drv: dev:pci0000:00 complete after 482.151 msecs
[19083.904023] PM: suspend of devices complete after 495.731 msecs
[19083.904026] PM: suspend devices took 0.496 seconds
[19083.904206] r8169 0000:04:00.0: PME# enabled
[19083.904214] pcieport 0000:00:1c.4: wake-up capability enabled by ACPI
[19083.952105] PM: late suspend of devices complete after 48.075 msecs
[19083.952935] ACPI: Preparing to enter system sleep state S3
[19083.955506] PM: Saving platform NVS memory
[19083.955781] Disabling non-boot CPUs ...
[19084.060007] CPU 1 is now offline
[19084.060010] SMP alternatives: switching to UP code
[19084.066213] Back to C!
[19084.066213] PM: Restoring platform NVS memory
[19084.066213] Enabling non-boot CPUs ...
[19084.066213] SMP alternatives: switching to SMP code
[19084.072292] Booting Node 0 Processor 1 APIC 0x1
[19084.065970] Initializing CPU#1
[19084.196368] CPU1 is up
[19084.197162] ACPI: Waking up from system sleep state S3
[19084.198477] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x103)
[19084.198490] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0xfc000004)
[19084.198493] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[19084.198498] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
[19084.198516] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[19084.198523] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xfc41fc31)
[19084.198527] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xfc20fc10)
[19084.198531] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x9090)
[19084.198536] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810008)
[19084.198541] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[19084.198567] pcieport 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x40b)
[19084.198574] pcieport 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xfc61fc51)
[19084.198578] pcieport 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xf7f0f700)
[19084.198581] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0xf0f0, writing 0xb0b0)
[19084.198587] pcieport 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810008)
[19084.198591] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[19084.198617] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x100, writing 0x105)
[19084.198625] pcieport 0000:00:1c.4: restoring config space at offset 0x9 (was 0x10001, writing 0xfc81fc71)
[19084.198628] pcieport 0000:00:1c.4: restoring config space at offset 0x8 (was 0x0, writing 0xf9f0f800)
[19084.198632] pcieport 0000:00:1c.4: restoring config space at offset 0x7 (was 0xf0f0, writing 0xc0c0)
[19084.198637] pcieport 0000:00:1c.4: restoring config space at offset 0x3 (was 0x810000, writing 0x810008)
[19084.198642] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[19084.198859] ata_piix 0000:00:1f.5: restoring config space at offset 0x1 (was 0x2b00003, writing 0x2b00007)
[19084.198876] nouveau 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[19084.198883] nouveau 0000:01:00.0: restoring config space at offset 0x9 (was 0x1, writing 0xa001)
[19084.198887] nouveau 0000:01:00.0: restoring config space at offset 0x7 (was 0x4, writing 0xf5000004)
[19084.198891] nouveau 0000:01:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xe000000c)
[19084.198894] nouveau 0000:01:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xf4000000)
[19084.198897] nouveau 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[19084.198901] nouveau 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x20100007)
[19084.198933] pata_jmicron 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[19084.198948] pata_jmicron 0000:03:00.0: restoring config space at offset 0x8 (was 0x1, writing 0xb401)
[19084.198953] pata_jmicron 0000:03:00.0: restoring config space at offset 0x7 (was 0x1, writing 0xb301)
[19084.198958] pata_jmicron 0000:03:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xb201)
[19084.198963] pata_jmicron 0000:03:00.0: restoring config space at offset 0x5 (was 0x1, writing 0xb101)
[19084.198968] pata_jmicron 0000:03:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xb001)
[19084.198973] pata_jmicron 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[19084.198980] pata_jmicron 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[19084.199030] r8169 0000:04:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[19084.199046] r8169 0000:04:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xf9000004)
[19084.199053] r8169 0000:04:00.0: restoring config space at offset 0x4 (was 0xfc01, writing 0xc001)
[19084.199058] r8169 0000:04:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[19084.199064] r8169 0000:04:00.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100407)
[19084.199109] 3w-xxxx 0000:05:00.0: restoring config space at offset 0xf (was 0x90100, writing 0x9010a)
[19084.199121] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x6 (was 0x0, writing 0xfb000000)
[19084.199125] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x5 (was 0x0, writing 0xfbc00000)
[19084.199129] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xd001)
[19084.199133] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x2008)
[19084.199137] 3w-xxxx 0000:05:00.0: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00003)
[19084.199153] pci 0000:05:01.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[19084.199167] pci 0000:05:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xfb800000)
[19084.199171] pci 0000:05:01.0: restoring config space at offset 0x3 (was 0x0, writing 0x2008)
[19084.199176] pci 0000:05:01.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900007)
[19084.199237] PM: early resume of devices complete after 0.917 msecs
[19084.199415] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[19084.199420] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[19084.199438] usb usb3: root hub lost power or was reset
[19084.199454] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[19084.199458] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[19084.199475] usb usb4: root hub lost power or was reset
[19084.199490] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[19084.199494] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[19084.199511] usb usb5: root hub lost power or was reset
[19084.199527] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[19084.199531] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[19084.199561] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[19084.199565] HDA Intel 0000:00:1b.0: setting latency timer to 64
[19084.199591] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[19084.199620] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[19084.199624] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[19084.199641] usb usb6: root hub lost power or was reset
[19084.199655] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[19084.199659] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[19084.199676] usb usb7: root hub lost power or was reset
[19084.199690] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[19084.199694] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[19084.199699] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[19084.199704] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[19084.199713] usb usb8: root hub lost power or was reset
[19084.199720] pci 0000:00:1e.0: setting latency timer to 64
[19084.199727] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[19084.199730] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[19084.199732] ata_piix 0000:00:1f.2: setting latency timer to 64
[19084.199734] ata_piix 0000:00:1f.5: setting latency timer to 64
[19084.199743] [drm] nouveau 0000:01:00.0: We're back, enabling device...
[19084.199748] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[19084.199750] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[19084.199753] pata_jmicron 0000:03:00.0: setting latency timer to 64
[19084.199754] nouveau 0000:01:00.0: setting latency timer to 64
[19084.199757] [drm] nouveau 0000:01:00.0: POSTing device...
[19084.199760] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xDF5D
[19084.199769] pcieport 0000:00:1c.4: wake-up capability disabled by ACPI
[19084.199773] r8169 0000:04:00.0: PME# disabled
[19084.199778] 3w-xxxx 0000:05:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[19084.199832] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xE59E
[19084.199905] sd 3:0:0:0: [sda] Starting disk
[19084.202141] serial 00:07: activated
[19084.202833] parport_pc 00:08: activated
[19084.244030] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xECAF
[19084.244110] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xEE2F
[19084.268017] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xF01D
[19084.268020] [drm] nouveau 0000:01:00.0: Reinitialising engines...
[19084.268081] [drm] nouveau 0000:01:00.0: Restoring GPU objects...
[19084.282445] [drm] nouveau 0000:01:00.0: Restoring mode...
[19084.282491] [drm] nouveau 0000:01:00.0: 0xD359: Parsing digital output script table
[19084.336011] [drm] nouveau 0000:01:00.0: 0xD3A2: Parsing digital output script table
[19084.340020] PM: resume of drv:usb dev:usb8 complete after 140.119 msecs
[19084.340026] PM: resume of drv:hub dev:8-0:1.0 complete after 140.123 msecs
[19084.340035] PM: resume of drv:usb dev:usb6 complete after 140.141 msecs
[19084.340063] PM: resume of drv:hub dev:6-0:1.0 complete after 140.167 msecs
[19084.340075] PM: resume of drv:usb dev:usb7 complete after 140.178 msecs
[19084.340081] PM: resume of drv:hub dev:7-0:1.0 complete after 140.181 msecs
[19084.392360] [drm] nouveau 0000:01:00.0: Restoring CRTC_OWNER to 0.
[19084.399285] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[19084.399287] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[19084.399289] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 2)
[19084.399292] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 4)
[19084.419388] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
[19084.419390] [drm] nouveau 0000:01:00.0: 0xD359: Parsing digital output script table
[19084.444008] PM: resume of drv:usb dev:usb4 complete after 244.121 msecs
[19084.444015] PM: resume of drv:hub dev:4-0:1.0 complete after 244.126 msecs
[19084.444047] PM: resume of drv:usb dev:usb5 complete after 244.156 msecs
[19084.444050] PM: resume of drv:usb dev:usb3 complete after 244.206 msecs
[19084.444054] PM: resume of drv:hub dev:5-0:1.0 complete after 244.161 msecs
[19084.444058] PM: resume of drv:hub dev:3-0:1.0 complete after 244.212 msecs
[19084.444064] PM: resume of drv: dev:ep_81 complete after 195.535 msecs
[19084.472011] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
[19084.472014] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
[19084.472019] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 3)
[19084.492122] [drm] nouveau 0000:01:00.0: Output DVI-I-2 is running on CRTC 1 using output C
[19084.492124] [drm] nouveau 0000:01:00.0: 0xD3A2: Parsing digital output script table
[19084.531123] ata3: SATA link down (SStatus 4 SControl 300)
[19084.534579] ata2: SATA link down (SStatus 4 SControl 300)
[19084.545109] ata1: SATA link down (SStatus 4 SControl 300)
[19084.548010] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 3)
[19084.548013] [drm] nouveau 0000:01:00.0: Output DVI-I-2 is running on CRTC 1 using output C
[19084.548018] PM: resume of drv:nouveau dev:0000:01:00.0 complete after 348.274 msecs
[19084.589092] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[19084.589094] ata5.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
[19084.605058] ata5.00: configured for UDMA/66
[19084.704009] usb 4-2: reset low speed USB device using uhci_hcd and address 3
[19085.011025] psmouse serio1: ID: 10 00 64
[19085.071555] logips2pp: Detected unknown logitech mouse model 116
[19085.075086] PM: resume of drv:usb dev:4-2 complete after 875.072 msecs
[19085.075092] PM: resume of drv:usbhid dev:4-2:1.0 complete after 875.067 msecs
[19085.136507] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[19085.388507] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[19085.504032] PM: resume of drv:usb dev:4-1 complete after 1304.050 msecs
[19085.504039] PM: resume of drv:hub dev:4-1:1.0 complete after 1304.046 msecs
[19085.640507] usb 3-1: reset full speed USB device using uhci_hcd and address 6
[19085.756010] PM: resume of drv:usb dev:5-2 complete after 1555.920 msecs
[19085.756017] PM: resume of drv:hub dev:5-2:1.0 complete after 1555.917 msecs
[19085.788117] pl2303 3-1:1.0: no reset_resume for driver pl2303?
[19085.788194] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[19085.788205] pl2303 3-1:1.0: device disconnected
[19085.788208] PM: resume of drv:usb dev:3-1 complete after 1588.063 msecs
[19085.788213] PM: resume of drv:usb dev:3-1:1.0 complete after 1588.067 msecs
[19085.869130] usb 4-1.4: reset full speed USB device using uhci_hcd and address 8
[19085.995137] snd-usb-audio 4-1.4:1.0: no reset_resume for driver snd-usb-audio?
[19085.995139] snd-usb-audio 4-1.4:1.1: no reset_resume for driver snd-usb-audio?
[19085.995142] snd-usb-audio 4-1.4:1.2: no reset_resume for driver snd-usb-audio?
[19085.996273] PM: resume of drv:usb dev:4-1.4 complete after 1796.233 msecs
[19085.996280] PM: resume of drv:usb dev:4-1.4:1.0 complete after 1796.230 msecs
[19085.996283] PM: resume of drv:usb dev:4-1.4:1.2 complete after 1796.212 msecs
[19085.996285] PM: resume of drv:usb dev:4-1.4:1.1 complete after 1796.225 msecs
[19085.996287] PM: resume of drv:usbhid dev:4-1.4:1.3 complete after 1796.207 msecs
[19086.057150] usb 5-2.1: reset full speed USB device using uhci_hcd and address 3
[19086.293164] snd-usb-audio 5-2.1:1.2: no reset_resume for driver snd-usb-audio?
[19086.293167] snd-usb-audio 5-2.1:1.3: no reset_resume for driver snd-usb-audio?
[19086.293320] PM: resume of drv:usb dev:5-2.1 complete after 2093.209 msecs
[19086.293329] PM: resume of drv:uvcvideo dev:5-2.1:1.0 complete after 2093.209 msecs
[19086.293331] PM: resume of drv:usb dev:5-2.1:1.2 complete after 2093.187 msecs
[19086.293334] PM: resume of drv:uvcvideo dev:5-2.1:1.1 complete after 2093.211 msecs
[19086.293336] PM: resume of drv:usb dev:5-2.1:1.3 complete after 2093.191 msecs
[19089.716506] ata4: link is slow to respond, please be patient (ready=0)
[19092.068540] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[19092.092624] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[19092.092628] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[19092.092632] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[19092.108247] ata4.00: configured for UDMA/133
[19092.112964] PM: resume of drv:sd dev:3:0:0:0 complete after 7913.058 msecs
[19092.112973] PM: resume of drv:scsi_device dev:3:0:0:0 complete after 7913.051 msecs
[19092.112978] PM: resume of drv:scsi_disk dev:3:0:0:0 complete after 7668.844 msecs
[19092.113056] PM: resume of devices complete after 7913.792 msecs
[19092.113079] pl2303 3-1:1.0: pl2303 converter detected
[19092.124567] usb 3-1: pl2303 converter now attached to ttyUSB0
[19092.573842] PM: resume devices took 8.376 seconds
[19092.573877] PM: Finishing wakeup.
[19092.573879] Restarting tasks ... done.
[19092.756205] r8169 0000:04:00.0: eth0: link up
[19092.756210] r8169 0000:04:00.0: eth0: link up
[19093.268590] 3w-xxxx: scsi6: Unknown scsi opcode: 0x85
[19093.268610] 3w-xxxx: scsi6: Unknown scsi opcode: 0x85
[19101.443557] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=40691 WINDOW=0 RES=0x00 RST URGP=0 
[19101.593480] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=40692 WINDOW=0 RES=0x00 RST URGP=0 
[19102.678047] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[19103.177323] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[19103.248008] eth0: no IPv6 routers present
[19103.677508] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[19104.177520] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[19104.677628] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[19105.179119] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[19105.679195] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[19106.159751] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=192.168.1.254 DST=192.168.1.64 LEN=338 TOS=0x00 PREC=0x00 TTL=64 ID=28105 PROTO=UDP SPT=1900 DPT=1901 LEN=318 
[19108.746214] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=40691 WINDOW=0 RES=0x00 RST URGP=0 
[19109.032785] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=40692 WINDOW=0 RES=0x00 RST URGP=0 
[19123.914165] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=40692 WINDOW=0 RES=0x00 RST URGP=0 
[19141.000034] Corrupted low memory at c000e11c (e11c phys) = 00004000
[19153.640873] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=40692 WINDOW=0 RES=0x00 RST URGP=0 
[19157.220020] sd 6:0:0:0: WARNING: Command (0x28) timed out, resetting card.
[20105.379142] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[20105.874538] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[20106.374256] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[20106.875573] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[20107.374453] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[20107.874153] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[20108.374467] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=178.63.89.8 DST=192.168.1.64 LEN=57 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=13203 DPT=7571 LEN=37 
[20108.856073] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=192.168.1.254 DST=192.168.1.64 LEN=338 TOS=0x00 PREC=0x00 TTL=64 ID=28544 PROTO=UDP SPT=1900 DPT=1901 LEN=318 
[20324.762936] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[20422.324545] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[20428.781454] usb 4-1.4: reset full speed USB device using uhci_hcd and address 8
[20578.157415] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[20857.843920] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[20861.686864] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
[20901.253447] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=39000 WINDOW=0 RES=0x00 RST URGP=0 
[20901.254418] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=39001 WINDOW=0 RES=0x00 RST URGP=0 
[20906.700952] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=64.4.61.30 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=118 ID=6815 DF PROTO=TCP SPT=1863 DPT=38813 WINDOW=0 RES=0x00 ACK RST URGP=0 
[20908.297045] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=39000 WINDOW=0 RES=0x00 RST URGP=0 
[20908.298033] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=39001 WINDOW=0 RES=0x00 RST URGP=0 
[20922.410262] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=39001 WINDOW=0 RES=0x00 RST URGP=0 
[20950.634444] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=92.123.153.56 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=39001 WINDOW=0 RES=0x00 RST URGP=0 
[20969.561914] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[21074.768212] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.110.198 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7337 DPT=7571 LEN=46 
[21206.096343] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=188.40.94.138 DST=192.168.1.64 LEN=66 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=7122 DPT=7571 LEN=46 
```

---

### Post by NightwishFan on 2010-12-26
A whole huge chunk of the log looks like it is sleeping and waking up. Are you resuming it from hibernation or something?

I would test a boot with acpi off. To run a boot command get to the menu where you can pick linux-generic or (recovery mode), highlight the top entry (not recovery mode) and press E. Find the line that says "kernel" and go the end of it (after quiet splash) and add a space and:
```
acpi=off
```

Press ctrl+X to boot. Any better?

---

### Post by Robbyx on 2010-12-27
> **NightwishFan said:**
> A whole huge chunk of the log looks like it is sleeping and waking up. Are you resuming it from hibernation or something?

I would test a boot with acpi off. To run a boot command get to the menu where you can pick linux-generic or (recovery mode), highlight the top entry (not recovery mode) and press E. Find the line that says "kernel" and go the end of it (after quiet splash) and add a space and:
```
acpi=off
```

Press ctrl+X to boot. Any better?

Thank you for your guidance so far. 

I have been deliberately using the sleep mode and have the panel widget for automatic sleep enabled.

I do not understand how using acpi can interfere with the boot process. I would have followed your test boot advice, just to see what would happen,  except my version of grub does not show a line with the word "kernel".

Is there somewhere I can see the start up script? Mine is hanging after the following entry

Starting preload: preload
checking battery state
starting timidity ++ alsa midi emulation

After the above entries appear in the boot up procedure the computer hangs. It is as if it is waiting for a response because I can drop into the command line by issuing Ctrl ALT F1.

I think it would be a good idea to find out what comes after Starting Timidity in my startup script. I do not know where to look.

Robin

---

### Post by NightwishFan on 2010-12-27
I believe they are located in /etc/init or /etc/init.d

---

### Post by Robbyx on 2010-12-27
I assume there is a master script running all those files in the init and int.d directories. 

Do you know which one calls the other scripts on startup?

---

### Post by Robbyx on 2010-12-27
> **Robbyx said:**
> I assume there is a master script running all those files in the init and int.d directories. 

Do you know which one calls the other scripts on startup?

Does anyone know the answer?

---

### Post by Jamie Jackson on 2011-01-04
> **NightwishFan said:**
> I see, it is actually unresponsive, ok, just to make sure, lets make sure all the required packages for Ubuntu are installed, run:
```
sudo apt-get --reinstall --install-recommends install ubuntu-desktop
```

Also run:
```
sudo dpkg-reconfigure gdm
```

I had the same symptoms, and the above fixed it for me. 

Thanks, NightwishFan,

Jamie

---


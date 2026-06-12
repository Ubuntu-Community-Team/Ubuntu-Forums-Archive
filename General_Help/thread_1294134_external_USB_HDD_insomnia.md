---
title: "external USB HDD insomnia"
date: 2009-10-17
forum: General Help
---

### Post by petru.marginean on 2009-10-17
[FONT=Arial]Hi,

I have an external Western Digital Element 1TB 3.5 HDD that I mainly use for backups, and I would like put it to sleep when it is not used. 
I can issue the sleep command, and the HDD actually goes to sleep just fine.
(If I hold my hand on it and I can feel how it stops spinning)
[/FONT][INDENT][FONT=Courier New, Courier, monospace][COLOR=#993300]$> date; sudo hdparm -Y /dev/sdd
Sat Oct 17 07:28:07 EDT 2009
  
/dev/sdd:
 issuing sleep command[/COLOR][/FONT]
[/INDENT][FONT=Arial]But after about 30 sec the HDD starts spinning again. Please note that it is unmounted.
I've checked the logs, and noticed a message exactly when it starts spinning:
[/FONT][INDENT][FONT=Courier New, Courier, monospace][COLOR=#993300]$> tail -f /var/log/messages
  [/COLOR][/FONT][FONT=Courier New, Courier, monospace][COLOR=#993300]//...
  [/COLOR][/FONT][FONT=Courier New, Courier, monospace][COLOR=#993300]Oct 17 07:28:38 ubuntu kernel: [490580.112025] usb 2-3: reset high speed USB device using ehci_hcd and address 5[/COLOR][/FONT]
[/INDENT][FONT=Arial]I was wondering[/FONT][FONT=Arial] why this reset comes about 30 sec after I put the harddrive to sleep, and how I can disable it.

Many thanks,
Petru

[/FONT]

---

### Post by pietjanjaap on 2009-10-17
The anser to your problem i do not know.

But if it is your backup drive you should not have it connected to your pc.
A virus, lightning, broken hardware(power unit), a hacker, can damage your drive, so you should disconnect it.

---

### Post by Sam on 2009-10-17
Try this:

1) Install [sdparm](apt:sdparm) package.

2) Run```
sdparm -C stop /dev/sdd
```

---

### Post by petru.marginean on 2009-10-17
Thanks for reply.
I already did this, but the harddrive does not stop spinning when using the 'stop' sdparm command:[INDENT][FONT=Courier New][COLOR=DarkRed]$> sdparm -C stop /dev/sdd
    /dev/sdd: WD        10EAVS External   1.75
[/COLOR][/FONT][/INDENT]The only way to stop it was using hdparm.

Here is the kernel version I use:[INDENT][FONT=Courier New][COLOR=DarkRed]$> uname -a
Linux ubuntu 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux
[/COLOR][/FONT][/INDENT]Regards,
Petru

---

### Post by petru.marginean on 2009-10-18
Strangely enough the command:[INDENT][FONT=Courier New][COLOR=DarkRed]$> sudo hdparm -y /dev/sdd[/COLOR][/FONT][FONT=Courier New]
[/FONT][/INDENT]it actually works (puts the HDD in standby), but only if the drive IS mounted!
This solves my problem, but still I do not understand why it works this way.

I also re-checked the command:[INDENT][FONT=Courier New][COLOR=DarkRed]$> [/COLOR][/FONT][FONT=Courier New][COLOR=DarkRed]sudo sdparm -C start /dev/sdd[/COLOR]
  [/FONT][/INDENT]that works as well if the drive is mounted...

Regards,
Petru

---

### Post by Sam on 2009-10-18
Oops just seen that:

You did
```
$> sdparm -C stop /dev/sdd
```

But I forgot to say it meant to be run as root. May you check if this works ?
```
sudo sdparm -C stop /dev/sdd
```

---

### Post by petru.marginean on 2009-10-18
Sam,

You are right, my first post had a typo (missing 'sudo').
In fact I've tried the command as root, but it first failed because the drive was unmounted.

Now both commands:
  [FONT=Courier New][COLOR=DarkRed]$> sudo hdparms -y /dev/sdd 
[/COLOR][/FONT]and 
  [FONT=Courier New][COLOR=DarkRed]$> sudo sdparms -C stop /dev/sdd[/COLOR]
[/FONT]work fine, but only when the drive is mounted (not sure why, see my prev. post).

Also the command:
  [FONT=Courier New][COLOR=DarkRed]$> sudo hdparms -Y /dev/sdd [/COLOR]
[/FONT]  works even the drive is unmounted, but only for about 30 sec. 
Then some [COLOR=DarkRed]"[/COLOR][FONT=Courier New, Courier, monospace][COLOR=DarkRed]reset high speed USB device using ehci_hcd"[/COLOR][/FONT] event (noticed in the [FONT=Courier New][COLOR=DarkRed]/var/log/messages[/COLOR][/FONT]) makes the HDD wake up.

Regards,
Petru

---

### Post by petru.marginean on 2012-07-17
Closing this

---


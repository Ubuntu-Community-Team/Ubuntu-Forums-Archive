---
title: "Flash STILL not working!"
date: 2010-05-29
forum: General Help
---

### Post by mclizardman24 on 2010-05-29
Okay, I'm just about fed up with this. I was running a dual boot with Ubuntu 9.10 and Windows 7. Flash content would not work for the Ubuntu side,(by not working I mean screen flashing and sounds laggaing with actions) and I was told to make it a full partion, didn't want to do that so I just took an older system and loaded as the only os on that one. Flash still not working, same symptoms. Downloaded it from the flash website instead of using the software center, same thing. Thought about upgrading to the newesy version, adn requested a CD, due to the fact that it would take like 4 hours to upgrade because of my 56k modem (yeah, time for comcast). And when the CD got here, linux wouldnt even take it, because when I put it in the cd tray, i got an error! I tried to put it in the Windows computer, and when it asked me to restart the computer to complete installation, guess what, an ERROR! Man, i want to like ubuntu, but they are making it pretty hard...

---

### Post by clhsharky on 2010-05-29
mclizardman24

You have some hardware issues, please list.

```
lspci
ls -al /usr/lib/mozilla/plugins/
ls -al /usr/lib/firefox-addons/plugins
```

Sharky

---

### Post by Zerocool Djx on 2010-05-29
Step 1) Light match

Step 2) Find tack hammer

---

### Post by lidex on 2010-05-29
Go here:
[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html")

---

### Post by mclizardman24 on 2010-05-30
> **clhsharky said:**
> mclizardman24

You have some hardware issues, please list.

```
lspci
ls -al /usr/lib/mozilla/plugins/
ls -al /usr/lib/firefox-addons/plugins
```Sharky



This is what I got
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
jake@jake-desktop:~$ ls -al /usr/lib/mozilla/plugins/
total 364
drwxr-xr-x 2 root root   4096 2010-05-26 16:24 .
drwxr-xr-x 4 root root   4096 2009-10-28 17:00 ..
lrwxrwxrwx 1 root root     37 2010-05-26 16:24 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rw-r--r-- 1 root root   5456 2010-01-16 11:28 librhythmbox-itms-detection-plugin.so
-rw-r--r-- 1 root root  96200 2009-11-11 04:09 libtotem-cone-plugin.so
-rw-r--r-- 1 root root 104768 2009-11-11 04:09 libtotem-gmp-plugin.so
-rw-r--r-- 1 root root  71612 2009-11-11 04:09 libtotem-mully-plugin.so
-rw-r--r-- 1 root root  75904 2009-11-11 04:09 libtotem-narrowspace-plugin.so
jake@jake-desktop:~$ ls -al /usr/lib/firefox-addons/plugins
total 8
drwxr-xr-x 2 root root 4096 2009-10-20 05:46 .
drwxr-xr-x 5 root root 4096 2009-10-28 16:59 ..

```

---

### Post by mclizardman24 on 2010-05-30
> **lidex said:**
> Go here:
[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

I typed in what it said for 32-bit machines, and got this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package swfdec-mozilla

```

---

### Post by PinchedNerve on 2010-05-30
Does flash not work on Firefox but it does in Google Chrome?

---

### Post by lovinglinux on 2010-05-30
> **mclizardman24 said:**
> I typed in what it said for 32-bit machines, and got this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package swfdec-mozilla

```

If the commands stops because of that error, then run each command line separately, but in sequence or use the installation tool instead of the commands. You can download it it [here](http://flash-aid-extension.blogspot.com/).

---

### Post by mclizardman24 on 2010-05-30
I just now upgraded to version 10.04, and reinstalled flash, and guess what, it still dosent't work! Man, this is REALLLLLLLLLLLLLLY frustrating. I don't know of anyone else who has had this problem.

---

### Post by lovinglinux on 2010-05-30
> **mclizardman24 said:**
> I just now upgraded to version 10.04, and reinstalled flash, and guess what, it still dosent't work! Man, this is REALLLLLLLLLLLLLLY frustrating. I don't know of anyone else who has had this problem.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by mclizardman24 on 2010-05-30
> **lovinglinux said:**
> Install [FLASH-AID]("http://flash-aid-extension.blogspot.com") extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR=Sienna]**Flash Optimization**[/COLOR]]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html") section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").

Flash Aide didnt work either. Sounds still lagging with actions. Maybe not flash causing problem? Youtube works fine.

---

### Post by mclizardman24 on 2010-06-02
Well, i tried it with Chrome and it still doesn't work. What happens is that when I play games, everything lags and the sounds lag with the actions about 3-5 seconds. youtube videos still work fine though. Anything, anybody? Please?

---

### Post by lovinglinux on 2010-06-02
> **mclizardman24 said:**
> Well, i tried it with Chrome and it still doesn't work. What happens is that when I play games, everything lags and the sounds lag with the actions about 3-5 seconds. youtube videos still work fine though. Anything, anybody? Please?

What is your system specs?

Do you have the proper driver for your video card installed?

What is the output of the following commands:

```
uname -a
```

```
locate libflashplayer.so
```

```
ls /usr/lib/mozilla/plugins/
```

---

### Post by mclizardman24 on 2010-06-03
> **lovinglinux said:**
> What is your system specs?

Do you have the proper driver for your video card installed?

What is the output of the following commands:

```
uname -a
``````
locate libflashplayer.so
``````
ls /usr/lib/mozilla/plugins/
```

Specs: Radeon 7500
Pentium 4 2.66ghz
1gb ram
dont know the other stuff

command output

```

jake@jake-desktop:~$ uname -a
Linux jake-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
jake@jake-desktop:~$ locate libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so
jake@jake-desktop:~$ ls /usr/lib/mozilla/plugins/
flashplugin-alternative.so             libtotem-gmp-plugin.so
libjavaplugin.so                       libtotem-mully-plugin.so
librhythmbox-itms-detection-plugin.so  libtotem-narrowspace-plugin.so
libtotem-cone-plugin.so
jake@jake-desktop:~$ 

```

---

### Post by lovinglinux on 2010-06-03
It could be a pulseaudio issue. Unfortunately I'm not good in troubleshooting that and I'm not using Gnome anymore.

---

### Post by mclizardman24 on 2010-06-03
Okay, what do you suppose it is though, because this happened when I was running it with a dual boot with windows 7 as well.

---

### Post by lidex on 2010-06-04
> **mclizardman24 said:**
> Specs: Radeon 7500
Pentium 4 2.66ghz
1gb ram
dont know the other stuff

command output

```

jake@jake-desktop:~$ uname -a
Linux jake-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
jake@jake-desktop:~$ locate libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so
jake@jake-desktop:~$ ls /usr/lib/mozilla/plugins/
flashplugin-alternative.so             libtotem-gmp-plugin.so
libjavaplugin.so                       libtotem-mully-plugin.so
librhythmbox-itms-detection-plugin.so  libtotem-narrowspace-plugin.so
libtotem-cone-plugin.so
jake@jake-desktop:~$ 

```

Remove that 'flashplugin-alternative.so' from '/usr/lib/mozilla/plugins/' and see what happens when you restart your browser.

---

### Post by mclizardman24 on 2010-06-15
> **lidex said:**
> Remove that 'flashplugin-alternative.so' from '/usr/lib/mozilla/plugins/' and see what happens when you restart your browser.
 
how would I remove that?

---

### Post by lidex on 2010-06-16
In a terminal:
```
sudo rm /usr/lib/mozilla/plugins/flashplugin-alternative.so
```

---

### Post by lovinglinux on 2010-06-28
> **mclizardman24 said:**
> Okay, what do you suppose it is though, because this happened when I was running it with a dual boot with windows 7 as well.

If it doesn't work in Windows 7 as well, then I would try to clean up the CPU fan. Flash is very CPU intensive and can increase CPU temperature a lot. When that happens, performance goes down considerably and flash stutters.

---


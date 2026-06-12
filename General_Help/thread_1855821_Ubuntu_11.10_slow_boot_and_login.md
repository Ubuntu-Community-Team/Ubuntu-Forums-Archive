---
title: "Ubuntu 11.10 slow boot and login"
date: 2011-10-07
forum: General Help
---

### Post by zaphod777 on 2011-10-07
Hey guys I just upgraded to Ubuntu 11.10 and it is extremely slow booting and when logging in I will wait 20+ min and it does nothing. The whole time the fan is spinning like crazy. 

Does anyone know how I can fix this?

---

### Post by malinkb on 2011-10-24
I can confirm having the same issue. I don't really know whats trigger it. 
It dosen't take 20+ minutes for me, but it is some minutes slower than 11.04. 
I think the total bootprocess takes about 2-3 minutes

---

### Post by zaphod777 on 2011-10-24
> **malinkb said:**
> I can confirm having the same issue. I don't really know whats trigger it. 
It dosen't take 20+ minutes for me, but it is some minutes slower than 11.04. 
I think the total bootprocess takes about 2-3 minutes

try upgrading your BIOS. After I did the problem went away and now my machine works great.

---

### Post by pr3zident on 2011-10-24
> **malinkb said:**
> I can confirm having the same issue. I don't really know whats trigger it. 
It dosen't take 20+ minutes for me, but it is some minutes slower than 11.04. 
I think the total bootprocess takes about 2-3 minutes

same problem my kingring starts on startup when i want to type my password in i have to wait a minute or 3 to type my password in

---

### Post by oldtimer7777 on 2011-10-24
> **zaphod777 said:**
> Hey guys I just upgraded to Ubuntu 11.10 and it is extremely slow booting and when logging in I will wait 20+ min and it does nothing. The whole time the fan is spinning like crazy. 

Does anyone know how I can fix this?

You guys check your hardware? Like your HDD status in disk checking utility?:

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by oldtimer7777 on 2011-10-24
> **pr3zident said:**
> same problem my kingring starts on startup when i want to type my password in i have to wait a minute or 3 to type my password in

If you use a Live Stick of Ubuntu 11.10 on a USB Flash Drive, does it take less time to boot from the USB Flash Drive of Ubuntu???

---

### Post by Diskdoc on 2011-10-25
Having a similar problem, but AFTER I log in on the login screen. Takes minutes of harddrive trashing before I get to the desktop. Worked fine in Natty.

---

### Post by Spyderkid on 2011-10-25
Ok people, first of all, soon as it goes into the Ubuntu loader screen press any of the F keys, F5 for example, then it will change and some text will come up...

Please watch the text, and write down any errors you see. (or anything else that sounds bad)

Then please post these errors here :)....



**Also, did any of you install Ubuntu from CD?**

---

### Post by Diskdoc on 2011-10-25
Nope, upgraded. I had a look in dmesg and syslog, looks ok. Posted my bootcharts [here]("http://ubuntuforums.org/showthread.php?t=1861688&page=2"). But. The booting seems better now, a little.

---

### Post by Spyderkid on 2011-10-25
i upgraded too and it completely ruined my computer, so I had to do a re-install. You may have to do the same :S

---

### Post by Mark Phelps on 2011-10-25
Personally, I would advise AGAINST upgrading your BIOS, solely in the hopes of speeding up the boot, unless all of the following is true:
1) You are EXPERIENCE at upgrading BIOS
2) You have a way of saving off the current BIOS -- in such a manner that it can be recovered
3) You have a way of restoring the saved BIOS, without having to boot into an OS to do it.

As one person already discovered, BIOS upgrades can easily brick your PC.  You should not be doing them just because you want something to be faster.

---

### Post by sorabsuperstar on 2011-10-25
Having the same problem (boot screen comes up fast, but takes several minutes till username/pw can be keyed in). Quite annoying.

Unlike all the other 'bugs' in Oneric (like the bug Unity, and the bug Gtk3, and all the applications that buggraded to Gtk3....:P) this one cannot be fixed by using Kubuntu: kdm loging screen shows the same symptoms.

I cannot comprehend how people here can blame hardware and BIOS for this. I mean how comes the hardware only busts if one is trying to boot Oneric, but gets magically fixed as soon you boot an older version of Ubuntu, other Linus Distris, or Windows. Given that the same bug is present on many different hardware setups, this is yet another problem with Oneiric, and needs to be fixed in Oneric.

---

### Post by spindler on 2011-10-26
Ubuntu 11.10 is proving to be very buggy.    I thought it was tested prior to release?   What are we all part of the beta test team?

I am having continues issues with MySQL, PHPMYADMIN and my network connection goes down a lot....which means my website goes down. 

The rest of my network is fine.   I think it must be the new upgrade.

---

### Post by Spyderkid on 2011-10-26
it works perfectly fine now though, after re-installing. No problems at all

---

### Post by Spyderkid on 2011-10-26
I still suggest a re-install if any of you can. Just back up your important data onto Ubuntu 1 then re-install

---

### Post by spindler on 2011-10-26
What I did was upgrade from 11.04...which caused a whole bunch of issues.   

Are you suggesting I reformat my drive and then reinstall 11.10?... or do you suggest reattempting the upgrade?

---

### Post by diacetylM on 2011-10-27
I'm also finding Ubuntu 11.10 very slow. I upgraded a desktop from Ubuntu 11.04 to 11.10 and it's slow from the login screen. I installed Xubuntu 11.04 (and 11.10) btw. I noticed that two screen managers seemed to be loaded: the Xfce seemed to loaded first, then the gdm(?) loaded so that the Gnome backtop loaded ontop of the functional X desktop.  For example, there were no icons on the desktop. To fix this, I'd kill the xfce display manager process (I think) which would cause it to reload "overtop" of the Gnome background, so I'd get a functional desktop again. This got annoying so I installed Gnome, but it seems to me that two desktop / display managers are loading (I'm using an NVIDA driver, I'm talking about the process that controls the desktop background and behaviour, though the Gnome panel was functional as it's a different process I suppose).

After updating to Gnome, things started to get slow at login time. It seemed to be getting slower and slower so I switched from Gnome 3 to Gnome classic then Gnome classic with no effects. Now I basically can't do anything on the computer. If the screensaver comes on, it's 10 seconds before the prompt for the password comes up and about a minute before the desktop appears. Getting the application menu down takes half a minute, then getting the submenu to pop out takes another half minute.  The terminal takes 20 seconds to load and so does gedit. I wouldn't dare try loading Libre Office Writer.

I can't connect to my network and I'm prompted for the password which I enter easily (as I've got it memorized, plus I am using a 6 year old laptop right now which is running Xubuntu 11.04 and it works great and I'm not updating to 11.10 right now).

I'm about to get my desktop's specs but it's taking a while to get the terminal to give my mouse and keyboard focus so that I can sudo reboot ... waitin for the password prompt... waiting ... my computer should NOT be this slow.  It wasn't even this slow yesterday, so whatever the problem is, it seems to be getting worse.

Okay, I have a P4 2.8 GHz w/ 1 Gbytes RAM. 2 Hard drives, with Xubuntu 11.10 on the newer 120 Gbyte HD loaded from Grub. Even the Xubuntu splash screen (prior to the login screen) is so slow that it's not animated.

---

### Post by diacetylM on 2011-10-28
The process chewing up my processor was avgscand, so I uninstalled AVG.

However, there still seems to be a conflict due to lightdm and gdm loading. One background (via lightdm) loads a background and functional desktop, but then another background loads over top (so I can't access desktop icons). 

I tried "update-rc.d script remove" for a number of processes in rc5.d which I don't need (e.g. speech synthesizer, ALSA as my sound card doesn't work, etc.) but those processes still load. As the readme in /etc/rc5.d suggests, I renamed the processes I wanted to remove f/ S##whatever to K##whatever, but I used "remove" instead of "default" (and for script I used both the old and new names). The processes still start.

What I can't seem to figure out is how linux decides which greeter to boot, then how each session is defined and what loads based on those sessions.

Any suggestions?

---

### Post by Spyderkid on 2011-10-29
Im suggesting exactly that, back up your media onto ubuntu 1. insert live CD and choose format and isntall

---

### Post by dboy on 2011-10-30
Same thing here. Did the upgrade install from 11.04 to 11.10. Computer now trashed. Upgrade appeared to work. Tried a second reboot due to system being extremely sluggish. Now after second reboot, box is dead. This version is garbage. Highly recommend NOT upgrading unless you enjoy wasted time and data loss. It's not your BIOS, it's not a "hardware issue". The issue is that this is a crap install.

---

### Post by Technium on 2011-11-10
Same problem for me. Upgraded from 11.04 on a *fast* laptop to 11.10 and now have to sit and wait a minute after logging in before the desktop comes up. This used to take mere seconds.

Really if upgrade is going to continue be offered as a valid option then the first response can't be "you should clean install".

What can I do to provide extra information?

---

### Post by Spyderkid on 2011-11-10
As I have said, the only solution I have found is to re-install your computer with Ubuntu 11.10

(back up your files first)

---

### Post by Technium on 2011-11-10
Indeed, you said that. However, I still feel that someone must care about this issue and would prefer some diagnostics before I flatten the machine.

Here's the bootchart. Although it looks like auto-login is not enabled, it really is. Note this is Unity2D as I have stability issues with regular Unity (and it exhibits the same problems).

[http://static.inky.ws/image/810/image.jpg]("http://static.inky.ws/image/810/image.jpg")

Using: nVidia Corporation GF108 [Quadro NVS 4200M].

---

### Post by jfd3220 on 2011-11-27
I am having this problem as well. The major slowdown is after login. I used to be at the desktop in less that 2 seconds.  Now it's taking about 20 seconds.  I upgraded from 11.04.  Has nobody figured out what the problem is?

---

### Post by jfd3220 on 2011-12-03
As Spyderkid mentioned it looks like reinstallation is the fix.  Something seems to go wrong when upgrading.  I created a virtual machine with 11.10 and it boots very quickly and it's only a few seconds from login to desktop.

---

### Post by jfd3220 on 2011-12-03
Well so much for that. Formatted the drive and reinstalled 11.10 and it's taking forever to load again.  The boot time to the login screen is short but it is taking way too long from login to desktop.

---

### Post by Spyderkid on 2011-12-03
jfd3220, can you give me a few of your computer specs?

eg, RAM, HardDisk size (or SSD size), you using 64bit? so on

---

### Post by jfd3220 on 2011-12-03
I have a Lenovo T410 with Intel core i7 620M, intel X25-V 40GB SSD, and 4GB of RAM.  I have been using 64-bit Ubuntu on this laptop since I bought it.

---

### Post by Spyderkid on 2011-12-03
ok, your specs are fine...

It may possibly be the 64bit, AMD64 can do very random things sometimes, it's not as stable as i386...

---

### Post by inqusitor on 2012-02-21
Has anyone found a true fix? I have very slow boots of like 4 mins to get to the log in screen. I have also noticed that is I plug in a usb to transfer data it takes from 5 to 10 mins to even mount and see it.  I have windows xp and ubuntu 9.04 and both load fast and have none of the problems loading and lagging I see with my 11.10.

---

### Post by zaphod777 on 2012-02-21
see if you can update your BIOS that fixed my problem.

---

### Post by Normalex on 2012-03-05
This is the slowest part after I entered the password.

less /var/log/lightdm/lightdm.log

[+4.47s] DEBUG: Prompt greeter with 1 message(s)
[+4.47s] DEBUG: Wrote 44 bytes to greeter

[+15.35s] DEBUG: Read 8 bytes from greeter
[+15.35s] DEBUG: Read 14 bytes from greeter

where did these 14 seconds went?

auth.log

Mar  4 23:39:26 novels-computer dbus[949]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.32" (uid=104 pid=1914 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1525 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Mar  4 23:39:37 novels-computer lightdm: pam_unix(lightdm:session): session closed for user lightdm
Mar  4 23:39:38 novels-computer lightdm: pam_unix(lightdm:session): session opened for user novels by (uid=0)
Mar  4 23:39:38 novels-computer lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Mar  4 23:40:10 novels-computer polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.53 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Mar  4 23:40:24 novels-computer dbus[949]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.63" (uid=1000 pid=2159 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1525 comm="/usr/sbin/console-kit-daemon --no-daemon ")

---

### Post by xianbei on 2012-03-12
I've had this issue as well. However, mine did not start with the upgrade to 11.10.

With 11.10 everything was good. Then, after trying to change my grub background from purple to whatever i ended up with the cheezy Debian universe background. At this point, bootup was still normal.

Then  i upgraded the Windows Vista partition to service pack 2 to accommodate MS Access 2010, and that's when the slowdown occurred.

I have read some that a video driver mismatch can create this delay.

Anyone?

Thanks!

---

### Post by LuckyNeo on 2012-03-29
For me, slow boot is still occurring after reinstall.

---

### Post by vincrap on 2012-04-16
Hi, I'm sort of new to Ubuntu, so bear with me if I'm a little slow at it. After having a crappy distro on my other laptop, I decided with my new netbook I'd just use ubuntu proper. A couple days ago I installed it, replacing XP entirely. My boot up now take minutes. Here's my dmesg:

```
[    2.136170]  sda: sda1 sda2 < sda5 >
[    2.137282] sd 2:0:0:0: [sda] Attached SCSI disk
[    9.016441] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  563.537524] udevd[285]: starting version 173
[  563.621857] lp: driver loaded but no devices found
[  563.632241] Adding 1037308k swap on /dev/sda5.  Priority:-1 extents:1 across:1037308k 

```

That's somewhere in the middle, and it just keeps going up from there. Any ideas?

---

### Post by prismctg on 2012-04-16
TRy removing some start-up application.. may be it will help u .

---

### Post by vincrap on 2012-04-16
The only startup app that runs is the GNOME login sound

---


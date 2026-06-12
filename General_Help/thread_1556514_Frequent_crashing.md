---
title: "Frequent crashing"
date: 2010-08-19
forum: General Help
---

### Post by AVHATION on 2010-08-19
I am experiencing frequent crashing, not apparently linked to any particular keyboard action. System Log File Viewer shows that immediately before each  crash Pulse Audio was trying to do something; this is a typical example:
Aug 19 17:50:48 henry-desktop kernel: [   16.645113] type=1505 audit(1282236648.852:8):  operation="profile_replace" pid=642 name="/usr/lib/connman/scripts/dhclient-script"
Aug 19 17:50:48 henry-desktop kernel: [   16.735389] type=1505 audit(1282236648.940:9):  operation="profile_load" pid=708 name="/usr/bin/evince"
Aug 19 17:50:49 henry-desktop kernel: [   16.827981] type=1505 audit(1282236649.032:10):  operation="profile_load" pid=708 name="/usr/bin/evince-previewer"
Aug 19 17:50:49 henry-desktop kernel: [   16.849772] type=1505 audit(1282236649.056:11):  operation="profile_load" pid=708 name="/usr/bin/evince-thumbnailer"
Aug 19 17:50:49 henry-desktop kernel: [   17.376171] apm: BIOS not found.
Aug 19 17:50:58 henry-desktop pulseaudio[1045]: ratelimit.c: 2 events suppressed
Aug 19 17:51:21 henry-desktop pulseaudio[1296]: ratelimit.c: 4 events suppressed
Aug 19 17:51:27 henry-desktop pulseaudio[1296]: ratelimit.c: 1 events suppressed


Above are the current latest entries, before the next crash.  I have reinstalled Ubuntu and updated and upgraded it to 10.4. In an effort to solve the problem prior to that, I deleted all references to Pulseaudio in Synaptic with the apparent result that sometime later the login screen would not work which why I had to resort to reinstalling Ubuntu.  The symptom has carried over from my previous machine to this one; the only common hardware is the second hard drive which contains my files, no OS.  The first drive has both Win XP and Ubuntu in different partitions. Of possible relevance may be that although number lock is set to on in the BIOS, I have to set it myself after starting. One final clue, to restart the frozen machine I have been holding Control Atl Delete for several seconds with apparent success.

---

### Post by sydbat on 2010-08-19
> **AVHATION said:**
> I am experiencing frequent crashing, not apparently linked to any particular keyboard action. System Log File Viewer shows that immediately before each  crash Pulse Audio was trying to do something; this is a typical example:
Aug 19 17:50:48 henry-desktop kernel: [   16.645113] type=1505 audit(1282236648.852:8):  operation="profile_replace" pid=642 name="/usr/lib/connman/scripts/dhclient-script"
Aug 19 17:50:48 henry-desktop kernel: [   16.735389] type=1505 audit(1282236648.940:9):  operation="profile_load" pid=708 name="/usr/bin/evince"
Aug 19 17:50:49 henry-desktop kernel: [   16.827981] type=1505 audit(1282236649.032:10):  operation="profile_load" pid=708 name="/usr/bin/evince-previewer"
Aug 19 17:50:49 henry-desktop kernel: [   16.849772] type=1505 audit(1282236649.056:11):  operation="profile_load" pid=708 name="/usr/bin/evince-thumbnailer"
Aug 19 17:50:49 henry-desktop kernel: [   17.376171] apm: BIOS not found.
Aug 19 17:50:58 henry-desktop pulseaudio[1045]: ratelimit.c: 2 events suppressed
Aug 19 17:51:21 henry-desktop pulseaudio[1296]: ratelimit.c: 4 events suppressed
Aug 19 17:51:27 henry-desktop pulseaudio[1296]: ratelimit.c: 1 events suppressed


Above are the current latest entries, before the next crash.  I have reinstalled Ubuntu and updated and upgraded it to 10.4. In an effort to solve the problem prior to that, I deleted all references to Pulseaudio in Synaptic with the apparent result that sometime later the login screen would not work which why I had to resort to reinstalling Ubuntu.  The symptom has carried over from my previous machine to this one; the only common hardware is the second hard drive which contains my files, no OS.  The first drive has both Win XP and Ubuntu in different partitions. Of possible relevance may be that although number lock is set to on in the BIOS, I have to set it myself after starting. One final clue, to restart the frozen machine I have been holding Control Atl Delete for several seconds with apparent success.If you can, remove the HDD that has only your files on it and run Ubuntu for a few hours and see if it crashes. If not, then you have a bad HDD that is causing your problems.

Either way, back everything up so you do not lose any of your data.

---

### Post by AVHATION on 2010-08-20
Thank you, I'll try your suggestion later.  I have just run Disk Utility which shows both discs to be "Good".  However, it shows that my OS disk has a read error rate value of 175945830 while my data disc shows a value of only 231 ( also "Good").  Do you think that this point towards a faulty OS disc rather than the data disc?

---

### Post by AVHATION on 2010-08-21
Disconnected the data drive (the one which I transferred from old system to new) and I have had another crash. The only common factor now is Ubuntu 10.4 I believe. The OS disc SMART data is still showing "Healthy".

---

### Post by AVHATION on 2010-08-22
Another reason for suspecting Ubuntu is that when I was able to boot into WinXP there was never a problem.  Unfortunately I have lost that facility when  reloading Ubuntu and inadvertently overwriting the WinXP partition.

---

### Post by AVHATION on 2010-08-26
I have now reloaded again 10.04.01 from a downloaded CD i.e. not by upgrading on a brand new hard drive.  The first crash has occurred after about 10 mins, while adjusting the screensaver settings. I am really disappointed that 10.4 is not a stable upgrade. Can anyone advise me how to diagnose the problem?

---

### Post by AVHATION on 2010-11-02
My problem continues. I have eliminated hardware faults and Win XP works fine. Can anyone steer me towards a method for finding out what was going on moments before each Ubuntu 10.4 crash?

---

### Post by matt_symes on 2010-11-02
Hi

After it freezes do the caps lock or scroll lock lights flash?

Kind regards

---

### Post by AVHATION on 2011-01-11
Hi Matt, 
Sorry not to have responded before now; no lights appear to flash on crash.  However, I think may have a workaround. I remembered that  trying to set the screensaver to not operate at any time (to eliminate a variable) 
always caused a crash so I have removed all reference to screensaver with  Synaptic.  So far all is well!

---

### Post by AVHATION on 2011-04-01
My symptoms continue.  Curiously, even though I have removed all references to screensaver via Synaptic the machine still sleeps after about 10 mins.  The crashing is apparently random but I do wonder if there is a way to tell what happens at the moment of the crash? Win XP continues to be fine.

---

### Post by matt_symes on 2011-04-01
Hi

Yes. These things are a pain.

Try to eliminate X first. Have a look in /var/log/xorg.0.log, /var/log/messages and ~/.xsession-errors. Disable compiz.

Kind regards

---

### Post by AVHATION on 2011-04-13
Very helpful advice, thanks.  I think that the last crash at 2049 hours was preceded by the following:

Apr 13 20:49:08 henry-desktop pulseaudio[991]: ratelimit.c: 3 events suppressed
Apr 13 20:49:16 henry-desktop pulseaudio[1199]: ratelimit.c: 8 events suppressed
Apr 13 20:54:04 henry-desktop kernel: Kernel logging (proc) stopped.
Apr 13 20:54:04 henry-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="623" x-info="http://www.rsyslog.com"] exiting on signal 15.
Apr 13 20:54:38 henry-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Apr 13 20:54:38 henry-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="609" x-info="http://www.rsyslog.com"] (re)start
Apr 13 20:54:38 henry-desktop rsyslogd: rsyslogd's groupid changed to 103
Apr 13 20:54:38 henry-desktop rsyslogd: rsyslogd's userid changed to 101
Apr 13 20:54:38 henry-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 13 20:54:38 henry-desktop kernel: [    0.000000] Initializing cgroup subsys cpu

Therefore I have used the Ubuntu Software Centre to remove all traces of Pulseaudio. Compiz is still installed - I'll delete that after the next crash.
Thanks again.

---

### Post by AVHATION on 2011-04-13
Unfortunately, having made the changes above,  I cannot start Ubuntu.

---

### Post by matt_symes on 2011-04-13
Hi

> Compiz is still installed - I'll delete that after the next crash.
Thanks again.

You did not want to delete Compiz, just disable it. Did you uninstall it ?

> Unfortunately, having made the changes above, I cannot start Ubuntu.

What changes did you make ?

Kind regards

---

### Post by AVHATION on 2011-04-15
Hi Matt,
I deleted all references to Pulseaudio, using the Ubuntu Software centre, including the related items which it said I could remove.  I did not change anything relating to Compiz.  Is there a way to start up in the previous configuaration (like Restore in Windows?)?  I have tried using the screen where I choose between Ubuntu (many versions listed) and Windows without success.
P.S. When starting the problem is that the automatic login does not work, neither does choosing "other" login.

---

### Post by matt_symes on 2011-04-16
Hi

> **AVHATION said:**
> Is there a way to start up in the previous configuaration (like Restore in Windows?)?

That depends on what you have changed. You can reset Gnome to its defaults but apart from that, no.

> I have tried using the screen where I choose between Ubuntu (many versions listed) and Windows without success.

That will just select different versions of the kernel. The different kernels will still use the configuration settings installed and the applications and services already configured.

> P.S. When starting the problem is that the automatic login does not work, neither does choosing "other" login.

I am not quite with you here. If you want GDM to log you in directly then have a look at...

System->Administration->Login and select automatically login and select your user name.

If it is taking you to the command line when you start then there are a number if reasons this can happen.

Kind regards

---

### Post by AVHATION on 2011-04-16
Hi Matt,
The snag is that I cannot reach the screen which gives me the menus for Applications, System etc.  The screen simply flashes black and white veretical bars and I have to switch off or use control/Alt/Delete to restart. No command promtt option appears.  Is there some other way to get at the System menu to revert it to manual?
Regards,
Henry

---

### Post by linuxmaniack on 2011-04-16
It may be your hard disk. Go to system, Administration, then disk utility. Go to the Hard disk that ubuntu is installed. Somewhere on screen, you will find the disk's health . If you are using ubuntu 11.04, or unity, click on the ubuntu logo on the top left of the screen, and in the search bar, type in disk utility, And click on it.   Hope this helps,

Linuxmaniack,

---

### Post by matt_symes on 2011-04-16
Hi

> **linuxmaniack said:**
> It may be your hard disk. Go to system, Administration, then disk utility. Go to the Hard disk that ubuntu is installed. Somewhere on screen, you will find the disk's health . If you are using ubuntu 11.04, or unity, click on the ubuntu logo on the top left of the screen, and in the search bar, type in disk utility, And click on it.   Hope this helps,

Linuxmaniack,

I concur. Check your hardware. Perform a memory test. Check cables, seatings, temperature, remove dust.

> Is there some other way to get at the System menu to revert it to manual?

Not quite sure what you mean by this. If you want to boot to command prompt then edit your kernel command line in grub.

On the grub kernel select screen, select your kernel and press **e** to edit it.

Add the word **single** to the end and remove quiet splash. My kernel line would be change from this

```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=78ea72dd-14de-48b7-ad0c-e3d3149dc405 ro quiet splash
```

to this

```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=78ea72dd-14de-48b7-ad0c-e3d3149dc405 ro single
```

Press ctrl + x  will continue the boot.

If you can use the command line from the console have a play. Does it crash ?

Is that what you mean by manual ? If not, my apologies.

Kind regards

---

### Post by AVHATION on 2011-04-28
Thanks Linuxmaniac - I cannot log in to Ubuntu to perform the checks you recommend.  However, the machine continues to work ok with Windows so hopefully the discs and RAM are ok. 

Matt- thanks for your patience. I tried editing the grub by deleting "quiet splash" and adding "single" to the end of that line to no avail.  

However, I noticed that the more recent grubs all were prefixed with:

recordfail
insmod ext2
set root ='(hd0,9)'

I tried deleting "recordfail" to no avail - "recordfail" reappeared when I looked again.

Interestingly, when I looked at the grub for  much earlier version of Ubuntu, ( orange lifebelt logo) record fail was not present and I found that it loaded ok. I had to log in manually.

I really want to get the latest version working and I think the problem may in the automatic login procedure or the retained password detail. I have tried logging in as "another" without success. Is there some way to by-pass the automatic login screen by changing something via grub?

---

### Post by linuxmaniack on 2011-04-29
Try using a live cd?

---

### Post by AVHATION on 2011-04-29
Good idea  Linuxmaniac.  I booted from a CD (I did not install).  First time all went well but when using System Testing the mouse pointer disappeared from view.  Reloaded but got the flashing screen problem before load was completed.  Reloaded again and used Disk Utility - file systems in all checkable partitions proved to be "clean" and both discs were "Healthy". I repeated the tests several times; twice I got a crash report, the first of which which I submitted as a bug report. (Judging by the associated bug reports this is not an uncommon problem.)  It's nice to see a Ubuntu screen again and I am tempted to re-install it; the trouble is I would lose all my pictures and Firefox bookmarks, unless someone knows how to get at then without successfully starting up the OS.

---

### Post by matt_symes on 2011-05-02
Hi

> the trouble is I would lose all my pictures and Firefox bookmarks, unless  someone knows how to get at then without successfully starting up the  OS.


You can do all that from the live CD and an external hard/pen drive. 

Start from the LiveCD and mount the external hard drive. Copy your pictures accross to the external hard drive.

For firefox you can copy across the hidden .mozilla directory in your home directory or chroot into the hard drive on your PC and export them from firefox. Can i also suggest something like Xmarks. It allows you to sync your bookmarks to the cloud. It's free.

[www.xmarks.com/](www.xmarks.com/)

If you reinstall, can i suggest a seperate home directory and maybe a seperate data directory for you data files. 

To give you an example. I have a root partition, a home partition and two data partitions for 10.04 LTS. The two data partitions are shared across all the distributions installed on my laptop.

Kind regards

---

### Post by AVHATION on 2011-05-17
Thanks Matt. I don't think I can retrieve my pictures because they are stored within the OS (Graphics - F-Spot etc) or within the associated root-pictures etc. to which I cannot access.  Using the live cd and "pictures" reveals nothing.

Before I can reload Ubuntu I think I need to find out which partition the troublesome one is on and overwrite it - any ideas?

By the way, I have used the recovery modes of "repair broken packages" of which there were 15 or so, and "update grub loader".  When I "resume boot" I can enter my login name and password and get a Welcome to Ubuntu line and $ which I think is the command line. When I command "startx" the screen goes black with just the mouse arrow showing.  Is there some way I can use this command line to work round the apparent login issue?  If not I'll resort to the reload.
Regards,
Henry

---

### Post by AVHATION on 2011-05-18
Just to let you know I have reloaded 10.04, formatting the partition which contained the previous copy.  Fingers crossed now!

Thanks again for your efforts and interest.
Regards,
Henry

---

### Post by AVHATION on 2011-05-19
Doom gloom!  My crashing symptom has reappeared after several good sessions and over 2 hours into the one which ended in the crash (flashing black screen) at 1527hr. Ubuntu had not been updated since the initial download.  Screensaver settings had not been even looked at. The machine had been left unattended for a while downloading camera images via F-spot.
 The last few lines of Syslog log are below:

May 19 15:27:01 henry-desktop acpid: client connected from 1178[108:114]
May 19 15:27:01 henry-desktop acpid: 1 client rule loaded
May 19 15:27:04 henry-desktop pulseaudio[1053]: ratelimit.c: 4 events suppressed
May 19 15:27:04 henry-desktop kernel: [   23.328042] eth0: no IPv6 routers present
May 19 15:27:12 henry-desktop ntpdate[1286]: adjust time server 91.189.94.4 offset 0.056191 sec
May 19 15:28:03 henry-desktop AptDaemon: INFO: Initializing daemon
May 19 15:34:03 henry-desktop AptDaemon: INFO: Quiting due to inactivity
May 19 15:34:03 henry-desktop AptDaemon: INFO: Shutdown was requested


Again, Pulseaudio seems to have been at work for the first time, shortly before the crash.


Any new ideas guys?
Regards,
Henry

---

### Post by AVHATION on 2011-05-27
Further information from Xlog after the last crash at 1802 hr today is copied below. A clue continues to be Pulseaudio hitting a rate limit,  Also I was using the machine so why the screensaver  warning  appears I cannot imagine. Could a virus be at work? Any ideas for dealing with this long-standing problem? Windose continues to be 100% reliable.
Comments welcome.
Henry

 May 27 17:17:01 henry-desktop CRON[3741]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 27 17:44:43 henry-desktop pulseaudio[1071]: ratelimit.c: 1 events suppressed
May 27 18:02:25 henry-desktop kernel: [12415.176015] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 27 18:02:25 henry-desktop kernel: [12415.176030] render error detected, EIR: 0x00000000
May 27 18:02:25 henry-desktop kernel: [12415.176050] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 848853 at 848852)
May 27 18:02:27 henry-desktop kernel: [12417.012017] [drm:i915_gem_idle] *ERROR* hardware wedged
May 27 18:02:27 henry-desktop gnome-session[978]: WARNING: Detected that screensaver has left the bus
May 27 18:02:28 henry-desktop acpid: client 869[0:0] has disconnected
May 27 18:02:28 henry-desktop acpid: client connected from 4100[0:0]
May 27 18:02:28 henry-desktop acpid: 1 client rule loaded
May 27 18:02:29 henry-desktop kernel: [12418.794321] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
May 27 18:02:29 henry-desktop kernel: [12419.124010] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 27 18:02:29 henry-desktop kernel: [12419.124019] render error detected, EIR: 0x00000000
May 27 18:02:29 henry-desktop kernel: [12419.124851] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 848860 at 848852)
May 27 18:02:31 henry-desktop kernel: [12421.188015] [drm:i915_gem_idle] *ERROR* hardware wedged
May 27 18:02:31 henry-desktop acpid: client 4100[0:0] has disconnected
May 27 18:02:32 henry-desktop acpid: client connected from 4108[0:0]
May 27 18:02:32 henry-desktop acpid: 1 client rule loaded
May 27 18:02:32 henry-desktop kernel: [12422.314112] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
May 27 18:02:33 henry-desktop kernel: [12422.652011] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 27 18:02:33 henry-desktop kernel: [12422.652022] render error detected, EIR: 0x00000000
May 27 18:02:33 henry-desktop kernel: [12422.652855] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 848862 at 848852)
May 27 18:02:35 henry-desktop kernel: [12424.704020] [drm:i915_gem_idle] *ERROR* hardware wedged
May 27 18:02:35 henry-desktop acpid: client 4108[0:0] has disconnected
May 27 18:02:35 henry-desktop acpid: client connected from 4116[0:0]
May 27 18:02:35 henry-desktop acpid: 1 client rule loaded
May 27 18:02:36 henry-d

---

### Post by mouse2mouse on 2011-06-19
I think you should download the OS again and burn it to another DVD. It's possible that something happened either during the original download or the DVD creation. If this doesn't help you, try another OS like Crunchbang and see if that works, so you can know for sure if it's the system or the computer. I've bought DVD's to load other operating systems only to have to download it myself, because the DVD I bought was screwed up. Ubuntu has been about the most trouble free system I have used. The only other one I depended on while learning what I can is Fedora. Good luck to you.

---

### Post by AVHATION on 2011-06-21
I think I have a workaround to overcome my problem. After reloading Ubuntu 10.4 (LTS) for the nth time and studying Syslog I found some lines indicating errors including the following sequence:

Jun 18 21:28:34 henry-desktop kernel: [ 9396.633117] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 143927 at 143923)
Jun 18 21:28:36 henry-desktop kernel: [ 9398.544018] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun 18 21:28:36 henry-desktop gnome-session[971]: WARNING: Detected that screensaver has left the bus
Jun 18 21:28:37 henry-desktop acpid: client 850[0:0] has disconnected
Jun 18 21:28:37 henry-desktop acpid: client connected from 1565[0:0]
Jun 18 21:28:37 henry-desktop acpid: 1 client rule loaded
Jun 18 21:28:37 henry-desktop pulseaudio[1561]: pid.c: Stale PID file, overwriting.
Jun 18 21:28:37 henry-desktop pulseaudio[1561]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-lysrGLPuDp: Connection refused
Jun 18 21:28:38 henry-desktop kernel: [ 9400.351255] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jun 18 21:28:38 henry-desktop kernel: [ 9400.684014] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung


I know not what any of this actually means but by Googling "Hangcheck timer elapsed" I found another forum ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507504?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507504?comments=all))
which described an unsolved issue with Ubuntu when run by a particular chipset (Intel i845). This happened to be my chipset, so I took the recommended actions of removing Compiz (using Ubuntu Software Centre), setting the screensaver to "blank screen", and setting the power saving options to "never".  No more crashes to date.  (My earlier effort to fix by removing Pulesaudio was a blind alley.) Hopefully the issue between the Intel chipsets affected and Ubuntu will be solved expertly in due course.  In the meantime I am pleased to have got my Ubuntu back.

I hope this helps others who may encounter the same issue.

---

### Post by AVHATION on 2011-06-21
Thanks Mousetomouse for your ideas above. I was confident about my hardware because Win XP was trouble free. 
Regards,
Avhation

---

### Post by AVHATION on 2011-08-12
My crashing symptoms continue, mostly once per day or so, but sometimes more frequently.  It seems that my i845 chipset is not well suited to Lucid. Can anyone advise if the latest Ubuntu is any better suited or should I revert to an earlier version than Lucid?

---

### Post by AVHATION on 2011-08-15
The answer is here:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

I hope a fix will emerge in due course.

---


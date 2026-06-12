---
title: "Sometimes, no login screen with 10.10"
date: 2011-01-26
forum: General Help
---

### Post by quadproc on 2011-01-26
Have you seen this?

Sometimes, perhaps 10-15% of the time, when I boot Ubuntu version 10.10 the system gets to the  point where it plays the login drumroll but it never displays the login window.  Instead, the splash window remains on the screen but the dots are not changing.  Since I cannot type into the nonexistent login box I cannot proceed so I push the reset button.  The next boot seems to work OK every time.

I have not seen this problem on any of the other Ubuntu releases that I have used.

This system has an Intel 950 CPU, 6 GiB RAM, several SATA disks.  Using the Mesa driver that came as part of 10.10 and two HD4870 graphics cards set up for crossfire.  There is no xorg.conf file.

Do you know what is causing this?  Any ideas on where to look or what to try?  Thanks.

quadproc

---

### Post by gordintoronto on 2011-01-26
Does this system crash only happen when the computer is cold?

---

### Post by quadproc on 2011-01-26
> **gordintoronto said:**
> Does this system crash only happen when the computer is cold?
An excellent question, but no, the problem can occur after the system has been on for hours or it may occur on a fresh cold start.

Since you mentioned temperature, my sensors show various temperatures between 38 (CPU and mother board) down to 30 (ISA adaptor).  The case is a HAF.

quadproc

---

### Post by Krytarik on 2011-01-27
Anything against to install/run the proprietary video driver?
If not, try installing them via "System -> Administration -> Additional Drivers".
Could be possible that the default driver can't handle a crossfire setup.

---

### Post by quadproc on 2011-01-27
> **Krytarik said:**
> Anything against to install/run the proprietary video driver?
If not, try installing them via "System -> Administration -> Additional Drivers".

I do have reservations regarding fglrx: it can really louse up a system if I forget to remove it before upgrading the kernel, for example.  And I read that the ATI drivers will fall into support hole soon due to the various development activities associated with Ubuntu and fglrx and Xorg giving way to Wayland.  But I suppose that I could try installing it to see if it is different.  Such a test might help to identify which package is causing the problem.> 
Could be possible that the default driver can't handle a crossfire setup.I do not think so.  Crossfire has to be explicitly enabled to make it active and I suspect that the Mesa package does not enable it by default.

I do have additional info regarding the problem: the last time that it happened, I used ssh from another computer to connect to the system running 10.10 and ssh worked fine.  So I did a ps -e and I have included that output below.  I also tried the assumption that it was only the display that was wrong so I clicked the mouse button and, sure enough, I was able to enter my password (in the blind).  The system logged me in but I still was stuck with the dead splash screen so I used a reset to get out.

Here is the ps output:
 ```
 PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 migration/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 migration/2
   10 ?        00:00:00 ksoftirqd/2
   11 ?        00:00:00 watchdog/2
   12 ?        00:00:00 migration/3
   13 ?        00:00:00 ksoftirqd/3
   14 ?        00:00:00 watchdog/3
   15 ?        00:00:00 migration/4
   16 ?        00:00:00 ksoftirqd/4
   17 ?        00:00:00 watchdog/4
   18 ?        00:00:00 migration/5
   19 ?        00:00:00 ksoftirqd/5
   20 ?        00:00:00 watchdog/5
   21 ?        00:00:00 migration/6
   22 ?        00:00:00 ksoftirqd/6
   23 ?        00:00:00 watchdog/6
   24 ?        00:00:00 migration/7
   25 ?        00:00:00 ksoftirqd/7
   26 ?        00:00:00 watchdog/7
   27 ?        00:00:00 events/0
   28 ?        00:00:00 events/1
   29 ?        00:00:00 events/2
   30 ?        00:00:00 events/3
   31 ?        00:00:00 events/4
   32 ?        00:00:00 events/5
   33 ?        00:00:00 events/6
   34 ?        00:00:00 events/7
   35 ?        00:00:00 cpuset
   36 ?        00:00:00 khelper
   37 ?        00:00:00 netns
   38 ?        00:00:00 async/mgr
   39 ?        00:00:00 pm
   41 ?        00:00:00 sync_supers
   42 ?        00:00:00 bdi-default
   43 ?        00:00:00 kintegrityd/0
   44 ?        00:00:00 kintegrityd/1
   45 ?        00:00:00 kintegrityd/2
   46 ?        00:00:00 kintegrityd/3
   47 ?        00:00:00 kintegrityd/4
   48 ?        00:00:00 kintegrityd/5
   49 ?        00:00:00 kintegrityd/6
   50 ?        00:00:00 kintegrityd/7
   51 ?        00:00:00 kblockd/0
   52 ?        00:00:00 kblockd/1
   53 ?        00:00:00 kblockd/2
   54 ?        00:00:00 kblockd/3
   55 ?        00:00:00 kblockd/4
   56 ?        00:00:00 kblockd/5
   57 ?        00:00:00 kblockd/6
   58 ?        00:00:00 kblockd/7
   59 ?        00:00:00 kacpid
   60 ?        00:00:00 kacpi_notify
   61 ?        00:00:00 kacpi_hotplug
   62 ?        00:00:00 ata_aux
   63 ?        00:00:00 ata_sff/0
   64 ?        00:00:00 ata_sff/1
   65 ?        00:00:00 ata_sff/2
   66 ?        00:00:00 ata_sff/3
   67 ?        00:00:00 ata_sff/4
   68 ?        00:00:00 ata_sff/5
   69 ?        00:00:00 ata_sff/6
   70 ?        00:00:00 ata_sff/7
   71 ?        00:00:00 khubd
   72 ?        00:00:00 kseriod
   73 ?        00:00:00 kmmcd
   74 ?        00:00:00 khungtaskd
   75 ?        00:00:00 kswapd0
   76 ?        00:00:00 ksmd
   77 ?        00:00:00 aio/0
   78 ?        00:00:00 aio/1
   79 ?        00:00:00 aio/2
   80 ?        00:00:00 aio/3
   81 ?        00:00:00 aio/4
   82 ?        00:00:00 aio/5
   83 ?        00:00:00 aio/6
   84 ?        00:00:00 aio/7
   85 ?        00:00:00 ecryptfs-kthrea
   86 ?        00:00:00 crypto/0
   87 ?        00:00:00 crypto/1
   88 ?        00:00:00 crypto/2
   89 ?        00:00:00 crypto/3
   90 ?        00:00:00 crypto/4
   91 ?        00:00:00 crypto/5
   92 ?        00:00:00 crypto/6
   93 ?        00:00:00 crypto/7
   98 ?        00:00:00 scsi_eh_0
   99 ?        00:00:00 scsi_eh_1
  101 ?        00:00:00 scsi_eh_2
  102 ?        00:00:00 scsi_eh_3
  105 ?        00:00:00 kstriped
  106 ?        00:00:00 kmpathd/0
  107 ?        00:00:00 kmpathd/1
  108 ?        00:00:00 kmpathd/2
  109 ?        00:00:00 kmpathd/3
  110 ?        00:00:00 kmpathd/4
  111 ?        00:00:00 kmpathd/5
  112 ?        00:00:00 kmpathd/6
  113 ?        00:00:00 kmpathd/7
  114 ?        00:00:00 kmpath_handlerd
  115 ?        00:00:00 ksnapd
  116 ?        00:00:00 kondemand/0
  117 ?        00:00:00 kondemand/1
  118 ?        00:00:00 kondemand/2
  119 ?        00:00:00 kondemand/3
  120 ?        00:00:00 kondemand/4
  121 ?        00:00:00 kondemand/5
  122 ?        00:00:00 kondemand/6
  123 ?        00:00:00 kondemand/7
  124 ?        00:00:00 kconservative/0
  125 ?        00:00:00 kconservative/1
  126 ?        00:00:00 kconservative/2
  127 ?        00:00:00 kconservative/3
  128 ?        00:00:00 kconservative/4
  129 ?        00:00:00 kconservative/5
  130 ?        00:00:00 kconservative/6
  131 ?        00:00:00 kconservative/7
  373 ?        00:00:00 scsi_eh_4
  374 ?        00:00:00 usb-storage
  376 ?        00:00:00 scsi_eh_5
  377 ?        00:00:00 usb-storage
  379 ?        00:00:00 scsi_eh_6
  380 ?        00:00:00 scsi_eh_7
  393 ?        00:00:00 scsi_eh_8
  394 ?        00:00:00 scsi_eh_9
  402 ?        00:00:00 kjournald
  409 ?        00:00:00 scsi_eh_10
  410 ?        00:00:00 usb-storage
  425 ?        00:00:00 flush-1:0
  426 ?        00:00:00 flush-1:1
  427 ?        00:00:00 flush-1:2
  428 ?        00:00:00 flush-1:3
  429 ?        00:00:00 flush-1:4
  430 ?        00:00:00 flush-1:5
  431 ?        00:00:00 flush-1:6
  432 ?        00:00:00 flush-1:7
  433 ?        00:00:00 flush-1:8
  434 ?        00:00:00 flush-1:9
  435 ?        00:00:00 flush-1:10
  436 ?        00:00:00 flush-1:11
  437 ?        00:00:00 flush-1:12
  438 ?        00:00:00 flush-1:13
  439 ?        00:00:00 flush-1:14
  440 ?        00:00:00 flush-1:15
  441 ?        00:00:00 flush-8:32
  442 ?        00:00:00 flush-8:16
  443 ?        00:00:00 flush-8:0
  470 ?        00:00:00 upstart-udev-br
  473 ?        00:00:00 udevd
  656 ?        00:00:00 edac-poller
  795 ?        00:00:00 udevd
  796 ?        00:00:00 udevd
  805 ?        00:00:00 usbhid_resumer
  866 ?        00:00:00 kpsmoused
  944 ?        00:00:00 radeon/0
  945 ?        00:00:00 radeon/1
  946 ?        00:00:00 radeon/2
  947 ?        00:00:00 radeon/3
  948 ?        00:00:00 radeon/4
  949 ?        00:00:00 radeon/5
  950 ?        00:00:00 radeon/6
  951 ?        00:00:00 radeon/7
  952 ?        00:00:00 ttm_swap
 1005 ?        00:00:00 hd-audio0
 1093 ?        00:00:00 kslowd000
 1095 ?        00:00:00 kslowd001
 1097 ?        00:00:00 radeon/0
 1098 ?        00:00:00 radeon/1
 1099 ?        00:00:00 radeon/2
 1100 ?        00:00:00 radeon/3
 1101 ?        00:00:00 radeon/4
 1102 ?        00:00:00 radeon/5
 1103 ?        00:00:00 radeon/6
 1104 ?        00:00:00 radeon/7
 1116 ?        00:00:00 hd-audio1
 1124 ?        00:00:00 kjournald
 1131 ?        00:00:00 hd-audio2
 1177 ?        00:00:00 rsyslogd
 1188 ?        00:00:00 sshd
 1193 ?        00:00:00 dbus-daemon
 1202 ?        00:00:00 gdm-binary
 1207 ?        00:00:00 avahi-daemon
 1208 ?        00:00:00 avahi-daemon
 1209 ?        00:00:00 NetworkManager
 1211 ?        00:00:00 modem-manager
 1213 ?        00:00:00 console-kit-dae
 1306 ?        00:00:00 gdm-simple-slav
 1312 ?        00:00:00 cupsd
 1323 ?        00:00:00 wpa_supplicant
 1324 ?        00:00:00 dhclient
 1328 tty7     00:00:00 Xorg
 1351 tty4     00:00:00 getty
 1355 tty5     00:00:00 getty
 1362 tty2     00:00:00 getty
 1363 tty3     00:00:00 getty
 1366 tty6     00:00:00 getty
 1371 ?        00:00:00 acpid
 1372 ?        00:00:00 anacron
 1375 ?        00:00:00 irqbalance
 1385 ?        00:00:00 cron
 1386 ?        00:00:00 atd
 1521 ?        00:00:00 dbus-launch
 1522 ?        00:00:00 dbus-daemon
 1523 ?        00:00:00 gnome-session
 1528 ?        00:00:00 gconfd-2
 1531 ?        00:00:00 gnome-settings-
 1559 tty1     00:00:00 getty
 1592 ?        00:00:00 gvfsd
 1593 ?        00:00:00 metacity
 1595 ?        00:00:00 gdm-simple-gree
 1597 ?        00:00:00 gnome-power-man
 1598 ?        00:00:00 gdm-session-wor
 1604 ?        00:00:00 pulseaudio
 1606 ?        00:00:00 rtkit-daemon
 1610 ?        00:00:00 polkitd
 1612 ?        00:00:00 upowerd
 1722 ?        00:00:00 flush-7:0
 1723 ?        00:00:00 flush-7:1
 1724 ?        00:00:00 flush-7:2
 1725 ?        00:00:00 flush-7:3
 1726 ?        00:00:00 flush-7:4
 1727 ?        00:00:00 flush-7:5
 1728 ?        00:00:00 flush-7:6
 1729 ?        00:00:00 flush-7:7
 1730 ?        00:00:00 flush-8:112
 1744 ?        00:00:00 gconf-helper
 1746 ?        00:00:00 sshd
 1815 ?        00:00:00 sshd
 1816 pts/0    00:00:00 bash
 1846 pts/0    00:00:00 ps
```quadproc

---

### Post by Krytarik on 2011-01-27
I haven't heard such things regarding the fglrx driver so far.
You could try to run the Open Source Edge driver instead, they also support hw-accel and should be adapted to whatever will change in the xserver:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)

I don't believe that listing of the running processes will help us in that case.
Check instead "/var/log/Xorg.0.log" and "/var/log/messages" for error messages.

---

### Post by quadproc on 2011-01-27
> **Krytarik said:**
> I haven't heard such things regarding the fglrx driver so far.
You could try to run the Open Source Edge driver instead, they also support hw-accel and should be adapted to whatever will change in the xserver:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)

I will study this and see what I can learn.
> 
I don't believe that listing of the running processes will help us in that case.
Check instead "/var/log/Xorg.0.log" and "/var/log/messages" for error messages.Yes, I only looked at the processes to see if xorg was there.

I did not see anything interesting in Xorg.0.log; there were no errors listed, a couple of warnings related to "falling back to old probe method", one related to "open ACPI failed" and one relating to the lack of Cyrillic alphabet.  The remainder were mostly informational messages.

Likewise, the messages log did not have anything obvious in it but it would very easy for something to be missing and I would not recognize that fact.  Nevertheless, there was lots of commentary in this log regarding setting up and running the graphics cards; I knew that they were running anyway because I did get the splash screen displayed.

Something else that I have noticed: when the failure occurs, sometimes the splash screen is displayed in small scale and not centered, as though all of its dimensions have been cut in half; most times it appears at normal size and location.

quadproc

---

### Post by Krytarik on 2011-01-27
Try the OSED I mentioned.

Try to disable the splash screen:
- edit the file "/etc/default/grub"
- remove "splash" from the options for "GRUB_CMDLINE_LINUX_DEFAULT"
- run "sudo update-grub" after that

You may also attach both of the mentioned log files, I would also look them through then.

---

### Post by quadproc on 2011-01-27
> **Krytarik said:**
> Try the OSED I mentioned.

Try to disable the splash screen:
- edit the file "/etc/default/grub"
- remove "splash" from the options for "GRUB_CMDLINE_LINUX_DEFAULT"
- run "sudo update-grub" after that

You may also attach both of the mentioned log files, I would also look them through then.
OK, last thing first: I tried to attach the log files but they were rejected for being too long.  I welcome a suggestion for an alternate method of transferring them.

I can readily remove the splash so I will try this right away.  The difficult thing will be knowing if it made a difference since the problem occurs at unpredictable times.

I will probably postpone the edge driver until after I have run without splash for a while.  I really don't want to change two things at once.

Thanks for help and interest.

quadproc

---

### Post by Krytarik on 2011-01-27
> **quadproc said:**
> OK, last thing first: I tried to attach the log files but they were rejected for being too long.  I welcome a suggestion for an alternate method of transferring them.I was afraid of that, then you can just upload them as compressed files.
> **quadproc said:**
> 
I can readily remove the splash so I will try this right away.  The difficult thing will be knowing if it made a difference since the problem occurs at unpredictable times.

I will probably postpone the edge driver until after I have run without splash for a while.  I really don't want to change two things at once.

I also recommend proceeding that way.

---

### Post by quadproc on 2011-01-27
OK, I have finally managed to get logged in to the forums (recently, I have been getting a lot of responses from the forum software which say "thank you for logging in" followed by another page which says "you are not logged in" and it often takes numerous retries to finally get logged in.

Trying again to attach the two log files but they are compressed this time.

quadproc

---

### Post by Krytarik on 2011-01-28
Yeah, there is currently an issue with the availability of the forums, although I didn't experience serious drops in the last two weeks:
[http://ubuntuforums.org/announcement.php?f=331](http://ubuntuforums.org/announcement.php?f=331)

As of your logs, I also don't see any serious error messages, but I'm bit concerned about the repeated statements of the monitor modes. It may make sense to create a "xorg.conf" and specify the values there.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by quadproc on 2011-01-28
> **Krytarik said:**
> 

As of your logs, I also don't see any serious error messages, but I'm bit concerned about the repeated statements of the monitor modes. It may make sense to create a "xorg.conf" and specify the values there.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
I could readily copy over the xorg.conf that I use with Ubuntu 10.04; I know that I didn't have this "stalling" problem with releases before 10.10.

Here is the latest in diagnosing things: with the splash removed from the kernel options, I still get the stalling problem.  What I saw when I had removed the splash option and when the boot occurred normally was the screen showing a bunch of tiny text when the splash would have been occurring; the messages were normal stuff such as ":checking battery state" (yes, battery state even though is a desktop and the only battery in it is for the clock).

When the stalling problem occurred, I got a bunch of tiny text when the splash would have occurred but the messages seemed to be different.  And when the login screen should have appeared, nothing.  So I connected to this system with ssh, confirmed that Xorg was running, started another incarnation of X on display 1 (sudo startx -- :1), and tried ctrl alt F8 on the stalled system.  The only thing on the screen was a little tiny cursor in the upper left corner.  The screen was not responsive to keyboard input.

All of this makes me very suspicious of Xorg.

quadproc

---

### Post by Krytarik on 2011-01-28
Tiny, you say?! It shouldn't be that tiny. It seems to boot with a higher than usual resolution or even with "framebuffer" enabled.

Please post the contents of "/boot/grub/grub.cfg" and "/etc/initramfs-tools/conf.d/splash", if that file exists.

Regarding the "checking battery state" thing, since the kernel is build to support different devices it is supposed to do that. It can even stuck after displaying that message, but that hasn't anything to do with the actual issue.

---

### Post by quadproc on 2011-01-28
> **Krytarik said:**
> Tiny, you say?! It shouldn't be that tiny. It seems to boot with a higher than usual resolution or even with "framebuffer" enabled.
Yes, it is very small.  The resolution may be high; I haven't looked to see how many pixels each character uses.
> 
Please post the contents of "/boot/grub/grub.cfg" and "/etc/initramfs-tools/conf.d/splash", if that file exists.
I will attach the grub.cfg.  The /etc/initramfs-tools/conf.d directory only contains RESUME; there is no splash file.  But the symptoms have changed a bit: even though I restored the /etc/default/grub file to contain "quiet splash" and I ran update-grub, I no longer get a splash at boot time.  But when I shut the system down then I get a splash-type of display.  I wonder if something took away my splash file?  (I did do an apt-get update and it did change at least one thing but I am not sure what.)

quadproc

---

### Post by Krytarik on 2011-01-28
You're not supposed to have the "splash" file in the mentioned directory, it is sometimes used to hold an option to invoke the "framebuffer" at startup, it is sometimes necessary to enable the splash screen when running proprietary video drivers from AMD/Nvidia.

Of course, you could try that as well: create those file and put the following entry in it:
```
FRAMEBUFFER=y
```You have to update initramfs after that:
```
sudo update-initramfs -u
```This is an excerpt of the readme of the Plymouth boot splash (/usr/share/doc/plymouth/README.Debian):
> High-color graphics on nVidia, ATI and other cards
--------------------------------------------------

Our default configuration uses low-color graphics on cards or drivers
for which "Kernel Mode Setting" (in-kernel graphics drivers) are not
available.

This is because the driver that permits high-color graphics tends to
cause issues with suspend and resume, and we opted to prefer that
working.

For nVidia and ATI users, the default "nouveau" and "radeon"
drivers are Kernel Mode Setting enabled, but do not always
provide 3D capability at the current time. By switching to
using the restricted/non-free nvidia-glx or fglrx drivers,
you will gain 3D capability at the loss of a high-color
splash screen.

You can however chose to enable high-color (and resolution) console
if you find it doesn't affect suspend/resume for you, or you don't
use that feature.

There are various methods of doing this, the most robust is the
following four steps:

Append video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT in
/etc/default/grub
sudo update-grub

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -uBut you should definetely also try set the boot/console resolution like I have. I remember having a similar behaviour, while tinkering with those options. I can't remember the exact behaviour though.
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[B]GRUB_GFXMODE=800x600
[/B]#GRUB_GFXPAYLOAD=800x600
[B]GRUB_GFXPAYLOAD_LINUX=800x600
[/B]
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by quadproc on 2011-01-29
> **Krytarik said:**
> 
But you should definetely also try set the boot/console resolution like I have. I remember having a similar behaviour, while tinkering with those options. I can't remember the exact behaviour though.

> 
[B]GRUB_GFXMODE=800x600
[/B]#GRUB_GFXPAYLOAD=800x600
[B]GRUB_GFXPAYLOAD_LINUX=800x600
[/B]I have now done quite a bit of experimenting/booting with this system and I am beginning to see a pattern.  It appears that the Mesa driver does not initialize some things that it needs to in the graphics hardware (two HD4870s in my case).  If the last thing that I did happened to leave the graphics system in an unhappy state then it stays unhappy into the login process and the next session.

I tried the 800x600 resolution noted above but that caused a corrupted display.  I looked in the vbemode listing and found lots of valid combinations; I tried 1280x960 and found that this was too much so I backed it down to 640x480 and obtained the same results as I had at the beginning of installing Ubuntu 10.10 so I decided to leave it there for now.  Time will tell if that has any effect on the stalling problem.

I observe that the /etc/default/grub resolution appears to be intended to affect only the grub screen.  Once the real session has started then something else controls the resolution.  Trouble is, I don't know where to find those parameters.

Earlier I had mentioned that I saw a tiny cursor at the top of the screen.  I now understand that the size of this cursor is indirectly telling me what the resolution setting is.  At its smallest, that tiny cursor was indicating the maximum resolution possible on this monitor, 1920x1080.

I still do not know whether or not the stalling problem is still occurring.  Another dozen or so sessions should give me an idea of whether the problem is still present.

I think that I would like to try the OSED driver but I do not recall having seen a URL for getting it.  And, perhaps even more importantly, how to remove it?  Could you point me to those?  Thanks.

quadproc

---

### Post by Krytarik on 2011-01-29
> **quadproc said:**
> 
I observe that the /etc/default/grub resolution appears to be intended to affect only the grub screen.  Once the real session has started then something else controls the resolution.  Trouble is, I don't know where to find those parameters.
Yeah, it affects the grub menu screen, the boot splash, and actually also the console.

You can set the resolution in "xorg.conf" or with "xrandr" by following the same guide I posted earlier:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
> **quadproc said:**
> 
I think that I would like to try the OSED driver but I do not recall having seen a URL for getting it.  And, perhaps even more importantly, how to remove it?  Could you point me to those?
> **Krytarik said:**
> 
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)

To install, actually *upgrade*, run those commands:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

```To *downgrade* again, you can use

- ppa-purge:```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```- Synaptic: filter the packages which have been upgraded using the "Origin" filter, "force" down the version of the packages listed there as installed to either "maverick" or "maverick-updates", then remove the PPA via "Settings -> Repositories -> Other Software"

So far I always downgraded manually, giving me more control of what is happening.

---

### Post by quadproc on 2011-01-29
Thanks for the details.  I studied the information regarding the open source driver and concluded that I would be introducing too many variables into the situation now by trying to that route at the present time.

Therefore, I opted for my next-in-line choice, namely, fglrx. I tried to install the 10.8 version of fglrx because that is the version that I had been using on the 10.04 Ubuntu release but that attempt failed due to some kind of a version incompatibility (even though --listpkg reported Maverick as being on the list), so I obtained version 11.1 and installed that without significant problems (there was a lot of complaining about missing SUSE files but that didn't affect the install).

When I rebooted after the install, I was presented with a splash screen!  It is too soon to tell if all of the graphics problems are cured, but this is definitely encouraging.

If my hypothesis is correct, namely that there is something missing in the startup procedure with the Mesa driver, then I think that it needs a bug report.

My situation is not yet completely resolved but a few days should tell me if there are problems remaining.

quadproc

---

### Post by quadproc on 2011-01-29
Here is a little more information: I still have not resolved the original problem, namely, how to prevent the splash crash when using the default open source driver, so I have been doing more searching and I found reports of similar problems from other users.  It does seem to be a race condition probably involving the framebuffer.  See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605667](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605667) entry #38 in particular.

quadproc

---

### Post by Krytarik on 2011-01-30
I'm not really sure that it's the same issue, not at least because the intel driver is run in those case. And the behaviour is also markedly different. Do you have error messages like the ones in the bug report in any of your Xorg logs?
> [    25.710] (EE) Screen(s) found, but none have a usable configuration.
[    25.710] 
Fatal server error:
[    25.710] no screens found


---

### Post by quadproc on 2011-01-30
> **Krytarik said:**
> I'm not really sure that it's the same issue, not at least because the intel driver is run in those case. And the behaviour is also markedly different. Do you have error messages like the ones in the bug report in any of your Xorg logs?
No; the only error that I have seen in the xorg log was one where I made a mistake: I applied my xorg.conf file which specifies the fglrx driver, but I had not installed the driver.  Of course, that problem was solved by installing the driver.

So far, this system has behaved well during splash with the fglrx driver in place.  After I get some more startups done to be confident of it, then I plan to try removing the fglrx driver to be sure that the original problem still exists.

In my research on this subject, I found several bug reports dating back to at least Ubuntu version 9.04 which suggest that some race condition has been causing problems similar but not necessarily identical to what I saw.  The software folks seemed to think that they had solved the problem so I wonder if this old bug managed to slip through and re-emerge in 10.10?

quadproc

---

### Post by quadproc on 2011-01-30
Update:

I removed fglrx and restored the default Mesa driver.  On the second boot the system stalled just before the login screen with a distorted splash screen on display.  I now have no doubt that the problem is in the default driver's interaction with the rest of the software.

quadproc

---

### Post by Krytarik on 2011-01-30
> **Krytarik said:**
> Anything against to install/run the proprietary video driver?
If not, try installing them via "System -> Administration -> Additional Drivers".
Could be possible that the default driver can't handle a crossfire setup.
Here we are then, after 3 days! ;)

---

### Post by quadproc on 2011-01-31
> **Krytarik said:**
> Here we are then, after 3 days! ;)
Yes; I still do not have a solution for my original problem, i.e. how to get the default radeon driver to function reliably.  I do have a workaround, namely fglrx, which I can probably use until Ubuntu version 11.04 is released.

Since I now know how to reproduce the problem I filled out a bug report and submitted it.  It is launchpad bug # 711056 for anyone interested.  We will see what happens.

quadproc

---


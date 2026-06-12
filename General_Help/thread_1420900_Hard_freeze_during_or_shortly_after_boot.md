---
title: "Hard freeze during or shortly after boot"
date: 2010-03-03
forum: General Help
---

### Post by mogrify on 2010-03-03
Running Karmic.  My problem is that within a few minutes of booting the machine, it freezes.  The keyboard and mouse do nothing; the keyboard LEDs do not light up.  Whatever is on the screen stays there - X or a console.  Ctrl-Alt-Del does not work; neither does Alt-SysRq-REISUB.  The machine stops responding to ping and won't accept any remote connections.  I have to do a hard reset with the power button.

Sometimes it happens during the boot process; sometimes it's a few minutes afterward, and I get to look at log files for a while until it stops responding.

Here's what I've tried:

[LIST]
[*]It happens in recovery mode as well as a regular startup.
[*]It happened when I booted from an Ubuntu Server CD and did rescue mode.
[*]I ran memtest86+ and it completed successfully with no errors (and it didn't freeze)
[*]It doesn't happen if I just sit in the grub menu for a while.
[*]I've looked at what log files I can; there's nothing that looks like a severe error, and it fails at different times during the boot process, so it doesn't seem like whatever's going wrong is getting logged.
[*]It happens with the latest kernel I have (2.6.31-19-generic), as well as the oldest (2.6.28-16-generic)
[/LIST]

It seems like there must be some hardware issue, but I'm not sure where to start looking.  I'd appreciate any suggestions, and I'd be happy to post more information (assuming I can get it off the machine within a few minutes).

---

### Post by saluja04 on 2010-04-09
I am having a similar (if not identical issue).  I recently installed Karmic using a livecd, and partitioned the drives to dual boot WinXP SP3 with the following structure:

60 gb - winxp (ntfs)
 2 gb - swap
12 gb - / (ext4)
28 gb - /home (ext4)

The machine is an older one--a pentium 4 2.8ghz with 1gig ram.  As you may already be able to tell, I am fairly new to Ubuntu.  The WinXP installation seems to be working fine.  I was able to get it running without a hitch on other machines, but this one is giving me trouble.

The machine will boot to the desktop 75% of the time, and when it does, it will connect to the network, but when I try to open Firefox, it totally freezes.  The 25% of the time it doesn't get to the desktop, it will freeze at the Ubuntu splash screen.  I tried to use the recovery option, and got to the desktop, but as soon as I ran Firefox, the same result occurred.  When it freezes, I have the same issues as mogrify described above--ctrl-alt-del doesn't work, and i have to do a hard reset.

Thank you in advance for your help.  I can provide whatever additional information you request.  Hopefully this issue will be resolved soon, otherwise I guess I'll have to stick it out until the Lucid final is released later this month.

Cheers

---

### Post by the grey side on 2010-04-10
I had similar problems:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1375948](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1375948)

Installing the 2.6.32.3 kernel worked for me. Instructions here:

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8708228&postcount=38](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8708228&postcount=38)

Later kernels might work as well. This worked for some, but not for others.

---


---
title: "Multiple Ubuntu Problems"
date: 2012-02-26
forum: General Help
---

### Post by Donavon on 2012-02-26
I currently have no OS on my desktop computer.  I have burn ubuntu 11.10 on a cd, and a usb multiple times (both 64 and 86 bit).  

One of the problems is that when I click to install it, it just goes to a black screen.  If I put it in nomodeset then install it, it goes to the install and shows 4 dots blinking, then a few minutes later it goes to a black screen.  The 64 bit version seems to go to a black and white theme looking screen (the screen where i can install, or try it, etc).  

I remember one of the errors I had was "bad target number", and one of the other errors was "sp5100 tco timer mmio address oxbafe00 already in use".

I can't give you my pc specs because I don't know them, and there is no os installed to find out, but I can tell you I have a "hp omni 120 all in one".

Any help will be greatly appreciated.  Thank you

---

### Post by wyliecoyoteuk on 2012-02-26
Can you get into the BIOS screen?
It probably has UEFI firmware (a new type of BIOS).
However, Ubuntu should be compatible with UEFI.
[Parted magic]("http://partedmagic.com/doku.php?id=downloads") is a liveCD distro with lots of faultfinding tools, might be useful.

---

### Post by Donavon on 2012-02-26
Thanks for the quick reply.

Yes, I can get into my BIOS.  I set it to the default setting and saved it.  However I am still having problems installing.

It will get to the screen where it asks me to install, try ubuntu, test memory, etc. after that I click install, and it just goes black - the same thing happens for 'try ubuntu without installing' as well.

-edit-  

I forgot to mention - If I set it to nomodeset, then click install, it will go to a screen where it shows the ubuntu logo, and there is 4 loading dots under it.  it will stay like that for a couple minutes, then it will go black.

---

### Post by mcduck on 2012-02-26
What graphics card do you have?

---

### Post by Donavon on 2012-02-26
Integrated AMD Radeon HD 6320

[Specs]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c03028724&lc=en#N196")

---

### Post by oldfred on 2012-02-26
While nomodeset seems to work for many have you tried either the generic or Radeon settings?

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

If an HP computer do you have the typical HP all four primary partitions used? You may have to delete one partition. And you should make a repairCD, the set of DVDs that are the image of the hard drive as purchased and a full image backup of your system. 

You should shrink the Windows partition from inside Windows, but not create new partitions as it will convert from basic to dynamic which does not work with Linux.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by Donavon on 2012-02-26
Thank you for the reply.

I will definitely be testing the alternatives you mentioned.

I currently have two partitions:  [[FONT=Lucida Console][SIZE=2][COLOR=Indigo]Image[/COLOR][/SIZE][/FONT]]("http://i44.tinypic.com/15pk5n6.jpg")
I done a clean install on Windows, therefore deleted all partitions.  I next went on with the install
without creating a new partition (I let it create itself), and then seen that it also created the *recovery partition*.

I do have a few questions: When I shrink the C: partition, how much space should I leave for the Ubuntu
partition? When shrinking the partition, is it safe, and will it do any damage to my current files?

Thank you

---

### Post by oldfred on 2012-02-26
As long as you use Windows to shrink and leave at least 30% free space, as Windows likes lots of room to work, you should be ok. Of course with any system change you should have good backups and a Windows repairCD. Reboot Windows several times as after a partition size change it wants to run chkdsk or make other internal repairs.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by DeathShot on 2012-02-26
> **Donavon said:**
> Thank you for the reply.
 When I shrink the C: partition, how much space should I leave for the Ubuntu
partition? When shrinking the partition, is it safe, and will it do any damage to my current files?

Ubuntu doesn't need too much space, 15 gigs will be plenty for the operating system and any software you want to install, I never went over that without having a ton of data on my system. Your data partition (you should always have a sepearate partition for you data) can be as large or as small as you want, just estimate how much you think you will use, or give it everything you aren't using.

As for is it safe, I have only ever used gparted to resize my partitions but I never had a problem. Windows might have to run a chdsk but that isn't a big issue. Always leave a few extra gigs free though and defragment your partition before shrinking.

---

### Post by Donavon on 2012-02-26
Thank you for the replies.

So my progress:
I have tried adding each of these lines at one point:

> 
*i915.modeset=1*
i915.modeset=0
xforcevesa
nomodeset
radeon.modeset=0
nouveau.modeset=0


Only two of them work, and they are:
> 
radeon.modeset=0
nomodeset


However, the ones that  work, it goes to the screen where it shows the Ubuntu logo, and there are 4 dots under it loading.  It sits there for about 2-3 minutes, then gives me a bunch of errors like ("bad target number" "failed to change the mode of /etc/passwd" etc).

---

### Post by oldfred on 2012-02-26
Sometimes some additional boot parameters are required. May be best to search for your system with Ubuntu to see if others have had & solved issue.

Sometimes a BIOS setting can also be an issue:


How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by Donavon on 2012-02-26
Actually did that for a couple hours, and no luck.  I guess I'll use trial and error.  Thanks

---

### Post by Donavon on 2012-02-27
After trying all night to find the solution, I still have not succeeded.

I don't know what else I can try.  Does anyone know of any other ways to possibly fix it?

---

### Post by oldfred on 2012-02-27
Have you seen this thread?

[SOLVED] Ubuntu will not install from CD on HP Omni 100
[http://ubuntuforums.org/archive/index.php/t-1831797.html](http://ubuntuforums.org/archive/index.php/t-1831797.html)

---

### Post by Donavon on 2012-02-27
Thank you for that thread.  I read over it, and I'm gonna be completely honest- I hardly understood anything from that thread (I am completely new to linux).

I used the alternative install CD, and got it installed.  However after I get to the grub menu, and choose the ubuntu os, it takes me to a loading screen, then goes black.

---

### Post by oldfred on 2012-02-27
Then does nomodeset or booting with the recovery mode (second entry in menu) work?

---

### Post by Donavon on 2012-02-27
Thanks for the reply.

Sadly, no, neither one work.  It's the same issue, the screen goes black.  However at one point (I'm not sure what I did), there was a blinking cursor, and a messed up background flashing with it.

I did however manage to install the 10.04 lucid version, but I would like to have the most recent version.

---

### Post by Donavon on 2012-02-28
Sorry for the bump.

Is there anything else I can try to fix this?

Here is one of the errors I get: "Failed to change the mode of /etc/passwd- to 0600"
Another one: "bad target number"

At one point my cursor and background was blinking on and off.

I can only get to the "ubuntu loading screen (where the logo and 4 dots are at), if I use nomodeset, and radeon.modeset, but of course after it sits there for a few minutes, it goes black.

---


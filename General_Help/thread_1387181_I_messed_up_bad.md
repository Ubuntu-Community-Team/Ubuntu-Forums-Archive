---
title: "I messed up bad"
date: 2010-01-21
forum: General Help
---

### Post by dingusmoose on 2010-01-21
I have ubuntu 9.10 installed on my HD.  I wanted to install a xp partition.  The xp disk led me to the partition menu and there were 2 partitions.  One for >180gb and one for about 7 gb so thinking that the seven was a previous attempt at a partition on my part i deleted it.  Windows would not let me install in the blank space created and now when i try to load ubuntu i get a "Error loading operating system message".  Any ideas what i deleted, how to get my ubuntu working again, or how to salvage my files? Any help would be appreciated

---

### Post by jamesisin on 2010-01-21
Run the Live CD and see what sort of damage you did by, for instance, running:

sudo fdisk -l

You may have only deleted something simple like your swap partition.  Could be horrible, but we don't know yet.

---

### Post by smo0th on 2010-01-21
wind0ze messed up your GRUB loader, boot from live cd to [restore GRUB]("http://ubuntuforums.org/archive/index.php/t-24113.html")

**G**

---

### Post by dingusmoose on 2010-01-21
here's the results of the sudo fdisk -l


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x956c956c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23330   187398193+  83  Linux
/dev/sda2           23331       24320     7952175    7  HPFS/NTFS

---

### Post by jamesisin on 2010-01-21
Your swap partition is gone.  That 83 Linux partition should have both your / and /home (unless you loaded /home elsewhere) so your data should be ok for the moment.  You'll just have to recreate your swap partition.

Also, for the future, you can use GParted to alter your partition size and thereby make enough space to add Windows.  However, I would recommend just loading Windows as a Virtual Machine instead.

(Grub is probably broken so do follow those above instructions to get that working again.)

---

### Post by dingusmoose on 2010-01-21
Thanks for the help so far, if i restore the grub will that get ubuntu working again? Im definitely going with the windows vm, im done trying to install that

---

### Post by fjf314 on 2010-01-21
It should. Right now your system likely just doesn't know where it needs to look to load Ubuntu. Restoring your boot loader should take care of that.

And as jamesisin said, you will want to recreate your swap partition, too.

---

### Post by Barriehie on 2010-01-21
And perhaps initiate some sort of backup procedure. 8)

---

### Post by dingusmoose on 2010-01-22
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23330   187398193+  83  Linux
/dev/sda2           23331       24320     7952175    7  HPFS/NTFS

I tried marking sda1 as / on the partition menu and sda2 the swap, however when i went to proceed I recieved a message saying sda1 not marked for formatting directorys containing system files(/boot, /etc...) will be deleted during install, in a few more words.  The error did not mention the /root, but i thought i would bring it up here before proceeding. 

Also the partitioner found 8mb of free space.  should i make this the swap instead of sda2 or leave this for the grub

---

### Post by Fire$torm on 2010-01-22
@dingusmoose,

There are pros and cons for both Dual Booting and VM.
VM: The main advantage with VM is the ease running a second OS without rearranging your HD partitions. The main disadvantage is VM uses alot of system resources because you are running two OS's concurrently.

Dual Booting: Since you can run only one OS at a time system resources are conserved. The disadvantage is of course having to repartition you HD.

There is no need to fear dual booting though, it just requires a little time and *planning*. You do need to be aware that in reguards to Windows OS's, they MUST be installed on the HD before before any non-windows OS(s).
Just in case you are still interested in dual booting I will add another post in a little while with suggestions and links.

Peace.

P.S. My main system dual boots win7-HP x64 & Karmic Desktop x64 :KS

---

### Post by jamesisin on 2010-01-23
Interesting.  I suppose I would do something like this:

First, load up the live CD and check your sda1 to make sure your file system is really there.  You should see much that is familiar.  I trust you can manage navigating around that directory.

Second, assuming all is well with your file system (especially your /home directory) then you can use gparted to recreate your swap partition.

Finally, check grub according to the other instructions.

I don't know if the errors you are seeing are related to this, but my inclination would be to fix things in this order just in case.

---

### Post by Fire$torm on 2010-01-23
@dingusmoose,

Ok, at the end of this post are the links for the utilities to help you repartition your HD and tutorials to help you set up Dual Booting.
The reason it took so long for my 2nd post was because I had to test a few things.
The boot utilities listed are meant for USB Thumb Drives. *MultiBootISO* will allow you to have PartedMagic (which includes gparted), memtest86+, Ultimate Boot CD (A krazy set of utils for testing/torturing a computer), and Ubuntu Karmic Desktop on a single bootable thumb drive.

*Basic instructions:*
Format your thumb drive (FAT32) in windows, run MultibootISO to setup your thumb drive, decompress the zip files for PartedMagic - memtest86+ - UltimateBootCD, then copy them to your thumb drive along with your Ubuntu Karmic ISO, and lastly modify menu.lst file.

[I]Note:
[/I]Attached to this post is a zip file containing a modified menu.lst that I set up for everything listed above. To use just rename the menu.lst file on thumb drive and copy the modified file to thumb drive. I have tested the file and it works.
If you have any questions just post to this thread.

Hope this helps.

Peace.

[BootMyIso Download]("http://www.pendrivelinux.com/downloads/BootMyISO/BootMyISO-v0.2.exe") **[COLOR=Red]||[/COLOR]** [MultibootISO Download]("http://www.pendrivelinux.com/downloads/MultiBootISOs/MultiBootISOs-v0.3.exe") **[COLOR=Red]||[/COLOR]**  [PartedMagic 4.5 Download]("http://linuxfreedom.com/partedmagic/pmagic-4.5.iso.zip") [COLOR=Red]**||**[/COLOR] [Memtest86+ v4.00 Download]("http://www.memtest.org/download/4.00/memtest86+-4.00.iso.zip")

[Ultimate Boot CD Download]("http://www.ultimatebootcd.com/download.html") [COLOR=Red]**||**[/COLOR]  [LifeHaker Dual Boot Tutorial]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+lifehacker%2Ffull+%28Lifehacker%29") **[COLOR=Red]||[/COLOR]**  [Customizing Grub2 Tutorial]("http://ubuntuforums.org/showthread.php?t=1296225")

> **jamesisin said:**
> .....PS: Your first two links don't work. They both redirect back to pendrivelinux (main page).

Opps, I checked the links and the links themselves are valid. The redirect must have something to do with ubuntuforums.org. Anyhow here are the links to the Pendrivelinux articles:  [COLOR=Red]**||**[/COLOR]  [boot-iso-from-usb-flash-drive [COLOR=Red]**||**[/COLOR] ]("http://www.pendrivelinux.com/boot-iso-from-usb-flash-drive/") [boot-multiple-iso-from-usb-multiboot-usb]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/")  [COLOR=Red]**||**[/COLOR] 
Sorry for the inconvenience.

---

### Post by jamesisin on 2010-01-23
Fire$torm - Ok, first let me say thank you.  You are a seriously dedicated member of the community and I appreciate your participation.  That being said, I really don't see the benefit of using a dual boot system over virtualization.  It is the future of multi-system computing and that future is now.  Even MS finally got on board with virtualization.  Anything that can be accomplished with a separate boot can be better accomplished with virtualization.  The strongest benefit that comes to mind is that a VM is accessible without leaving the host system.  By contrast in a dual boot scenario you have to leave one system to access the other.  Of course, the final decision is up to the OP.  I just don't see the sense of one clearly so knowledgeable as yourself advocating dual booting over virtualization.

Oh, and thanks for all the cool links.  I know I'll be using some of them.

PS: Your first two links don't work.  They both redirect back to pendrivelinux (main page).

---

### Post by JiuJitsu500 on 2010-01-23
Wow I have to agree to that that completely... and add Mac should get on board too [insert explative here if in agreance]....

Virtualization makes things much, much easier of it's working right (though yes, it can be a pain).... But bigger pains come from dual-booting I find. Whether on a windows, mac, or Linux/UNIX host, virtualizing the others (even the illegal for now Mac virtualization) for necessity is faster and easier to quit if something messes up... not to mention it cuts out problmes with booting completely (see: all the problems with Wubi, GRUB/Boot.INI fighting) so no tweaking or changing scripts anywhere is necessary... Just my opinion though... Any reason in particualr you advocate dual-booting rather than Virtualizing an OS? I am always open , and never mean to criticise, but I do feel strongly against dual-booting if you already have a working OS and can get virtualbox for free on any host...

Just sayin :) And those links for sure, by the way I'll find myself delving into as well, thanks for those :)

---

### Post by Jackzor on 2010-01-23
I rather like my Windows 7/Ubuntu Karmic dualboot. I have had no issure with it whatsoever and I share all my files on a ntfs partition. Everything is perfectly smooth. The reason I did it in the first place was for the hardware usage.. Although I don't use it for anything. I still wanted it. ANYWAYS. I had had absolutly no problems with dualbooting Windows 7/Ubuntu Karmic. I have done it on my laptop along with my girlfriend's.(In hopes that she would use Ubuntu over 7../failed) Anyways. Dualboot ftw.

---

### Post by jamesisin on 2010-01-23
Let's not hijack this thread.  I created an appropriate thread for us to, erm, discuss VM's and D-B's:

[http://ubuntuforums.org/showthread.php?p=8710448](http://ubuntuforums.org/showthread.php?p=8710448)

---

### Post by d3v1150m471c on 2010-01-23
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Read that.

---

### Post by jamesisin on 2010-01-23
d3v1150m471c - Are you directing the OP to the "Four-step Process to Add Swap" section?

---

### Post by Fire$torm on 2010-01-23
Fixed link problem. See my previous post :popcorn:

---

### Post by Fire$torm on 2010-01-25
For anyone that is interested check out the links below:
**[COLOR=Red]-->[/COLOR]** [COLOR=RoyalBlue][Linux ISO image to Hard Disk install]("http://do-it-blog.de/it-blog/linux-stuff/linux-iso-image-to-hard-disk-install")[/COLOR] **[COLOR=Red]<--[/COLOR]** and **[COLOR=Red]-->[/COLOR]** [COLOR=RoyalBlue][UbuntuServerFlashDriveInstaller]("https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller")[/COLOR] **[COLOR=Red]<--[/COLOR]**

A "BIG" Thank You to WOTHed for the links.
Read Post #17 from this thread **[COLOR=Red]--->[/COLOR]** [8.04 usb install with no cd-rom drive problems?]("http://ubuntuforums.org/showthread.php?t=1366295") **[COLOR=Red]<---[/COLOR]**

Peace.

---


---
title: "Windows 7 bootloader broken"
date: 2011-04-03
forum: General Help
---

### Post by jvacek996 on 2011-04-03
Hello forum, I am *trying to* dual boot windows 7 and Elementary OS (a beautiful Ubuntu subdistro).
when i start up i have a GRUB where i can choose from the elementary entry and its recovery mode and the W7 entry. whenever i choose W7 it shows me a broken grub. i think i previously managed to install grub onto it but it got broken.
Is there a way to put the original windows 7 bootloader so that it goes first through Grub and then into Lilo or whatever the name is?
I also have splashtop OS on the /dev/sda1 so i think if i installed lilo onto that partition it would work with SOS too (splashtop operationg system? SOS? get it? aaaah), but i don't have the skills to make my own command lines.
And yes, i do like elementary. you should give it a try too. its free after all.

help please?

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x514405b4

   Device Boot      Start         End      Blocks          Id  System
/dev/sda1   *           1           27006   216925663+   7  HPFS/NTFS
/dev/sda2           27007       30402    27272192    83  Linux


---

### Post by jvacek996 on 2011-04-03
bump

---

### Post by adjbck on 2011-04-03
> **jvacek996 said:**
> bump

No one helps a pedobear. NO ONE
On other subjects bump im interested in the answer

---

### Post by jvacek996 on 2011-04-03
...i actually need help. but thanks for noticing my signature.

---

### Post by wilee-nilee on 2011-04-03
We need more information the best way to do this is to click on the bootscript link in my sig and follow the directions to generate a text file. Come back to the thread open a reply, click on the **(#)** in the reply panel for code tags and paste all the text between. Let us know what you have as far as media I.E. do you have a install or recovery for W7 disc, and the same for Ubuntu.

---

### Post by jvacek996 on 2011-04-03
easy enough, here it is.
I've got a W7 disk and a Ubuntu 10.10 disk as well as elementary Jupiter.
I've got a 16 GB SD card and a 640GB External HDD if that helps too

---

### Post by techunit on 2011-04-03
Hi! I'll see what I can do.

Pedobear? is that a minecraft thing or am I really out of the loop.

Grub you should first boot into elementaryOS and open a terminal and type ```
sudo update-grub
```

that will reload grub.

In order to fix the Windows MBR (will wipe out grub requiring either elementary reinstall or grub to be installed again.) You need to pop in your windows cd and complete the following.
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

after doing this step your elementary won't boot. But windows should.
you can now either reinstall elementaryOS onto the partition it created. Or follow the install grub guide found at the link below.

If you choose to reinstall grub you may find a guide below.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Surely this will help with that.

Please I am not an expert so please if you have any doubts and I don't blame you for having them please reask the question with the information presented to you. I will drop a line to another member on the forum to come and take a look for you.

Sincerely, 

Tobias

---

### Post by LostFarmer on 2011-04-03
From the boot script:
> Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 487401656 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.  That is not good. You broke the MS's boot code by installing grub to sda1. You will need to rewrite Win 7 boot code to its volume. I do not use Win 7 and do not know how its done. Doing a grub update will be of no help.

---

### Post by drs305 on 2011-04-03
*techunit's* solution should do what you want.

Once you get Windows working on it's own, you can boot the Ubuntu LiveCD and reinstall Grub2. After doing this Grub2 will be the controlling bootloader: you will see options for your Linux OS and Windows. If you select Windows, you will be transferred to the Windows bootloader.

If all the Windows boot files are still intact, you could accomplish the first half via the LiveCD as well, by partially installing lilo. This will simply install instructions on the MBR to go to the Windows partition and use the Windows bootloader. To do this:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Only run those two commands. Windows should now boot directly. If this doesn't work, use the Windows repair disks so Windows boots. 

To reinstall Grub2 and allow it to take control during boot:
```
sudo mount /dev/sda2
sudo grub-install --root-directory=/mnt /dev/sda

```

If you don't see Windows in the menu after you boot to your normal Linux OS, run:
```
sudo update-grub
```

---

### Post by jvacek996 on 2011-04-03
Yeah i think it booted straight into Windows but the Windows loader is broken as I already said. Thanks. Now I can't even boot into elementary anymore, but I'll try the Windows disc as you said.

---

### Post by drs305 on 2011-04-03
I should have anticipated that. lilo just pointed back to the Windows bootloader, and it's the contents of those files that direct the old linux reference.

I am not experienced with the Windows repair disk so when you repair it I don't know if it is going to retain the option to boot into grub or not. You want to completely wipe the Windows bootloader files and reinstall them so it no longer references the old Ubuntu OS.

Once you get it working, or whenever you really need to get back into Linux, using the 'grub-install' command while on the LiveCD will allow it to boot.

---

### Post by jvacek996 on 2011-04-03
Yeah, the windows CD doesn't do anything about it, the advanced features don't do anything, they don't even show up. I'll boot into a live CD an reinstall grub with the other line you gave me

---

### Post by techunit on 2011-04-03
Reinstalling grub while Windows boot files are still corrupted will give you more of a headache please wait I'll get an alternative guide.

---

### Post by techunit on 2011-04-03
This is a guide for restoring the windows MBR without the Windows Disk,

[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

Here is another guide that goes in more depth.
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)
please note its a little old so no promises.

---

### Post by jvacek996 on 2011-04-03
Ok, I will stop everything I am doing right now, waiting for you to reply (no homo).
Just so that it's clear, when I startup I am told that no such partition was found. That is because it is loading sda1 straight away I think, the sda2 contains elementary. I think that's the case because it printed the same thing when I tried the Windows 7 entry from grub when j still had the choice.
when I tried to ' sudo mount /dev/sda2 it told me that it can't find it in fstab nor mtab but I guess those are the ones on the CD.
whn I ran 'sudo grub-install /dev/sda' and the same with sda2 it told me that the dev isn't mounted.
Hope it helps with future helping :P
Also, to avoid any weird questions, I am on my iPhone right Now, that's why windows is so crucial to me.

---

### Post by techunit on 2011-04-03
If you can't get to your windows partition or your linux partition then you should boot from a live cd for now.

Ok jvacek996

I posted a guide above your post that should get windows booting again. It is old but I'll keep looking.

---

### Post by jvacek996 on 2011-04-03
Ok so I did ' sudo ms-sys -f /dev/sda1 ' and when I started up it told me that there is something wrong with some tables, I already forgot what it said ( guess I'm not making it any better for you). I thought that it might have damaged it so bad zhat the windows cd might as well want to repair it now so Now I am trying the windows cd again and this time it is "attempting repairs" so I'll see what does that do, I'll repl once it is done.

---

### Post by techunit on 2011-04-03
Sounds like a pretty good plan.

---

### Post by jvacek996 on 2011-04-03
No, cd didn't do anything. It said it couldn't be done automatically. The thing it said is an invalid partition table. I guess I am in deep **** now.

---

### Post by techunit on 2011-04-03
Did you look at this Link?
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

try doing it in the live CD.

---

### Post by jvacek996 on 2011-04-03
I did that earlier on before but with no results. Well now the live cd recognises my NTFS as... Well it doesn't recognise it.
I would say a lot of things but I don't want to get banned. Do you think that a fresh windows intall would do? I backed up my 70 gigs of music and am basically able to do the jump.

---

### Post by jvacek996 on 2011-04-03
I guess it was world backup day for a reason.

---

### Post by wilee-nilee on 2011-04-03
Since the cd is now recognizing windows try this, I have highlighted the two commands to run and have included the rest if needed.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
**BootRec.exe /FixBoot** (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

I would be running a chkdsk /r at some point as well.

---

### Post by techunit on 2011-04-03
Try the above suggestion first.

I didn't want to suggest that immediately but yeah a clean Windows install would fix windows. When installing windows leave the Elementary OS partition alone. Then when its finished installing windows reboot into your live cd (elementaryOS) and install grub.

If Windows isn't immediately available try ```
sudo update-grub
```
then you should be set.
_______________________________

What likely happened was when you shrunk your windows partition to make room for Elementary you either used Gparted or The Installers partitioner and that corrupted your windows boot config.

If you leave the ElementaryOS partition alone you should be able to just reinstall grub and be set.

---

### Post by jvacek996 on 2011-04-03
> **wilee-nilee said:**
> Since the cd is now recognizing windows try this, I have highlighted the two commands to run and have included the rest if needed.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
**BootRec.exe /FixBoot** (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

I would be running a chkdsk /r at some point as well.

If I would've known that I guess it would've saved some time, but sadly enough it is too late now

---

### Post by techunit on 2011-04-03
I am sorry I am trying to help as fast as I can.

---

### Post by jvacek996 on 2011-04-03
But thanks for all the help guys, I really appreciated it. It sad how daft I was but I guess we all learn from our mistakes. I'll do a little intro for anyone who will come across this in the first post.
Thanks a lot and good luck.
This thread is now shamefully solved

---

### Post by jvacek996 on 2011-04-03
> **wilee-nilee said:**
> Since the cd is now recognizing windows try this, I have highlighted the two commands to run and have included the rest if needed.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
**BootRec.exe /FixBoot** (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

I would be running a chkdsk /r at some point as well.

> **techunit said:**
> I am sorry I am trying to help as fast as I can.

It is ok, it's not your fault :) I guess it was time for a fresh start anyway

---

### Post by wilee-nilee on 2011-04-03
> **jvacek996 said:**
> If I would've known that I guess it would've saved some time, but sadly enough it is too late now

Sounds like your reinstalling, if you don't have W7 professional or above which allows imaging and backups at any time down load the clonzilla iso and make use of it. If you had an image of sda1 right now you would just slip it back in. I use the W7 imager as I have pro and the clonezila back up as well, I have slipped in the windows 7 version several times still activated.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by techunit on 2011-04-03
Please please please. Don't give up on linux because of this experience. Feel free to drop me a line PM me or what ever for help.

---

### Post by kio_http on 2011-04-03
Not you can always make the windows bootloader chainload to grub using [EasyBCD]("http://neosmart.net/dl.php?id=1").

---

### Post by jvacek996 on 2011-04-03
I have enterprise thanks to my stepfather's institute technician but I think it is too late because I technically lost the whole partition.

---

### Post by jvacek996 on 2011-04-03
> **techunit said:**
> Please please please. Don't give up on linux because of this experience. Feel free to drop me a line PM me or what ever for help.

Rick astley's Never gonna give you up describes my attitude towards Ubuntu the best.

---

### Post by techunit on 2011-04-03
Beyond the terrible music reference, a good way to look at this. I had a terrible experience with Ubuntu once upon a time and Now I am power user.

---

### Post by jvacek996 on 2011-04-03
Anyways, the first thing I'll do once I'm done with installing windows is put elementary on, and no one is going to make me go the easybcd way by bribing me with sending private messages as *caugh* no one *caugh* did.

---

### Post by drs305 on 2011-04-03
> **jvacek996 said:**
> Anyways, the first thing I'll do once I'm done with installing windows is put elementary on

A reinstall of elementary shouldn't be necessary if the partition table is ok; but if you do make sure you do not install Grub2 to a partition - only to the sda MBR. The problem occurred when Grub2 was mistakenly installed on the Windows (sda1) partition.

A normal installation of Windows, followed by a normal (re)installation of Grub2 via the LiveCD should have both OS's working properly.

---

### Post by techunit on 2011-04-03
> **drs305 said:**
> A reinstall of elementary shouldn't be necessary if the partition table is ok; but if you do make sure you do not install Grub2 to a partition - only to the sda MBR. The problem occurred when Grub2 was mistakenly installed on the Windows (sda1) partition.

A normal installation of Windows, followed by a normal (re)installation of Grub2 via the LiveCD should have both OS's working properly.
Thank you for clarifying what I was trying to say earlier.

---

### Post by jvacek996 on 2011-04-03
I noticed what you said earlier on but I think i can get the Lilo to recognise the elementary without installing grub whasoever. I managed o do it before with some software with an actual GUI on windows. Hiwever i am a BURG fan so i might install that after everything has settled down. But my top priority now is to get some well deserved sleep, it's 22:00 in Brussels anyway and even though it's not FRIIIDAY FRIIIDAY I gotta be fresh tomorrow morning for school. Thanks once again guys, all the help was much appreciated.

---

### Post by techunit on 2011-04-03
Not a problem. I would reinstall grub if your going to use burg.

---

### Post by jvacek996 on 2011-04-03
Is that necessary? I don't think it is but then I am the one who just had to reinstall his windows 7 because of doing something stupid.

---

### Post by techunit on 2011-04-03
I believe that burg actually relies on Grub so yes.

---

### Post by jvacek996 on 2011-04-03
Therefore it is most probably installed with it I guess. Fir some reason it is easier for me to install BURG than GRUB, although I already had some trouble with it before, back in the nooby days. Not like I'm not a noob now, but you know, now I'm not typing root apt-get update.

---

### Post by techunit on 2011-04-03
Well just trying to keep you out of trouble as much as possible.

---

### Post by wilee-nilee on 2011-04-03
Burg is a tweaked version of grub, leave both in place. Burg will run without grub still there but I would leave it as a back up.

---

### Post by techunit on 2011-04-03
He's going to need to reinstall grub because grub is installed but lilo is partially installed over it. So... arg so confused.

---

### Post by jvacek996 on 2011-04-04
> **kio_http said:**
> Not you can always make the windows bootloader chainload to grub using [EasyBCD]("http://neosmart.net/dl.php?id=1").
actually yeah, easy BCD is really easy to use. thanks for that!

---


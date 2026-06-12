---
title: "urgent help needed trouble in getting my old window files"
date: 2010-09-12
forum: General Help
---

### Post by ryansdistrict on 2010-09-12
hello i am trying to get my windows files from ubuntu 
long ago it was working for me i had window files mounted but i dont know what am doing wrong its nto working 
please can you guide me step step to get my files back
here are my 
ryan@ryan-tecra:~$ sudo fdisk -l
output: 


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x98d907b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   17  Hidden HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       17676   141871628   17  Hidden HPFS/NTFS
/dev/sda3   *       29127       30402    10238976    7  HPFS/NTFS
/dev/sda4           17676       29127    91981825    5  Extended
/dev/sda5           17676       28655    88194048   83  Linux
/dev/sda6           28655       29127     3786752   82  Linux swap / Solaris

---

### Post by sgosnell on 2010-09-12
Punctuation was invented for a reason.  Please learn to use it.  It makes reading your typing much easier.

Your files are somewhere on sda1, sda2, or sda3.  I have no idea where, because you could have saved them on any partition.  You can mount the Windows partitions in Ubuntu, and access the files.  You'll need to mount all the partitions and search them for the files you want.  You should be able to open Nautilus, the file manager, from Places, and then click on the partitions and mount them.  They won't show up as c:, d:, or whatever as they do in Windows, but they're the same, whatever they're called.

---

### Post by ryansdistrict on 2010-09-12
but am stuck with this error 


root@ryan-tecra:/home/ryan# mount /dev/sda2 /media/win2/ -t ntfs -o nls=utf8,umask=0222
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.




am not able to enter windows to chk for errors and the disk utility not doing the job
what should i do in this case ?

---

### Post by thestig_992 on 2010-09-13
I'm also stuck with this error, and i cant run chkdsk like it says to since the only install disk i have is an Asus OEM version that restores the installation to factory settings.

Is there a way to run chkdsk without a full copy of windows?

---

### Post by coffeecat on 2010-09-13
> **ryansdistrict said:**
> but am stuck with this error 

...

In the first case run chkdsk /f on Windows
then reboot into Windows twice.

...

am not able to enter windows to chk for errors and the disk utility not doing the job
what should i do in this case ?

There is only one thing you can do in this case. There are no Linux ntfs tools which will fix the NTFS partition, so you have to use chkdsk. Since you can't boot into your own Windows, you will have to take the hard drive out of the machine, put it into a USB enclosure and then plug that into another machine running Windows and use that other machine's Windows to run chkdsk.

If you haven't got or can't get hold of a USB enclosure then you could install the HD from your machine into the other Windows machine as a secondary drive. And if you can't borrow or use another Windows machine, then you're stuck. The only way of repairing that NTFS partition is to use chkdsk.

Actually, you're not quite stuck. You could use data recovery software (such as photorec) but I would not recommend that if there is the slightest chance of being able to use chkdsk somehow.

**Edit:** just realised when I saw thestig_992's post, that if you have Vista or W7, you can download a recovery disc to run chkdsk. That's probably better than taking out your hard drive. But if XP - you don't say which version you have - you would need the MS installation disc. See my post below.....

---

### Post by coffeecat on 2010-09-13
> **thestig_992 said:**
> Is there a way to run chkdsk without a full copy of windows?

If you're running Vista or Windows 7, you could download a recovery disc from here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

If XP, you'd need a Microsoft install CD, which I know you don't have.

---

### Post by thestig_992 on 2010-09-13
Thanks for the link to that file, i couldnt get any peers for it though, so i found an alternate link on the pirate bay. (Dont worry the file is perfectly legal, made by microsoft and not able to install windows or anything).

so yeah, ryansdistrict, if you cant download coffeecats file try this one.
[http://thepiratebay.org/torrent/5760089/Windows_7_Recovery_Disc_64-Bit_%28x64%29_Edition]("http://thepiratebay.org/torrent/5760089/Windows_7_Recovery_Disc_64-Bit_%28x64%29_Edition")

Im gonna go try it out now, wish me luck XD

---

### Post by coffeecat on 2010-09-13
> **thestig_992 said:**
> Thanks for the link to that file, i couldnt get any peers for it though, so i found an alternate link on the pirate bay.

I notice you're getting the Windows 7 disc. There is another way if you have access to another Windows 7 machine that's working. In W7, click on the start button and type 'repair disc' (or 'repair disk' if you're American :wink:) into the search field. Click on the 'Create a System Repair disc' (or disk) and then follow the prompts.

Microsoft were going to include this facility in Vista SP1, but pulled it at the last moment. But there is a way of creating a repair disc in Vista, see here:

[http://www.istartedsomething.com/20080324/recover-create-a-recovery-disc-vista-sp1-rtm/](http://www.istartedsomething.com/20080324/recover-create-a-recovery-disc-vista-sp1-rtm/)

It's a little hair-raising, but I've done it. So, no need for torrents if you have access to a friend's/relative's Vista/W7.

---

### Post by thestig_992 on 2010-09-13
I did find some tutorials to do that, the problem is though that i cant boot at all, once it gets past grub it just sits there with a blank screen. I have an asus OEM copy that will let me restore to factory settings, i guess im just gonna have to go with that and then use my backup from about a month ago...

ty for the help though

---


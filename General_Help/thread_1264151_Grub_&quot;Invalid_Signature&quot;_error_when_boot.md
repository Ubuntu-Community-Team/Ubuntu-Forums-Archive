---
title: "Grub &quot;Invalid Signature&quot; error when booting windows"
date: 2009-09-11
forum: General Help
---

### Post by cak3 on 2009-09-11
I have 3 hard disks. THe first one has windows, the second windows programs, and the third linux. Grub is installed to the MBR of the third, and it is my primary boot disk. Everything was working fine, but then, when I chose to boot to windows (which I had done before just fine), grub told me "Error 13: Invalid Signature" (or something like that). I made sure it pointed to the right paritition ((hd0,0) or /dev/sda1) and it did. I had wanted to upgrade to grub2 anyway, and I figured that would fix it, so I did that, and had it recheck and regenerate everything on its own. It generated an entry for windows (Windows 7, though it detected it as a Vista loader, but that is normal). Ubuntu booted fine in grub2, but when I tried to boot into windows, i got ```
Booting 'Windows Vista (loader) (on /dev/sda1)'
error: invalid signature
Press any key to continue
```
Upon pressing a key I was returned to the grub menu.

I figured it was a problem with windows then, so I booted into a windows 7 install CD, used the bootrec.exe program to repair the boot sector, and for good measure write a Windows MBR to the first hard disk. When booting from grub, same deal, but when I told the computer to boot from the first HDD, windows booted just fine.

So... anybody got any ideas?

fdisk -l:```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45824581

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       60801   385985722+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005bb9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007e5e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          25      200781   83  Linux
/dev/sdc2              26       65705   527574600    5  Extended
/dev/sdc3           65706       91201   204796620    7  HPFS/NTFS
/dev/sdc5              26       38270   307202931   83  Linux
/dev/sdc6           38271       65705   220371606   83  Linux

```

---

### Post by luckyu on 2009-09-11
hey,
 i think your problem is that grub is using the wrong device name. instead of /dev/sda1 it should be /dev/hd0 or something like that.

what I need you to do is show me```
dmesg
```

also show me /boot/grub/menu.lst file

from there i will determine your problem

---

### Post by cak3 on 2009-09-11
The output of 'fdisk -l' would indicate that the device names are correct, but I am attaching the output of 'dmesg' anyway. 

The relevant stuff is probably here:
```

$ sudo dmesg | grep sd[abc]
[   34.167023] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[   34.167028] sd 0:0:0:0: [sda] Write Protect is off
[   34.167030] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.167038] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.167076]  sda: sda1 sda2
[   34.193693] sd 0:0:0:0: [sda] Attached SCSI disk
[   35.012733] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[   35.012738] sd 1:0:0:0: [sdb] Write Protect is off
[   35.012740] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   35.012748] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.012778]  sdb:<6>usb 2-6: configuration #1 chosen from 1 choice
[   35.040306]  sdb1
[   35.040338] sd 1:0:0:0: [sdb] Attached SCSI disk
[   36.070214] sd 2:0:0:0: [sdc] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[   36.070219] sd 2:0:0:0: [sdc] Write Protect is off
[   36.070221] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   36.070229] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.070259]  sdc: sdc1 sdc2 < sdc5 sdc6 > sdc3
[   36.115180] sd 2:0:0:0: [sdc] Attached SCSI disk
[   39.540724] kjournald2 starting: pid 922, dev sdc5:8, commit interval 5 seconds
[   39.553978] EXT4-fs: mounted filesystem sdc5 with ordered data mode
[   44.592423] EXT4 FS on sdc5, internal journal on sdc5:8
[   45.265730] kjournald2 starting: pid 2277, dev sdc1:8, commit interval 5 seconds
[   45.266803] EXT4 FS on sdc1, internal journal on sdc1:8
[   45.266868] EXT4-fs: mounted filesystem sdc1 with ordered data mode
[   45.272555] kjournald2 starting: pid 2278, dev sdc6:8, commit interval 5 seconds
[   45.272939] EXT4 FS on sdc6, internal journal on sdc6:8
[   45.281889] EXT4-fs: mounted filesystem sdc6 with ordered data mode

```

As to the menu.lst, grub2 doesn't have one. It has been replaced by /boot/grub/grub.cfg (attached in first post). That file is automatically generated from scripts in /etc/grub.d/ and is updated whenever 'update-grub' is exectuted. (you can also prefedine fixed entries that it will include). 

the relevant bit of the grub.cfg is:
```

 51 ### BEGIN /etc/grub.d/30_os-prober ###
 52 menuentry "Windows Vista (loader) (on /dev/sda1)" {
 53     set root=(hd0,1)
 54     chainloader +1
 55 }

``` (the line numbers are because I copied it out of vim).

Actually, looking at that now, I wonder if it shuoldn't be (hd0,0) instead... I will reboot and the post another update about that.

Oh, apparently the output of dmesg is too large a file to attach as a text file. Oh well.

EDIT: So I tried changing it to root=(hd0,0) but it said "no such partition". So, that wasn't the problem. Or at least not the solution. It could be related to the problem. "Invalid signature" seems to suggest that it is finding something, it just doens't like it for some reason.

---

### Post by cak3 on 2009-09-12
So, a google search for "grub invalid signature" returned this thread as the first result, which isn't entirely helpful. I guess google gives ubuntuforums.org high priority. Oh yea, anyway... bump.

---

### Post by ronparent on 2009-09-12
If you change the boot order in bios, is there still a valid windows MBR on that drive to boot directly into windows. I suspect the problem may be a windows problem rather than grub. You should probably check that out. Post back your results.

---

### Post by cak3 on 2009-09-12
> **ronparent said:**
> If you change the boot order in bios, is there still a valid windows MBR on that drive to boot directly into windows. I suspect the problem may be a windows problem rather than grub. You should probably check that out. Post back your results.

Yea, I kinda mentioned that in the first post, though it wasn't very clear. I have a windows MBR on the first HDD, and if I choose to boot from that HDD (via the BIOS boot selection menu, same idea as changing the boot order) I can get into windows. I didn't have a windows MBR on that drive until I wrote it from the win 7 disk after I started having this issue, since I couldn't get to windows via grub.

I agree that it seems likely that it  has something to do with windows, but the error is within grub, so I am hoping to at least figure out what "invalid signature" means and what needs to be done to fix it.

---

### Post by cak3 on 2009-09-13
anyone?

---

### Post by SuaSwe on 2009-09-13
Considering the fact that you are able to boot into that same Windows installation (at least this is what I gathered) when not using GRUB, it would appear that the Windows installation is fine - e.g., I'd say the issue is with GRUB and its interpretation of your Windows drive. Maybe it's having issues with the boot sequence, or the way the hard drives are connected physically? 

You have two partitions on hd0. What is on each one? I personally find it odd that GRUB2 didn't find partition 0 on hd0, considering that should be this one:

/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS <<<<<<
/dev/sda2           12749       60801   385985722+   7  HPFS/NTFS

... but maybe I'm just talking out my *rse. :D

It doesn't help your situation that the grub.cfg file isn't to be edited manually even if we knew what was wrong with it!

---

### Post by cak3 on 2009-09-13
The second partition on hd0 is all my user data for windows (the first one begin just the system itself). I was looking at the cfg file, and it seems grub2 calls the first partition (hdx,1) instead of 0 (which matches the /dev/sdx1 scheme). I assume this is so at least, since it uses (hd2,1) as the root when booting linux (which works) and the boot partition is the first one.

It could be something with the drive, thats a good idea. I'll try writing grub to the MBR of one of the others and see if it works. Won't be able to do that till later today though.

---

### Post by SuaSwe on 2009-09-13
hd0,0 (equal to /dev/sda1) would be the first partition on the first hard drive, which I believe is the one GRUB2 should be pointing at as that's the system partition, according to what you've described (makes sense size-wise as well). As such, I personally cannot see any issues with your grub.cfg file and its reference to the Windows drive; it would appear that the problem lies elsewhere.

Did anything at all change before all this happened, especially hardware changes? Could you find out what the exact error was that you got when you were still using GRUB Legacy? GRUB2 isn't exactly a well-known entity as it stands. :D

---

### Post by SuaSwe on 2009-09-13
hd0,0 (equal to /dev/sda1) would be the first partition on the first hard drive, which I believe is the one GRUB2 should be pointing at as that's the system partition, according to what you've described (makes sense size-wise as well). As such, I personally cannot see any issues with your grub.cfg file and its reference to the Windows drive; it would appear that the problem lies elsewhere.

Did anything at all change before all this happened, especially hardware changes? Could you find out what the exact error was that you got when you were still using GRUB Legacy? GRUB2 isn't exactly a well-known entity as it stands. :D

---

### Post by cak3 on 2009-09-13
So, I didn't to have to restore the windows MBR again, so I decided to install grub to the one drive that didn't have a bootloader yet (/dev/sdb). I went to boot windows from that, and I got a different error! "BOOTMGR not found..." It told me to press Ctrl+alt+del to restart, which suggested that it was a windows problem, since grub seems to just take you back to the menu if it can't boot. Anyway, I didn't want to deal with a new problem, so I said, heck with it, and installed grub to the first HDD (with windows on it). And it worked. 

Which is great, but weird, since I am pretty sure I was able to boot when grub was installed on a different drive...

I am not complaining, since it works. I might mess around some more later, to figure out more about how this works, but for now I am done. Thanks for the help.

---

### Post by zulek87 on 2009-10-28
hi!

I got same issue.

After installing ubuntu 9.10 beta grub2 couldn't find my Win Xp.
So i followed the rules:

# apt-get install os-prober
# update-grub2

And it worked fine, till I updated my grub2 to the grub-pc.

Now I have exactly the same message: Invalid signature


I have grub installed at windows partition:)

/////////////////////////////////////////////////////////////////////

So i solved it.
[B]
my disk with windows and linux is /dev/sdb[/B]

**sudo gedit /boot/grub/device.map**

**(hd0)    /dev/sda     _change to_****       (hd0)    /dev/sdb**

save

then

[B]sudo os-prober
sudo update-grub[/B]
**sudo reboot **
;)

---

### Post by DrWarm on 2009-11-02
Sorry could you explain how you installed grub on the windows partition (if that's what you did)?

When I update grub2 i get:
```
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done
```
Now that line of grub-probe with the error makes me think it's that, so i checked out /boot/grub/device.map but got only:
```
(hd0)	/dev/sda
```

So all i need to do is:
> (hd0) /dev/sda change to (hd0) /dev/sdb

I don't want to try it until I've had confirmation from someone, as I'm not super keen to reinstall windows again, as i just did it!

Anyway this is my output from fdisk:
```
sudo fdisk -l /dev/sda

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d2c0565

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2549    20474811    5  Extended
/dev/sda2            2550      121601   956278784    7  HPFS/NTFS
/dev/sda5               1         486     3903732   82  Linux swap / Solaris
/dev/sda6             487        1459     7815591   83  Linux
/dev/sda7            1460        2549     8755393+  83  Linux

```

```
sudo fdisk -l /dev/sdb

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001f164

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13        5737    45977600    7  HPFS/NTFS
/dev/sdb3           11430      121601   884956160    7  HPFS/NTFS

```

So obviously windows is located on hd2, and i think that 100mb boot partition it makes is sdb1. 

I want to be careful with this, as I only just reinstalled windows 7 again, and don't want to mess it up! Any help would be great.

Thanks

---

### Post by satellite360 on 2009-11-02
Removed - see response below

---

### Post by satellite360 on 2009-11-03
> **DrWarm said:**
> Sorry could you explain how you installed grub on the windows partition (if that's what you did)?

When I update grub2 i get:
```
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done
```
Now that line of grub-probe with the error makes me think it's that, so i checked out /boot/grub/device.map but got only:
```
(hd0)	/dev/sda
```

So all i need to do is:


I don't want to try it until I've had confirmation from someone, as I'm not super keen to reinstall windows again, as i just did it!

Anyway this is my output from fdisk:
```
sudo fdisk -l /dev/sda

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d2c0565

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2549    20474811    5  Extended
/dev/sda2            2550      121601   956278784    7  HPFS/NTFS
/dev/sda5               1         486     3903732   82  Linux swap / Solaris
/dev/sda6             487        1459     7815591   83  Linux
/dev/sda7            1460        2549     8755393+  83  Linux

```

```
sudo fdisk -l /dev/sdb

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001f164

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13        5737    45977600    7  HPFS/NTFS
/dev/sdb3           11430      121601   884956160    7  HPFS/NTFS

```

So obviously windows is located on hd2, and i think that 100mb boot partition it makes is sdb1. 

I want to be careful with this, as I only just reinstalled windows 7 again, and don't want to mess it up! Any help would be great.

Thanks

DrWarm, try adding this to /etc/grub.d/40_custom
```
menuentry "Windows 7 (on /dev/sdb1)" {
insmod ntfs
set root=(hd1,1)
chainloader +1
}
```
Not a fix, exactly, but should allow you to access your Windows partition until the os-prober starts working properly

---

### Post by DrWarm on 2009-11-04
Wow thanks alot, worked a treat!!!!! Thanks again!

---

### Post by elgordo123 on 2009-11-07
I had this same problem after and update to Ubuntu 9.10.  Took forever to find solution - nothing on this thread worked, but lead me in right direction.   
Noticed when I did sudo update-grub it came back with weird errors so did this:
sudo apt-get install os-prober
sudo os-prober, made sure it showed both linux and windows
sudo mv /boot/grub/device.map /boot/grub/device.map.bak
sudo update-grub (came back clean)
reboot (all is well)

---

### Post by jtliii on 2009-11-12
Thanks elgordo123! That fixed it for me.

---

### Post by easy2002 on 2009-11-14
> **elgordo123 said:**
> 
sudo apt-get install os-prober
sudo os-prober, made sure it showed both linux and windows
sudo mv /boot/grub/device.map /boot/grub/device.map.bak
sudo update-grub 

thank you very much!

---

### Post by easy2002 on 2009-11-14
ooh, my first post for two years :D
[sorry for offtopic]

---

### Post by DrWarm on 2009-11-14
Thankyou elgordo123, works great as everyone else has stated. Sometimes it's the simplest solution that works!

---

### Post by RickyMcRick on 2009-11-30
Just trying to follow elgordo123's suggestion and had a question -
after entering 'sudo os-prober' to the command terminal, what does it mean  'make sure it shows both linux and windows'?

When I enter 'sudo os-prober' I only get the following message:
'/dev/sdb1:Microsoft Windows XP Home Edition:Windows:chain'
but it doesn't tell me anything about linux. Is there something I've missed?

I've got ubuntu 9.10 on my first hard drive, and windows xp on my second, and grub2 isn't letting me boot into the windows drive (even though I can boot windows using the bios settings).

thanks (ps. i've only had ubuntu for 3 days and don't know what I'm doing)

---

### Post by lupeatx on 2009-12-04
> **zulek87 said:**
> hi!

I got same issue.

After installing ubuntu 9.10 beta grub2 couldn't find my Win Xp.
So i followed the rules:

# apt-get install os-prober
# update-grub2

And it worked fine, till I updated my grub2 to the grub-pc.

Now I have exactly the same message: Invalid signature


I have grub installed at windows partition:)

/////////////////////////////////////////////////////////////////////

So i solved it.
[B]
my disk with windows and linux is /dev/sdb[/B]

**sudo gedit /boot/grub/device.map**

**(hd0)    /dev/sda     _change to_****       (hd0)    /dev/sdb**

save

then

[B]sudo os-prober
sudo update-grub[/B]
**sudo reboot **
;)


This fixewd my problem. Now I can boot to Windows

---

### Post by Jim55 on 2009-12-08
After I reduced the ubuntu partition size I could not access XP ... "invalid signature" error.  I tried what is suggested here but it did not not help ...
jim@JimBigOne:~$ sudo apt-get install os-prober
Reading package lists... Done
Building dependency tree       
Reading state information... Done
os-prober is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-15
  linux-headers-2.6.31-15-generic-pae
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jim@JimBigOne:~$ sudo os-prober
/dev/sdb1:Microsoft Windows XP Professional:Windows:chain
jim@JimBigOne:~$ sudo mv /boot/grub/device.map /boot/grub/device.map.bak
mv: cannot stat `/boot/grub/device.map': No such file or directory
jim@JimBigOne:~$ 

Any suggestions as to how to get my XP back?  Ubuntu still works.

---

### Post by Jim55 on 2009-12-08
XP is in sdb1 and unbuntu is in ext4 in sdb5 that is in sdb2

[IMG]file:///tmp/moz-screenshot-1.png[/IMG]

[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by Ciwan on 2009-12-08
Thank You elgordo123

---

### Post by Jim55 on 2009-12-09
This fixed my problem

sudo grub-mkdevicemap
sudo update-grub2

---

### Post by DeadGoat on 2009-12-15
hell-o everybody...
just a not-even-a-rookie in linux world... got same problem here, was very headache... tried to boot 7 with grub and suddenly the```
error: invalid signature
```appear... press 'enter', it return to previous grub menu... then search over the net and find this thread, tried all the possibilities and tutorial given in this thread but still failed. At the very moment i want to gave up (gonna format n reinstall 7...deymm) then i tried this ```
sudo apt-get install grub2
``` the 7 shine again... woahhh watta relief... thanx to all the output u guys posted that lead me here so now i can continue my quest in Dragon Age: Origin ;)

---

### Post by trellis2 on 2009-12-15
Thanks elgordo123 muy bien!!! I've tried so many complicated schemes and once again simplicity does the trick.

---

### Post by 73ckn797 on 2009-12-19
> **zulek87 said:**
> **sudo gedit /boot/grub/device.map**

I am learning grub2 quickly. I had the same learning curve with grub legacy when first beginning to use Ubuntu 8.04.

This tip (quoted) led me to my solution. I only had to use the command I quote to resolve the booting Windows issue.

I was having the "invalid signature" error. I started with 9.10 on the first drive (sda), a data drive (sdb). I then installed a 3rd drive which was a PATA connection. The other drives are SATA. The BIOS lists the PATA first in the device list on boot-up. Boot order was sda, sdb & sdc. The sdc drive was the newly added drive. On that drive I installed Windows XP. Looking at the out put of ```
fdisk -l
``` and ```
blkid
``` the drives were listed properly.

When booting, the Windows drive returned the "invalid signature" message. I could boot Windows if I designated the sdc drive as first boot device so I knew there was no problem there.

I went and entered the command to edit "device.map". Once in there I found the list was: ```
(hd0)      /dev/sda
(hd1)      /dev/sdb
```I added ```
(hd2)      /dev/sdc
```Then I ran in terminal: ```
sudo update-grub2
```On reboot Windows loads and all is again right in my Ubuntu world. The device (sdc) was not mapped at all and any attempts to update grub2 returned errors for the sdc drive.

This was on another computer my wife uses.

A little bit of searching solved the problem and I have learned more about grub2.

---

### Post by ktechman on 2010-01-07
Worked for me

Thank you Zulek87

Ktechman

---

### Post by Leppie on 2010-01-07
running:
```
sudo grub-mkdevicemap
```
should regenerate your device.map

after which you can update your grub.cfg normally:
```
sudo update-grub  ##update-grub2 really is for upgrades from grub legacy
```

---

### Post by Bosluis on 2010-01-11
> **Jim55 said:**
> This fixed my problem

sudo grub-mkdevicemap
sudo update-grub2

Excuse my ignorance, but where do you enter these?

Thank You

Bosluis

---

### Post by Bosluis on 2010-01-11
> **Bosluis said:**
> Excuse my ignorance, but where do you enter these?

Thank You

Bosluis

Sorry,  ran in terminal, now I am sorted too!

Bosluis

---

### Post by luke_lukem on 2010-01-14
Hi everyone,

I just had the "invalid signature" error today, 
with my Windows 7 partition, and i guess it's caused by messing with grub menu entries, executing "sudo update-grub" too many times.

I solved it by editing /boot/grub/device.map, as did [73ckn797]("http://ubuntuforums.org/showthread.php?t=1264151&page=4")

After adding an entry for my second hard disk, it looked like this:
```
(hd0)      /dev/sda
(hd1)      /dev/sdb
```

After that, ran:
```
sudo update-grub
```

And everything started working again, just like the orthers posted.

Thank you all for this guide, saved my day :-)

---

### Post by Peter Strauss on 2010-01-25
[deleted by author]

---

### Post by C-ramm on 2010-01-29
When I run `sudo update-grub2` I get:

```

grub-probe: error: no mapping exists for 'nvidia_cdiibcai1'
done

```


Everything was working perfectly before I ran `sudo apt-get upgrade` earlier this evening. All I have setup in /boot/grub/grub.cfg is:

```

menuentry "Windows 8 (loader) (on /dev/mapper/nvidia_cdiibcai1)" {
  chainloader +1
}

```

Do I have to define `nvidia_cdiibcai1` in /boot/grub/device.map somehow?

---

### Post by Leppie on 2010-01-30
> **C-ramm said:**
> When I run `sudo update-grub2` I get:

```

grub-probe: error: no mapping exists for 'nvidia_cdiibcai1'
done

```Everything was working perfectly before I ran `sudo apt-get upgrade` earlier this evening. All I have setup in /boot/grub/grub.cfg is:

```

menuentry "Windows 8 (loader) (on /dev/mapper/nvidia_cdiibcai1)" {
  chainloader +1
}

```Do I have to define `nvidia_cdiibcai1` in /boot/grub/device.map somehow?
not sure why grub2 didn't pick it up, but according to menu.lst you are using lvm for xp, so you have to load the lvm module. is it loaded now, or are you no longer using lvm?

---

### Post by C-ramm on 2010-01-30
I haven't changed my setup at all; so as I far as I know, I am still using lvm.

I tried enabling this in the menuentry block for the Windows 7 loader (sorry for the typo before), but I am getting the same error. 

For clarity, here is the block in /boot/grub/grub.cfg again:

```

menuentry "Windows 7 (loader) (on /dev/mapper/nvidia_cdiibcai1)" {
        insmod lvm
        chainloader +1
}

```

---

### Post by Leppie on 2010-01-30
could you post your grub defaults file:
```
cat /etc/default/grub
```

---

### Post by Aitaix on 2010-02-01
thank you [elgordo123]("http://ubuntuforums.org/member.php?u=29426")

---

### Post by C-ramm on 2010-02-01
output of cat /etc/default/grub:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

```

---

### Post by Leppie on 2010-02-01
edit your the grub defaults file:
```
gksudo gedit /etc/default/grub
```
and add the following line at the end:
```
GRUB_PRELOAD_MODULES=lvm
```
save and exit and run update-grub:
```
sudo update-grub
```

check that the menu entry for your 7 install is now complete.

---

### Post by C-ramm on 2010-02-08
Sorry for the delay! I just tried this, and I recieved the same result. My /etc/default/grub is:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

GRUB_PRELOAD_MODULES=lvm

```

And my result is still:

```

$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/mapper/nvidia_cdiibcai1
grub-probe: error: no mapping exists for `nvidia_cdiibcai1'
done

```

---

### Post by Leppie on 2010-02-08
try the following command first then:
```
sudo grub-mkimage --output=/boot/grub/core.img ext2 _chain part_msdos part_gpt biosdisk lvm

```
then try running update-grub again:
```
sudo update-grub
```

---

### Post by C-ramm on 2010-02-08
No luck again. Might have narrowed it down a bit though:

```

$ sudo grub-mkimage --output=/boot/grub/core.img ext2 _chain part_msdos part_gpt biosdisk lvm

grub-mkimage: error: cannot stat /usr/lib/grub/i386-pc/_chain.mod

```

I checked the directory and noticed that there was a "chain.mod", but not one with an underscore. I removed it and tried again:

```

$sudo grub-mkimage --output=/boot/grub/core.img ext2 chain part_msdos part_gpt biosdisk lvm

```

It seemed to work, so I continued:

```

$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/mapper/nvidia_cjbdfafb1
grub-probe: error: no mapping exists for `nvidia_cjbdfafb1'
Found Windows 7 (loader) on /dev/mapper/nvidia_cdiibcai1
grub-probe: error: no mapping exists for `nvidia_cdiibcai1'
done

```

Seems to be picking it up twice now for whatever reason.

---

### Post by Leppie on 2010-02-08
could you post your device.map?
```
cat /boot/grub/device.map
```

---

### Post by C-ramm on 2010-02-08
```

$ cat /boot/grub/device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```

---

### Post by Leppie on 2010-02-08
run the following command:
```
sudo grub-mkdevicemap
```
then run updaet-grub again:
```
sudo update-grub
```

---

### Post by C-ramm on 2010-02-09
Same result. :-( Device list in 'device.map' is the same as well.

---

### Post by Leppie on 2010-02-10
are you actually able to access the logical volume?
did you install the lvm2 package?
```
sudo apt-get install lvm2
```

---

### Post by Elumako on 2010-02-11
Halp!

I'm a "less than n00b" trying to get Ubuntu to play nice with Windows 7 on the same machine, and it doesn't seem to be going so well.

I'm seeing the exact same error message as a few other folks, it seems, and it started as soon as I ran the *.19 system update yesterday.

:(

Output of: fdisk -l

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92b46aa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb84bb84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19273   154810341   83  Linux
/dev/sdc2           19274       20023     6024375   82  Linux swap / Solaris

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00012c91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux
```

---

### Post by meierfra. on 2010-02-11
Elumako:  Your case looks quite different. Could you start your own thread? Thanks


Leppie:  I don't know  much about raid. But "dev/mapper/nvidia_cdiibcai1" sounds like a fake raid and not a lvm.

---

### Post by C-ramm on 2010-02-12
I ran:

```
$ sudo apt-get install lvm2
```
and then:

```
$ sudo apt-get install lvm2
```

But I am still getting the same result.

Yes, I can mount the drive and navigate through it normally using:

```
$ sudo mount /dev/mapper/nvidia_cdiibcai1 myMnt/
```

(Note: mounting nvidia_cdiibcai produces a "mount: /dev/mapper/nvidia_cdiibcai already mounted or myMnt/ busy" error")

---

### Post by Leppie on 2010-02-12
> **meierfra. said:**
> Leppie:  I don't know  much about raid. But "dev/mapper/nvidia_cdiibcai1" sounds like a fake raid and not a lvm.
to be honest, i don't know much about raid either... have too much rubbish stored on drives to setup a fake raid and play around with it...

C-ramm, try modifying the preload modules in your grub defaults file:
```
gksudo gedit /etc/default/grub
```and modify the following line like this:
```

GRUB_PRELOAD_MODULES="lvm raid"
```
then run update-grub again:
```
sudo update-grub
```

---

### Post by C-ramm on 2010-02-12
No dice :-( Same result after sudo update-grub:

```

Found Windows 7 (loader) on /dev/mapper/nvidia_cdiibcai1
grub-probe: error: no mapping exists for `nvidia_cdiibcai1'
done

```

---

### Post by Leppie on 2010-02-12
but is this a raid or lvm?
can you access myMnt?

---

### Post by C-ramm on 2010-02-12
> but is this a raid or lvm?

Honestly, I had never heard of lvm before posting on this thread (and I am still not entirely sure what it is). The grub wiki describes lvm as:


*LVM volumes are named (volumegroup-volumename). This is the same format as the name of the devices in /dev/mapper. *


So my guess is that this is "lvm".

> can you access myMnt? 

Yes. After mounting I can cd into the mount, create, edit and move files around as normal.

---

### Post by C-ramm on 2010-02-12
I hate to say this, but I gave up :-(. I formatted my 9.10 partition and installed a new Windows 7 loader. This loader detected my previous Windows 7 installation and I can properly boot into it now.


If there is anyone else out there having this problem, then maybe stay away from grub2 for the time being.

---

### Post by mrzero on 2010-03-12
> **elgordo123 said:**
> I had this same problem after and update to Ubuntu 9.10.  Took forever to find solution - nothing on this thread worked, but lead me in right direction.   
Noticed when I did sudo update-grub it came back with weird errors so did this:
sudo apt-get install os-prober
sudo os-prober, made sure it showed both linux and windows
sudo mv /boot/grub/device.map /boot/grub/device.map.bak
sudo update-grub (came back clean)
reboot (all is well)

Thank you very much it works for me fine;)

---

### Post by sureshmagix on 2010-03-15
> **luke_lukem said:**
> hi everyone,

i just had the "invalid signature" error today, 
with my windows 7 partition, and i guess it's caused by messing with grub menu entries, executing "sudo update-grub" too many times.

I solved it by editing /boot/grub/device.map, as did [73ckn797]("http://ubuntuforums.org/showthread.php?t=1264151&page=4")

after adding an entry for my second hard disk, it looked like this:
```
(hd0)      /dev/sda
(hd1)      /dev/sdb
```after that, ran:
```
sudo update-grub
```and everything started working again, just like the orthers posted.

Thank you all for this guide, saved my day :-)

thanks it worked :d

---

### Post by dcody on 2010-03-15
> **Leppie said:**
> running:
```
sudo grub-mkdevicemap
```
should regenerate your device.map

after which you can update your grub.cfg normally:
```
sudo update-grub  ##update-grub2 really is for upgrades from grub legacy
```

Sir Leppie - you are the man of the hour...this was just the ticket.
Thanks billions.

---

### Post by Jander666 on 2010-03-29
Here is what i did, having the same problems as the other raid user:

try booting up grub and highlighting your existing one that says Windows 7 or vista

hit e and above the chainloader +1 put in there: set root=(hd0,1)

hit ctrl+x and see if windows will boot, if so all i had to do was go into the grub.cfg file
and add that same set root line to the file were it just put chainloader +1 everything works
fine now. 

My setup is two drives in raid for win7 and a separate none raid drive set for running Ubuntu 9.10

Thanks to all on here for the help, it lead me to my solving my problem! You all rule!

---

### Post by madhu1990 on 2010-03-29
> **lupeatx said:**
> This fixewd my problem. Now I can boot to Windows
Thanks a lot @zulek87 your solution worked perfectly! :)

---

### Post by DragonSlayer73 on 2010-04-08
Please help..

I recently upgraded to grub2.
I have windows 7 and ubuntu installed.
Ubuntu boots fine.
However Windows 7 will not boot.
Tried changing chainloader +1 to +4 as one person suggested the tried /bootmgr.
After changing to /bootmgr i get invalid signature.

Booted with Win 7 disk and went to recovery console snd noticed drive letter has changed from c: to d:.
Is this my problem?
And if so how can I fix it?

---

### Post by loseby on 2010-04-09
well I just fixed my problem by following the solution from 

[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8262566&postcount=18]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8262566&postcount=18") which is quoted below

> Re: Grub "Invalid Signature" error when booting windows
I had this same problem after and update to Ubuntu 9.10. Took forever to find solution - nothing on this thread worked, but lead me in right direction.
Noticed when I did sudo update-grub it came back with weird errors so did this:
sudo apt-get install os-prober
sudo os-prober, made sure it showed both linux and windows
sudo mv /boot/grub/device.map /boot/grub/device.map.bak
sudo update-grub (came back clean)
reboot (all is well)

---

### Post by pzoco on 2010-04-28
Hi.

I have the same problem.

I did a normal ```
# apt-get upgrade
```Rebooted

And tried to boot my Windows 7, and got an error "Invalid Signature" (What the H.. is that?)

fdisk -l
```
Disk /dev/sda: 500.1 Gb, 500107862016 byte
255 heads, 63 sectors/track, 60801 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe5a7fa6b

    Enhed Opstart   Start         ****     Blokke   Id  System
/dev/sda1   *           2       60801   488376000    f  w95 udvidet (LBA)
/dev/sda5               2       60801   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 203.9 Gb, 203928109056 byte
255 heads, 63 sectors/track, 24792 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdcb0e9f2

    Enhed Opstart   Start         ****     Blokke   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 slutter ikke på en cylindergrænse.
/dev/sdb2              13       12798   102692984    7  HPFS/NTFS
/dev/sdb3           12799       24792    96341805    5  Udvidet
/dev/sdb5           12799       24298    92373718+  83  Linux
/dev/sdb6           24299       24792     3968023+  82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 Gb, 1000204886016 byte
255 heads, 63 sectors/track, 121601 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6e9f6e9

    Enhed Opstart   Start         ****     Blokke   Id  System
/dev/sdc1   *           1      120850   970727593+  83  Linux
/dev/sdc2          120851      121601     6032407+   5  Udvidet
/dev/sdc5          120851      121601     6032376   82  Linux swap / Solaris

```grub.cfg
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb5 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb5 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

---

### Post by koepi123 on 2010-06-29
hey guys,

same problem after installing ubuntu after win xp on same HDD.
I tried it several times, its indeed the ubuntu versions/grubs fault that win xp cant boot after ubuntu install.

so.

I fail already at the recommended command : 
"sudo os-prober, made sure it showed both linux and windows"

because there is only windows shown.

at 2nd when I disabled with your help the problem "invalid signature" I continue booting xp like normal, have a short look at the win xp introduction and then I get a BLUESCREEN ( unmountable boot volume ).

how can I make sure that linux AND windows is shown after that os-prober-command ?

greetz

koepi

---

### Post by Leppie on 2010-06-29
[koepi123]("http://ubuntuforums.org/member.php?u=1103888"), please start a new thread for your issue.

---

### Post by koepi123 on 2010-06-29
I am talking of a specific problem that has already been "predicted" by posters.

when I start a new topic they and I need to discuss everything again. thats a waste of time, isn't it?

besides that I don't want to bother ppl who have no, only might have a clue about it, when I met someone who experienced same and can answer much more accurately ...

still want me to open a new thread?

---

### Post by Dreaded Claymore on 2010-09-09
> **Jander666 said:**
> Here is what i did, having the same problems as the other raid user:

try booting up grub and highlighting your existing one that says Windows 7 or vista

hit e and above the chainloader +1 put in there: set root=(hd0,1)

hit ctrl+x and see if windows will boot, if so all i had to do was go into the grub.cfg file
and add that same set root line to the file were it just put chainloader +1 everything works
fine now. 

My setup is two drives in raid for win7 and a separate none raid drive set for running Ubuntu 9.10

Thanks to all on here for the help, it lead me to my solving my problem! You all rule!

This worked perfectly for me, thank you Jander666. But, I don't know how to put that line into grub.cfg. It says not to edit it. How do I use the /etc/default/grub file to add that line to grub.cfg?

This is my first post, and my first time using Linux, I'm an absolute beginner

---

### Post by nealien on 2010-09-24
i stopped reading the posts in this thread a long time ago, when they stopped making sense.  you guys are all doing sooo much work when the answer is sooo simple.  im posting this from windows as i just fixed it myself with no help (first time for everything i guess lol).  

go to synaptic package manager.  search for grub 2.  install...

open terminal and type
sudo update-grub

reboot and windows should work now.  at least it did for me.  i realize that not all of us have the same configurations, but this should still work.

for the record, i have 4 hdds.  2 storage, 1 windows xp sp3, and 1 ubuntu.  after reinstalling windows from a virus i encountered this prob.  this is how i fixed it.  ;)

fyi, the post above this appears to be the manual way of doing what i did.  i think lol

---

### Post by jcma1987 on 2011-05-23
Hi there,

Having added the below to /etc/grub.d/40_custom I now receive an 'invalid signature' error when booting XP from the grub2 bootloader:

menuentry "Windows XP" {
insmod ntfs
set root=(hd0,1)
chainloader (hd0,1)+1


Unlike the previous posters, I am using PGP WDE which could be causing this issues. Below is the output of RESULTS.txt. Any help would be very much appreciated. 

Many thanks in advance

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   479,023,545   479,023,483   7 NTFS / exFAT / HPFS
/dev/sda2         479,025,150   625,141,759   146,116,610   5 Extended
/dev/sda5         479,025,152   619,096,063   140,070,912  83 Linux
/dev/sda6         619,098,112   625,141,759     6,043,648  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda5        31621b00-296f-42a4-ba46-a163052a8b06   ext4       
/dev/sda6        5c137f76-ef05-4fe1-a266-44aaf51ddf16   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=31621b00-296f-42a4-ba46-a163052a8b06 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=31621b00-296f-42a4-ba46-a163052a8b06 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=31621b00-296f-42a4-ba46-a163052a8b06 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=31621b00-296f-42a4-ba46-a163052a8b06 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=31621b00-296f-42a4-ba46-a163052a8b06 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=31621b00-296f-42a4-ba46-a163052a8b06 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows XP" {
insmod ntfs
set root=(hd0,1)
chainloader (hd0,1)+1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=31621b00-296f-42a4-ba46-a163052a8b06 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5c137f76-ef05-4fe1-a266-44aaf51ddf16 none            swap    sw              0       0
/dev/sr0   /media/cdrom0   udf,iso9660 user,noauto,exec   0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 274.544593811 = 294.790012928  boot/grub/core.img                             1
 236.989498138 = 254.465536000  boot/grub/grub.cfg                             1
 251.279548645 = 269.809360896  boot/initrd.img-2.6.35-28-generic              2
 275.342918396 = 295.647207424  boot/initrd.img-2.6.38-8-generic               2
 275.425216675 = 295.735574528  boot/initrd.img-2.6.38-8-generic-pae           2
 274.854393005 = 295.122657280  boot/vmlinuz-2.6.35-28-generic                 1
 264.120422363 = 283.597144064  boot/vmlinuz-2.6.38-8-generic                  1
 264.186950684 = 283.668578304  boot/vmlinuz-2.6.38-8-generic-pae              1
 275.425216675 = 295.735574528  initrd.img                                     2
 275.342918396 = 295.647207424  initrd.img.old                                 2
 264.186950684 = 283.668578304  vmlinuz                                        1
 264.120422363 = 283.597144064  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  fd 70 8c 92 34 36 7e af  a9 5a 86 8f 99 71 57 2a  |.p..46~..Z...qW*|
00000010  fd a5 5e 80 de e7 6c 39  5f d6 db 6a 33 b7 0d dd  |..^...l9_..j3...|
00000020  72 10 8f be 98 f8 71 0e  08 15 a9 a3 af 1b 7f c7  |r.....q.........|
00000030  96 86 82 c4 91 47 fe 42  35 a2 2d d1 c4 6e 6c 8d  |.....G.B5.-..nl.|
00000040  7e c8 97 55 f3 f8 ff cf  d7 b0 b0 07 57 42 74 3a  |~..U........WBt:|
00000050  ef cc e8 2a a6 6f df 30  5c b8 3f 40 39 bb 54 cb  |...*.o.0\.?@9.T.|
00000060  5c 0b 9d 8f a9 08 2e 13  37 77 d0 bb 3d 46 1b 36  |\.......7w..=F.6|
00000070  ff 4c 75 9e 39 e0 1d ba  82 be 37 86 15 a1 5b aa  |.Lu.9.....7...[.|
00000080  27 34 8b 2e 81 36 1e e5  da 98 ae 1c 5b cb a8 86  |'4...6......[...|
00000090  a4 4d 64 58 61 93 a7 e5  04 e5 0a 3e ba 27 dc 95  |.MdXa......>.'..|
000000a0  83 84 ba 37 50 08 92 e0  45 44 1f ee c7 aa 81 52  |...7P...ED.....R|
000000b0  20 7b 18 e7 ff 87 d3 af  b5 20 57 ce 66 7b 59 60  | {....... W.f{Y`|
000000c0  14 1a e5 82 5b 5c 32 f5  71 3c f7 e0 28 49 5a c0  |....[\2.q<..(IZ.|
000000d0  2d fc ba b2 81 d4 2e 68  de ba c8 ca f2 37 1d a2  |-......h.....7..|
000000e0  14 4d a4 d2 31 89 62 df  3f 3c 21 06 f2 b8 d3 67  |.M..1.b.?<!....g|
000000f0  e3 cf 9f bf 09 23 33 d6  8e 88 9c fd 7c 56 29 6b  |.....#3.....|V)k|
00000100  d5 20 dc e5 f9 32 58 e9  07 00 30 99 a2 33 bb 4a  |. ...2X...0..3.J|
00000110  3e b9 85 3b ef 77 15 63  b5 b4 43 95 37 b5 80 bf  |>..;.w.c..C.7...|
00000120  9e 35 c5 e0 59 67 68 26  56 e3 06 b1 f3 35 bf 40  |.5..Ygh&V....5.@|
00000130  ff 66 43 91 94 7a 16 b0  e7 14 37 f6 c1 63 4b 5f  |.fC..z....7..cK_|
00000140  54 fc 22 39 09 46 f9 8f  a3 d2 a3 bb 26 b3 21 14  |T."9.F......&.!.|
00000150  6a 57 f5 76 3d 65 50 d0  6c d4 d9 f1 54 02 87 be  |jW.v=eP.l...T...|
00000160  4c ec 40 3c d1 af 1d 15  0e 98 7d 38 d9 02 98 19  |L.@<......}8....|
00000170  71 90 46 fb f2 7a 40 1b  f3 54 81 cd 3b 3d f3 32  |q.F..z@..T..;=.2|
00000180  53 21 f7 74 80 25 7e e9  6b 48 1b 65 ca 27 62 5c  |S!.t.%~.kH.e.'b\|
00000190  d3 7f 08 f7 e4 bf 44 b2  dc c6 98 a4 7a b3 af 9d  |......D.....z...|
000001a0  b7 96 8f c5 6a 41 1d b6  d7 a2 47 26 7d 03 bd b5  |....jA....G&}...|
000001b0  e0 97 68 0c af 0f 8d be  dd f0 09 ca f2 70 ba 9f  |..h..........p..|
000001c0  89 b9 6f 82 50 88 06 a5  dd 1e a9 3c 73 54 14 47  |..o.P......<sT.G|
000001d0  a7 fb bb 6c 1b 19 2a c8  f4 64 7a 0f cc 1e 73 6c  |...l..*..dz...sl|
000001e0  d0 9f 94 be a8 77 fc 40  89 64 5d 36 4b 94 7e e1  |.....w.@.d]6K.~.|
000001f0  d7 90 ba 35 9c 9b 51 d4  b3 63 25 95 02 45 d7 0c  |...5..Q..c%..E..|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by SpawnHappyJake on 2011-06-10
I get that error, "Invalid Signature" when I try to boot FreeDOS from GRUBII.
In Linux Mint (which really is Ubuntu), I used qemu-img to make a 300MB hard drive image, then used qemu to install FreeDOS onto that image using the "FreeDOS full cd" iso. Then I mounted that image (had to use offset=32256), and I copied the files to a thumb drive on which I installed GRUBII. I added an entry to chainload KERNEL.SYS, and I get that error when I try to load FreeDOS off the thumb drive from GRUBII. I'd really rather not use up 300 MB of RAM to do a memdisk, and I would like to save stuff and browse my thumb drive from FreeDOS. :(

---


---
title: "Chainloading TrueCrypt with GRUB2"
date: 2009-08-02
forum: General Help
---

### Post by th3voic3 on 2009-08-02
I have my System encrypted according to [this guide]("http://www.steve-oh.com/blog/index.php/2009/03/12/ubuntu-vista-dual-boot-full-encryption-with-truecrypt/")

Now I have switched to GRUB2 and tried to adapt the code to chainload the TrueCrypt bootloader

```
menuentry "Windows Vista" {
       insmod chain
    set root=(hd0,1)
    chainloader (hd0,2)/truecrypt.mbr
}
```

When I choose the Windows Vista entry it loads the TrueCrypt bootloader, but says it is damaged. Could that really be the case or is that because my code is flawed?

---

### Post by z0mb1 on 2009-08-16
I'm having the exact same issue, so any guidance on how to resolve would be great.  I'm "working around" the issue by installing grub2 into the boot partition, and escaping the truecrypt loader, which then boots grub2 menu.  However when installing grub2 it does warn that installing in a partition is not recommended :(

---

### Post by th3voic3 on 2009-10-31
Since 9.10 is out now and grub2 is the standard...well I'm still having the same issue. Does anybody have an idea?

---

### Post by no_angst on 2009-11-01
Nothing to add except "me too".  Just upgraded to 9.10 and would like to get my Truecrypt encrypted Windows partition back.  Not a major problem as I don't boot into it very much any more, and I can still mount it with Truecrypt from within 9.10 for the files if I need them, but it would be nice to have it working again.

---

### Post by M4NIC on 2009-11-02
Unfortunately I have to use Win (at least its 7) and Im a bit annoyed with the fact that clean installations of 9.10 (at least the alternate version) dont bother asking where I want GRUB2 to be installed, and instead go on and rewrite the MBR.

What I wanted to do was install GRUB onto the /boot partition (as generally advised in Ubuntu + truecrypt tutorials) and thus chaiload GRUB through the TrueCrypt loader by pressing ESC. 
GRUB2 now just shows a brief "GRUB loading" message and then just proceeds to load ubuntu. When pressing shift to see the options of the menu windows is not even mentioned, and using the grub-update in the terminal fails to find any other entries other than ubuntu and the memtest.

My plan of action is now to recover the truecrypt loader through the recovery CD I made, and then manually reinstall GRUB2 on to /boot. Luckily Ive got the CD though, as I would be in deep sh*t. 

A matter of future consern maybe? Im sure there will be people not as lucky as me with a damaged truecrypt recovery CD or some similar situation :/

---

### Post by The Cog on 2009-11-02
It looks odd to me that the root is (hd0,1) but you are then trying to chainload (hd0,2). You do realise that grub2 numbers partitions from 1 upwards instead of the 0 upwards that grub1 used? So try using root (hd0,2) or chainload (hd0,1).

Of course, I'm guessing because I've never looked at how truecrypt boots.

---

### Post by iarkin on 2009-11-04
I have
```
menuentry "vista (tc)" {
set root=(hd0,2)
chainloader (hd0,3)/truecrypt.mbr
boot
}
```
and I get the same "truecrypt bootloader is damaged" message. Any help would be greatly appreciated.

<ubuntu9.10rant>
Why on _earth_ do they let out a new version of ubuntu out with a beta-version bootloader and known broken 3G modem support?

The least I expect is that things that worked the previous version still will...
</ubuntu9.10rant>

---

### Post by iarkin on 2009-11-04
In my search for a booting goodness i have stumbled upon
[http://www.keneks.net/blog/2009/05/hide-unhide-makeactive-partitions-with-grub-2-parttool/](http://www.keneks.net/blog/2009/05/hide-unhide-makeactive-partitions-with-grub-2-parttool/)
From link:
```
#make a partition active ("makeactive" in grub legacy)
parttool (hd0,4) boot+
```

Not that it helped me, but it may be a step in the right direction

---

### Post by t0p on 2009-11-04
> **iarkin said:**
> 
<ubuntu9.10rant>
Why on _earth_ do they let out a new version of ubuntu out with a beta-version bootloader and known broken 3G modem support?


Can someone point me in the direction of a full description of this "broken 3G modem support"?  I've only used Karmic in live cd session so far, and my Huawei E160X dongle-modem works fine.  But if there's any likelihood that it may stop working, I don't really want to install Karmic until it's fixed.

So: link, anyone?

---

### Post by iarkin on 2009-11-04
> **t0p said:**
> Can someone point me in the direction of a full description of this "broken 3G modem support"?  I've only used Karmic in live cd session so far, and my Huawei E160X dongle-modem works fine.  But if there's any likelihood that it may stop working, I don't really want to install Karmic until it's fixed.

So: link, anyone?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

But Kernel 2.6.32-rc5 works, so that's what i'm using.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc5/)

---

### Post by no_angst on 2009-11-04
Well, for some reason I also lost the ability to mount my TC partition in Ubuntu, so last night I used the TC boot CD to decrypt Vista.  Not what I wanted, but I guess file or folder level encryption (or a TC container) will have to do for now.

> <ubuntu9.10rant>
Why on _earth_ do they let out a new version of ubuntu out with a beta-version bootloader and known broken 3G modem support?

The least I expect is that things that worked the previous version still will...
</ubuntu9.10rant> 

<BOLD><AT TOP OF LUNGS><!!!!> **[SIZE="3"]AGREE 100%!!![/SIZE]** </!!!!></AT TOP OF LUNGS></BOLD>
](*,)

---

### Post by robpower on 2009-11-06
I add myself to the list of people interested in a solution.
Here's my** grub.cfg **that bring me to a truecrypt error that says the truecrypt bootloader is corrupted.
Note:
(hd0,1) is sda1, Ubuntu /boot partition,
(hd0,3) is sda3, Windows Partition
```
#!/bin/sh
echo “Adding Windows” >&2
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows XP" {
        insmod chain
        set root=(hd0,3)
	parttool (hd0,3) boot+
        chainloader (hd0,1)/truecrypt.mbr
}
```
And here is the **old menu.lst** section of grub-legacy:
Note: partition numbering convention is [grub2] = [grub-legacy]+1, so here
(hd0,0) means sda1, Ubuntu /boot partition,
(hd0,2) means sda3, Windows Partition
```
title Windows Vista/Longhorn
rootnoverify (hd0,2)
makeactive
chainloader (hd0,0)/truecrypt.mbr
boot

```
If anyone knows anything that could helps, we would really appreciate.

---

### Post by plut0 on 2009-11-07
I have the same error, looking for a solution also.

---

### Post by Spliff85555 on 2009-11-15
Same problem here.
Is there a fix / work-around / solution already?

---

### Post by benzinerwin on 2009-11-16
The problem is:

**legacy-****grub** works fine with truecrypt when you install just the tiny loader into the mbr that in turn loads the other loader-stages from the boot partition.

**grub2 **installs into the mbr, embeds the core.img (24KB) starting at sector 1 and thus overwriting parts of the truecrypt loader.

I cannot find a way to make grub2 not persist on embedding the core image. The doc & wiki aren't helping at all.

However, there must be a way - otherwise grub2 is basically worthless.

---

### Post by ranch hand on 2009-11-16
If you read the link in my sig you will learn a little of how grub2 works.  The first 3 links in it are great, in depth treatments on the subject.

The first link, I know, does have some discussion on encrypted drives.  The second one is a live thread by the guy in the best position to help you.

I am pretty useless here as I do not use encryption and therefore don't know much about it.

---

### Post by sq377 on 2009-12-17
For anyone still looking, I think I found a simple solution.

> If the TrueCrypt Boot Loader is frequently damaged (for example, by inappropriately designed activation software) or if you do not want the TrueCrypt boot loader to reside on the hard drive (for example, if you want to use an alternative boot loader/manager for other operating systems), you can boot directly from the TrueCrypt Rescue Disk (as it contains the TrueCrypt boot loader too) without restoring the boot loader to the hard drive. Just insert your Rescue Disk into your CD/DVD drive and then enter your password in the Rescue Disk screen.

[How to make grub2 boot an iso]("http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/")

---

### Post by dpsousa on 2010-06-20
> **sq377 said:**
> For anyone still looking, I think I found a simple solution.



[How to make grub2 boot an iso]("http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/")
I am probably late on this, but since it looks like this problem is still unsolved, the solution you pointed out, does NOT work for the Truecrypt or any other common ISO.

From your link:
*"PLEASE NOTE: grub itself can NOT boot CDROM images/ISOs. Neither version 1 nor version 2 of grub. Grml provides this feature via its isofrom bootoption. Grub2 strongly simplifies this setup with its loopback option but grub alone will NOT be enough. It’s the live system (as for example grml) that has to support this “boot from ISO” feature."*

---

### Post by gyurman on 2010-06-27
Can you solve this?

---

### Post by dino99 on 2010-06-27
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/484102](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/484102)

[http://grub.enbug.org/TrueCrypt](http://grub.enbug.org/TrueCrypt)

[http://ohioloco.ubuntuforums.org/showthread.php?p=8610542](http://ohioloco.ubuntuforums.org/showthread.php?p=8610542) (last post)

---

### Post by danmiddle2 on 2010-08-22
> **sq377 said:**
> For anyone still looking, I think I found a simple solution.



[How to make grub2 boot an iso]("http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/")

I couldn't get that to work, but I have solved this. I installed grub and removed grub2 :-)

---

### Post by nico23 on 2010-10-02
f**k grub2!

if grub 2 is so great with its new features why cant it boot the truecrypt rescue disk iso?

it it not possibe? the is the vmlinuz and squasfs stuff for linux images and i really dont know how to setup grub2 for the truecrypt iso. no solution and someone here saying its not working???

wtf!

where is truecrypt writing its bootloader exactly?

can someone tell me a solution to get beack to grub1 and chainload truecrypt mbr like i did before... i experienced problems with this and i wread grub1 to sda and sda1 maybe because of that.

why did they put in f***ing grub2 in ubuntu now? and wtf are they thinking not even asking for install of grub2 o the live install disk (only alternate install cd asks for grub2 to be installed)

now i see that grub2 can boot isos from harddisk i really like to use it! but i dont want to truecryt boot leader chainload grub2 when i press esc i want to default boot in my linux with grub2!

i wread about a solution for grub1 chainloading grub2 but ubuntu deinstalls grub2 on grub1 package installation. its a mess. the hole concept of boot leaders on harddisks is! it should be taked away from the harddisk and bios should handle bootloaders

---

### Post by double1116 on 2010-10-23
I got this to work by getting grub2 to boot the TrueCrypt rescue ISO. However, the above link isn't exactly what you need.

1. Copy the rescue ISO to /boot
2. sudo apt-get install syslinux
3. sudo cp /usr/lib/syslinux/memdisk /boot
4. Add /etc/grub.d/40_windows_truecrypt:
#!/bin/sh
exec tail -n +3 $0
# Windows with TrueCrypt
menuentry "Microsoft Windows" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    linux16 ($root)/memdisk iso raw
    initrd16 ($root)/truecrypt.iso
}

Step 4 will add the entry whenever updating grub. You'll have to modify some of this to fit your situation. Such as the (hd0,msdos3) partition is your /boot, and the numbers start at 1. 

Hope this helps.

---

### Post by Padreic on 2010-10-30
> **double1116 said:**
> I got this to work by getting grub2 to boot the TrueCrypt rescue ISO. However, the above link isn't exactly what you need.

1. Copy the rescue ISO to /boot
2. sudo apt-get install syslinux
3. sudo cp /usr/lib/syslinux/memdisk /boot
4. Add /etc/grub.d/40_windows_truecrypt:
#!/bin/sh
exec tail -n +3 $0
# Windows with TrueCrypt
menuentry "Microsoft Windows" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    linux16 ($root)/memdisk iso raw
    initrd16 ($root)/truecrypt.iso
}

Step 4 will add the entry whenever updating grub. You'll have to modify some of this to fit your situation. Such as the (hd0,msdos3) partition is your /boot, and the numbers start at 1. 

Hope this helps.

Thank you, but that doesn't work for me. Every time I try booting Truecrypt, grub tells me "you have to boot the kernel first".
Anybody got this to work? If so, what may I be doing wrong?

Thanks in advance

---

### Post by Uborted on 2010-11-14
double1116's instructions worked for me :) overly worded details below. Sorry for spelling it out, but I really hope this will help save somebody the headaches.

I have an 80G hard drive. I installed windows vista on the 1st 50G, then ran TrueCrypt to encrypt it and install the truecrypt bootloader. When crypting, truecrypt spits out an iso image of it's rescue disk, which I saved on a USB stick & CD. I labeled it truecryptDesktop.iso.

I then installed Ubuntu using the Alternate CD. I used the partitioning section to create a 400mb ext3 format partition designated as boot. I used the partitioner to use the remaining space for an encrypted partition. When the encrypted partition showed up, I formatted it as a logical volume. Then I used the logical volume manager to create two partitions in the logical volume: 4gigs formatted as "swap", and the rest formatted as ext3 and designated as the root file system.

When I finished formatting and installing ubuntu, I logged into ubuntu (it had re-written the MBR, so windows was no longer available).

using disk manager, I found out which partition was my 400mb boot partition. My boot partition was the 3rd partition, sda3.

I created a directory in the filesystem directory called MyMount, and mounted sda3 into this folder.

sudo mkdir /MyMount/
sudo mount /dev/sda3 /MyMount/

I then copied the truecryptDesktop.iso recovery image and memdisk to sda3.
(executed from the desktop in terminal, where I saved truecrypt.iso from my USB stick).

sudo cp truecryptDesktop.iso /MyMount/
sudo cp /usr/lib/syslinux/memdisk /MyMount/

I checked that the files were copied correctly by looking in MyMount, then unmounted the volume.

sudo umount /MyMount/

I needed to tell Grub2 that there is another option. I opened up the file 40_custom, where the custom entries are looked for by grub2.

sudo gedit /etc/grub.d/40_custom

This is what it looked like after I edited and saved it:

#!/bin/sh
exec tail -n +3 $0
# Vista TrueCrypt
menuentry "Truecrypted Vista" {
insmod part_msdos
insmod ext3
set root='(hd0,msdos3)'
linux16 ($root)/memdisk iso raw
initrd16 ($root)/truecryptDesktop.iso
}

I said "insmod ext3" because that was the filesystem type of my boot partition. I said (hd0,msdos3) because my boot partition is on sda (hd0) and is partition 3 (msdos3).

I needed to alter the grub defaults so that it would actually show me the boot options, which you can otherwise do by pressing/holding shift at boot time. I figured out how to alter the /etc/default/grub file by reading the Grub2 doc:
[https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29](https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29)

The only thing left to do was to refresh the grub2 system files:

sudo update-grub

When I restarted, "Truecrypted Vista" was a boot option, and when selected displayed the same menu as available on the truecrypt rescue iso CD.

Yes! finally works after trying so many things and wasting so many hours. Thanks double1116!

Here are two other useful pages that helped me figure this all out (they use grub, not grub2, so it was only a starting place):
[http://ubuntuforums.org/showthread.php?t=761530](http://ubuntuforums.org/showthread.php?t=761530)
[http://www.steve-oh.com/blog/index.php/ubuntu-vista-dual-boot-full-encryption-with-truecrypt/](http://www.steve-oh.com/blog/index.php/ubuntu-vista-dual-boot-full-encryption-with-truecrypt/)

---

### Post by Padreic on 2010-11-14
my bad. it works now. i had the wrong partition. had to write msdos2 instead of msdos3…

---

### Post by th3voic3 on 2010-11-15
Ok after reading the long explaination I got it working now, too. Thanks!

---

### Post by MrPotter on 2010-12-14
> **Uborted said:**
> double1116's instructions worked for me :) 

For me too! Thx for the instructions! But there is a little problem with the rescue iso: everytime I select my windows partition the truecrypt bootloader gives me the following error: ```
"it appears you are creating a hidden os. is this correct (y/n)"
``` If I press "no" the regular boot screen appears and I can enter the passphrase. Does anybody know how to disable the message?

---

### Post by dnewton on 2011-01-24
thanks everyone for the instructions on this. i was able to get this working but, like MrPotter, i'm getting the question about creating a hidden os every time i boot win7. has anybody found a way around this?

---

### Post by akandi on 2011-02-05
Hi
I'm trying to set up multi-boot with Windows and Ubuntu on:
dev/sda1 Windows (encrypted)
dev/sda5 Logical partition, ext4 Ubuntu not encrypted, size:100GB (at about 100GB into the drive, if that matters)

I tried:
menuentry "Windows 7" {
    insmod part_msdos
    insmod ext4
    set root='(hd0,msdos1)'
    linux16 (hd0,msdos5)/boot/memdisk iso raw
    initrd16 (hd0,msdos5)/boot/truecrypt.iso
}

memdisk keeps telling me something like: bootstrap too large to load...

by the way, I don't care if it's Grub2 chainloading TrueCrypt bootloader or the other way around, but TrueCrypt doesn't seem to find Grub2 if I install it to /dev/sdb2 or /dev/sdb5...I can't install it on /dev/sdb1 I guess.

---

### Post by auftable on 2011-04-01
> **MrPotter said:**
> For me too! Thx for the instructions! But there is a little problem with the rescue iso: everytime I select my windows partition the truecrypt bootloader gives me the following error: ```
"it appears you are creating a hidden os. is this correct (y/n)"
``` If I press "no" the regular boot screen appears and I can enter the passphrase. Does anybody know how to disable the message?

I don't know, but I reported it as a bug to the truecrypt developers.

---

### Post by derfan on 2011-10-17
Hi ;)

I am following this thread since quite a while and would like to thank you for your explanations. For me it was working nicely, except that I would also see the "hidden OS error".

Since a week I reinstalled my system and I am now using TC 7.1 and Ubuntu 11.10. The TC ISO wont boot anymore, memdisk says "Not enough memory to decompress image (need 0xcaf3c002 bytes)". I am not sure if I did something wrong or if it is indeed the new version of tc and/or grub. I did some further research about this but couldn't find anything. Is anyone else having the same problem?

While researching I found this thread:
[http://www.linuxquestions.org/questions/linux-software-2/dual-booting-with-ubuntu-using-grub-2-and-a-truecrypt-windows-installation-877873/](http://www.linuxquestions.org/questions/linux-software-2/dual-booting-with-ubuntu-using-grub-2-and-a-truecrypt-windows-installation-877873/)
leading to a nice piece of software called grub2tc:
[https://gitorious.org/grub2tc/](https://gitorious.org/grub2tc/)
From the grub2tc README: grub2tc converts the TrueCrypt boot loader into a multiboot kernel that can be loaded from grub2.

Unfortunately this tool didn't work for me either (I still guess its because of the new TC version), but the readme file of the grub2tc project nicely explains the "hidden OS" error along with some other interesting information about the grub and tc mbr.

More from the grub2tc README:
If the TrueCrypt bootloader prints"Error: It appears you are creating a
hidden OS." then some remainders of the TrueCrypt MBR are still sticking
around.  You can either ignore this and reply "n", or you can venture into
hacking your MBR to disable this message:
1. Make sure that it really is a TrueCrypt MBR:
    dd if=$yourhd count=8 bs=1 skip=6
   prints "TrueCryp"
2. Remove the TrueCrypt marker:
    echo 'grub<3tc' | dd of=$yourhd count=8 bs=1 seek=6

Cheers,
Benjamin

---

### Post by rogonow on 2012-02-17
I don't have a separated partition as boot. My solution, after very much searching to get an acceptable boot system:
Unmount Windows (like XP) permanently in Ubuntu.
TrueCrypt Windows partition in Windows + make TrueCrypt repair CD.
Repair GRUB with corresponding Ubuntu live CD (LTS 10.04 in my case)

This will launch Ubuntu always when it boots from the hard drive.
For Windows, I use the TrueCrypt repair CD as boot CD. My Windows partition is hidden although I didn't select to make a hidden one. I launch boot menu to select boot device.

I can mount my Windows in Ubuntu. I can read my Ubuntu in Windows.

I don't know how to make a separated partition for the boot: I don't want to mess up my disk. I still can restore to what it was.

---

### Post by mcbatranu on 2012-11-09
I just succeded to create a similar installation of this multi-boot and there are some tricks I feel I should share here. First, I am using Ubuntu 12.10 and Windows 7 (with Truecrypt 7.1a). 
After going to the steps described very well by Uborted I further discovered that if I use ext4 filesystem then the entry "insmod ext4" from the config will not work as there is no ext4 module in my /boot folder. On the other hand, I found that on grub2 I can use the ext2 module for all ext# filesystems and so it worked with the entry "insmod ext2".
The next problem was that after reaching the Truecrypt bootloader in the boot sequence I had a problem with the "hidden OS" message which I corrected with the instructions from derfan.
The final problem I had was the after all this, my password was not recognized as ok, so I had to enter the repair menu of the Truecrypt Rescue Disk after the iso was mounted by grub and restore the keyfiles to the drive (option 3 I guess).

---


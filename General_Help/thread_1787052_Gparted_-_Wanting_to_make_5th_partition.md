---
title: "Gparted - Wanting to make 5th partition"
date: 2011-06-20
forum: General Help
---

### Post by sammya on 2011-06-20
Hey guys. So basically I am wanting to create a 5th partition from my HDD to install a copy of XP. I currently have Ubuntu 11.04 which is using 2 partitions and ChromeOS which is also using 2. Here is a screen shot:

[IMG]http://i56.tinypic.com/ixxc1x.jpg[/IMG]

So I went ahead and moved some space from sda2 and make ~20gb of unallocated space then tried to make a NTFS partition (for installing XP) until i got an error telling me I have only have 4 partitions and mentioned something about a extended partition...?

I am fairly new at this and have no idea what to do. I have GParted on a Live USB, a copy of XP of a bootable USB and I am ready to install it next to ChromeOS and Ubuntu. How can I make this happen?

Thanks a heap

---

### Post by haqking on 2011-06-20
> **sammya said:**
> Hey guys. So basically I am wanting to create a 5th partition from my HDD to install a copy of XP. I currently have Ubuntu 11.04 which is using 2 partitions and ChromeOS which is also using 2. Here is a screen shot:

[IMG]http://i56.tinypic.com/ixxc1x.jpg[/IMG]

So I went ahead and moved some space from sda2 and make ~20gb of unallocated space then tried to make a NTFS partition (for installing XP) until i got an error telling me I have only have 4 partitions and mentioned something about a extended partition...?

I am fairly new at this and have no idea what to do. I have GParted on a Live USB, a copy of XP of a bootable USB and I am ready to install it next to ChromeOS and Ubuntu. How can I make this happen?

Thanks a heap

You can only have 4 Primary partitions on drive maximum (using MBR more with GPT). Or 3 and a Extended in which you can have as many logical as you like (within reason)

To change what you have im afraid you would have to delete one of the partitions then in the free space then create a extended with however many logicals in it as you like.

see mine for an example

---

### Post by YesWeCan on 2011-06-20
It's all here: [http://www.dedoimedo.com/computers/gparted.html#mozTocId801746](http://www.dedoimedo.com/computers/gparted.html#mozTocId801746)

A MBR partition table can only have 4 partitions. Creating more than 4 requires a trick where a partition is a special type called "extended", to which additional "logical partitions" may be added.

So you have to remove one of your 4 partitions and then create an extended partition, then add logical partitions to it.

[edit] haqking, you beat me to it. :)

---

### Post by haqking on 2011-06-20
> **YesWeCan said:**
> It's all here: [http://www.dedoimedo.com/computers/gparted.html#mozTocId801746](http://www.dedoimedo.com/computers/gparted.html#mozTocId801746)

A MBR partition table can only have 4 partitions. Creating more than 4 requires a trick where a partition is a special type called "extended", to which additional "logical partitions" may be added.

So you have to remove one of your 4 partitions and then create an extended partition, then add logical partitions to it.

[edit] haqking, you beat me to it. :)

Ha ;-) Ive had too much coffee, im multitasking at the speed of a thousand crazed women ;-)

---

### Post by sammya on 2011-06-20
thanks for the replies guys. looks like i am going to remove chromium's partitions so i only have 2 primary partitions. if i do this what will happen with my grub bootup ?

---

### Post by YesWeCan on 2011-06-20
[types quickly while haqking is busy grinding more beans]

Well, I'd be inclined to put XP as the first partition. It will prefer it that way. Linux OS and swap can be on a logical partition. I am not sure whether GParted can move a partition from primary to logical or not, never tried it. That guide should tell you.

---

### Post by haqking on 2011-06-20
> **YesWeCan said:**
> [types quickly while haqking is busy grinding more beans]

Well, I'd be inclined to put XP as the first partition. It will prefer it that way. Linux OS and swap can be on a logical partition. I am not sure whether GParted can move a partition from primary to logical or not, never tried it. That guide should tell you.

I was boiling the kettle ;-)

yep agree with what you said ;-)

oh and im pretty sure Gparted will not allow change of primary to logical or vice versa ;-(

---

### Post by sammya on 2011-06-20
what will happen to the grub menu once i remove both of chromiums primarty partitions leaving me with sda2 and linux swap

---

### Post by haqking on 2011-06-20
> **sammya said:**
> what will happen to the grub menu once i remove both of chromiums primarty partitions leaving me with sda2 and linux swap


mmm well sda2 is your root / and boot so im pretty sure your grub will remain ?

i think ? :confused:

Drink lots of coffee and work into the night, if all else fails back up all data and do a complete rebuild, great way to learn.

No one knows anything unless they have at least spent one night with no sleep and partitions software and some jolt cola ;-)

enjoy

---

### Post by YesWeCan on 2011-06-20
> **sammya said:**
> what will happen to the grub menu once i remove both of chromiums primarty partitions leaving me with sda2 and linux swap
As haqking says, Grub will still work provided Ubuntu is still in sda2. Your Grub menu won't change. If you try to boot Chromium it won't work. To make the Grub menu current you have to run 'sudo grub-update' in Ubuntu and one of the things this causes Grub to do is scan all your disks looking for OSs to put in the boot menu.

You will need to put swap in a different partition so that you can use sda1 for XP. You will need to change the entry in /etc/fstab for the identifier of the swap partition or Ubuntu will complain during boot. While you are moving partitions around you could just comment out the swap entry and then reinstate it once everything is complete and working (Ubuntu doesn't have to have a swap space unless you system has very little RAM. If you have 1GB or more it will work fine for this).

Note that once you have installed XP your Grub will not work at all and you won't be able to boot Ubuntu. So you then need to re-install Grub. If you have a live Ubuntu that is the same version as your HD UBuntu this is pretty easy.
Running the live CD:
[COLOR="Navy"]sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]

Once you have booted back into Ubuntu, run [COLOR="Navy"]sudo update-grub[/COLOR] to add Windows to the menu.

---

### Post by srs5694 on 2011-06-20
You do *not* need to delete partitions! You can use my [FixParts](http://www.rodsbooks.com/fixparts/) program to convert one or more of your existing partitions into logical partitions, which will then enable you to create additional logical partitions and, if you convert at least two, to create another primary partition. There are some important caveats, though:


[list]
[*]The details of what you can convert depend on the current disk layout. It's almost always possible to convert the first partition, and given your description, I suspect it will be possible to convert /dev/sda3, but not both /dev/sda1 and /dev/sda3.
[*]You can change what can be converted by resizing and/or moving partitions. Basically, you need at least one free sector immediately prior to a partition to convert it into a logical partition. Also, a primary cannot exist between two logicals.
[*]I don't know whether Chrome OS requires primaries. If it does, you should leave /dev/sda3 and /dev/sda4 as primaries.
[*]Swap space is easy to delete and re-create, if necessary, even without FixParts.
[/list]


If I were setting it up from scratch, I'd do this:


[list]
[*]Primary for Windows XP
[*]Primary for Chrome OS C-STATE
[*]Primary for Chrome OS C-ROOT
[*]Extended partition, holding

[list]
[*]Logical shared-data partition (FAT or NTFS)
[*]Linux swap
[*]Ubuntu
[/list]

[/list]


Given your current layout, though, I recommend you do this:


[list=1]
[*]Back up anything you can't afford to lose.
[*]If necessary, shrink or delete the swap space (/dev/sda1) so that there's a gap between it and /dev/sda2. (Just one sector is enough of a gap.)
[*]If there's no gap between /dev/sda2 and /dev/sda3, shrink /dev/sda2 so that there is such a gap.
[*]Use FixParts to convert /dev/sda1 and /dev/sda2 to logicals. They'll become /dev/sda5 and /dev/sda6, respectively, and I'll refer to them as such.
[*]Resize /dev/sda6, if necessary, so that there's enough free space in and out of the extended partition for Windows XP and a data-exchange partition.
[*]Resize the extended partition, if necessary, so that there's enough space *outside* of it (between it and the ChromeOS partitions) to hold Windows XP and enough space *inside* it to hold a data-exchange partition.
[*]Create a FAT or NTFS logical data-exchange partition inside the extended partition.
[*]Create a new NTFS primary partition for Windows XP. It will come after the extended partition but before the ChromeOS partitions.
[*]Use sfdisk to back up your partition table. The command "sudo sfdisk -d /dev/sda > sda.txt" does this, storing the data in sda.txt. This file will serve as insurance should something go wrong later. (Windows XP's installer has been known to damage partition tables, for instance, although the layout I've just described shouldn't trigger the bug I know about.)
[/list]


The resulting layout will be a bit weird, since your extended partition (and therefore the logical partitions it contains) comes before the primary partitions. Although this is unusual, it's legal. If you preferred, you could juggle things around so that the primaries, or at least the Windows XP primary, came first; but this would involve moving the start point of your Linux partition, and that type of operation is both time-consuming and risky. IMHO, you're better off doing it the strange way.

You may need to re-install GRUB -- but that would be true after you're done installing Windows, anyhow.

---

### Post by haqking on 2011-06-20
> **srs5694 said:**
> You do *not* need to delete partitions! You can use my [FixParts]("http://www.rodsbooks.com/fixparts/") program to convert one or more of your existing partitions into logical partitions, which will then enable you to create additional logical partitions and, if you convert at least two, to create another primary partition. There are some important caveats, though:


[LIST]
[*]The details of what you can convert depend on the current disk layout. It's almost always possible to convert the first partition, and given your description, I suspect it will be possible to convert /dev/sda3, but not both /dev/sda1 and /dev/sda3.
[*]You can change what can be converted by resizing and/or moving partitions. Basically, you need at least one free sector immediately prior to a partition to convert it into a logical partition. Also, a primary cannot exist between two logicals.
[*]I don't know whether Chrome OS requires primaries. If it does, you should leave /dev/sda3 and /dev/sda4 as primaries.
[*]Swap space is easy to delete and re-create, if necessary, even without FixParts.
[/LIST]


If I were setting it up from scratch, I'd do this:


[LIST]
[*]Primary for Windows XP
[*]Primary for Chrome OS C-STATE
[*]Primary for Chrome OS C-ROOT
[*]Extended partition, holding
[LIST]
[*]Logical shared-data partition (FAT or NTFS)
[*]Linux swap
[*]Ubuntu
[/LIST]
 
[/LIST]


Given your current layout, though, I recommend you do this:


[LIST=1]
[*]Back up anything you can't afford to lose.
[*]If necessary, shrink or delete the swap space (/dev/sda1) so that there's a gap between it and /dev/sda2. (Just one sector is enough of a gap.)
[*]If there's no gap between /dev/sda2 and /dev/sda3, shrink /dev/sda2 so that there is such a gap.
[*]Use FixParts to convert /dev/sda1 and /dev/sda2 to logicals. They'll become /dev/sda5 and /dev/sda6, respectively, and I'll refer to them as such.
[*]Resize /dev/sda6, if necessary, so that there's enough free space in and out of the extended partition for Windows XP and a data-exchange partition.
[*]Resize the extended partition, if necessary, so that there's enough space *outside* of it (between it and the ChromeOS partitions) to hold Windows XP and enough space *inside* it to hold a data-exchange partition.
[*]Create a FAT or NTFS logical data-exchange partition inside the extended partition.
[*]Create a new NTFS primary partition for Windows XP. It will come after the extended partition but before the ChromeOS partitions.
[*]Use sfdisk to back up your partition table. The command "sudo sfdisk -d /dev/sda > sda.txt" does this, storing the data in sda.txt. This file will serve as insurance should something go wrong later. (Windows XP's installer has been known to damage partition tables, for instance, although the layout I've just described shouldn't trigger the bug I know about.)
[/LIST]


The resulting layout will be a bit weird, since your extended partition (and therefore the logical partitions it contains) comes before the primary partitions. Although this is unusual, it's legal. If you preferred, you could juggle things around so that the primaries, or at least the Windows XP primary, came first; but this would involve moving the start point of your Linux partition, and that type of operation is both time-consuming and risky. IMHO, you're better off doing it the strange way.

You may need to re-install GRUB -- but that would be true after you're done installing Windows, anyhow.


nice post, interesting, i had never heard of FixParts before.....looks very useful indeed.

not my issue but cheers.

---

### Post by YesWeCan on 2011-06-20
FYI I was just playing with GParted. Although it won't allow me to move a primary partition into an extended partition, it will allow me to copy and paste one. Which is slick.

---

### Post by haqking on 2011-06-20
> **YesWeCan said:**
> FYI I was just playing with GParted. Although it won't allow me to move a primary partition into an extended partition, it will allow me to copy and paste one. Which is slick.


cool, nice info ;-)

---

### Post by srs5694 on 2011-06-20
> **YesWeCan said:**
> FYI I was just playing with GParted. Although it won't allow me to move a primary partition into an extended partition, it will allow me to copy and paste one. Which is slick.

That's a copy operation, though; it requires that the extended partition already exist, and it copies all the data. That's certainly a useful operation sometimes, but it's not the most efficient way to deal with the OP's issues.

---


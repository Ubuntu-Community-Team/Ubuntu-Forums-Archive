---
title: "Need help - Windows does not boot.."
date: 2009-07-11
forum: General Help
---

### Post by Luciifer on 2009-07-11
Well, here's the story.

I have Windows XP Home Edition installed. I was tired of it and decided to try Ubuntu (done before, worked fine). So my XP was installed on drive D and I also had nothing on drive C (about 12GB). So I installed Ubuntu on it and everything worked fine. 
Then this Update Manager pops-up and tell me to download the updates. So I click the update button but I get this message saying I haven't got enough space. About 330mb.
I went back to Windows (it worked fine back then) and got partition Magic 8.0 or something. I added about 150mb to the C drive and I think that's when everything went wrong.. I thought it was fine and it asked me to reboot the PC so I did. As soon as it started I got this GRUB 17 error.. I googled it with my Ubuntu Live CD and didn't find any solution. So I used my Recovery CD to delete the C drive from my computer (desperate)..
And that didn't help a thing.. Windows wouldn't boot now.. I tried bootfix and such.. 
If I try to boot it now it says 'insert proper boot device...' but if I point it to my harddrive ( F8 ) I just get a linking underscore in the left under corner.. 

I really don't know what to do now.. I'm on my Live CD now and I can access my Windows folders etc. I don't want to lose anyting.. 

Is it possible to access boot.ini trough Ubunutu? 

Here's the GParted:
[[IMG]http://h.imagehost.org/0855/wdsa.png[/IMG]]("http://h.imagehost.org/view/0855/wdsa")

---

### Post by howefield on 2009-07-11
Using GParted, delete the logical partitions you have there and then create a primary ntfs drive using the whole disk. Then run your recovery disk again.

---

### Post by carml on 2009-07-11
If I recall correct,Windows need to be installed into a primary partition,not a extended one.If I were you I would look for a valid cd or iso of XP and try to boot and format all the partition from there.

---

### Post by Luciifer on 2009-07-11
> **howefield said:**
> Using GParted, delete the logical partitions you have there and then create a primary ntfs drive using the whole disk. Then run your recovery disk again.

Sorry but I'm a complete nooby in this. Please explain me a bit 'wider'.
Which is the 'logical partitions'? The first and last one? If so, I can only click on 'new' when I right click on them..

> **carml said:**
> If I recall correct,Windows need to be installed into a primary partition,not a extended one.If I were you I would look for a valid cd or iso of XP and try to boot and format all the partition from there.

Thanks for the idea. I'll try that if Howefield's idea doesn't work.

---

### Post by elliotn on 2009-07-11
U must use gparted in live cd. Boot in a liveCd then go to terminal and type sudo gparted

---

### Post by carml on 2009-07-11
Hoewfiels is suggesting my same idea: boot with the Livecd of Ubuntu if you have one and go to System->Aministration->Partition Editor,then delete all the existing partitiuons and once you've done use the recovery cd of Windows Xp.
If you need more explanations just ask and someone will answer you :)

---

### Post by howefield on 2009-07-11
> **elliotn said:**
> U must use gparted in live cd. Boot in a liveCd then go to terminal and type sudo gparted

Loading GParted from the live cd is all the OP will need, no reason to use terminal and sudo.

---

### Post by Luciifer on 2009-07-11
> **carml said:**
> Hoewfiels is suggesting my same idea: boot with the Livecd of Ubuntu if you have one and go to System->Aministration->Partition Editor,then delete all the existing partitiuons and once you've done use the recovery cd of Windows Xp.
If you need more explanations just ask and someone will answer you :)

I am on my Live CD.

You mean I should delete the /dev/sda5? Won't I lose all my files?

---

### Post by elliotn on 2009-07-11
Other thing get a Xp cd and try to c if it will get a ms windows xp partition, if it does try repairing it then restore grub, then add xp to menu.lst

---

### Post by howefield on 2009-07-11
> **Luciifer said:**
> Which is the 'logical partitions'? The first and last one?.

With the live cd booted and GParted loaded, click on sda5 and delete, then highlight sda1 and delete, then apply.

You should now be ready to create a primary ntfs drive using the whole disk, (you don't have to use all the disk, you can leave space for another partition to use as a data partition, or to dual boot, whatever, but make sure you ntfs partition is at the start of your drive, ie no blank space before it.

---

### Post by elliotn on 2009-07-11
> **Luciifer said:**
> I am on my Live CD.

You mean I should delete the /dev/sda5? Won't I lose all my files?

Deleting it! U will lose all data, rather resize the partition

---

### Post by carml on 2009-07-11
Yes you'll loose all files if you don't have any backup.Before you delete that partition you can try to mount your Windows partition and copy all important files,then proceed as suggested before.I think you should use a pendrive to copy your files,because you can't make use of the Cd drive at the moment.

---

### Post by Luciifer on 2009-07-11
> **carml said:**
> Yes you'll loose all files if you don't have any backup.Before you delete that partition you can try to mount your Windows partition and copy all important files,then proceed as suggested before.I think you should use a pendrive to copy your files,because you can't make use of the Cd drive at the moment.

Awhh..

---

### Post by howefield on 2009-07-11
> **elliotn said:**
> Other thing get a Xp cd and try to c if it will get a ms windows xp partition, if it does try repairing it then restore grub, then add xp to menu.lst

What's this, how to wreck your weekend in one easy step ? ;)

Where does grub and adding xp to menu.1st come into this ?

Unless I have misread, the OP wants to get XP back on his machine and working.

---

### Post by Luciifer on 2009-07-11
> **carml said:**
> Yes you'll loose all files if you don't have any backup.Before you delete that partition you can try to mount your Windows partition and copy all important files,then proceed as suggested before.I think you should use a pendrive to copy your files,because you can't make use of the Cd drive at the moment.

If I rightclick on it, the mount option is not high-lighted, it says unmount.

So I should download Pendrive..? I really really don't want to lose my files.
Especially the firefox bookmarks and such..

---

### Post by Luciifer on 2009-07-11
> **howefield said:**
> What's this, how to wreck your weekend in one easy step ? ;)

Where does grub and adding xp to menu.1st come into this ?

Unless I have misread, the OP wants to get XP back on his machine and working.

The 'OP'?

-Sorry for double post.

---

### Post by howefield on 2009-07-11
> **Luciifer said:**
> The 'OP'?

Original Poster.

---

### Post by carml on 2009-07-11
> **Luciifer said:**
> 
So I should download Pendrive..? 
I mean a flash drive also kwnown as Usb drive,not a software :)

---

### Post by Luciifer on 2009-07-11
> **howefield said:**
> Original Poster.

Oh k.

So I just googled Pendrive and found out what it is. 
So what to do when I got the Pendrive? Boot etc. Then go to my Windows files and copy to my CD (another one)? 

Also, anyone knows how to get to my XP firefox bookmarks without import trough Windows..? :|

---

### Post by carml on 2009-07-11
Yes you can also use your second hard drive,just mount it before you erase the damaged partitions.

---

### Post by howefield on 2009-07-11
> **Luciifer said:**
> If I rightclick on it, the mount option is not high-lighted, it says unmount.

Close GParted and from the Places menu, do you see your disk ?

Click on it, and it should give you an icon on the desktop for your hard drive, from which you can get at your files for copying over to a pen drive.

PS. Once you are sorted, xmarks is a great firefox addon which stores a copy of your bookmarks online and dropbox is worth looking at for online file storage, 2 gig free. Nice way of backing them up.

---

### Post by Luciifer on 2009-07-11
> **howefield said:**
> Close GParted and from the Places menu, do you see your disk ?

Click on it, and it should give you an icon on the desktop for your hard drive, from which you can get at your files for copying over to a pen drive.

PS. Once you are sorted, xmarks is a great firefox addon which stores a copy of your bookmarks online and dropbox is worth looking at for online file storage, 2 gig free. Nice way of backing them up.

Yep, I got the disk. 

But I didn't backup my bookmarks.. Means I can't get to them now..?

---

### Post by carml on 2009-07-11
Maybe yes. :(

---

### Post by Luciifer on 2009-07-11
I found some bookmarks. 

Guys, thanks a lot for the help. Really appreciate it!

But can I use a DVD-RW 4.7GB to store the files etc.?

---

### Post by howefield on 2009-07-11
> **Luciifer said:**
> I found some bookmarks. 

Guys, thanks a lot for the help. Really appreciate it!

But can I use a DVD-RW 4.7GB to store the files etc.?

Probably not if you are using the optical drive for the Live CD, unless this is a second optical drive you are talking about ?

Can you email them to yourself ?

---

### Post by Luciifer on 2009-07-11
> **howefield said:**
> Probably not if you are using the optical drive for the Live CD, unless this is a second optical drive you are talking about ?

Can you email them to yourself ?

Erm.. Well, I have 2 drives. 

In one of them, there's the Live CD. Nothing in the other one.
Not sure if they're both optical.. How can I find out?

What do you mean, email them to myself? Bookmarks only?
I just put my USB stick and placed them on it.

---

### Post by carml on 2009-07-11
> **Luciifer said:**
> Erm.. Well, I have 2 drives. 

In one of them, there's the Live CD. Nothing in the other one.
Not sure if they're both optical.. How can I find out?

What do you mean, email them to myself? Bookmarks only?
I just put my USB stick and placed them on it.

Go to Applications->Accessories->Terminal and type ```
lspci -v
``` then post here the result.

---

### Post by Luciifer on 2009-07-11
> **carml said:**
> Go to Applications->Accessories->Terminal and type ```
lspci -v
``` then post here the result.

There: 

> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8157
    Flags: bus master, fast devsel, latency 0
    Memory at dc000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
    Flags: bus master, 66MHz, fast devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fa000000-fbefffff
    Prefetchable memory behind bridge: e0000000-f8ffffff
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at b800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at c000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at c400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at c800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f9fffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fbf00000-fbffffff
    Prefetchable memory behind bridge: 30000000-300fffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at fc00 [size=16]
    Memory at 30100000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8227
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at b400 [size=256]
    I/O ports at b000 [size=64]
    Memory at f9fff800 (32-bit, non-prefetchable) [size=512]
    Memory at f9fff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:00.0 VGA compatible controller: nVidia Corporation NV36.4 [GeForce FX 5700VE] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 9573
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Expansion ROM at fbee0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: nvidiafb

02:0a.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
    Subsystem: Creatix Polymedia GmbH Device 0003
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at fbfffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

02:0d.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
    Subsystem: ASUSTeK Computer Inc. Device 811a
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 23
    Memory at fbff8000 (32-bit, non-prefetchable) [size=16K]
    I/O ports at e800 [size=256]
    Expansion ROM at 30000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: skge
    Kernel modules: skge


---

### Post by carml on 2009-07-11
Ok you have only one optical drive also kwnown as Dvd drive.The last'poster suggestion was to understan if you got all your bookmarks (it was quite 10 posts ago),you can't use a cd or dvd when using a Live cd if you have got only a optical drive.

---

### Post by Luciifer on 2009-07-11
> **carml said:**
> Ok you have only one optical drive also kwnown as Dvd drive.The last'poster suggestion was to understan if you got all your bookmarks (it was quite 10 posts ago),you can't use a cd or dvd when using a Live cd if you have got only a optical drive.

Meaning I should 'make' the pendrive?
& I guess I can only use Ubuntu 8.10 [http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/) since I'm on a live cd?

---

### Post by carml on 2009-07-11
No you can copy your file to yuor pendrive or to an other hard drive,there's no need to make a bootable pendrive.That would be used for other purposes.

---

### Post by Luciifer on 2009-07-11
> **carml said:**
> No you can copy your file to yuor pendrive or to an other hard drive,there's no need to make a bootable pendrive.That would be used for other purposes.

Alright but I don't have enough space - it's just one of 1GB and another one of 2GB..
I need more. Lol.
Can I try using a DVD-RW? Or will it mess up?

---

### Post by carml on 2009-07-11
No you can't until you're using the Live cd,if you can't backup all of your data,get an other pendrive or delete unnecessar files or try to send to a friend via email the 1 Gb of data you can't save.

---

### Post by Luciifer on 2009-07-11
> **carml said:**
> No you can't until you're using the Live cd,if you can't backup all of your data,get an other pendrive or delete unnecessar files or try to send to a friend via email the 1 Gb of data you can't save.

Ok.. I'll try to upload some to my website too..

Thanks a lot!! :)

---


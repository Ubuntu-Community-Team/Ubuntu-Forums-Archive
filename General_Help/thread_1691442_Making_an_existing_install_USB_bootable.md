---
title: "Making an existing install USB bootable?"
date: 2011-02-19
forum: General Help
---

### Post by foogoo on 2011-02-19
Hi all,

I've searched extensively on Google and here and can't seem to find anything addressing what I'm trying to do.

The motherboard of my notebook (Ubuntu 9.10) completely died earlier this week. I pulled the hard drive and got an external case for it. Is it possible to have it boot into my original Ubuntu via USB?

Trying to do so as-is comes up with multiple Grub errors (Invalid Environment block, file not found, etc.) and I've tried addressing these Grub errors separately with no luck, but I have a feeling I'm skipping a basic step somewhere to make a primary drive USB bootable without reformatting.

Any help? Thanks.

---

### Post by Hakunka-Matata on 2011-02-19
What is your hardware setup?  Are you trying to use the drive you removed from your notebook on a regular PC?

---

### Post by foogoo on 2011-02-19
> **Hakunka-Matata said:**
> What is your hardware setup?  Are you trying to use the drive you removed from your notebook on a regular PC?

Thanks for the response. The drive was removed from a Dell inspiron (not sure the exact model) and now it's in an external SATA enclosure. I have it plugged into my Asus netbook though my goal is to make it USB bootable on any machine, if possible. The files are accessable from the ubuntu on the netbook, just not bootable.

---

### Post by Hakunka-Matata on 2011-02-19
> Is it possible to have it boot into my original Ubuntu via USB?

Please explain your setup

---

### Post by Hakunka-Matata on 2011-02-19
so the hard drive is in a SATA enclosure pluged into a Asus Netbook.  What is the interface type from that SATA enclosure to the Asus Netbook?  I'm guessing it has a USB interface to a USB port on your Netbook?

---

### Post by Hakunka-Matata on 2011-02-19
You've been a member since Aug-2008, so I'm guessing you know your way around Ubuntu pretty well.  Can you boot from that drive in the external SATA enclosure?, does it show up in BIOS?  Running a system off USB is clunky in my experience, I have a Acer Aspire One Netbook that I boot with a USB installed Ubuntu-10.10 system.  It is SLOW, but I installed to the USB using a second USB Live CD plugged into the same computer.  It works but it's not really practical for me, too slow.

Your should be able to copy via the 'dd' command the entire contents of your SATA enclosure drive onto a USB if the USB is large enough, no?

---

### Post by YesWeCan on 2011-02-19
> **foogoo said:**
> Hi all,

I've searched extensively on Google and here and can't seem to find anything addressing what I'm trying to do.

The motherboard of my notebook (Ubuntu 9.10) completely died earlier this week. I pulled the hard drive and got an external case for it. Is it possible to have it boot into my original Ubuntu via USB?

Trying to do so as-is comes up with multiple Grub errors (Invalid Environment block, file not found, etc.) and I've tried addressing these Grub errors separately with no luck, but I have a feeling I'm skipping a basic step somewhere to make a primary drive USB bootable without reformatting.

Any help? Thanks.

So you have an internal HD installation now running off USB. Grub is confused because it is still looking for the /boot files on an internal drive. As a minimum you probably need to chroot into the drive and run update-grub and grub-install.

---

### Post by foogoo on 2011-02-19
> **YesWeCan said:**
> So you have an internal HD installation now running off USB. Grub is confused because it is still looking for the /boot files on an internal drive. As a minimum you probably need to chroot into the drive and run update-grub and grub-install.

Thanks again for the responses.

Yes, the drive from the defunct Dell notebook is now in a SATA-USB enclosure plugged into my Asus. I don't plan on running it off USB permanently, I'd like to log into my original configuration to tie up some loose ends and make notes on what needs to be copied/configured on my new setup since the notebook literally died without warning.

It shows up on the bios and mounts fine, it's just not booting. From the responses it sounds like a grub issue? I updated Grub but it ended up updating the Grub on my netbook drive :rolleyes:. Looks like I forgot about chroot, I will try that now.

---

### Post by YesWeCan on 2011-02-19
There may be an easier way. From a live cd you can do something like 

grub-install --root-directory=/dev/usb/... /dev/usb

Substitute the real paths. This should install grub to the usb mbr with refrences to the root partition on the usb.

---

### Post by YesWeCan on 2011-02-19
I am sure there is a Grub problem here. The thing is that Grub is not relative, as it were. It doesn't default to using the /boot files of the nearest Ubuntu partition. Instead, when you first installed it grub latched on to the device name of the internal disk. But now the device name has changed. So it should be just a matter of reinstalling grub with a new reference for /boot.
When you get it to boot, do the update-grub for good measure.
If the simle method doesn't work you will have to do the chroot method.

---

### Post by Hakunka-Matata on 2011-02-19
> Yes, the drive from the defunct Dell notebook is now in a SATA-USB enclosure plugged into my Asus.

You can't simply set that drive as the First Boot drive in BIOS?

---

### Post by YesWeCan on 2011-02-19
> **Hakunka-Matata said:**
> You can't simply set that drive as the First Boot drive in BIOS?
If it was Windows that might work. The trouble is that Grub is quite versatile and it can boot an OS that isn't on the same drive. So it has to use an absolute address method. When the internal drive was transformed into an exteral USB drive its bios reference changed. I think this is why it complains of missing files; Grub still thinks it is on an internal drive.

It may also be the case that the /boot/grub files wont work due to incorrect references too. If so an update- grub has to be done before the grub-install. This can only be done from the booted Ubntu or by chroot.

---

### Post by foogoo on 2011-02-20
Ok, I've been messing with it all night and I'm trying not to screw it up more, so I tried Method 3 from here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

When I reboot from the external, I get:
"invalid arch independent ELF magic" and I get the grub rescue prompt.

Then I noticed that my netbook grub menu actually contains the entries for the external, likely somehow from update-grub (even though it was ran while chroot'ed onto the external :confused:). But when I select the appropriate entry to get the external to boot, I get:
"you need to load the kernal first".

Any idea what's going on?

---

### Post by YesWeCan on 2011-02-20
The Grub thing is sort of simple in principle but in practice it it can be very fiddly and easily tie one up in knots.
Forum member **Herman** has excellent info all about Grub. He advocates SuperGrubDisk as a very good tool to make things boot:  [http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)
I have never used it but it is worth looking into. Herman's site is very good and covers lots of aspects of booting and he would definitely know how to resolve this problem.

---

### Post by kiyop on 2011-02-20
If Super GRUB2 disk cannot solve the problem, read the following.

Set BIOS configuration, make the internal HDD is first in boot order.

Without connecting the USB-HDD, boot Ubuntu installed in the internal HDD.
After the Ubuntu booted correctly, connect the USB-HDD and confirm the partition of ubuntu in the USB-HDD can be mounted.

In terminal, execute
$ sudo update-grub

Restart and press Shift key during boot to make the grub2 menu displayed.

Select the entry concerning the USB-HDD ubuntu.

If the above fails, the incorporation of correct module to initramfs may solve the problem.

1) $ lsmod
to make sure which modules are necessary to access the USB-HDD.

2) chroot to the partition of Ubuntu in the USB-HDD

3) add the modules' names in [FONT=Arial]/*etc*/*initramfs*-*tools*/*modules*[/FONT]

4) # mkinitramfs -o initrd.img-2

5) exit from chroot.

6) copy generated initrd.img-2 and the correct kernel(/boot/vmlinuz-...) in the partition of Ubuntu in the USB-HDD, to the partition in the internal partition.

7) set up grub2 menuentry correctly. For example, add
/etc/grub.d/40_custom
the following:
```
menuentry "Ubuntu in USB-HDD" {
insmod ext2
search --file --set /initrd.img-2
linux /vmlinuz-[COLOR=red][copied from the USB HDD][/COLOR] root=UUID=[COLOR=red][UUID of the Ubuntu root partition in USB-HDD][/COLOR] ro
initrd /initrd.img-2
```

8 ) $ sudo update-grub

9) restart and select "Ubuntu in USB-HDD" in GRUB2 menu.

---

### Post by oldfred on 2011-02-20
See this bug as it applies to Karmic and that version of grub2. Several workarounds posted. USB live version fix: Post #50

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784)

---


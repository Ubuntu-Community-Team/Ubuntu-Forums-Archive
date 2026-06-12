---
title: "Messed up my kernel"
date: 2006-04-15
forum: General Help
---

### Post by vavoem on 2006-04-15
Hi there

I messed up my kernel.

Yep i know i'm stupid.

I was fooling around with adept and managed to screw up my entire kde
I apt-get install -reinstall kubuntu-desktop and fixed that

however when i rebooted i got the following message

VFS: Cannot open root device "hda1" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel Panic - not syncing: VFS: Unable to mount root fs on unkown-block(0,0)

I booted from the live-cd and ran the following commands.

sudo mount /dev/hda1 /mnt/linux
sudo chroot /mnt/linux /bin/bash
apt-get update
apt-get install --reinstall linux-image-2.6.12-9-386

but i keep on getting the same problems


please it's not only my kernel that is panicking anymore!

---

### Post by PriceChild on 2006-04-15
I think that's nothing to do with your kernel, just your grub!

Doing those commands from the live cd won't change the linux on your root, just the pretend one being run in your ram.

Post your /boot/grub/menu.lst and lemme take a look :)

---

### Post by vavoem on 2006-04-15
As i have no means of copy pasting them to you 
i'll send you the menu option wich goes wrong


Title          kernel 2.6.12-10-686
root          (hd0,0)
kernel        /boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro
initrd         /boot/initrd.img-2.6.12-10-686
savedefault
boot

There's one under it wich is the same except for single behind 3rd line

---

### Post by PriceChild on 2006-04-15
I "think" that you should be able to reinstall the grub to sort out booting into the kernel:

>   Default  GNOME - HOWTO: Restore GRUB (if your MBR is messed up)
Written by vnbuddy2002

Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.

After this, you should at least be able to get into a terminal.

---

### Post by vavoem on 2006-04-15
Thats it i had it.
I'm just going to reinstall the entire system
I wasn't to happy with some things anyway and  wanted them setup differently anyway.](*,)

---

### Post by syg00 on 2006-04-15
[QUOTE=vavoem]
VFS: Cannot open root device "hda1" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel Panic - not syncing: VFS: Unable to mount root fs on unkown-block(0,0)
[/quote]This generally means that either the driver for the controller chip for the boot device (say SATA) isn't available, or the filesystem isn't.
Grub has basically done its job by this stage of boot.
> I booted from the live-cd and ran the following commands.

sudo mount /dev/hda1 /mnt/linux
sudo chroot /mnt/linux /bin/bash
apt-get update
apt-get install --reinstall linux-image-2.6.12-9-386Sounds sane to me, although I have yet to get my head fully around apt-get. Does that get the initrd as well  ???.

Edit: guess I shouldn't take so long to respond ... ;)

---

### Post by vavoem on 2006-04-15
I managed to screw up the whole packaging system and dslected a whole bunch of packages wich should not have been dselected 
the adept program is way to tricky i'm never gonna use it again.

I managed, with the boot cd, and chroot to get into my filesystem and i ran the command mkinitrd - o /boot/initrd.img-2.6.12-9-386 
after that i was able to boot my system

however
sound didint work
network didnt work
video was only 640*480

and a whole bunch of programs wouldn't start 

I'm starting over 
Learning from this cruel experience and set up my system is it should.

I made some errors in the beginning and will not make them this time.
However i don't think the misses is going to be too happy i'll be all night in front of the computer again.:rolleyes:

---


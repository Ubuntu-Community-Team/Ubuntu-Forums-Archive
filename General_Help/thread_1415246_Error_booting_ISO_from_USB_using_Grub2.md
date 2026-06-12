---
title: "Error booting ISO from USB using Grub2"
date: 2010-02-24
forum: General Help
---

### Post by mac9416 on 2010-02-24
Hello,

I am trying to set up a USB drive to boot multiple ISOs using Grub2. So far I have installed Grub2 to my flash drive and dropped lucid-desktop-i386.iso into the boot/isos directory.

Here is what my grub.cfg looks like:

> menuentry "Ubuntu Live Lucid 32bit" {
loopback loop /boot/isos/lucid-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/isos/lucid-desktop-i386.iso noeject noprompt --
initrd (loop)/casper/initrd.lz
}

When I attempt to run that, I get "error: You need to load the kernel first." To me, that sounds like "Hey, dummy, you've made some very simple mistake in the grub.cfg and you need to ask some folks who know what they're doing."

Any suggestions? Thanks in advance!

---

### Post by stlsaint on 2010-02-24
did you extract the iso instead of just copy/pasting the iso?

---

### Post by mac9416 on 2010-02-24
Nosir, I just copied/pasted. I thought I could boot from a plain ISO. If so, am I barking up the wrong tree with that config? If not, is that the correct config to use if I extract the ISO?

---

### Post by terabyte1 on 2010-02-24
Is it just me or is Ubuntu getting a lot better? I've not had a bug for months - really! Its working really well on 9.10, no problems with grub2 or Office or anything. The journaling is working like hot cow manure:P and the code is soid and working fine. Can't say the same for kubuntu though - its still shaky and has problems if I touch the bottom bar it starts to fall apart (the desktop). Why I'm on Ubuntu now Kubuntu.


Terabyte1 :guitar:

---

### Post by mac9416 on 2010-02-24
OK, I decided to try and boot this from the grub command line. Here's what I got:

```
> insmod loopback
> insmod ntfs
> loopback loop /boot/isos/lucid-desktop-i386.iso
> linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/isos/lucid-desktop-i386.iso quiet splash noprompt --
> initrd (loop)/casper/initrd.lz
Device loop: Unknown filesystem
```

OK, so Lucid is a no-go. Maybe a bad ISO?

```
> loopback loop /boot/isos/LinuxMint-8.iso
> linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/isos/LinuxMint-8.iso quiet splash noprompt --
error: invalid magic number
```

Does it take magic numbers to make this happen?!  ;)

Maybe that'll help someone debug this. It's Greek to me.

---

### Post by stlsaint on 2010-02-25
yea i am trying the same thing via grub with menu.lst on usb drive...im stuck also at the config file!!

---

### Post by nikhilbhardwaj on 2010-02-25
i can tell you that it does work
that's how i've installed mint on this machine
and it works with lucid too 
i've tried that

my suggestion would be
go into the grub2 console
by pressing c at the splash screen

and then type the commands manually
```

insmod ntfs
set root=(hd0,1)
loopback loop /boot/isos/lucid-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/isos/lucid-desktop-i386.iso noeject noprompt --
initrd (loop)/casper/initrd.lz
boot

```
this way you can also use the autocomplete feature too
and don't forget to change the root=(hd0,1) according to your configuration
replace insmod ntfs with its equivalent for an ext4 partition if you have that

this will however not work with legacy grub.

---

### Post by mac9416 on 2010-02-25
Thanks for the reply, nikhilbhardwaj,

Even with 'set root=(hd0,1)', I continue to get the same errors that I had before.


I found [this howto]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/") that tells how to make a multiboot iso flash drive, but it requires a Windows app to set things up. I want to avoid using Windows if possible.

---

### Post by mac9416 on 2010-02-25
Perhaps it would help to mention that after I mount the ISO as a loopback device 'ls (loop)' returns "Device loop: Unknown filesystem." So it seams that the ISO is never being mounted.

---

### Post by mac9416 on 2010-02-25
Problem solved.

Apparently Grub2 doesn't like to boot ISOs from NTFS flash drives. After reformatting the flash drive to FAT32 and setting Grub back up, I managed to get the boot process of one of the ISOs started.

However, the boot process halted and I was dropped to an '(initramfs)' prompt. Looking back at the boot output, I saw that it was complaining about my Windows XP partition not being mountable because XP was hibernated. It also provided a command to remove the hibernation file. After executing that and rebooting, my ISOs booted beautifully.

Here is my grub.cfg for anyone interested:

```
menuentry "Ubuntu Live Lucid 32bit" {
    set isofile=/boot/isos/lucid-desktop-i386.iso

    loopback loop $isofile
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt --
    initrd (loop)/casper/initrd.lz
}
menuentry "Mint Linux 8 32bit" {
    set isofile=/boot/isos/LinuxMint-8.iso

    loopback loop $isofile
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt --
    initrd (loop)/casper/initrd.lz
}
```

Thank y'all for your help!

---


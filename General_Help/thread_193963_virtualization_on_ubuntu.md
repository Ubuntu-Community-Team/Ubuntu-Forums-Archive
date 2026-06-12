---
title: "virtualization on ubuntu?"
date: 2006-06-10
forum: General Help
---

### Post by E1000 on 2006-06-10
I am wondering if there are any modearately easy ways to implement virtualization in ubuntu?
I had been looking into QEMU but for some reason I cant get that to work (even when i apt-get it, qemu throws errors at me when i try to start it). Xen is a possiblity but it requires a custom kernel, and I cant get it to boot properly with the Ubuntu initrd. OpenVZ looks good too but the install is complicated and I havent even tried it yet.

anyways, I was wondering if there are any handy guides out there for virtualization on ubuntu? Id like to avoid VMware being that its mucho expensive for a poor student like myself.

---

### Post by henrikwidth on 2006-06-10
VMware-server beta doesnt cost anything, and works just fine for me :)

---

### Post by E1000 on 2006-06-10
well, I finally found a solution; QEMU

I had previously been trying precompiled binaries and had all sorts of errors, but there are some really excelent tutorials in the wiki that helped me get qemu running with all the bells and whistles.

heres the links
Basic tutorial
[https://wiki.ubuntu.com/Installation/QemuEmulator](https://wiki.ubuntu.com/Installation/QemuEmulator)
Kernel module to aid performance
[https://wiki.ubuntu.com/KQEmu](https://wiki.ubuntu.com/KQEmu)

---

### Post by myworld122 on 2006-06-10
can anybody tell me whether this would work if I would like to install Windows XP on my ubuntu machine?

---

### Post by E1000 on 2006-06-11
I've heard mixed results about windows, but its prety easy with the guides in the Wiki, so you aught to give it a try, repost here and tell us if it works.

once you use the guides to install qemu, use this 
[https://wiki.ubuntu.com/DapperQemuInstall](https://wiki.ubuntu.com/DapperQemuInstall)
and modify it to work for windows XP... ie, when specifying the boot location, point to /dev/cdrom instead of the ubuntu cd image.

the only thing i cant get to work is sound, although I cant tell why... just a warning.

---

### Post by dignome on 2006-06-11
[QUOTE=E1000]
the only thing i cant get to work is sound, although I cant tell why... just a warning.[/QUOTE]

Make sure the windows guest can see the sound card in the Device Manager.  The default sound card emulated is the isa? sb16 which is not PlugNPlay so you must go to Add New Hardware and let the guest scan for it.  The alternate is to use the other emulated soundcard with:

-soundhw es1370

Also check out:

qemu -audio-help

for configuring the host-side bits.

---

### Post by E1000 on 2006-06-11
well, after several hours of manpages and google searches I'v done it
[IMG]http://i26.photobucket.com/albums/c145/e1000sn/xp-setup.jpg[/IMG]
[IMG]http://i26.photobucket.com/albums/c145/e1000sn/xp-bootup.jpg[/IMG]
[IMG]http://i26.photobucket.com/albums/c145/e1000sn/windows-actionshot.jpg[/IMG]
 
the command I use to start my virtual XP machine is "qemu -kernel-kqemu -soundhw all -m 192 -hda ~/windows.img" Sound works because I compiled in sdl this time (and entered the parameter '-soundhw all'). I use full hardware virtualization through the kqemu kernel module and it has vastly increased my performance (although I didnt use it during install because I heard it could bug up a windows XP install)

Now I will enter my bed, because it is very late here.
-Evan

---

### Post by Jason_25 on 2006-06-11
Do usb sticks/drives work on the windows host?  Have you tried the Fat32 partition option?  Does networking work?  I found qemu to be stable, but I could not easily move files from the guest to the host, or get networking to function.

---


---
title: "clonezilla grub2 entry"
date: 2010-06-13
forum: General Help
---

### Post by pythonscript on 2010-06-13
I'm trying to create an entry to boot the newest, lucid-based version of the clonezilla ISO using grub2. Here's my current entry:

```

menuentry "Clonezilla" {
 loopback loop (hd0,2)/boot/grub/clonezilla-live-20100521-lucid.iso
 linux (loop)/live/vmlinuz boot=live union=aufs nolocales noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=(hd0,2)/boot/grub/clonezilla-live-20100521-lucid.iso
 initrd (loop)/live/initrd.img
}

```My boot partition is /dev/sda2 and the iso is located in the /boot/grub/ directory. The ISO boots, but after a few seconds of booting, it says:
```

Begin: Running /scripts/live-premount...
Done.

```

then hangs for a few minutes, and eventually says that it failed to boot and that /bin/sh can't access tty: job control turned off and dumps me to an initramfs terminal. Any help here? I can't figure out what I'm doing wrong!

---

### Post by pythonscript on 2010-06-14
Based on the clonezilla website, I created this grub2 entry (reproducing *exactly what they have on the website for booting an iso with grub2*). Here's what they have:

```

menuentry "Clonezilla" {
  set isofile="/boot/grub/clonezilla-live-20100521-lucid.iso"
  loopback loop $isofile linux (loop)/live/vmlinuz boot=live union=aufs nolocales noprompt  vga=788 ip=frommedia toram=fileystem.squash.fs findiso=$isofile
 initrd (loop)/live/initrd.img } EOF 

```

But it's still not working... anyone have any ideas based on the new entry (or the old one, for that matter, since neither is working).

---

### Post by pythonscript on 2010-06-14
After much hacking away at this, I've finally figured it out. 

```
echo "Adding Clonezilla 5-21-2010 Lucid-based..." >&2
cat << EOF
menuentry "Clonezilla 5-21-2010 Lucid-based" {
 loopback loop "/etc/grub.d/iso/clonezilla-live-20100521-lucid.iso" 
 linux (loop)/live/vmlinuz boot=live union=aufs nolocales noprompt gfxpayload=800x600x16 ip=frommedia findiso="/etc/grub.d/iso/clonezilla-live-20100521-lucid.iso"
 initrd (loop)/live/initrd.img
}
EOF
```

This successfully boots, and the software does work.

---

### Post by SyBorg on 2010-07-29
Gee thanks mate! Worked like a charm!

By the way... Love your avatar :)

Python rulez!

---

### Post by LewRockwellFAN on 2011-02-26
If I understand correctly pythonscript has stored a Clonezilla iso inside the file structure of a bootable ubuntu installation and has told grub2 to give him the option of booting from that iso as if it were a cd. Is that right or have I misunderstood? And am I right in assuming that with that kind of setup it would not be possible to use the iso based Clonezilla to image the partition that contains the iso, since it would presumably be mounted?

I've been trying to make a bootable hard drive based Clonezilla by putting the extracted files, not an iso or zip or any kind of archive directly on their own small partition based on the instructions here [http://clonezilla.sourceforge.net/livehd.php](http://clonezilla.sourceforge.net/livehd.php) with details of my own attempts so far to make those instructions work here [https://sourceforge.net/projects/clonezilla/forums/forum/663168/topic/4387557](https://sourceforge.net/projects/clonezilla/forums/forum/663168/topic/4387557) , but so far I haven't been able to make it work. Is there any reason this iso approach can't be used on a separate partition?

---

### Post by gus2986 on 2011-03-20
Hello,
The idea is to restore C:/ windows xp from D: ubuntu clonezilla 10-10 GRUB 2  Automatic restore by booting menu but after a week I get working clonezilla with some problems:
EOF
echo "RESTORE PC2" >&2
cat << EOF
menuentry "RESTORE PC2" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 140c-3521
    loopback loop /ubuntu/iso/clonezilla-live-20110113-maverick.iso
    set root=(loop)
    linux (loop)/live/vmlinuz boot=live live-config union=aufs nolocales noprompt gfxpayload=800x600x16 
    ip=frommedia nosplash toram=filesystem.squashfa    
    ocs_live_run="ocs-live-restore"
    ocs_live_extra_param="-g en_US.UFT-8 -t -k NONE -g auto -e1 auto -e2  -b -c restoreparts serge-image sda1" 
    initrd (loop)/live/initrd.img
}
EOF    

Problem1: Runs manual, clonezilla is not taking the parameters to run automatic. 
Problem2: Clonezilla runs ONLY with a USB clonezilla boot format, connected to a usb port.
Thanks for help.

---

### Post by LewRockwellFAN on 2011-04-04
@ [gus2986]("http://ubuntuforums.org/member.php?u=1265032") and anyone interested,
After 2 weeks you may have noticed you don't get many responses to additional comments in threads marked "solved".  For what it is worth, I've used Clonezilla for years, booting it from a CD, with no problems and I think I know all the ins and outs of using it in that manner, but I have never been able to get it to boot from a hard drive despite spending some time on the Clonezilla forum and discussing it with the developer who was stumped as to why I couldn't get it to work. For me the problem was getting grub2 to behave so if I were going to pursue it further I would take the issue to a grub forum. But I'm not doing so because atm 2 other approaches to the same goal seem more likely to be satisfactory. Mainly I plan to learn to use partimage and another similar program, the name of which I don't recall atm, instead of Clonezilla because installing them in a complete working Ubuntu installation instead of a dedicated partition seems to be pretty straight forward. By doing it that way, I can clone or restore an installation and still be able to use my computer for something else while that is going on. Of course to do this you need enough disk space for a redundant installation.

This may not apply to you but if I were going to pursue the booting clonezilla from a hard drive approach more I'd first look into changing my boot loader to LILO. Because while lots of people have managed to make it work with grub2, on my system that approach completely defeated me and the Clonezilla guru (Steve I believe his name is) and for me the problem was clearly that grub2 refused to act as it was supposed to and the only way forward we could see was to manually edit a config file that you aren't supposed to edit manually but is supposed to be updated from info in another config file that you are SUPPOSED to edit manually. For me the automatic part just didn't work, so it was really a grub2 problem, not a Clonezilla problem. And if the manual editing approach worked I'd have to redo it every time an update wiped out the changes.  I'm really over fiddling around with grub2, as it never seems to work right if you attempt anything the least bit out of the ordinary with it and LILO intrigues me anyway because you can add entries like "Try to boot from whatever is in the CD drive." and also because it has a reputation for doing what it is told like a well mannered ap instead of second guessing you and assuming it is smarter than it really is.

---

### Post by flash007 on 2011-04-11
I got it to work from a "partition" but it only worked from the boot partition that was /dev/sda5  OR in grub terms, (hd0,5).  I'm using LVM but not for the /boot partition.  I tried to get it to boot from a separate logical volume but could not.  so I opened the clonezilla iso image and copied all to /boot and it worked.  Luckily, I had enough partition space to do this.  Note that my OS was ubuntu 9.04 so I had to upgrade to grub2 (version 1.96).  I was tried to fully automate going from 32bit 9.04 to 64bit 10.04.2. and using clonezilla recovery image to re-image the root filesystem.

---

### Post by pasu11 on 2011-05-11
Hi, thanks for the very useful information. It helps me created a working clonezilla live entry in grub2. However, I have to add "live-config" ( boot=live live-config) otherwise it will show localhost.localdomain login: and halt there. Adding live-config solves the problem. By the way I am using clonezilla-live-1.2.8-23-amd64.iso and save the iso to /home/isos/ folder.

Thanks again!!


OS: Mint 10 64bit

---

### Post by Quackers on 2011-05-11
It works very well from the grub2 menu.
Have a look here 
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---


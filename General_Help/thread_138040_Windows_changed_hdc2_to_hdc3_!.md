---
title: "Windows changed hdc2 to hdc3 !"
date: 2006-03-01
forum: General Help
---

### Post by tnasniv on 2006-03-01
Hi, i installed Windows XP after ubuntu.
Before this, i reduced my /home partition (hdc1) then i installed windows xp on the free space but it itself set on the hdc2 partition and replaced the / mount point on hdc3 !

I had made a boot floppy (because i knew windows will erase the mbr) who works well, so i changed on menu.lst all hd0,1 to hdc0,2 (hdc2 -> hdc3) because he wouldn't boot otherwise.

But i think that there's a lot (or not ?) of other files in my linux partition that i have to edit to set hdc2 to hdc3 (or hd0,1 to hd0,2) but don't know their names, i just changed menu.lst on both floppy and hardisk and i modified /etc/fstab.

I am runnin on a breezy live cd and can access to all my partition (/home, /, swap) so their not broken.

But when i use the floppy boot disk it says after some test (grub passed well i think there's no more files to change on the floppy) that it can't mount /dev/hdc2, some files must refer to it but where ?

Than you !

---

### Post by tnasniv on 2006-03-01
the only file i found is :
mtab which contained hdc2 i changed for hdc3, i'm testing right now !

(sudo grep -wr hdc2 * 2>/dev/null) !

EDIT: didn't changed anything, the system boot, passed grub then it show ubuntu logo ("loading essential driver") then back to console style and says :

mount: mounting /dev/hdc2 on root failed ...
(others message related to the fact that it try to mount / on /dev/hdc2)

fdisk -l :
/dev/hdc1               1       10369    83288961   83  Linux **/home/vincent**
/dev/hdc2   *       10370       13762    27254272+   7  HPFS/NTFS **windows**
/dev/hdc3           13763       14961     9630967+  83  Linux /****
/dev/hdc4           14962       15017      449820    5  Extended
/dev/hdc5           14962       15017      449788+  82  Linux swap / Solaris **swap**

menu.lst :
...
# groot=(hd0,2)
...
title           Ubuntu, kernel 2.6.15-16-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-16-386 root=/dev/hdc2 ro vga=788 quiet spla sh
initrd          /boot/initrd.img-2.6.15-16-386
savedefault
boot

EDIT !!
lol... whit this copy paste i see something strange, i think that for grub (hd0,2) means hdc3 but /dev/hdc2 means ... hdc2 ? so windows, will change to test...

---


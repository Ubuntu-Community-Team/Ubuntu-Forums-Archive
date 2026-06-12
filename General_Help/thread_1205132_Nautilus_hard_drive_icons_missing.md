---
title: "Nautilus hard drive icons missing"
date: 2009-07-05
forum: General Help
---

### Post by m4cph1sto on 2009-07-05
I can mount and use my ntfs drives/partitions with no problems, but some of the drives have icons missing in Nautilus and in the Places > Removable Media menu.  I've attached a picture to show what I mean:

[IMG]http://files.getdropbox.com/u/1402548/drive-icons.png[/IMG]

When I mount the drives, the icon shown on the desktop is the "default" blank icon.  I can change this to any custom icon, but it does not affect the icon shown in the Nautilus menus.  

This seems to be a bug, but I'm hoping there's a way to manually get Nautilus to display the right icon.  Anyone know how?

---

### Post by michy99 on 2009-07-05
Is there any difference concerning where the ones with the blank icons are mounted as compared to the ones with the disk icons?

---

### Post by m4cph1sto on 2009-07-05
There's no difference that I'm aware of.  They're all ntfs.  Two of them (Data and Music) are auto-mounted with ntfs-3g, this is my fstab entries for them:

/dev/sdd2 /media/Data ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.UTF-8 0 0
/dev/sdb3 /media/Music ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.UTF-8 0 0

The partition "XP 32" has the normal removable disk icon when it's unmounted, but when I mount it the icon changes to that blank icon.  The partition "Vista 32" has normal icon behavior.  I don't know why this bug is happening with one icon and not the other.

---

### Post by Tamanegi on 2009-10-30
Hi! I'm having the same problem after upgrading to 9.10 and also after a clean install of 9.10. When I'm I run sudo nautilus i have icons and it looks fine. I have this problem only with my ntfs partitions. This is a small but annoying bug. I think there is some problem with my privileges, but i cannot change anything neither with chmod. Could you fix it? What should I do? Thanks

---

### Post by B3rt on 2009-10-31
I have the same problem, also after updating from 9.04 to 9.10

In places --> removable media I have on every mount 2 icons, 1 blank and 1 as drive icon
The blank icon gives an error when clicked on that the mount is already done, the drive icon show me the mounted drives 
(all mounts are remote sshfs mounts)

How do I remove these white icons so only the mounted drives are shown?!

---

### Post by Tamanegi on 2009-11-03
I solved it! I deleted every file windows created on my NTFS drive. E.g. System volume information, drive info and stuff. Now I have my icons in nautilus. I didn't test it on windows (cause i get rid of my win) so be careful, this may break the volume compatibility with win. But no problem so far in ubuntu.

---


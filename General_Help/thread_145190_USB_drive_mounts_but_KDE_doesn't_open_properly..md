---
title: "USB drive mounts but KDE doesn't open properly."
date: 2006-03-15
forum: General Help
---

### Post by [S|G] on 2006-03-15
Hello, I recently got a USB pendrive and KDE doesn't seem to recognize where it is mounted properly. When I plug it into my computer it automatically mounts in /media/KINGSTON AND /media/sda1, and I can access my files using the terminal or navigating to the directory with Konqueror.

However, when I click the KINGSTON icon on my desktop, Konqueror keeps trying to open media:/sda1 and nothing else happens. Same goes to when I go to "storage media" on KDE's system applet.

Here is my mtab:
```

diego@SnowGust:/media$ cat /etc/mtab
/dev/hda5 / reiserfs rw 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
/dev/hda2 /boot reiserfs rw,notail 0 0
/dev/hda6 /dos vfat rw 0 0
/dev/hda4 /home ext3 rw 0 0
/dev/hda1 /windows ntfs rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
/dev/sda1 /media/KINGSTON vfat rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sda1 /media/sda1 vfat rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

```

By the way, why is it being mounted on two different places? It doesn't really bother me, but I think it is somewhat unnecessary.

However what is really bugging me is if there is a way to fix the desktop's link to the pendrive.

Thanks a lot!

---

### Post by incubus on 2006-03-16
EDIT: sorry, I didn't read with attention.

Can you try manually unmounting one of them to see if the error persists?

incubus

---

### Post by sbassett on 2006-03-16
S|G when did this start? It seems like something may have gotten borked. Where there any recent updates to kubuntu? I have seen a couple instances on the board concerning this today, the other concerning KDE and K3b.

---

### Post by [S|G] on 2006-03-16
Actually, it started when I compiled a new kernel (2.6.15). I managed to get the pendrive recognized but I have this problem in KDE. Maybe I activated some option that confused it?

---


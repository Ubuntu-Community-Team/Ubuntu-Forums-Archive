---
title: "One thing I dont like about GNOME. Can u help me to fix it?"
date: 2006-05-11
forum: General Help
---

### Post by piggyaugu on 2006-05-11
By default, nautilus brings up all mounted partitions on the desktop. 

That was annoying when I have 6or7 partitions. So I disabled that option in gconf-editor. But another problem comes up, the external storage devices like USB HD dont show either. Can I turn it into showing only the external ones?:confused:

---

### Post by louis_nichols on 2006-05-11
You can symlink the folder to your desktop. It won't be the exact same thing, but works. Assuming your external hd is mounted under /mnt/external, you'd have to do this:

ln -s /mnt/external  ~/Desktop/external

---

### Post by piggyaugu on 2006-05-11
[QUOTE=louis_nichols]You can symlink the folder to your desktop. It won't be the exact same thing, but works. Assuming your external hd is mounted under /mnt/external, you'd have to do this:

ln -s /mnt/external  ~/Desktop/external[/QUOTE]

That's not my point. In fact, the reason I wanted to bring up the externals, it's by that, I can umount them with one hand ...(with mouse actually)....

---

### Post by louis_nichols on 2006-05-11
I know what you mean, but I don't think nautilus can discriminate between various kinds of volumes

---

### Post by Sutekh on 2006-05-11
If the partitions are mounted under /media then they will show up on the desktop when the option is enabled in the gconf-editor.  

If you want some volumes visible on the desktop and others not, then I would say you should change the mount points.  If you want the partition on the desktop, mount it under /media, if you don't want it on the desktop, don't mount it under media.  

Then enable the volumes_visible option in gconf-editor.

---

### Post by piggyaugu on 2006-05-11
[QUOTE=louis_nichols]I know what you mean, but I don't think nautilus can discriminate between various kinds of volumes[/QUOTE]

I think I had Fedora Core 5 able to do the trick (well, before the system collapsed through a total update). I am not sure how they did that.

---

### Post by piggyaugu on 2006-05-11
[QUOTE=Sutekh]If the partitions are mounted under /media then they will show up on the desktop when the option is enabled in the gconf-editor.  

If you want some volumes visible on the desktop and others not, then I would say you should change the mount points.  If you want the partition on the desktop, mount it under /media, if you don't want it on the desktop, don't mount it under media.  

Then enable the volumes_visible option in gconf-editor.[/QUOTE]

This is a good idea. Thx. I'll try that.

---

### Post by piggyaugu on 2006-05-11
[QUOTE=Sutekh]If the partitions are mounted under /media then they will show up on the desktop when the option is enabled in the gconf-editor.  

If you want some volumes visible on the desktop and others not, then I would say you should change the mount points.  If you want the partition on the desktop, mount it under /media, if you don't want it on the desktop, don't mount it under media.  

Then enable the volumes_visible option in gconf-editor.[/QUOTE]


No, it doesnt work. I've tried. It turns out that nautilus just pick up every partition other than / or home in my fstab.

Still waiting for an idea .......

---

### Post by louis_nichols on 2006-05-11
[QUOTE=piggyaugu]No, it doesnt work. I've tried. It turns out that nautilus just pick up every partition other than / or home in my fstab.

Still waiting for an idea .......[/QUOTE]

This doesn't happen in my case. I have 3 other partitions mounted, besides / and /home and they don't show up on my desktop. Only removable media. I have no idea why this is (or isn't lol) though

---

### Post by ComplexNumber on 2006-05-11
i can't see the problem. on my machine, the only icons that are there by default are trash, computer, and  home folder.  if i put a disk in, it automounts and the disk icon appears. when i eject, the disk icon disappears. same for the floppy. the windows XP icon is mounted in media but it doesn't show up on my desktop, so i created a symlink, created my own windows icon, then attached it to it. i'm using fedora core 5.

---

### Post by DOtSlaSHuCantCME on 2006-05-11
just comment out(#)the one you dont want to show up in your fstab. Mount them when needed by console our disk thingy .

---

### Post by mcduck on 2006-05-12
In Breezy there actually is an option in gconf-editor to hide all internal drives from desktop, so that external media (CD's, USB sticks etc.) still get an icon in desktop.. With Dapper, the setting doesn't exist any more. :(

I can't remember the exact setting, but it was under system, not apps/nautilus..

---

### Post by louis_nichols on 2006-05-12
[QUOTE=mcduck]In Breezy there actually is an option in gconf-editor to hide all internal drives from desktop, so that external media (CD's, USB sticks etc.) still get an icon in desktop.. With Dapper, the setting doesn't exist any more. :(

I can't remember the exact setting, but it was under system, not apps/nautilus..[/QUOTE]

Well, if you remember the name, chances are it can still be set...

---

### Post by piggyaugu on 2006-05-12
[QUOTE=mcduck]In Breezy there actually is an option in gconf-editor to hide all internal drives from desktop, so that external media (CD's, USB sticks etc.) still get an icon in desktop.. With Dapper, the setting doesn't exist any more. :(

I can't remember the exact setting, but it was under system, not apps/nautilus..[/QUOTE]

I didnt find anything in "system". I've run several search for "external", got nothing.

---

### Post by mcduck on 2006-05-15
[QUOTE=louis_nichols]Well, if you remember the name, chances are it can still be set...[/QUOTE]
I booted my breezy install to check this. This is what breezy had in gconf-editor:
```

system/storage/display_drives_with_removable_media
               display_external_drives
               display_internal_hard_drives
               display_scsi_drives
               display_scsi_optical_drives
```
Having two first enabled, and others disabled hides all your hard drives, but you still get icons for removable medias. In Dapper, however, there isn't even system/storage in gconf-editor ](*,)

---


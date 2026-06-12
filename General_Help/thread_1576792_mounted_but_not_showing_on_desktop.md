---
title: "mounted but not showing on desktop"
date: 2010-09-17
forum: General Help
---

### Post by UncleBoarder on 2010-09-17
I thought anything mounted to /media would appear on the desktop?

mount /dev/sdb1 /media/data

does mount sdb1... files are available in Terminal.  But there is no icon on the desktop.  Why?  What do I need to do to get a desktop icon?

---

### Post by themusicalduck on 2010-09-17
It should be enabled by default I think, but try this.

Press alt+f2 and type gconf-editor and hit enter.

Go to apps > nautilus > desktop

Check that volumes_visible is checked.

---

### Post by thinkinhurtz on 2010-09-17
This fix is for xfce but I'm quite sure it is the same in ubuntu...
simply right click on the desktop, then click 'desktop settings' or something similar. After that click the 'Icons' folder at the top of the window and then select the icons you would like to have displayed on the desktop

I hope that helps.

---

### Post by UncleBoarder on 2010-09-17
I neglected to mention that OTHER volume icons DO show on the desktop.  Just not this one.

Actually I originally had this one in fstab and it showed as well, but I now have it mounted in fstab to the /mnt directory and I'm using fstab to bind a subdirectory to /media/data

I hope that made sense.  Bottom line, the volume does mount but doesn't show on desktop.  Other volumes (like "Backup" below) do display on the desktop.  Here's my fstab...


proc                                       /proc                    proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=bb061f28-1a40-49b2-8fd8-03e6b3c5a6ed  /                        ext4  errors=remount-ro    0  1  

# swap was on /dev/sda5 during installation
UUID=fb609b91-7322-4903-9309-2f0d3a6b87d4  none                     swap  sw                   0  0  

# My shared volume /dev/sdb1
UUID=e0352916-43a0-431c-bd64-08a5f3182543  /mnt/shared              ext3  defaults,user,errors=remount-ro    0  0  

# Moving /home
/mnt/shared/Ubuntu/home                    /home                    bind  defaults,bind        0  0  

# Bind /mnt/shared/Ubuntu to appear as "data" volume on desktop
/mnt/shared/Ubuntu              /media/data            bind  defaults,bind        0  0
 
# Backup volume /dev/sdc1
UUID=468C14BE8C14AB07              /media/backup            ntfs  defaults,uid=1000,gid=1000,umask=002

---

### Post by themusicalduck on 2010-09-17
Ah, right.

I'm not sure if it's possible for Ubuntu to see those mounted folders as devices. Someone else might know an option to add to the fstab that tells it to do that, but after googling a bit, it doesn't look like there is such an option to use that is obvious.

Might it work just to create a link to the folder in the /mnt/shared directory and then copy that link to the Desktop? You could change the icon to the volume icon to make it look more uniform. I found it under the icon set folder (either ~/.icons or /usr/share/icons) in devices folder.

---

### Post by UncleBoarder on 2010-09-19
The answer is the mount order...

mount a drive to /media... it shows on desktop, and can be unmounted/remounted

mount a drive to /media AND mount it to /mnt... still shows on desktop but can not be unmounted/remounted

mount a drive to /mnt AND mount it to /media... won't show on desktop

So, two mounts of the same drive must be mounted to /media first.  And  if you unmount it, you'll have to unmount the second mount and remount  in the same order.

This might be true for mount --bind as well.  I didn't test.

---


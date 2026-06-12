---
title: "iPod persist with root permissions"
date: 2010-01-29
forum: General Help
---

### Post by frankbooth on 2010-01-29
Okay so my iPod auto mounts correctly to /media/IPOD (out of the box). But the permissions are set to root leaving me with no write permissions for syncing. Obviously it works if I sudo rhythmbox and then sync, but it's too much of a hassle and not very optimal (having to re-add the songs you want to sync etc).

   **So...**
 How do I make my iPod mount with permissions allowing me to read & write?
Previously (in 8.10 Intrepid Ibex) it used to auto mount with correct permissions.

**Some info that might be worth brining up:**
  This all started after I got my iPod back from Apple Store for repairs. I noticed they had updated the firmware and formated it to HFS+, I told them I wanted it changed to FAT32 and got it changed rather quickly.  Is it possible they f'd something up when formatting? If so, how do I correct it?

---

### Post by nothingspecial on 2010-01-29
HFS+ mounts read only by default. Are you sure they reformatted it.

Do you have access to a windows pc with iTunes, that`s the easiest way.

---

### Post by frankbooth on 2010-01-29
According to Palimpsest Disk Utility (System -> Administration -> Disk Utility):

'Type: W95 FAT32 (0x0b)'

(and unfortunately no, I don't have any window$ machine around)

---

### Post by nothingspecial on 2010-01-29
Have you tried changing the owernership of the iPod to your user.

---

### Post by frankbooth on 2010-01-29
> **nothingspecial said:**
> Have you tried changing the owernership of the iPod to your user.

Care to explain how this could be done? 

**I've tried the following:**

When trying to change permissions on /media/IPOD:

'Sorry, could not change the owner of "IPOD": Error setting owner:  Operation not permitted'

When creating the folder /media/IPOD (as root and then setting the correct  permissions) it mounts to /media/IPOD_ instead.

---

### Post by nothingspecial on 2010-01-29
```
sudo chown -R frank:frank /media/IPOD
```

---

### Post by Grenage on 2010-01-29
Could you not just add an fstab entry, with the 'user' flag/

---

### Post by frankbooth on 2010-01-29
> **nothingspecial said:**
> ```
sudo chown -R frank:frank /media/IPOD
```

'chown: changing ownership of `/media/IPOD': Operation not permitted'

---

### Post by frankbooth on 2010-01-29
> **Grenage said:**
> Could you not just add an fstab entry, with the 'user' flag/

/dev/sdd1        /media/IPOD        vfat        rw,user         0        1

like this?

---

### Post by nothingspecial on 2010-01-29
```
sudo blkid
``` with the ipod plugged in.

```
sudo mkdir /media/iPod
```

```
sudo nano /etc/fstab
```

add a line like this

```
UUID=?????????????   /media/iPod  vfat   rw,user,noauto  0   0
```

substituting the ?s for the letters and numbers you got from blkid.

---

### Post by Grenage on 2010-01-29
Exactly as above.  By using the UUID instead of common name (sdxx), you can be sure that other devices (usb key) won't use the mount point.  Remember that UUID will change if the partition changes, so if you repartition/format the drive, you'll need to update the UUID.

---

### Post by frankbooth on 2010-01-29
Thank you, works like charm! :D  Just a follow up question if I may...  The folder/icon (when ipod isn't connected) now showing up in 'Places' inside Nautilus, I suppose this is connected to fstab? Would it be possible to hide it or is this something that's hard coded?

---

### Post by Grenage on 2010-01-29
That's right, it's down to fstab + ubuntu.  If the mount point was elsewhere (/mnt/ipod) then it wouldn't show up in places.  Unfortunately I don't think it shows up there even when connected.

---

### Post by frankbooth on 2010-01-29
Alright, thanks for all the help guys :)

---


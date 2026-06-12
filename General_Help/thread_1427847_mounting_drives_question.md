---
title: "mounting drives question"
date: 2010-03-12
forum: General Help
---

### Post by ffxigotenks on 2010-03-12
this is something that I've wondered for a while and am very curious about... when I plug in a hard drive/flash drive/etc, it creates a folder in /media named either by the device or disk-X that did not exist previously, is there a way for me to have my own mount points that only exist when they are mounted. for example, I have a USB drive that isn't always mounted at boot, but I don't want it's mount point (/media/640ext/) to exist when it isn't connected, mostly for uses with conky, but also for the neatness of my /media folder. inane reasons, I know, but if I can make it happen it would make me happy anyway

---

### Post by kyletstrand on 2010-03-12
To make a mount point for any specific drive, just type the following into your command lind:

```
sudo mkdir /media/yourdrivename
```

To manually mount the drive, find the drive file in your /dev/ folder.  If you have nothing else connected at the time, it is generally going to be /dev/sdb1 (if you already have devices mounted, it might be /dev/sc1/ or /dev/sd1/ respectively).

After you find the drive you can manually mount the drive to your mount point using this in your terminal:

```
sudo mount /dev/sdb1 /media/yourdrivename
```

It's that easy.  To manually dismount the drive, use:

```
sudo umount /media/yourdrivename
```

If you want to automatically mount your drive, there is a good tutorial here: <a href="https://help.ubuntu.com/community/InstallingANewHardDrive">https://help.ubuntu.com/community/InstallingANewHardDrive</a>/

I'm not terribly familiar with automatic mounting, but hopefully it might help!

---

### Post by nothingspecial on 2010-03-12
Label the drive

Use gparted or one of the file system labeling programs eg e2label

See [[COLOR="Magenta"]here[/COLOR]]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by kyletstrand on 2010-03-12
Sorry, didn't read the question fully enough.  

I guess you didn't want the mount point to exist when the drive isn't connected.  Sorry don't know that.  You could always remove the mount point in the command line when you dismount the drive. I guess if you want to do it all manually.

---


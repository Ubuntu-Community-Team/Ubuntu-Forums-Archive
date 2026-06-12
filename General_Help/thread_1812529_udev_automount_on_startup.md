---
title: "udev automount on startup?"
date: 2011-07-26
forum: General Help
---

### Post by cwhittier on 2011-07-26
I have set some udev rules to automount usb drives when they are plugged in. I followed the answer provided here: [http://superuser.com/questions/53978/ubuntu-automatically-mount-external-drives-to-media-label-on-boot-without-a-us](http://superuser.com/questions/53978/ubuntu-automatically-mount-external-drives-to-media-label-on-boot-without-a-us)

The only issue I have left, is on startup. The drive shows up in nautilus, but it will not appear in the /media folder until i click on the drive via nautilus. I need the /media/DRIVENAME folder to be created at startup. Any ideas?

---

### Post by mikewhatever on 2011-07-26
...but USB devices are automounted by default, and the mount point corresponds to the partition label. Why did you need more rules for that.

---

### Post by cwhittier on 2011-07-26
USB devices are automounted by default by nautilus. I am running ubuntu 9.04, and nautilus is not running by default, because it's "show-desktop" setting is set to false (which from what I can tell causes nautilus to exit as soon as it's launched, because there are no windows to draw). Because of this, I had to find an alternate source of automounting USB drives.

---

### Post by cwhittier on 2011-07-26
I have found a solution.

The problem is, that the udev rules that try to mount the USB drive end up running on boot way before the system is up and running. To solve this, in the script that the USB rules spawn, add the following code:


RUNLEVEL=`/sbin/runlevel | cut -d " " -f 2`
until [ $RUNLEVEL -ge 1 ] && [ $RUNLEVEL -le 6 ]; do
      sleep 10
      RUNLEVEL=`/sbin/runlevel | cut -d " " -f 2`
done

This will wait until the system is initialized before trying to mount the drive, and a folder will show up in the /media folder.

Note: make sure that your launch of this script has a "&" at the end, so it does not block, otherwise if media is connected on boot, your system will hang indefinitely.

---

### Post by mikewhatever on 2011-07-26
Cool, thanks for updating.

---


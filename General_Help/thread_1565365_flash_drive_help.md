---
title: "flash drive help"
date: 2010-08-31
forum: General Help
---

### Post by philipballew on 2010-08-31
i am wondering if there is a way that i can make my flash drive that as soon as i stick it into my computer it will copy the files from a specificed directory onto my drive?

---

### Post by David Andersson on 2010-09-01
There are a few different ways to approach this. You want to start a copy script you have written yourself, when the device is inserted or mounted.

1) Settings in Nautilus. In the file browser, go to Edit>Preferences>Media. Find a Media Handling type or Other Media type, that matches your flash drive. You may have to try which type works. For that type, change action to Open With Other Application and Use A Custom Command. Enter the full path of your script.

2) Configure UDEV rules. See e.g.
[https://help.ubuntu.com/community/UsbDriveDoSomethingHowto](https://help.ubuntu.com/community/UsbDriveDoSomethingHowto)
[http://www.linuxquestions.org/questions/linux-desktop-74/running-a-script-when-auto-mounter-detects-usb-thumb-drive-insertion-529113/](http://www.linuxquestions.org/questions/linux-desktop-74/running-a-script-when-auto-mounter-detects-usb-thumb-drive-insertion-529113/)
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

3) Have a cron job start every few seconds to check if a new device has been added, and then start your script.

4) Using a package that listen to system events and that can start user configurable actions. Maybe the packages "halevt" or "ivman" in the repositories can help.

5) You write a script that detects system events. Maybe start with tail -1f /var/log/syslog and grep /dev/sdXX. (Like "tail -1f /var/log/syslog | grep ' mounted /dev/sdc1'" and work out mount point etc from there.) Let this script autostart when you login. Let this script start the script in the next section (that check directory and copies files) when it detects a device with a known mount point, or so.

Your copy script should be designed to check if the device really is a device it should act on. First it must check that the file system is of the expected type, then, if the directory has a very special name, it could check if that directory exists. If the check fails, the script should do nothing.

How the copy script gets to know exactly where the device is mounted, I think depends on what method is used.

(I have not tried any of the methods myself, except (1) for ext2/3/4 formatted usb sticks, which was classified as Unix Software.)

---

### Post by philipballew on 2010-09-02
so theres no like guide to get this done easily?

---

### Post by David Andersson on 2010-09-04
> **philipballew said:**
> so theres no like guide to get this done easily?

There is not one guide. There are guides for (2) UDEV (above) and for (4) Ivman (e.g.  [http://www.linux.com/archive/feature/56016](http://www.linux.com/archive/feature/56016) ). 

If "easy" means no editing text files, then (1) Nautilus Media Handling comes closes, but you still have to write a script, and you have to find out what media type it thinks your device is.

**In the meantime**

Until you have found the perfect solution, this might help.
[LIST]
[*] Make sure you have a "bin" directory in your home directory. If you just created "bin" logout and login to get it recognized.

[*] Create a directory "copyofspecial" in your home directory.

[*] Save this scripts as "mydevicemonitor" in your "bin" directory:
```

#!/bin/bash
# mydevicemonitor
# When a vfat is mounted, run program $1 with the mount point as argument.
# Example startup command: mydevicemonitor mycopyspecial
#
while sleep 5; do new=$(mount | awk '/type vfat/{print $3}' | sort); comm -23 <(echo "$new") <(echo "$old") | xargs -rl "$1"; old=$new; done

```

[*] Save this scripts as "mycopyspecial" in your "bin" directory:
```

#!/bin/bash
#
# If there is a dir named "special" in $1, then copy that dir
# to a dir with todays date: ~/copyofspecial/YYYY-MM-DD_HH.MM.SS
#

fromdir=$1/special
todir=$HOME/copyofspecial/$(date +%Y-%m-%d_%H.%M.%S)

if [ -d "$fromdir" ]; then
    cp -r "$fromdir" "$todir"
fi

```

[*] Test the scripts by typing the command "mymonitordevice mycopyspecial" in a terminal. Plug in a device. Wait a while. Safe remove the device. If the device had a "special" directory on it, it should have been copied to "copyofspecial".

[*] If it works, make mymonitordevice start automatically at login: go to *System > Preferences > Startup Applications*, click Add and enter the Command "mymonitordevice mycopyspecial" (without quotes). Type a Name and a Comment if you want. Logout and login.
[/LIST]

Edit: I forgot, after you have saved the scripts in "bin", you must make them executable.

---


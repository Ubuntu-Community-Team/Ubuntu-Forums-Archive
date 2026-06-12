---
title: "Live USB - no upgrade option"
date: 2011-10-17
forum: General Help
---

### Post by aoniumo on 2011-10-17
So I downloaded ubuntu 11.10 and put it in a usb flash drive.  I was able to boot to the usb flash drive hoping I could upgrade that way.   It gives me the following options to install it:

 1) Install ubuntu 11.10 alongside ubuntu 11.10. 
2) Upgrade ubuntu 11.04 to 11.10. 
3) Erase ubuntu 11.04 and reinstall 
4) Something else.  

I am able to select all options except &quot;Upgrade ubuntu 11.04 to 11.10&quot;.  Why is that? My current installation is not being detected.  Is there a way around this so my current 11.04 is detected?

I really need help with this one as I hate to choose option 1 or 3 above.  Upgrading via the update manager is not option for me as i mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=1862495](http://ubuntuforums.org/showthread.php?t=1862495)

---

### Post by aoniumo on 2011-10-20
Help?

---

### Post by garvinrick4 on 2011-10-20
[http://www.ubuntu.com/download/ubuntu/upgrade](http://www.ubuntu.com/download/ubuntu/upgrade)

---

### Post by aoniumo on 2011-10-20
As I said using the Update Manager would not work for me.  I used my phone's data to download the 700mb new Ubuntu 11.10.  My computer has a mobile network since there's not cable or dsl connection where I live.  This mobile connection often times disconnects and has a slow transfer rate (20kb/s) so it would take half a day to update providing I do not get disconnected.  If I get disconnected as I mentioned in another help thread, I would have to download the packages from scratch as there is no resume feature or partially downloading packages so you can resume if you get disconnected.

---

### Post by aoniumo on 2011-10-21
I tried it again, and I was wrong.  The 11.10 Live USB does detect my current 11.04.  It's just that the option to ugrade it is not selectable so I cannot upgrade.  There is the option to install it alongside 11.04, but the only drive of the three hard drives in my computer that shows as a place to install is the slowest of my hard drives which already has videos and pictures in it.  I'm not risking installing it there and have my files deleted.

So any other help would be appreciated.

---

### Post by aoniumo on 2011-10-22
Tried these commans - sudo apt-get update && sudo apt-get dist-upgrade - but it's only updating natty.

---

### Post by aoniumo on 2011-10-22
Downloaded alternative version and tried this:

sudo mkdir /cdrom
sudo mount -t iso9660 /path/to/alternate-iso/ubuntu.iso /cdrom -o loop (where ubuntu is saved so I changed these words)
sh /cdrom/cdromupgrade

I get this error:

Traceback (most recent call last):
  File "/tmp/tmp.jajiJjzHbq/oneiric", line 7, in <module>
    sys.exit(main())
  File "/tmp/tmp.jajiJjzHbq/DistUpgradeMain.py", line 172, in main
    logdir = setup_logging(options, config)
  File "/tmp/tmp.jajiJjzHbq/DistUpgradeMain.py", line 77, in setup_logging
    os.mkdir(backup_dir)
OSError: [Errno 13] Permission denied: '/var/log/dist-upgrade//20111021-1756'

---


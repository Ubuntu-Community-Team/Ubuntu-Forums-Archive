---
title: "SCP to ubuntu 9.10 does not wake external drive"
date: 2010-05-15
forum: General Help
---

### Post by luigi6699 on 2010-05-15
Totally bizarre issue happening here.  So, I have a wonderful ubuntu media center running on my network, with a WD Mybook USB terabyte drive storing all my media.  Everything works great.

Except file transfers.  When I transfer files over the network to the server, it's incredibly slow!  Aware that this could easily be a wireless problem or some other network connectivity issue, I tried connecting directly via 100baseT network cable.  Still, when I SCP a large file, my speeds are between 1 and 2MB/s!

In desperation, I logged in via SSH while a file was transferring, and poked around at everything I could find, all the while graphing the file transfer.  And I noticed something funny... when the disk was working on some other task, my transfer speeds shot up to 6-8MB/s!  So I tried something radical, and ran "du" on the root of the external drive... and watched my transfer speed soar!

If I kill the du, the speed briefly jumps up to 10 or 11MB/s, which is about the max I would expect from a 100mbit connection... and then drops back down to 1MB/s or below.

So here's my theory:  For some reason, SCP and SAMBA aren't bringing the disk out of PM "sleep" mode.  So all they have access to is the very slow speeds of a sleeping drive.  The moment I do something that wakes them up, BAM I get good speeds.  The peak after I kill "du" is SCP getting full bandwidth for a moment, before the drive goes back to sleep.

Anyone have any suggestions?  Surely smbd and sshd SHOULD be able to wake a disk up!  Disabling sleep mode on the drive is not an option, as it's plugged in 24/7 and I don't want to risk damaging the drive.  For now I can log in a second session and run ls -alR to bring the transfer speed up, but god forbid my wife ever wants to put a movie on the system! :(  (also, doing this adds a noticable load on the CPU... I can hear the fan kick into higher gear, and on one occasion the system even shut down from overheat!)

So, what are your suggestions, ubuntu gurus?

---

### Post by Guiness6 on 2010-06-02
I have the same problem. I have a WD 1.5 TB MyBook attached via USB and whenever anything tries to talk to it its ridiculously slow because it's not "awake". I found another post on here that seems to have a fix, but its a little vague. Maybe someone could help explain the **echo "on"** section to me?


> **9tails said:**
> Nevermind. I managed to disable automatic standby and the usb drive power management (apm) feature, but the load cycles count keeps increasing...

Anyway, in case you're reading this thread looking for a way to disable apm on usb drives, or the automatic spindown feature, here's how I did it.

If you want to disable spindown, run:

sudo sdparm -a /dev/sda
if the STANDBY attribute is set, change it to 0 using sdparm.

If you want to disable apm for an usb drive:

cd /sys/bus/usb/devices

Look for the directories containing a file called "product". If the file contains the string "Portable USB drive" or similar, that's the one you're looking for. Just do a sudo echo "on" > ./power/level and you have disabled apm for that drive.

---

### Post by Guiness6 on 2010-06-02
I possibly figured this out. I followed the above directions to find my device's usb power management config files. For me it was unser /sys/bus/usb/devices/1-2/power. There you will find the file named "level" and "autosuspend". The level file was already set to "on", but autosuspend was set to "2" which is also "on". I changed it to "1" using the following to edit the file.

```
sudo nano /sys/bus/usb/devices/1-2/power/autosuspend
```

Hopefully this will fix the problem. Personally, I don't care if the drive doesn't spindown to save power.

*EDIT* Autosuspend file should be set to "-1". However it depends on the kernel you have. Found this site. Which provides some explanation.

[http://www.blackberryforums.com/linux-users-corner/97661-enable-disable-config_usb_suspends-autosuspend-mode.html](http://www.blackberryforums.com/linux-users-corner/97661-enable-disable-config_usb_suspends-autosuspend-mode.html)

---

### Post by luigi6699 on 2010-06-12
Well this helps quite a bit... still working on figuring out which USB device is my hard drive - seems that many things in this laptop actually use the USB bus.  USB video?  Who knew!

But I don't mind having the drive spin down, I just want it to spin UP properly.  what controls the triggers for taking a drive out of sleep?

I'm sure there's something like hdparm.conf I could use to help my drive respond to smb and ssh based read/write requests.  I found a few related threads on controlling ATA hdd's in laptops:

[https://wiki.ubuntu.com/DanielHahler/Bug59695](https://wiki.ubuntu.com/DanielHahler/Bug59695)


[https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/19](https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/19)

[https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/63](https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/63)


Anyone else working on this?  Thank you Guiness6 for your help so far...

---


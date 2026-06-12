---
title: "mount USB-HDD on wakeup from sleep (10.04)"
date: 2010-08-31
forum: General Help
---

### Post by baustromverteiler on 2010-08-31
Hello everybody,

because of a bug that changes the device of an USB-HDD from /dev/sdb to /dev/sdc after wakeup I need to re-mount  my external usb-hdd on wakeup.

As far  I found out this could be done with an script in /usr/lib/pm-utils/sleep.d

I placed a script there and made it executalbe, the contents are: 

```

#!/bin/sh
sudo mount -a
echo "working" /home/max/Desktop/test.txt
exit 0

```

If I execute the script from shell the HDD gets mounted, when waking from sleep/standby the script writes "working" in the specified file but the hdd won't get mounted.

As I plan using the HDD as a NAS it's important it gets mounted again because otherwise the samashares are invalid :)

any hints apprecciated,

thanks, Max

(sorry for the typo in subject, can't edit it anymore ... )

---

### Post by ilovelinux33467 on 2010-08-31
so is the hard drive in /etc/fstab?

---

### Post by baustromverteiler on 2010-08-31
yes it's in fstab and mounted by UUID, if I run mount -a manually everything works as expected. It's just the script not working

---

### Post by ilovelinux33467 on 2010-08-31
I think it could be a problem with putting sudo in your script as that requires user input.

---

### Post by ilovelinux33467 on 2010-08-31
try adding the line to your script before the exit 0 line:

whoami >> /home/max/Desktop/whoami.txt

What is the output of /home/max/Desktop/whoami.txt

Just got to see if that script is running as root or normal user

---

### Post by baustromverteiler on 2010-08-31
thanks for your help and fast replies!

I just added the line you suggested.

If I add it in /usr/lib/pm-utils/sleep.d/40mount just "test.txt" is ceated, there's no whoami.txt, I double checked paths. If I execute the script manually whoami.txt is created.

I tried placing the script in /etc/pm/sleep.d and here "whoami.txt" is created and contains "root" but still nothing is mounted.

I tried both ways without the "sudo" but nothing changed.

---

### Post by baustromverteiler on 2010-09-01
anyone?  spent yesterday afternoon scratching my head and tinkering with shellscripts but didn't come up with anything :(

---

### Post by ilovelinux33467 on 2010-09-01
maybe put something like:

```
sleep 3
```

at the start of the script. This will give some time for the drive to be recognized before mount -a

Let me know if it works

---

### Post by baustromverteiler on 2010-09-02
Unfortunately not working too :(

---

### Post by baustromverteiler on 2010-09-06
I had a look into /var/log/pm-powersave.log and found the following:

```
/usr/lib/pm-utils/power.d/90mount false:mount: no such partition found
success.
/usr/lib/pm-utils/power.d/95hdparm-apm false:success.
/usr/lib/pm-utils/power.d/anacron false:success.
/usr/lib/pm-utils/power.d/powersave-policy-dirty-writeback false:success.
/usr/lib/pm-utils/power.d/powersave-policy-hda-powerdown false:success.
/usr/lib/pm-utils/power.d/sched-powersave false:**sched policy powersave OFF success.
```

I think this means the  UUID of the USB-HDD I need to mount is  not available during wakeup from sleep. 
I just tried ls > /dev/disk/by-uuid/ /home/max/Desktop and the UUID of the USB-HDD does not show up ... 

if I let the mountscript in /usr/lib/pm-utils/power.d output dmesg to a textfile the last line showing up is:

```
[ 3257.697214] usb-storage: waiting for device to settle before scanning
```

so this means the USB-HDD isn't yet detected when the script runs, so it fails to mount it. 

I added an extra "sleep" command to the script and now everything works fine!

For anyone facing the same problem, here's the script (placed in /usr/lib/pm-utils/power.d/ and made executable with sudo chmod +x mount) , if you use it just comment out the dmesg lines.

```

#!/bin/sh
sleep 10
dmesg | grep usb-storage > /home/max/Desktop/debug.txt
sleep 15
dmesg | grep usb-storage > /home/max/Desktop/debug1.txt

mount /dev/disk/by-uuid/4EB420BCB420A903 /mnt/Samsung -t ntfs -o umask=000
exit 0

```








Any thoughts on how I could  fix this issue?

regards, max

---

### Post by egalvan on 2010-09-06
I'd like some info to rattle around in my head...
if you please.


How is the partition formated?

Does it have a LABEL?

Can you post the pertinent fstab line?

Can you post the pertinent 'samashares' (? sic) line?
(or whatever you use to share the partition)


And last.. can you show the provenance of the "bug" that causes the change in 'sd' nomenclature?

---

### Post by baustromverteiler on 2010-09-06
please see post #10 for the solution I found.

This are the links to the bug-descriptions:

[https://bugzilla.kernel.org/show_bug.cgi?id=14442](https://bugzilla.kernel.org/show_bug.cgi?id=14442)
[https://bugzilla.kernel.org/show_bug.cgi?id=15396](https://bugzilla.kernel.org/show_bug.cgi?id=15396)

this is another thread addressing the same problem with another solution (which was not working for me):

[http://ubuntuforums.org/showthread.php?t=855289](http://ubuntuforums.org/showthread.php?t=855289)

regards, max

---

### Post by alexalecu on 2010-09-06
The resume script I had in /etc/pm/sleep.d was not reliable, sometimes it worked, but most of the times it did not. As baustromverteiler mentioned already, it was usually trying to mount the partitions on the USB drive before the device was ready.

I have added some **sleep** statements around the code in resume and it works now. Here is the script:

```
#!/bin/bash

case $1 in
    hibernate)
	;;
    suspend)
	umount /media/sdb1
	umount /media/sdb2
	cryptsetup luksClose sdb2
	eject /dev/sdb
        ;;
    thaw)
        ;;
    resume)
        sleep 7   # new
        mount /media/sdb1
	sleep 2   # new
	/bin/bash /home/user/.cryptOpen
	sleep 2   # new
	mount -t ext4 /dev/mapper/sdb2 /media/sdb2
	;;
esac
```

---

### Post by oneNF on 2010-09-08
While not being an expert I suggest you while loop through sleep cycles until the device is located, or a certain number of cycles have been completed.  
 
This way if there is an increase in the time taken (> sleep 25) to identify your device it will continue to check without the need for additional code.  (This tripped me up in batch files in the past when I used windows  :-)

---

### Post by danwood76 on 2010-09-13
By default udev should mount the usb disk to '/media/DISK-UUID' or to '/media/DISK-LABEL' so I am unsure why you are trying to mount it manually.
(maybe you are following a guide)

You should just point your samba shares to the udev mounted partitions location.

Where does the USB disk get mounted to if you dont mount itt yourself?
Udev usually ignores disks in the fstab by default so if you have it in there it wont auto mount.

---


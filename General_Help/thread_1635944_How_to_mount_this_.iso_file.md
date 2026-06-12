---
title: "How to mount this .iso file ?"
date: 2010-12-02
forum: General Help
---

### Post by xrobot on 2010-12-02
I am trying to mount an iso image of a videogame but I get error:

```

# mount CD1.iso /media/iso/ -t iso9660 -o loop
wrong fs type, bad option, superblock on / dev/loop0 damaged,
missing codepage or helper program, or other error
In some cases you may find useful information in syslog. Try
eg 'dmesg | tail'


# dmesg | tail
[196647.512617] Registered led device: iwl-phy0::TX
[198333.313214] lo: Disabled Privacy Extensions
[199261.592514] iwlagn 0000:06:00.0: Microcode SW error detected.  Restarting 0x82000000.
[199261.832506] Registered led device: iwl-phy0::radio
[199261.834160] Registered led device: iwl-phy0::assoc
[199261.835597] Registered led device: iwl-phy0::RX
[199261.836476] Registered led device: iwl-phy0::TX
[201253.182595] ISOFS: Unable to identify CD-ROM format.
[201266.407422] ISOFS: Unable to identify CD-ROM format.
[201443.329091] ISOFS: Unable to identify CD-ROM format.
```


If instead I right click on the iso and then click on mount archive, I get an empty disk.
How can I do ? :-s

---

### Post by lrgmmc on 2010-12-02
what command did you use to mount it?

---

### Post by xrobot on 2010-12-02
> **lrgmmc said:**
> what command did you use to mount it?

# mount CD1.iso /media/iso/ -t iso9660 -o loop
;)

---

### Post by karthick87 on 2010-12-02
Use the following comment to mount your iso image,
```
sudo mount -o loop -t iso9660 /wherever/iso/image/is/image.iso /media/iso/
```

[[COLOR=DarkRed]**You can also save the nautilus scripts from this link  to mount and unmount iso image.**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=87369")

---

### Post by lrgmmc on 2010-12-02
have a look here see if it helps.
[https://help.ubuntu.com/community/CdDvd/Burning](https://help.ubuntu.com/community/CdDvd/Burning)

---

### Post by xrobot on 2010-12-02
now I am using this command:

```
# mount CD1.iso /media/iso/ -o loop
```

without -t iso9660

and work :D

why ?

---

### Post by karthick87 on 2010-12-02
Also check this link

[http://ubuntuforums.org/showpost.php?p=7059338&postcount=3](http://ubuntuforums.org/showpost.php?p=7059338&postcount=3)

---

### Post by lrgmmc on 2010-12-03
Because it was probly a udf iso?

---

### Post by karthick87 on 2010-12-03
**The following script can mount both iso and udf images.**

**Mount**
[LEFT][COLOR=#000000]```
#!/bin/bash
 #
 # nautilus-mount-iso
 gksudo -u root -k /bin/echo &#8220;got r00t?&#8221;
 sudo mkdir /media/&#8221;$*&#8221;
 if sudo mount -o loop -t auto &#8220;$*&#8221; /media/&#8221;$*&#8221;
 then
 if zenity &#8211;question &#8211;title &#8220;ISO Mounter&#8221; &#8211;text &#8220;$* Successfully Mounted.
 Open Volume?&#8221;
 then
 nautilus /media/&#8221;$*&#8221; &#8211;no-desktop
 fi
 exit 0
 else
 sudo rmdir /media/&#8221;$*&#8221;
 zenity &#8211;error &#8211;title &#8220;ISO Mounter&#8221; &#8211;text &#8220;Cannot mount $*!&#8221;
 exit 1
 fi
```Copy / Paste the above script in your text editor and name it as [B]mount.sh
[/B][B]
Unmount[/B]
[LEFT][COLOR=#000000]```
#!/bin/bash
 #
 for I in &#8220;$*&#8221;
 do
 foo=`gksudo -u root -k -m &#8220;enter your password for root terminal
 access&#8221; /bin/echo &#8220;got r00t?&#8221;`
 sudo umount &#8220;/media/$I&#8221; && zenity &#8211;info &#8211;text &#8220;Successfully unmounted /media/$I/&#8221; && sudo rmdir &#8220;/media/$I/&#8221;
 done
 done
 exit0
```Copy / Paste the above script in your text editor and name it as **unmount.sh**

Now you want to make your script executable,type the following in terminal
```
sudo chmod +x /path/to/mount.sh
``````
sudo chmod +x /path/to/unmount.sh
```Then you should move both **mount.sh** and **unmount.sh** to **~/.gnome2/nautilus-scripts/**

Now you can right click your ISO file or UDF file and choose mount to mount your image and unmount to unmount your image.

[/COLOR][/LEFT]

[/COLOR][/LEFT]

[[COLOR=Red]**ALSO SEE THIS THREAD**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2978984&postcount=6")

---

### Post by ppv on 2010-12-03
The command without the iso9660 worked because the iso file was not in an iso9660 format. You could use -t auto so that the filesystem is checked automatically.

---


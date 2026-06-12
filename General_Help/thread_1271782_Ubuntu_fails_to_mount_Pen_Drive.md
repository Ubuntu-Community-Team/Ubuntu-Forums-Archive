---
title: "Ubuntu fails to mount Pen Drive"
date: 2009-09-21
forum: General Help
---

### Post by beastrace91 on 2009-09-21
Hey There,

So I went to plug in my jump drive this morning to grab a file off my system and Ubuntu failed to auto mount it... So I tried to manually mount it and I get the following results: ```
jeff@sager-lintop:~$ sudo mount -t vfat /dev/sdb /media/jumpdrive
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jeff@sager-lintop:~$ dmesg | tail
[53991.203610] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[53991.209232] sd 11:0:0:0: [sdb] 8060928 512-byte hardware sectors:(4.12 GB/3.84 GiB)
[53991.209875] sd 11:0:0:0: [sdb] Write Protect is off
[53991.209881] sd 11:0:0:0: [sdb] Mode Sense: 23 00 00 00
[53991.209886] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[53991.209894]  sdb: sdb1
[53991.212545] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[53991.212688] sd 11:0:0:0: Attached scsi generic sg2 type 0
[54013.154541] FAT: invalid media value (0x00)
[54013.154548] VFS: Can't find a valid FAT filesystem on dev sdb.

```

The same pen drive works fine on my other Ubuntu system (auto mounts as it should) but I really need to get it working on my main laptop again... Any idea what could be causing the issue?

EDIT: Also on my way to work I was thinking what I had changed recently and last night before this stopped working I had installed VirtualBox and configured it so I could attach USB devices to the VM. I added the following lines to my /etc/fstab ```
 vGid="`grep vboxusers /etc/group|cut -d\: -f3`" # Determine the devgid for the vboxusers group
 if [ "$vGid" ] && [ "`grep usbfs /etc/fstab`" == "" ] ; then
        echo "none /proc/bus/usb usbfs devgid=${vGid},devmode=664 0 0" >>/etc/fstab
        mount -a
 fi
```

I was following [this guide](https://help.ubuntu.com/community/VirtualBox/USB) when I did such. Do you think that could be the issue? I'll have to try commenting out said lines when I get home if it might be...

~Jeff

---

### Post by bogdan.veringioiu on 2009-09-21
Hi.

You could try to remove the line below from /etc/fstab:
none /proc/bus/usb usbfs devgid=xxx,devmode=664 0 0

Then insert your pen, and see if it automounts (you might try a restart after editing fstab).
Bogdan

---

### Post by beastrace91 on 2009-09-21
> **bogdan.veringioiu said:**
> none /proc/bus/usb usbfs devgid=xxx,devmode=664 0 0

Removing just that line did not help... going to try removing the whole entry now.

~Jeff

---

### Post by beastrace91 on 2009-09-22
Yep removing those lines from my fstab fixed the issue... And my devices still attach to my VirtualBox I wonder why they are included in there.

~Jeff

---


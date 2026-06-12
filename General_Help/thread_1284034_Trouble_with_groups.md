---
title: "Trouble with groups"
date: 2009-10-06
forum: General Help
---

### Post by Virus_ST on 2009-10-06
Hi! Not very recently I've posted a thread regarding running firewire devices on linux. It was generally concerning using ffado etc. Anyway I got no responses so I tried to work my way through the process step-by-step from scratch. The process is to get my firewire soundcard working on ubuntu.
To make it short things are going fairly well. I'm a total noob so sometimes I don't have a clue what I'm doing, but I'm carefully following instructions from the ffado site.
The problem I'm having is this:
```
  c) You don't have permissions to access /dev/raw1394. 'ls -l /dev/raw1394'
    shows the device-node with its permissions, make sure you belong to the
    right group and the group is allowed to access the device.

```here are the access details
```
ls -al /dev/raw1394
crw-rw---- 1 root root 171, 0 2009-10-06 11:57 /dev/raw1394

```As you can see the 'root' group is where I want to be. I've been adding myself to the group for about an hour now and I still can't figure anything out. I'm not a member of the group no matter how many times I call usermod.
Check it out:
```
ozren@Geo11:~$ id
uid=1000(ozren) gid=1000(ozren) groups=4(adm),20(dialout),24(cdrom),46(plugdev),106(lpadmin),121(admin),122(sambashare),1000(ozren)

```I hope I've been clear with my problems. Be gentle. Thanks.

---

### Post by Lars Noodén on 2009-10-06
I'm not quite sure what the correct group would be, but you might try putting [FONT="Courier New"]/dev/raw1394[/FONT] into the group plugdev, which you are a member of already.

```

sudo chgrp plugdev /dev/raw1394

```

---


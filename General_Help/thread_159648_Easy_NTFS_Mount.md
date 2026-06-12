---
title: "Easy NTFS Mount"
date: 2006-04-13
forum: General Help
---

### Post by scotishhaggis on 2006-04-13
hey guys i was had a script before i was given from some 1 on the IRC to auto mount NTFS partions. Cant rember how to do this now. i asked a few times in the IRC and keep getting to an old way to do it which i dont understand just being new to linux any 1 got any ideas?

---

### Post by taurus on 2006-04-13
Assuming your NTFS is on /dev/hda1, open a terminal by clicking Applications -> Accessories -> Terminal and type
```

sudo mkdir /windows
sudo mount -t ntfs /dev/hda1 /windows
df -h 

```

---

### Post by scotishhaggis on 2006-04-13
well i have 2 partions ntfs

---

### Post by justleen on 2006-04-13
try this from [ubuntuguide.org]("http://www.ubuntuguide.org/#automountntfs")

---

### Post by scotishhaggis on 2006-04-13
thats for 5.04 tho

---

### Post by taurus on 2006-04-13
[QUOTE=scotishhaggis]well i have 2 partions ntfs[/QUOTE]
If you tell me where they are (i.e. /dev/hda1, /dev/hda2...), then I can give you specific commands to type or how to modify your /etc/fstab so they would be mounted automatically upon boot...

---

### Post by justleen on 2006-04-13
[QUOTE=scotishhaggis]thats for 5.04 tho[/QUOTE]


that doenst matter.. this is unixversal

---

### Post by dom02 on 2006-04-13
[QUOTE=taurus]If you tell me where they are (i.e. /dev/hda1, /dev/hda2...), then I can give you specific commands to type or how to modify your /etc/fstab so they would be mounted automatically upon boot...[/QUOTE]

I have a similar problem with getting my second partition to mount.  I got the first one and I also got a third hard drive to mount, which is one partition.  But the second partiton on my pimary hard drive won't.  It's should be hda2.  I did everything I did with hda1 except up it in a different folder and changed it to /dev/hda2 instead but it didn't work.  I typed sudo mount /dev/hda2 /media/partition2/ -t ntfs -o umask=0222 and I get an error saying wrong fs type etc...

EDIT: Never mind i'm just dumb.  for some reason the partition was labeled hda5

---


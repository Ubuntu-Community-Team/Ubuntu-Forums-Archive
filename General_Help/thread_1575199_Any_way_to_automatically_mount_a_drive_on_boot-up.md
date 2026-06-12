---
title: "Any way to automatically mount a drive on boot-up?"
date: 2010-09-15
forum: General Help
---

### Post by dom134 on 2010-09-15
Hello, I am a complete newbie when it comes to Linux. I have just installed 10.04 and am enjoying the quick clean boot. I have a dual-boot option as I have come over from XP. Most of my data is still on the old 'c:/' drive and I have to manually mount it every boot-up. Is there any way to automate this process?

Thanks

---

### Post by spiky001 on 2010-09-15
Have you looked in places think it should be there

---

### Post by Joe of loath on 2010-09-15
You'll have to add it to /etc/fstab manually. There's a lot of info around the internet about it, just google 'ntfs fstab' and read through some stuff, copy some examples etc.

---

### Post by prshah on 2010-09-15
> **dom134 said:**
> Most of my data is still on the old 'c:/' drive and I have to manually mount it every boot-up. Is there any way to automate this process?

If you want the partition to be automatically (statically) mounted, you need to add the specific information to the /etc/fstab file. To edit the /etc/fstab file, open a terminal and issue the command```
gksudo gedit /etc/fstab
```

For example, you need to add an entry such as ```
# /dev/sda6
[color=red]UUID=AB707BCE707F8DE8[/color] [color=blue]/media/sda6[/color]     ntfs    [color=green]defaults,auto,umask=007,gid=46[/color] 0       1
```

In the above example (your details will differ), you can find out the correct UUID for your partition (the part in red) using the command```
sudo blkid /dev/sda6
``` (Replace sda6 with the actual partition device ID in your case).

You should also create the mount point (the part in blue)```
sudo mkdir /media/sda6
sudo chown root:plugdev /media/sda6

```

You need to be a member of group "plugdev". It is usually so by default. To check, open a terminal (Applications-Accessories-Terminal) and issue the command```
groups
``` and check if "plugdev" is listed.

Post back if you need more details. A look at your current partition/hdd structure will be helpful; give the following commands from a terminal (Applications-Accessories-Terminal)```
sudo fdisk -l
mount
```

---

### Post by dom134 on 2010-09-15
Thanks PRShah, it worked a treat!
And thanks JoL, when I typed 'ntfs fstab' there was masses of info.

---


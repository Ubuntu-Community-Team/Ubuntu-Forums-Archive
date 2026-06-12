---
title: "Ubuntu displaying too many hardrives"
date: 2010-01-09
forum: General Help
---

### Post by SilverShadow118 on 2010-01-09
I have two hard drives in my compy. One is 500 gb and the other is ~40 gb. I tried to install ubuntu on the 40 gb one because the 500 gb one is starting to die. When I use a live cd to install and partition the harddrive, it shows I have 3: 

[IMG]http://imgur.com/o3qzf.png[/IMG]

/dev/sdb] and /dev/mapper/nvidia_fhidaeja are physically the same drive but appear as two, independent but equal drives.I kinda just ignore it and move on. I install ubuntu and try to boot and I receive an error saying that grub can't be found. I install and repeat two more times and get the same message. I'm thinking the the "extra" drive has something to do with it, but I'm not sure. I've tried reformatting it and resetting bios but nothing seems to work. Any advice?

---

### Post by Jackzor on 2010-01-09
You have formated the 500?

---

### Post by SilverShadow118 on 2010-01-09
The 500 doesn't matter too much but it is formatted. It's the ~40gb one that I'm concerned about because the 500gb one is showing early signs of death.

---

### Post by falconindy on 2010-01-09
Disable your onboard RAID in your BIOS.

---

### Post by SilverShadow118 on 2010-01-09
I did that. I switched it to sata mode and still not luck :/

---

### Post by Jackzor on 2010-01-09
Um. Well I'm new to linux so I would know more about windows...

If you have a windows pc you could try hooking it to the windows machine and format with the cmd prompt

Just use (I think) format d: (If d drive is the 40 gb.)

I had a problem similar  to this before I started using ubuntu. My brother tried to dual boot and used gparted and I had like 12 partitions that didn't exist before. But I formated the whole drive and it fixed it. Now I have a dual boot of windows 7 and ubuntu 9.10

---

### Post by SilverShadow118 on 2010-01-09
That sounds like the best idea so far. I'll go with it and check back in awhile after reinstalling windows. Thanks for the help.

---

### Post by SilverShadow118 on 2010-01-10
Going into windows and reformatting doesn't work :/

---


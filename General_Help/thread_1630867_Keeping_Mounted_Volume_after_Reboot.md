---
title: "Keeping Mounted Volume after Reboot"
date: 2010-11-25
forum: General Help
---

### Post by jpboyrox on 2010-11-25
Okay, I'm a complete newbie, as in, one and a half hours with ubuntu so far. Generally things are going well. I am trying to create a link to my windows xp workgroup where all my data is stored (I was surprised that linux could even see it!) I mounted a volume on the desktop apparently... that worked fine until I rebooted and it had disappeared. it was fairly annoying that I had to go back into the network and re-mount the volume. How can I get it to stay put, even after rebooting? 
I have limited to zero knowledge of linux/ubuntu so you may need to break it down for me. thanks, a lot!

---

### Post by jpboyrox on 2010-11-25
I tried using 'Storage Device Manager' as someone suggested but emmm I didn't understand a word of it. In fact there weren't many words. Only acronyms

---

### Post by jpboyrox on 2010-11-25
I'm going to go to bed but pleeeease do comment. any help would be greatly appreciated. :D

---

### Post by jpboyrox on 2010-11-26
bump?

---

### Post by dino99 on 2010-11-26
into synaptic: look at ntfs-3g and samba

everything is done natively by ubuntu, no worry

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by NikoC on 2010-11-26
Maybe [this]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") is what you are looking for...

Good luck,

NikoC

---

### Post by Morbius1 on 2010-11-26
There's the poor man's way: Connect to the share in Nautilus and then Bookmark it ( Nautilus > Bookmarks > Add Bookmarks )
Shows up like a mapped drive does in Windows. You'll have to click on the bookmark to actually mount it.

Then there's the Gigolo way: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

* Personal Note: After years of doing it the traditional way through fstab I now use gigolo exclusively. It's a remarkable little utility that will browse, mount, automount, and even wait for the remote share to be available before it mounts.*

Then there's the traditional way.

---


---
title: "Removed Ubuntu but still booting in grub"
date: 2011-10-09
forum: General Help
---

### Post by mushroomsatsujin on 2011-10-09
Im new to Ubuntu and installed it on an external drive. Since it was working so well on my macbook and I was having problems with it, I decided to just keep windows on it and play with Ubuntu in a virtual machine

So I got rid of it by formatting the disk.

When I had it duel booted, I got an error that said "No such device: blah blah blah
Grub Rescue>"

Normally a reboot would fix this. Now it only goes to this.

I understand that formatting it probably caused this and there are files on my main disk that are causing it to boot to grub. 

How can I get it back to boot to windows like normal? Right now I can only run off my Ubuntu Live disk, but I can see that all my windows files are still intact.

---

### Post by mikejonesey on 2011-10-09
> **mushroomsatsujin said:**
> Im new to Ubuntu and installed it on an external drive. Since it was working so well on my macbook and I was having problems with it, I decided to just keep windows on it and play with Ubuntu in a virtual machine

So I got rid of it by formatting the disk.

When I had it duel booted, I got an error that said "No such device: blah blah blah
Grub Rescue>"

Normally a reboot would fix this. Now it only goes to this.

I understand that formatting it probably caused this and there are files on my main disk that are causing it to boot to grub. 

How can I get it back to boot to windows like normal? Right now I can only run off my Ubuntu Live disk, but I can see that all my windows files are still intact.

basically you have overwritten the master boot record, to write over this to get it back to windows only you need to use a windows recovery disc, if that is not availible find ms-sys deb pack from thailand or compile and build it from source from source forge.

---

### Post by mushroomsatsujin on 2011-10-09
Worked perfectly. Thank you so much.

---


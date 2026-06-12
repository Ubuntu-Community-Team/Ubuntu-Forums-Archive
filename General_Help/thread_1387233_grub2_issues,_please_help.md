---
title: "grub2 issues, please help"
date: 2010-01-21
forum: General Help
---

### Post by Lorenzo1985 on 2010-01-21
One of my hard drives seems to have died, unfortunately I think i've screwed up grub in the process of trying to repair it.

I'm having issues getting getting a proper menu in grub2, I get a grub prompt but can't get any further than than.

My system is set up as follows

/dev/sda5 is the boot partition 
/dev/sda6 is the root partition

Output of bootinfoscript: [http://pastebin.com/f59fa5b8b]("http://pastebin.com/f59fa5b8b")

I can access a live CD and tried the following:
> 
sudo mkdir /mnt/sda6
sudo mount /dev/sda6 /mnt/sda6
sudo mount --bind /dev /mnt/sda6/dev
sudo mount --bind /proc /mnt/sda6/proc
sudo mount /dev/sda5 /mnt/sda6/boot
sudo chroot /mnt/sda6 /bin/bash

update-grub


Unfortunatly this did not help much, can anyone tell me anything else i can try to try and recover this?

---

### Post by sisco311 on 2010-01-21
At the grub rescue prompt type:
```

insmod ext2
set root=(hd0,5)
linux	/vmlinuz-<hit tab to auto-complete>  root=/dev/sda6  ro quiet splash
initrd	/initrd.img<hit tab to auto-complete>
boot
```

---


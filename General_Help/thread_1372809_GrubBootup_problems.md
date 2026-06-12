---
title: "Grub/Bootup problems"
date: 2010-01-05
forum: General Help
---

### Post by DrFugly on 2010-01-05
OK so I think that I may have sunk myself. I'm using Ubuntu 9.10 Karmic Koala. I recently decided that I needed Grub 2, so I installed it and it worked (yaay). I then went and decided that I had waaaay to many menu entries. So I went and deleted the files in /boot/images (or something, I already forgot) that had anything other than: linux-header-2.31.16-generic-pae in it. I then went and did a: "sudo update-grub" and everything looked peachy. Except now my ubuntu partition doesn't boot up. Instead grub says:

[Linux-bzImage, setup=0x3400, size=0x3b7100]
[Initrd,addr=0x37862000, size=0x78d51e]

Ugh. So I go into recovery mode. Did a "pick broken packages" and then did a "update grub bootloader" then went into "boot normally". Once there I was dropped to my shell, I logged in then tried to start X server with: /etc/init.d/gdm restart

Only to be met with:
restart: Rejected send message, 1 method rules;....

So yeah I think that I dug myself into a hole and deleted the wrong files from the start, any ideas?

---

### Post by lindsay7 on 2010-01-05
You might look at this and see if anything here can help you.

[https://wiki.edubuntu.org/Grub2](https://wiki.edubuntu.org/Grub2)

---


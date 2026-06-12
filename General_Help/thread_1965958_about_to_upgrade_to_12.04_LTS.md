---
title: "about to upgrade to 12.04 LTS"
date: 2012-04-26
forum: General Help
---

### Post by imachavel on 2012-04-26
hope there are no errors. To clarify what I said in irc ubuntu servers earlier, the bad signature problem can probably be fixed by going through the steps in this paste bin:

[http://pastebin.ubuntu.com/947812/](http://pastebin.ubuntu.com/947812/)

however, I've been notified to use sudo -i instead of sudo su, because sudo su will write directly to the cache. Not sure really what this is all about, there are thousands of caches. But for further reading about sudo su, and it's benefits (and cons I suppose), here is a self help read page:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

have not had a single upgrade problem yet, but if I do I'll come re visit this thread from another computer. Thanks to the ubuntu development team for making this possible for me to have a completely free distro upgrade. (Thanks to mg&tl and all the other developers for writing everything and maintaining the kernel, hope you actually helped mg&tl LOL and didn't just muck about addressing iostream instead of finishing a make file :lolflag:)

upgrading now, haven't installed yet. If install does fail it seems there are some trouble shooting steps I can follow:

Ok, i had the exact same problem at least 9-10  times each time i formatted my /home partition and the windows  partition later.What i do every time is this:
  
[LIST=1]
[*]mount the ubuntu live cd and try ubuntu
[*]open terminal
[*]sudo fdisk -l (that gives a list of partition)
[*]sudo mount /dev/sdanumber_0f_disk_you_have_installed_the_ubuntu /mnt for example sudo mount /dev/sda2 /mnt
[/LIST]
  lets say number_0f_disk_you_have_installed_the_ubuntu=X 
  
[LIST=1]
[*]sudo mount /dev/sdaX /mnt/boot
[*]sudo mount --bind /dev /mnt/dev/
[*]sudo chroot /mnt
[*]grub-install /dev/sda
[*]sudo umount /mnt/dev
[*]sudo umount /mnt
[*]sudo reboot
[/LIST]

---


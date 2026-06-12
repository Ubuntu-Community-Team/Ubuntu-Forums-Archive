---
title: "View Bootup Listing"
date: 2010-01-26
forum: General Help
---

### Post by _dino_ on 2010-01-26
Hi experts,

I am Linux novice so please be detailed.  

I am running Ubuntu 9.10 Desktop and logging into Gnome.  I would like to see my bootup sequence as the system is booting up but I dont in Ubuntu 9.10.  Usually in RH or Fedora, when you start up the system the booting sequence will show listing successes or failures as system boots up.  How do I show same in Ubuntu 9.10.

Much Appreciated,
Dino

---

### Post by t4thfavor on 2010-01-26
I used to add some options in my /boot/grub/menu.lst, but it has moved since I last played with it. I know your solution will include adding a nosplash, and removing a quiet from the kernel optione in grub, I just don't know how to do it off hand.

---

### Post by lidex on 2010-01-26
You can get there by editing /etc/default/grub (it's a file) for grub2.

Info here:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

Scroll down to section "Configuring GRUB 2".

---

### Post by t4thfavor on 2010-01-26
I think you would change this line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to 
GRUB_CMDLINE_LINUX_DEFAULT="nosplash"
then follow the instructions at the top of the file.

but if you do this, you could break stuff, so do more research before attempting this.

---


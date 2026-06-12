---
title: "How to remove Windows XP from dual boot?"
date: 2010-02-06
forum: General Help
---

### Post by s3mperfitillidie on 2010-02-06
I want to move from Wubi to the full thing, but i have no removable media devices. >=[

---

### Post by User-007 on 2010-02-06
After you've deleted completely xp, open terminal and run 

```
sudo update-grub
```

That should delete windows xp from the grub..

User 007

---

### Post by s3mperfitillidie on 2010-02-06
> **User-007 said:**
> After you've deleted completely xp, open terminal and run 

```
sudo update-grub
```

That should delete windows xp from the grub..

User 007

How do i even delete xp?

---

### Post by Sylslay on 2010-02-06
In ubuntu 9.04 hash lines (4 lines about winxp) in menu.lst file at /boot/grub

In ubuntu 9.10 there is na menu.lst file.

Just findout how update grub2 configuration,

its grub.cfg file together wit grub2-update or os-update

ps hash = #

---

### Post by s3mperfitillidie on 2010-02-06
> **Sylslay said:**
> In ubuntu 9.04 hash lines (4 lines about winxp) in menu.lst file at /boot/grub

In ubuntu 9.10 there is na menu.lst file.

Just findout how update grub2 configuration,

its grub.cfg file together wit grub2-update or os-update

ps hash = #

Please simply that, im a noob when it comes to ubuntu.

---

### Post by jennifermq on 2010-02-06
The best way I've seen mentioned is to reinstall Ubuntu, when the install gets to the partition section have Ubuntu overwrite Windows (do not have Ubuntu install in a partition separate from Windows). Of course, save anything you want from Windows before doing that, installing Ubuntu like that will wipe everything off the hard drive you're installing it on.

---

### Post by s3mperfitillidie on 2010-02-06
> **jennifermq said:**
> The best way I've seen mentioned is to reinstall Ubuntu, when the install gets to the partition section have Ubuntu overwrite Windows (do not have Ubuntu install in a partition separate from Windows). Of course, save anything you want from Windows before doing that, installing Ubuntu like that will wipe everything off the hard drive you're installing it on.

Yeah, but i have no removable devices, so...

---

### Post by michy99 on 2010-02-06
Do people even read before replying? Before offering advice, you need to realize that the poster

1) Has a Wubi install.

2) Has no removable device.

If you don't understand the consequences of these two things, then your advice will probably do nothing but confuse things.

I think one of these pages will tell you how to do what you want:

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by s3mperfitillidie on 2010-02-06
A helpful post, finally, thanks.

---

### Post by nerdtron on 2010-02-06
You can move your existing Wubi installation to a full Ubuntu installation. This linkcan help: 
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)
Since you already installed Ubuntu via Wubi, I'm not sure if you have a spare partition to transfer it. You can also format other existing partitions and install GRUB in case you want to delete your other OS. Please note that this tool was tested only upto Wubi 8.04. I don't know if it works for the latest releases.

---

### Post by s3mperfitillidie on 2010-02-09
> **nerdtron said:**
> You can move your existing Wubi installation to a full Ubuntu installation. This linkcan help: 
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)
Since you already installed Ubuntu via Wubi, I'm not sure if you have a spare partition to transfer it. You can also format other existing partitions and install GRUB in case you want to delete your other OS. Please note that this tool was tested only upto Wubi 8.04. I don't know if it works for the latest releases.
[http://ubuntuforums.org/showthread.php?t=1402894](http://ubuntuforums.org/showthread.php?t=1402894)

---


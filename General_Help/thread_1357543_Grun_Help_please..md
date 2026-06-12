---
title: "Grun Help please."
date: 2009-12-17
forum: General Help
---

### Post by distortedecho on 2009-12-17
Hi.

After finishing this small weekend project:

[http://ubuntuforums.org/showthread.php?t=1317862](http://ubuntuforums.org/showthread.php?t=1317862)

I now need to tackle Grub.

I no longer have Windows partitions so no longer need a choice on boot. I just want to boot directly into Ubuntu.

How do I do this?

---

### Post by ean5533 on 2009-12-17
> **distortedecho said:**
> Hi.

After finishing this small weekend project:

[http://ubuntuforums.org/showthread.php?t=1317862](http://ubuntuforums.org/showthread.php?t=1317862)

I now need to tackle Grub.

I no longer have Windows partitions so no longer need a choice on boot. I just want to boot directly into Ubuntu.

How do I do this?
Are you running GRUB legacy or Grub 2? You can see what version you have by running

```
grub --version
```

Version 0.97 is legacy, version 1.96+ is Grub2.

If legacy, then edit the file /boot/grub/menu.lst with the following command:

```
sudo gedit /boot/grub/menu.lst
```

Find where it says "timeout XXX" (where XXX is a number) and change it to "timeout 0" (the number zero, not the letter O).

If Grub2, then edit the file /etc/default/grub with the following command:

```
sudo gedit /etc/default/grub
```

And find where it says GRUB_TIMEOUT="XXX" (where XXX is a number) and change it to GRUB_TIMEOUT="0". After saving your changes, run this command:

```
sudo update-grub
```

After you do these steps, reboot and your machine should boot straight to Ubuntu.

---

### Post by northern lights on 2009-12-17
> **ean5533 said:**
> ```
sudo gedit /boot/grub/menu.lst
```
```
sudo gedit /etc/default/grub
```

While I have nothing to add to the GRUB part of the post, please refrain from suggesting opening graphical apps with *sudo*. Use *gksu/kdesu* instead.
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by ean5533 on 2009-12-17
> **northern lights said:**
> While I have nothing to add to the GRUB part of the post, please refrain from suggesting opening graphical apps with *sudo*. Use *gksu/kdesu* instead.
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")
You're correct, my mistake. I get told this every time I sudo a GUI app and I still can't remember to do it. :(

---

### Post by distortedecho on 2009-12-17
Wow, thanks for your help ean5533!

Didn't know about gksu, but was sure to use gksu in place of sudo throughout ean's instructions.

Thanks again. Will reboot shortly to see if it works.

Oh - I also removed the stuff referencing Other OS's and the 2 XP options - just in case. That won't hurt anything, will it?

---

### Post by ean5533 on 2009-12-17
> **distortedecho said:**
> Wow, thanks for your help ean5533!

Didn't know about gksu, but was sure to use gksu in place of sudo throughout ean's instructions.

Thanks again. Will reboot shortly to see if it works.

Oh - I also removed the stuff referencing Other OS's and the 2 XP options - just in case. That won't hurt anything, will it?
If those OS's don't exist anymore, then no it won't hurt anything. If they do exist, then you won't be able to access them anymore until you put those lines back. :)

---


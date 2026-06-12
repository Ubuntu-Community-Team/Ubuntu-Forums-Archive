---
title: "Computer won't boot"
date: 2009-08-28
forum: General Help
---

### Post by Thomson072 on 2009-08-28
Ok, well a few days ago I installed ubuntu onto my laptop to try it out. I decided I didn't like it, so I deleted the partition that had ubuntu on. I figured that would be the easiest way to get rid of ubuntu. Obviosly not :(.

Windows worked fine, until I shut down my laptop. Now when I turn it on I get a black screen saying this:

GRUB loading stage 1.5.

GRUB loading, please wait...
Error 22.

Then it stays there, with no way I can see to get past it.

What can I do?

---

### Post by pmlxuser on 2009-08-28
PLease use the windows disk to do a recovery of MBR

i think it says repair when you boot from the disk 

you should rund a command > FIXMBR (something like that) in command prompt repair

---

### Post by Thomson072 on 2009-08-28
Problem, I don't and never have had the windows disk :(. It came preinstalled, with no disk included. I still have the ubuntu disk though if there is anything I can do with that?

Or am I just going to have to take it to a computer shop?

---

### Post by NoaHall on 2009-08-28
Well, I suppose you could always reinstall Ubuntu, which will repair GRUB, and the do a proper uninstall of Ubuntu (and Grub, if you want.)

---

### Post by pmlxuser on 2009-08-28
> **Thomson072 said:**
> Problem, I don't and never have had the windows disk :(. It came preinstalled, with no disk included. I still have the ubuntu disk though if there is anything I can do with that?


try to borrow from friends you don't need it to be the original.
If you had the skills i would advise that you just reinstall grub, which will probably show you your windows partition and then you would boot from that till you get the windows disk .


You can also use super grub disk found here

[http://en.kioskea.net/faq/sujet-2677-super-grub-disk-live-cd](http://en.kioskea.net/faq/sujet-2677-super-grub-disk-live-cd)

> 

Or am I just going to have to take it to a computer shop?

This is why i switched to Ubuntu. i can just download an image and get my system running.

---

### Post by nikhilk on 2009-08-28
> **Thomson072 said:**
> Problem, I don't and never have had the windows disk :(. It came preinstalled, with no disk included. I still have the ubuntu disk though if there is anything I can do with that?

You can reinstall GRUB instead of using the Windows bootloader.

[Here]("http://ubuntuforums.org/showthread.php?t=224351") the instructions on re-installing GRUB.

---

### Post by Thomson072 on 2009-08-28
> **NoaHall said:**
> Well, I suppose you could always reinstall Ubuntu, which will repair GRUB, and the do a proper uninstall of Ubuntu (and Grub, if you want.)

Done that, and now things are working well enough :).

Now how would I go about doing a proper uninstall? Is it possible without the windows disk?

Reading around it looks like it's probably not. I don't particularly mind that much now Ubuntu is just sitting there taking up 2GB of hard drive space, but it would be more convenient if I didn't have to choose between them every time...

Btw, thanks for the help everyone who has replied :)

---


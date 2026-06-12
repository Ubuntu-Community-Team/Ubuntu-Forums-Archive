---
title: "How can edit Grub"
date: 2009-07-18
forum: General Help
---

### Post by sunseeker888 on 2009-07-18
Hi Chaps

I am having too many updates in menu. HOw can I edit grub to remove the previous version?


I do not know the command.


Thanks in advance

---

### Post by robert3242 on 2009-07-18
I think you need to be a little clearer insofar was what you mean by 'previous version'. Do you mean that your Ubuntu system has two different kernels installed and these both show up in your GRUB menu? Or do you mean that you have more than one operating system on your computer and you want to remove one from GRUB?

Try to be as clear as you can in telling the folks here what is going on, and someone will be able to help you. The good news is, either way, it will probably be a pretty easy solution.

---

### Post by TuckLive on 2009-07-18
If you mean when you first boot your computer you get a list of kernels to load then you can edit your list in /boot/grub/menu.lst

---

### Post by Risoh on 2009-07-18
Try KGRUBEditor if you prefer GUI. It is KDE application, but it will work fine in Gnome as well.

---

### Post by TheNosh on 2009-07-18
> **Risoh said:**
> Try KGRUBEditor if you prefer GUI. It is KDE application, but it will work fine in Gnome as well.

+1

and it lets you easily add a background to grub if you like.

---

### Post by ramnarayan on 2009-07-18
> **TuckLive said:**
> If you mean when you first boot your computer you get a list of kernels to load then you can edit your list in /boot/grub/menu.lst



Don't mess around too much, make sure you know what you want to edit out.

Preferably make a copy of the menu.lst before fiddling so that you know what happens. 

**
You can do this to edit
```
sudo gedit /boot/grub/menu.lst
```

Once you get into menu.lst navigate to the entries you want removed - either delete them or if you want to play safe put a # in front of them. The latter keeps them hidden.

---

### Post by sunseeker888 on 2009-07-18
Thanks a lot chaps. Sorry I meant kernel versions. Anyway the menu.lst has been edited now


Have a wicked weekend all

---

### Post by Risoh on 2009-07-19
btw here is complete How to:
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

---


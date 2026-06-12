---
title: "Grub 2 question"
date: 2009-11-10
forum: General Help
---

### Post by Amgad elsaiegh on 2009-11-10
i need to remove all these options in the photo below except 1&2
how can i do that in GRUB 2
i used to do it in grub 1 using the startup manager but now it do not work correctly :(
[IMG]http://i35.tinypic.com/v2rd6a.jpg[/IMG]

---

### Post by winotree on 2009-11-10
I'd think that Synaptic Package Manager would do a real fine job of removing those, but if you like to get a second opinion...

---

### Post by ranch hand on 2009-11-10
As winotree has said, why do you not remove the 2 extra kernels?

This would, after running "sudo update-grub" remove all you want to remove except the first recovery entry.

You could also make a custom entry file and that would have only what you want and, if you use the right type of entry for Ubuntu, never need updating.

Please see my sig for link.  Some info there and more in the links it has, particularly the 1st 3.

---

### Post by Amgad elsaiegh on 2009-11-11
**winotree**
> I'd think that Synaptic Package Manager would do a real fine job of removing those, but if you like to get a second opinion...

How??

**ranch hand**
how to remove the extra kernels??

---

### Post by Amgad elsaiegh on 2009-11-11
no more answers yet ? :(

---

### Post by ottosykora on 2009-11-11
well go in synaptic to the base and there areth kernels, then select one you wish to uninstall and proceed as with any other software.

I had some which were not listed in the repository any more, those I simply deleted from the /boot folder.

---

### Post by psycho5 on 2009-11-11
Just search for that kernel 2.6.31-14 in synaptic package manager and then uncheck it, remove completely. 

then you just type sudo update-grub in terminal.

---

### Post by abhilashm86 on 2009-11-11
if you just want to remove from screen, not deleting  them, then open file which contains boot information,
```
sudo gedit /boot/grub/menu.lst

```

delete lines which you don't want, save and quit, you can manage time and others also........

---

### Post by ranch hand on 2009-11-11
> **abhilashm86 said:**
> if you just want to remove from screen, not deleting  them, then open file which contains boot information,
```
sudo gedit /boot/grub/menu.lst

```delete lines which you don't want, save and quit, you can manage time and others also........
This will not work with grub2.

---

### Post by Amgad elsaiegh on 2009-11-11
Thanks alot guys :) ,problem solved by serching for the old kernels in synaptic package manager & removing them then setting the default booting OS throw **gksudo gedit /etc/default/grub**,eventually running **sudo update-grub** in terminal

** i hope there will be a gui software for customizing GRUB 2 soon

---

### Post by ranch hand on 2009-11-11
Yes, there are a lot of people that feel exactly like you do.  I am sure there will be in time.

SUM is already more compatible.  I would give it some more time and it will work fine.

---


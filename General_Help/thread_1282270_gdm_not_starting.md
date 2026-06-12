---
title: "gdm not starting"
date: 2009-10-04
forum: General Help
---

### Post by deovrat on 2009-10-04
Hi,
    I was trying to change the splash screen of ubuntu.For changing the splash screen i installed splashy,then did the change in /boot/grub/menu.lst to include vga=791.I also did some update initrd(i don't remember exactly read it from a blog).But after doing that there were errors coming,something like splashy:connection failed (i don't remember exactly).So,I decided to remove splashy and get back to usplash.After installing usplash and restarting,gdm is not starting.

Also when i log into terminal i get many errors saying :-
bash: /dev/null : permission denied.

also if i am trying to do any other operation it is always giving some permission error,it seems as if the whole file system has become readonly.

When i tried to revert the change i did in menu.lst(logged in as root),it is not getting saved.System is saying that it is a read only file.

On boot , it is showing this error many times :-
return:24:Illegal number : starting

I am a ubuntu newbie,please help me out.

Thanks

---


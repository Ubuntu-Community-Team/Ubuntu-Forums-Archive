---
title: "Need a new graphical grub"
date: 2011-07-26
forum: General Help
---

### Post by twilightmann on 2011-07-26
My old grub just suddenly died without warning
but after much googling I havnt managed to fix it but I have managed to boot into linux (If you can call initramfs Linux) by entering commands like this
set root=(hd0,msdos4)
    linux /vmlinuz-2.6.38-10-generic
    initrd /boot/initrd.img-2.6.38-10-generic
    boot
but then I end up somewhere called initramfs and I don't know what to do
I did have a graphical boot to kubuntu but now I have nothing

---

### Post by Bucky Ball on 2011-07-26
Welcome. When you are booted into Ubuntu try, in a terminal;

```
sudo update-grub
```If that doesn't work, install this and run it:

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

Choose 'Install grub to MBR' option.

---

### Post by twilightmann on 2011-07-26
Thanks Bucky Ball for your reply but unfortunately there was no joy because the application no longer is available through sudo apt-get install boot-repair-ubuntu 
but thanks anyway

---

### Post by Bucky Ball on 2011-07-26
Yes it is. I'm working on my desktop which haven't used for an age and just installed and ran it. 

You have to follow the instructions on that page ... !!!

Open a terminal and type these three commands one at a time:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair-ubuntu
```Then locate boot repair in System>Admin. This info was right there on the link I posted. ;)

---

### Post by pAsM on 2011-07-26
Hello,
[INDENT]Why dont you try to install Berg in place of Grub, I am quite impressed with it
[/INDENT]

---

### Post by ddastoor on 2011-07-26
> set root=(hd0,msdos4)
linux /vmlinuz-2.6.38-10-generic
initrd /boot/initrd.img-2.6.38-10-generic
boot


From the OP, doesn't it look that you already are in th grub command line ?

when u boot, how do u get this far ? looks like u managed into grub..
when there, i believe there's a configfile option that helps u set the configfile to grub.cfg or menu.lst which has the correct and full optionsto boot into ubuntu?

---

### Post by twilightmann on 2011-07-27
Thanks Bucky Ball you are right but I keep on getting errors whilst using the software for example I don't know what to do when the terminal says for the 100th time apt-get command not found
Thanks PaSm I think I might just try this Burg if I can't get grub working

---

### Post by Bucky Ball on 2011-07-28
What happens when you open Update Manager and try that way? If that successfully updates you will find Boot-Repair in Synaptic Package Manager and can install it from there. I would stick with Grub for the moment. ;)

---

### Post by twilightmann on 2011-07-30
Problem solved
Re installed ubuntu

---


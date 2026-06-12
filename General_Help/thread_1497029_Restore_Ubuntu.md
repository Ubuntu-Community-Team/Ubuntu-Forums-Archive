---
title: "Restore Ubuntu"
date: 2010-05-30
forum: General Help
---

### Post by Nipuna on 2010-05-30
I am Still using Ubuntu 9.10 and I have Ubuntu 10.04 but I didn't  install Ubuntu 10.04. My Problem is this,

I tried to Configure  Xorg.conf file after that I can't log into Ubuntu. No GUI is coming Only  this is coming

" Log into nipuna@desktop: "

How to  Restore Ubuntu to Get back to normal?

Thanks

---

### Post by windfix on 2010-05-30
It's always smart to copy your old configuration file to a new name in case you need to restore it.  This would be something like 

cp /etc/X11/xorg.conf /etc/X11/xorg.bak

You could then do the reverse if you need to restore the original.  Assuming you didn't actually create a backup, you can edit xorg.conf from the command line and try to undo your changes.  Log in at that prompt with your username and password.  Then do:

sudo nano /etc/X11/xorg.conf

You'll give it your password for "root" editing access and be dropped into the nano text editor.  Once you make your changes, do CTRL-O to write the new file and CTRL-X to exit nano. Reboot.

---

### Post by BoneKracker on 2010-05-30
If you can't get it working by editing it, you could save the file under something like xorg.conf.old so you can refer to it later
```
sudo mv xorg.conf xorg.conf.old
```
and then generate a default xorg.conf that will hopefully work
```
sudo Xorg -configure
sudo mv xorg.conf.new xorg.conf

```

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

### Post by Jakiejake on 2010-05-30
Try:
> Ctrl + Alt + F7
Does That Help?

---

### Post by Nipuna on 2010-05-30
thanks

I'll Try then tell you all.

Thanks

---


---
title: "Change order of OS at Bootup"
date: 2006-02-25
forum: General Help
---

### Post by Monamogolo on 2006-02-25
Yesterday, I took the exciting leap of faith, and installed Ubuntu on a machine that already had Windows XP up and running. To my surprise everything except the internet connection went perfectly. 

So now I have both Ubuntu and Windows XP on my machine. As I am the only one of several users of the machine who is interested in Linux, I would like to be able to change the listing of OS alternatives, so that the default is Windows instead of Linux.

How do I do this? 

The other users are totally uninterested in having to wait for the list, and then within 10 seconds scroll down to Windows. They will be totally intimidated if the system rolls on into Ubuntu - they are the type who are terrified of turning the OFF button if something goes wrong and I'm not around to rescue them. But I'm no computer whizz myself. So getting this bootup list right is important in our particular context. Any help in simple english would be appreciated.

Mona

---

### Post by Koybe on 2006-02-25
Edit your grub config file.
```
sudo gedit /etc/grub/menu.lst
```

Change the line 
```
default 0
```
to the number of the line were windows appears at boot starting your count at zero.

---

### Post by captainstormy on 2006-02-25
edit the menu.list file.  

Open a terminal and type "sudo nautilus".  Then put in your password.  Navigate to /boot/grub

make a copy of the current menu file before doing anything else.

Heres what my file looks like for a reverance:
> 
title		Ubuntu
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1


make sure you have the paths right of course, but you get the idea of how things should look.  Ubuntu is my defualt, with windows the second option.  That should give you a good idea of how things are suppose to look, you should be able able to figure out what they should look like to have them boot the way you want.

---

### Post by aysiu on 2006-02-25
This is a handy reference:
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---


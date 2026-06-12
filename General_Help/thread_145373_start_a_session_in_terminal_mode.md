---
title: "start a session in terminal mode ?"
date: 2006-03-16
forum: General Help
---

### Post by tioneb on 2006-03-16
Hi,

I thought that it was in inittab, that we choose whether or not to start the X server.But I didn't find it out.

I'd need to start some sessions without X server, just in the terminal mode, how to do that ?

---

### Post by Titus A Duxass on 2006-03-16
There's an option at the log in screen to go text mode. It's a submenu from one of the three buttons.

---

### Post by Sutekh on 2006-03-16
Yup its in /etc/inittab.  Ubuntu uses ```
# The default runlevel.
id:2:initdefault:

```I *think* if you change this to 3 you get to a command line.  There may have been more tweaking though.

How about using one of the virtual consoles?  Ctrl + Alt + F1 to F6.  

Then Ctrl + Alt + F7 to get back to X.  You won't even need to stop your X session either.

---

### Post by tioneb on 2006-03-16
Thanks both I knew both ways to get the command line, but I'd like to go directly on the boot, like in the recovery mode. I think the inittab is the place where to look to tweak it :)

---

### Post by Ivan Matveich on 2006-03-16
update-rc.d -f gdm remove

---

### Post by tioneb on 2006-03-17
So the clean way is to change the
/etc/rc[COLOR="red"]?[/COLOR].d/S13gdm
for instance we can make a 
```
mv /etc/rc[COLOR="red"]?[/COLOR].d/S13gdm /etc/rc[COLOR="Red"]?[/COLOR].d/K13gdm 
``` then gdm isn't launched so we stay in the terminal mode and a start gdm will launch the WM

you choose the '[COLOR="red"]?[/COLOR]' in the folder rc[COLOR="red"]?[/COLOR]d and you change it into the boot/grub/menu.list
## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-18-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-18-386 root=/dev/hda1 [COLOR="Red"]?[/COLOR]  ro quiet splash
initrd          /boot/initrd.img-2.6.15-18-386
savedefault
boot

so you can tweak your boot :)

---


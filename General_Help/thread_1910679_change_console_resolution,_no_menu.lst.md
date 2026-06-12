---
title: "change console resolution, no menu.lst"
date: 2012-01-17
forum: General Help
---

### Post by TomZzz on 2012-01-17
I am trying to follow instructions to change my console resolution on 64 bit server 10.04. Various places tell me to edit /boot/grub/menu.lst but that file does not exist on my installation.
 
What now?
 
Thanks
TomZ

---

### Post by TeoBigusGeekus on 2012-01-17
The menu.lst file was used with grub legacy.
Ubuntu uses grub2 nowadays.
See [this]("https://help.ubuntu.com/community/Grub2#Resolution_Settings").

---

### Post by imachavel on 2012-01-17
for me:

cd /edit
bash: cd: /edit: No such file or directory
@-Dimension-4700:~$ sudo su
[sudo] password for : 
root@-Dimension-4700:/home/danel# cd /boot
root@-Dimension-4700:/boot# cd /grub
bash: cd: /grub: No such file or directory
root@-Dimension-4700:/boot# cd grub
root@-Dimension-4700:/boot/grub# cd menu.lst
bash: cd: menu.lst: No such file or directory
root@-Dimension-4700:/boot/grub# menu.lst
menu.lst: command not found
root@-Dimension-4700:/boot/grub# edit menu.lst
Warning: unknown mime-type for "menu.lst" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"

well I know very little about the terminal command line. Hell it's more involved then windows cmd, at least mostly. Well have you given this a shot:

[http://beginlinux.com/desktop_training/ubuntuhardyheron_cat/992-hardyheronresolution](http://beginlinux.com/desktop_training/ubuntuhardyheron_cat/992-hardyheronresolution)

Otherwise I just wouldn't know never had the screen resolution problem. What about system settings>displays then change it? That a bad idea??

---

### Post by JRV on 2012-01-17
If it is the text size in the grub menu that you are trying to change try this:
```

gksudo gedit /etc/default/grub

```

Remove the "#" from the line that says "#GRUB_GFXMODE=640x480".

You can change the resolution from 640x480 to something else if desired.

Then do a:
```

sudo update-grub

```

---

### Post by TomZzz on 2012-01-18
What I really wanted to do was add more lines to the Window, should have said that in the original question.

Z

---


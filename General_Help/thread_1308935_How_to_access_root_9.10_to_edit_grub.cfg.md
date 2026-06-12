---
title: "How to access root 9.10 to edit grub.cfg"
date: 2009-11-01
forum: General Help
---

### Post by dougggg on 2009-11-01
I just did an install and need to edit the boot menu but the normal command

sudo gedit /boot/grub/grub.cfg

doesnt work it ask ofr my password and pulls up the editor but wont let me save,  It worked with 9.04.   I get an error: 

You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again.

did something go wrong on the install or ...?

Thanks

---

### Post by ikacer on 2009-11-01
I don't think you are supposed to edit that file. I found a thread explaining it here:
[http://ubuntuforums.org/showthread.php?t=1278577]("http://ubuntuforums.org/showthread.php?t=1278577")

post #3 and #4 in the thread seems most useful.

---

### Post by dougggg on 2009-11-01
why does ubuntu seem to get harder as I go.   I need to add 
'vmalloc=512m' to the boot entry becuase I have a haupage tv card and my nvidia card needs that to work or it wont boot.  I can do it every time at boot with the e command but thats a pain.  I looked at the files in grub.d,  can somebody point me in the right direction to put the vmalloc=512m

---

### Post by retrow on 2009-11-01
I had problem saving it with gedit too. Instead of using gedit, I used nano - 

```
sudo nano /boot/grub/grub.cfg
```
Its a text editor which is very similar to old school DOS editor.

Change the lines for config file within nano and then to save, its Ctrl-X --> Hit Y to save changes, and Enter to save it as the same filename.

Why it let me save changes with nano and blocked me out when using gedit is beyond the scope of my understanding. I just know that nano worked for me.

Also I have no clue where the vmalloc statement is supposed to go.

---

### Post by lavinog on 2009-11-01
does this work:
```

gksudo gedit /boot/grub/grub.cfg

```

---

### Post by kerry_s on 2009-11-01
in grub2 it's /etc/default/grub

**gksudo gedit /etc/default/grub**

on line #9:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **vmalloc=512m**"

then save & run "**sudo update-grub**"

---

### Post by GogglesnTeeth on 2009-11-02
This worked perfectly!!!!
Thank you!

Sucks being a noob!

---

### Post by dougggg on 2009-11-03
Yep that did it. Thanks

---


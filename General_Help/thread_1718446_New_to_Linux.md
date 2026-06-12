---
title: "New to Linux"
date: 2011-03-31
forum: General Help
---

### Post by thomas515 on 2011-03-31
Im new to Linux and just installed Ubuntu 10.10.  I want to get a feel for command line first and was wondering how I would go about setting it to boot to the command line not gnome and then how do I start gnome from there if I wanted to use it.  Thanks for any help y'all might have

---

### Post by matt_symes on 2011-03-31
Hi

Welcome to the forums.

From the grub menu select the kernel you want to boot. Press **e** to edit the command line. Look for the line that says something like (your kernel may be different)

```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=3d48429c-7361-4ab8-8689-54407673b141 ro quiet splash
```

and change to (notice the word text at the end and the removal of other words)

```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=3d48429c-7361-4ab8-8689-54407673b141 ro **text**
```

Press ctrl + x to boot. That will boot into multi-user text mode where you can play.

To start x then type 

```
sudo service gdm start
``` 

if you want gdm or

```
startx
```

to start X.

To make this permanent you will need to edit grub.

You can just use a terminal as oppose to the console though.

Kind regards

---

### Post by thomas515 on 2011-03-31
Thanks very much.  how do I access the grub menu?

---

### Post by matt_symes on 2011-03-31
Hi

> **thomas515 said:**
> Thanks very much.  how do I access the grub menu?

I should have asked; have you installed to a partition or are you using Wubi ?

Press the shift key to access the grub menu from a partition install at boot up. Not sure from Wubi. Never used it.

Kind regards

---

### Post by thomas515 on 2011-03-31
I guess it would be a partition install.  Ive got it installed on an external HD.

---

### Post by matt_symes on 2011-03-31
Hi

> **thomas515 said:**
> I guess it would be a partition install.  Ive got it installed on an external HD.

Try pressing the shift key,  and keep it pressed, when the computer first boots.

If not i can talk you through editing and rebuilding grub.

Kind regards

---

### Post by thomas515 on 2011-03-31
thanks a lot

---

### Post by thomas515 on 2011-03-31
That worked but it didn't save the setting.  When i rebooted, it went straight the the GUI.  How do I set it to always boot to command line?

---

### Post by matt_symes on 2011-03-31
Hi

> **thomas515 said:**
> That worked but it didn't save the setting.  When i rebooted, it went straight the the GUI.  How do I set it to always boot to command line?

Yes, that was temporary just to make sure you were sure :D

As i said, if you want to make that permanent you need to edit and rebuild grub.

Open a terminal and type

```
sudo nano /etc/default/grub
```

Enter your password. It will not be echoed to the screen. This is normal.

Look for the line that says 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and change to

```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```

Press ctrl + o to save and ctrl+ x to exit.

then type 

```
sudo update-grub
```

when it has finished type

```
sudo shutdown -r now
```

to reboot.

If that works, please mark this thread as solved.

Kind regards

---

### Post by thomas515 on 2011-03-31
Yeah I saw that after I posted it.  Thanks a lot for the help.  It works fine.  Any suggestions for resources for learning Ubuntu (or Linux in general) command line?

---

### Post by matt_symes on 2011-03-31
Hi

For bash shell scripting read this _first_

[http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)

It's a great site recommended by Sisco and he knows his scripting. Having read it myself, i can say it's a good introduction.

For general bash commands just Google or read the man pages.

Kind regards

---

### Post by thomas515 on 2011-03-31
Cool.  Thanks again for all the help.

---

### Post by nothingspecial on 2011-03-31
> **matt_symes said:**
> Hi

For bash shell scripting read this _first_

[http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)

It's a great site recommended by Sisco 

:-\"

And to add
[http://wiki.bash-hackers.org/start](http://wiki.bash-hackers.org/start)
[http://sunsite.ualberta.ca/Documentation/Gnu/screen-3.9.4/html_chapter/screen_toc.html](http://sunsite.ualberta.ca/Documentation/Gnu/screen-3.9.4/html_chapter/screen_toc.html)
[http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml)
[http://regexlib.com/CheatSheet.aspx](http://regexlib.com/CheatSheet.aspx)
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

### Post by matt_symes on 2011-03-31
Hi

> **nothingspecial said:**
> :-\"

And to add
[http://wiki.bash-hackers.org/start](http://wiki.bash-hackers.org/start)
[http://sunsite.ualberta.ca/Documentation/Gnu/screen-3.9.4/html_chapter/screen_toc.html](http://sunsite.ualberta.ca/Documentation/Gnu/screen-3.9.4/html_chapter/screen_toc.html)
[http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml)
[http://regexlib.com/CheatSheet.aspx](http://regexlib.com/CheatSheet.aspx)
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

Nice :popcorn:

Kind regards

---


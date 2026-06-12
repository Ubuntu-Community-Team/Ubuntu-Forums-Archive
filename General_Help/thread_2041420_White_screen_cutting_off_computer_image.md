---
title: "White screen cutting off computer image"
date: 2012-08-12
forum: General Help
---

### Post by GleebleGlorb on 2012-08-12
Hello, all!
I'm new to Linux, having started only a few days ago. I finished downloading all the updates out since Ubuntu 12.04, which is the Linux distro I use. And everything was going great!
Until this happened.

[IMG]http://i1146.photobucket.com/albums/o539/Diego_Velez_Davila/d349218e.png[/IMG]

Hmm... I'm not sure if you can see clearly, since I'm doing this with less than half a screen, but there's a huge section of white covering up my screen, running from the bottom, to the right, which is much thicker.

I don't think it's a problem with the screen itself, since, when I boot up and need to log in, it isn't there. It just sort of flickers in AFTER I log into my Gnome Shell account.

Any help would be greatly appreciated. :)

---

### Post by flipper T on 2012-08-12
i had something similar months ago, & for the life of me, cannot remember what it was ! sorry.

however, it was an error pop up of some sort, with background & text in white & therefore unreadable. however, if you tried to mark up the text using your mouse, in the same way you mark up text in a document or web site, the text became readable / copyable / paste-able in ubuntu forums-able. :)

give it a go. if works, paste text here or google search it.

ps have you been trying to set up a dual monitor ? think mine was caused by that. if so, i know the answer :)

---

### Post by GleebleGlorb on 2012-08-12
Tried copying anything that might be present, hidden in the white. Nothing. Seems to just be empty space occupying my monitor.

I sincerely doubt I've been trying to set up a dual monitor, since I haven't the slightest idea of what that is.  :confused:

---

### Post by flipper T on 2012-08-12
ok, open a terminal (ctrl alt t)

and type this in

```
sudo remove /etc/X11/xorg.conf
```

enter your password when prompted.

reboot

ps does this only happen in gnome shell? how about unity? does it only happen on your primary desktop, does it happen on your other desktops?

---

### Post by GleebleGlorb on 2012-08-12
"No such file or directory."
Used the terminal to check myself and there was no xorg.config file.

Went to check just that a minute before and Unity works fine. Seems to be just the Gnome shell.
Guess I could just use Unity...

---

### Post by flipper T on 2012-08-12
ok back in terminal, try


```
sudo apt-get remove gnome-shell-extensions-*
```


then


```
DISPLAY=:0 gnome-shell --replace &
```

---

### Post by GleebleGlorb on 2012-08-12
Huh... Well, I did what you told me, and it seemed to work for a few minutes before coming back.
In the end, though, I ran through the process of installing the Gnome Shell again, and it cleared it up. :D

Thank you very much for your help, though. :)

---


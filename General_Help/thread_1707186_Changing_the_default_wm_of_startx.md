---
title: "Changing the default wm of startx"
date: 2011-03-15
forum: General Help
---

### Post by KeiNivky on 2011-03-15
I'll use i3-wm, just want to know how can I start it instead of gnome using startx.

By the way, where can I get detailed info on X? I am a little confused, don't really understand what startx really starts, what X is and what does it do, how to config... This kind of thing.

---

### Post by wojox on 2011-03-15
When you start and get to GDM click on your user name, or enter it, then at the bottom panel you should see a 'sessions' tab click it and choose i3-wm.

As for startx it starts the x-server and what ever is in your ~/.xinitrc file

---

### Post by KeiNivky on 2011-03-16
Thanks, I was able to do it.

But something is troubling me. The default xinitrc file located in /etc/X11/ didn't had any reference to gnome. How come it was the default environment to be loaded?

---

### Post by lithopsian on 2011-03-16
Gnome starts X, not the other way around.  There is a script called gdm which does a few "gnome"-ey things and then kicks off X, the does some more "gnome"-ey things.

You can get rid of gdm but then you'll have to start X some other way, usually with startx.

---

### Post by KeiNivky on 2011-03-16
> **lithopsian said:**
> Gnome starts X, not the other way around.  There is a script called gdm which does a few "gnome"-ey things and then kicks off X, the does some more "gnome"-ey things.

You can get rid of gdm but then you'll have to start X some other way, usually with startx.

I already took care of gdm, but in a awkward way. I appended ".bkp" to the files gdm and gdm.conf. Before that I tried using the command 

```
update-rc.d -f gdm remove
```

But gnome restarted the same after the boot.

Is there a "most correct" method than mine?

---

### Post by Krytarik on 2011-03-16
First, please revert your changes! Then, if you really want to boot into the command line instead of GDM, follow this guide:
[http://ubuntuforums.org/showthread.php?p=9644518](http://ubuntuforums.org/showthread.php?p=9644518)

Btw.: You have to differentiate between "Gnome" and "GDM". In fact Gnome is run *after* X. When you run GDM, it starts X, then when you choose Gnome at the login screen and login, GDM starts a X window session with Gnome.

---

### Post by KeiNivky on 2011-03-16
Thanks!

But I have another problem now... If I run i3 directly, there's no sound. If I run gdm first, then the sound works.
It seems that gdm configure some things before loading the X environment. Is there a way of knowing that so I can put it in my .xinitrc file?

---

### Post by wojox on 2011-03-16
> **KeiNivky said:**
> Thanks!

But I have another problem now... If I run i3 directly, there's no sound. If I run gdm first, then the sound works.
It seems that gdm configure some things before loading the X environment. Is there a way of knowing that so I can put it in my .xinitrc file?

Add this to .xinitrc. It will log errors.

```
exec i3 -V >>~/.i3/i3log >&1
```

---

### Post by KeiNivky on 2011-03-17
More problems...

I tried that. In the first two tries it complained about the "&". In  the third it runned, but went to a black screen. And now I can't enter  i3 via startx, to do so I must run gdm first and select it there.

When I run startx, it goes to a black screen and stays there... The only  way the get out is to type ctrl+alt+f1. Way back to the terminal a  message is popping periodically, on and on, "No protocol specified". 
After that if I run startx again I get 
"xauth: error in locking authority file /home/fkei/.Xauthority"


By the way, it didn't put info on the i3log file.

I have no idea why this started to happen. I already reinstalled i3 and  also deleted my i3 config file to check if it's an error of it...
I left only the line "exec i3" and still doesn't work

---

### Post by sisco311 on 2011-03-17
Try this in ~/.xinitrc:
```
exec ck-launch-session dbus-launch ---sh-syntax -exit-with-session i3
```

---

### Post by KeiNivky on 2011-03-17
@sisco311

I Tried that. It clears the window, but don't start X, and prompt some things, then it goes back to the original place. It happens really fast, running several times I could see that the prompts are, in this order, about fsck, my partitions, init and firefox. Back in the terminal there are some things written about Xorg, but none is error (I guess). In the end there's this "waiting for X server to shut down(...)".

Should I look for something in the xorg log?

---


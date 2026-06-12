---
title: "Trying to get rid of GUI"
date: 2011-05-08
forum: General Help
---

### Post by smmurf on 2011-05-08
I've just installed Ubuntu 11.04 and now want to disable any GUI by default but leave possibility to start it sometimes if necessary.

So I've already tried to disable it with update-rc.d and had no success (I haven't been using linux for a while, so a lot of things are different now). Then I tried to rename gdm.conf, but then I lost possibility to start gdm manually. Editing gdm.conf runlevels list has no effect.

I really don't need GDM, so startx is enough, but then unity and wifi doesn't work (only at a glance, maybe there is something else).

Is there any way to get full functional GUI and disabled GDM startup?

---

### Post by sisco311 on 2011-05-08
You can disable gdm with a .override file:
```
echo manual | sudo tee -a /etc/init/gdm.override
```

See:
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)
[http://upstart.ubuntu.com/cookbook/#...untu-transient](http://upstart.ubuntu.com/cookbook/#...untu-transient)
and
[http://upstart.at/2011/03/11/overrid...-ubuntu-natty/](http://upstart.at/2011/03/11/overrid...-ubuntu-natty/)

---

### Post by smmurf on 2011-05-08
Thank you! Looks like that's it!
Now reading upstart cookbook :)

But some questions remain :(
When system starts up, I see black screen. It is because all text consoles are on tty[1-6], and the 7th is active. How it can be changed to set tty1 to be active at startup?

---

### Post by sisco311 on 2011-05-09
> **smmurf said:**
> 
When system starts up, I see black screen. It is because all text consoles are on tty[1-6], and the 7th is active. How it can be changed to set tty1 to be active at startup?

It's because the splash screen... Try to disable it.

Edit the **/etc/default/grub** file and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with GRUB_CMDLINE_LINUX_DEFAULT="quiet". Then generate a new Grub2 config file:
```
sudo update-grub
```

---

### Post by smmurf on 2011-05-09
Great, that solved the problem.
Thank you :)

Now almost everything works as I want, but if there are some additional questions I think I have to ask them in separate thread.

Thank you again.

---

### Post by nothingspecial on 2011-05-09
> **smmurf said:**
>  wifi doesn't work 

I suggest installing wicd-curses

network-manager starts when Gnome does.

wicd starts at boot

wicd-curses is a nice ncurses interface for configuring it.

---

### Post by smmurf on 2011-05-09
nothingspecial, thanks, that had to be my next question :)

But I have problems with that now. When I try to connect with wicd-curses I get message "validating authentication" and then "not connected". Passphrase is correct, because after all I can connect when Gnome is running using the same passphrase.

I see no way to debug it or see a log.

Or it's better to create special topic for that?

Also if I try to run wicd directly, I get message "rename failed" and wicd quits, what does it mean?

---

### Post by nothingspecial on 2011-05-09
wicd and network-manager conflict

I'm not sure if this is your problem because it is a while since I've used network-manager.

Back in the day, installing wicd removed network-manager and vice-versa bur I have a feeling that is not the case any more.

I usually install minimal and build up so I cannot help you for sure, but......

First try  ```
sudo service network-manager stop
```

Then try launching wicd-curses again.

If your wireless works there should be no reason why wicd wouldn't work if network-manager does.

---


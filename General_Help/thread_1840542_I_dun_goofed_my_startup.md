---
title: "I dun goofed my startup"
date: 2011-09-07
forum: General Help
---

### Post by WikedX on 2011-09-07
I tried setting up xubuntu so that it didnt run with a gui at first. Since I mostly use emacs on this, I wanted to have to manually start up xfce

Anyway here is what I did
sudo update-rc.d -f gdm remove
echo "false" | sudo tee /etc/X11/default-display-manager

So now when I try loading xubuntu it hangs on the "xubuntu loading screen". Its not showing the pretty one either, its showing the text one with the 4 dots under it.

I was able to log into the recovery console though, and start GDM manually to get where I am right now(posting this message). I'm trying to repair my start up. I tried this
sudo update-rc.d gdm defaults 30 01
echo "/usr/bin/gdm" | sudo tee /etc/X11/default-display-manager

but nope, not workin. 

Any ideas?

---

### Post by WikedX on 2011-09-07
EVERY SINGLE TIME I make a post here I fix it myself within 5 seconds

The answer was I had to make it:
/usr/sbin/gdm

Notice the sbin. I had it as just bin before.

Whatever I guess.

But now to ask the question: how do I boot without the gui? The method I tried, as I said, simply broke xubuntus startup

---

### Post by Toz on 2011-09-07
You didn't mention which version of xubuntu you are using. Maybe this would work? [http://www.thecoderanger.com/disable-gdm-at-system-boot-ubuntu-10-10-maverick/]("http://www.thecoderanger.com/disable-gdm-at-system-boot-ubuntu-10-10-maverick/")

---

### Post by Habitual on 2011-09-08
> **WikedX said:**
> EVERY SINGLE TIME I make a post here I fix it myself within 5 seconds

The answer was I had to make it:
/usr/sbin/gdm

Notice the sbin. I had it as just bin before.

Whatever I guess.

But now to ask the question: how do I boot without the gui? The method I tried, as I said, simply broke xubuntus startup

[http://www.linuxquestions.org/questions/linux-newbie-8/xubuntu-prevent-xfce-loading-on-startup-650171/](http://www.linuxquestions.org/questions/linux-newbie-8/xubuntu-prevent-xfce-loading-on-startup-650171/)

or change runlevel in /etc/inittab

---

### Post by Toz on 2011-09-08
> **Habitual said:**
> or change runlevel in /etc/inittab

/etc/inittab has been deprecated in favour of the upstart method. In fact, the file no longer exists.
```
man inittab
``` or [http://upstart.ubuntu.com/]("http://upstart.ubuntu.com/") for more information.

---


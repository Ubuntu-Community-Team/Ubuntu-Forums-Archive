---
title: "How light can I make Ubuntu run?"
date: 2009-11-13
forum: General Help
---

### Post by 98xjdmb on 2009-11-13
Ok, so here is the thing. I have an old (6+ years!) desktop computer that has been running Ubuntu for about a year as my main computer. Works great, love it! I recently purchased a new laptop that now receives 99% of my computing (dual boot Ubuntu and Win7, which i surprisingly use them about 50-50). What i want to do is clean up my desktop to the most bare bones it can be. The only things i want to use it for are as a super simple file server, a super occasional web browser, and where i can do  my totally legal bit-torrenting. I really like how simple ubuntu can be, but don't know how to make it a skeleton. What do you recommend i use? Thanks!

---

### Post by lykwydchykyn on 2009-11-13
For starters, switch from GNOME to some lightweight window manager or desktop environment.  I'd recommend LXDE.

Just do:
```

sudo apt-get install lxde

```

When it's done installing, log out, change your 'session' type to LXDE, and enjoy a decent boost in responsiveness.

---

### Post by 98xjdmb on 2009-11-13
Great start there, thanks

What about what programs i have installed. would uninstalling unused programs improve performance?

---

### Post by bodhi.zazen on 2009-11-13
You can try any of the various lighter weight versions of Ubuntu such as 

Crunchbang, lubuntu, or I made a light res-in, Zenix:

[http://zenix-os.net/index.php?nav=home](http://zenix-os.net/index.php?nav=home)

When using Zenix on my netbook, logging into Fluxbox, Zenix uses just under 100 Mb RAM and when installed users 2.5 Gb HD Space.

---

### Post by OneMixDJ on 2009-11-16
Compaq Presario 5280 Desktop with 384MB Ram.
Ubuntu Hardy now with LXDE desktop:

[[IMG]http://i989.photobucket.com/albums/af14/OneMixDJ/th_lxde_onemixdj.png[/IMG]](http://s989.photobucket.com/albums/af14/OneMixDJ/?action=view&current=lxde_onemixdj.png)

The only I need to do (when I have time) is to remove GNOME Desktop.

I installed LXDE to replace GNOME Desktop and now have it as default.

The only thing is really a "clean-up" item because it seems that the menu selection in the upper left corner is really from GNOME desktop and not LXDE (a little conflict there). I think once I remove GNOME desktop, that should help.

However, the overall responsiveness, even with GNOME desktop still installed, is noticeable enough. 

I have a Dell Optiplex GX-1 PII 266MHz (with 448MB RAM) that I only tried in the past to install Ubuntu Ibex and it didn't do all that great. It's running XP now with MP3 Rocket and Vuze but I would like to eventually replace with a lightweight Linux solution. I might wait for official Lubuntu release or try Masonux on it in the meantime. At the same time, neither MP3 Rocket or Vuze is supported by Wine so I have to figure that part out too.

---

### Post by gordintoronto on 2009-11-17
> **OneMixDJ said:**
> Compaq Presario 5280 Desktop with 384MB Ram.
Ubuntu Hardy now with LXDE desktop:


Fabulous!  I have an old machine with an AMD K6, which is probably just a tad faster than your CPU, but it only has 64 MB of memory, and I have completely failed to get any GUI version of Linux running on it.

---

### Post by winotree on 2009-11-18
> **98xjdmb said:**
> Ok, so here is the thing. I have an old (6+ years!) desktop computer that has been running Ubuntu for about a year as my main computer. Works great, love it! I recently purchased a new laptop that now receives 99% of my computing (dual boot Ubuntu and Win7, which i surprisingly use them about 50-50). What i want to do is clean up my desktop to the most bare bones it can be. The only things i want to use it for are as a super simple file server, a super occasional web browser, and where i can do  my totally legal bit-torrenting. I really like how simple ubuntu can be, but don't know how to make it a skeleton. What do you recommend i use? Thanks!
Someone earlier in the week posted this link [http://andyduffell.com/techblog/?p=361](http://andyduffell.com/techblog/?p=361) which could serve as a jumping-off point for you.

---

### Post by OneMixDJ on 2009-11-18
> **gordintoronto said:**
> Fabulous!  I have an old machine with an AMD K6, which is probably just a tad faster than your CPU, but it only has 64 MB of memory, and I have completely failed to get any GUI version of Linux running on it.


gordintoronto, you might need 128MB RAM for any type of GUI.

You might be able to get away with 96MB RAM, but not sure where the line is drawn. 

If you can manage a upgrade to 128MB RAM with LXDE as your desktop choice, you might be good to go. \\:D/

---


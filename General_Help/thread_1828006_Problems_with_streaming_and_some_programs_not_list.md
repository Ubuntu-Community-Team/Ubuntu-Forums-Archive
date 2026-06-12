---
title: "Problems with streaming and some programs not listed in menu"
date: 2011-08-18
forum: General Help
---

### Post by branko.savic on 2011-08-18
Hi guys,

I just installed lubuntu 11.04 on my laptop and I love the speed!

However I have run into some difficulties, and I was hoping to be able to get some help here!

1. There are some sites that stream live audio or video feeds, that I like to watch sometimes, but even tough I have VLC player and what not installed, it does not work!

For example, if I click on this link: mms://rts.videostreaming.rs/rts in chromium browser, it tells me that it has to open a separate program, when I click open program it takes me to a blank page and nothing happends!

2. I like to play chess, and I have installed a few chess programs, but to my surprise, everything is not visible in the games menu.

I therefore have to go to /usr/games and find installed games from there! 

The games I have this problems with are: Polyglot, scid and xboard.

Hope that here is someone that can help me out, thanks in advance!

---

### Post by branko.savic on 2011-08-18
Anyone?

---

### Post by frankbooth on 2011-08-19
> **branko.savic said:**
> 1. There are some sites that stream live audio or video feeds, that I like to watch sometimes, but even tough I have VLC player and what not installed, it does not work!

For example, if I click on this link: mms://rts.videostreaming.rs/rts in chromium browser, it tells me that it has to open a separate program, when I click open program it takes me to a blank page and nothing happends!
Sadly, Chromium isn't up to par with Firefox when it comes to plugins. I'm sure you can open the URL in *vlc*, it works fine with *mplayer*.

> **branko.savic said:**
> 
2. I like to play chess, and I have installed a few chess programs, but to my surprise, everything is not visible in the games menu.

I therefore have to go to /usr/games and find installed games from there! 

The games I have this problems with are: Polyglot, scid and xboard
Unfortunetly adding menu entries in Lubuntu isn't as user-friendly as it should. You can make your own entries by creating a *.desktop* file like this:

**1)** Launch Leafpad, or another text editor.

**2)** Type:
```

[Desktop Entry]
Encoding=UTF-8
Name=NAME-OF-GAME
Exec=PATH-TO-GAME
Icon=PATH-TO-ICON
Terminal=false
Type=Application
Categories=Application;Game;
StartupNotify=false

```

And save it as *NAME-OF-GAME.desktop*

**3)** Move it to */usr/share/applications/* either by using PCManFM or by using the terminal:
```

sudo mv NAME-OF-GAME.desktop /usr/share/applications/

```

---

### Post by kerry_s on 2011-08-19
you can use alacarte to edit the menu. make sure when you install it you turn off recommends so it don't pull in a bunch of gnome parts.

---

### Post by branko.savic on 2011-08-19
> Sadly, Chromium isn't up to par with Firefox when it comes to plugins. I'm sure you can open the URL in *vlc*, it works fine with *mplayer*.

I tried installing Firefox and now I get the following message:

Firefox doesnt know how to open this link, because the mms protocol is not associated with any program!

How can I fix that?

I have tried following the instructions provided here: [http://www.cinlug.org/node/316](http://www.cinlug.org/node/316)

and here: [https://answers.edge.launchpad.net/ubuntu/+question/34257](https://answers.edge.launchpad.net/ubuntu/+question/34257)

But so far I have been unsucessfull!

Thanks!

---

### Post by branko.savic on 2011-08-20
I would really appreciate an answer toward resolving this problem!

Thanks!

---

### Post by claracc on 2011-08-21
I could open and watch the video in the link you provided, opening it with firefox 3.6.20, then firefox asks me which program has to be used, I  select smplayer and after one minute more or less I can see the video. 

VLC cannot play this video.

---

### Post by coldraven on 2011-08-21
I'm using Ubuntu 10.10.
I pasted your link mms://rts.videostreaming.rs/rts into mplayer and it played immediately.
Using Firefox it asked me to select which application, Totem by default and mplayer started up and played OK. In Firefox type "about:plugins" in the address bar. See the attached screenshot. I hope that your computer has enough resources to use Firefox.

---

### Post by branko.savic on 2011-08-23
> **coldraven said:**
> I'm using Ubuntu 10.10.
I pasted your link mms://rts.videostreaming.rs/rts into mplayer and it played immediately.
Using Firefox it asked me to select which application, Totem by default and mplayer started up and played OK. In Firefox type "about:plugins" in the address bar. See the attached screenshot. I hope that your computer has enough resources to use Firefox.

Yes, when I used ubuntu I had no problems opening the link, but with lubuntu it just doesnt work!

I switched to lubuntu because its so much faster the  ubuntu!

---


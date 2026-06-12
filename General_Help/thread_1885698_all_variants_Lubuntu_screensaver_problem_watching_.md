---
title: "all variants Lubuntu screensaver problem watching videos or listening to music"
date: 2011-11-23
forum: General Help
---

### Post by esbrinartot on 2011-11-23
I've recently installed lubuntu 11.10 32 bits. Everything works fine except the screensaver.

The screensaver always activates when I'm listening music or watching a film. I've tried with VLC, Gnome-player and Totem.

Even if I go to the Setup of totem and I disable the screensaver when I play sound or video I have the same problem. Each 5 or ten min I have to move the mouse...

I've also tried to install caffein but seems that caffein doesn't work neither.... 

I really hate to activate or deactivate the screensaver constantly???

Any solution? Anyone has the same problem? Anyone has an ida of the problem?

I think is related to Xscreensaver and gnome screensaver... But no idea when the problem will be solved or maybe the won't

---

### Post by oldtimer7777 on 2011-11-23
I have always had this same problem. It is normal, unfortunately. 

> **esbrinartot said:**
> I've recently installed lubuntu 11.10 32 bits. Everything works fine except the screensaver.

The screensaver always activates when I'm listening music or watching a film. I've tried with VLC, Gnome-player and Totem.

Even if I go to the Setup of totem and I disable the screensaver when I play sound or video I have the same problem. Each 5 or ten min I have to move the mouse...

I've also tried to install caffein but seems that caffein doesn't work neither.... 

I really hate to activate or deactivate the screensaver constantly???

Any solution? Anyone has the same problem? Anyone has an ida of the problem?

I think is related to Xscreensaver and gnome screensaver... But no idea when the problem will be solved or maybe the won't

---

### Post by esbrinartot on 2011-11-23
What a pity. Small details mark the difference sometimes. Seems an stupid bug but for me is important. In my opinion improvements or modifications must be introduced when they work.

Do you know if in other distibutions as linux mint LXDE have the same problem?

---

### Post by 4Orbs on 2011-11-23
The only player(of many) I've used that reliably disables screensavers is vlc, and that works only in fullscreen mode.

---

### Post by esbrinartot on 2011-11-24
Hi Orbs.
I will try again VLC. VLC for me has a problem. I have a low internet connection and I use to watch video podcast, Totem IS great because I can buffer 100% of the podcast and with VLC is not possible.  (VLC has no buffer storage...)

Can I do the same With VLC????

---

### Post by stinkeye on 2011-11-24
Is it your screensaver or your monitor blanking when idle 
for 10 mins?
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1877801")

---

### Post by esbrinartot on 2011-11-24
stinkeye, my problem is different than yours and the link you give I guess is useless for me. My screensaver works well. The only problem I have is that I want to disable the screensaver when I I'm watching a film or a videopodcast. In case I decide to disable the configuration manually I can do it but please we are on the 21st Century... I want to avoid do it manually each time.

I just do all I can to do it to disable the screensaver when I'm watching a film with totem, gnome-mplayer or VLC.(I will try again VLC with full screen)

I think the problem is all the mentioned software are designed to work with gnome screensaver and know many people or distributions are using xscreensaver.

---

### Post by amjjawad on 2011-12-02
Hi there,

> **esbrinartot said:**
> In case I decide to disable the configuration manually I can do it but please we are on the 21st Century... I want to avoid do it manually each time.
Being in the 21st century or even the 31st century doesn't make everything prefect. There is NO prefect OS, period. This is a fact :)

Perhaps what I'm going to explain is NOT the "perfect" solution for you but for me, it works the way I want.

This is what I would do if I were you:

1- Either to disable the Screensaver

[IMG]http://i42.tinypic.com/24mf9eo.jpg[/IMG]

And because I'm sure you will NOT like this suggestion ...

2- [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#I_want_to_bind_a_key_to_lock_my_screen.2C_how_do_I_do_it.3F](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#I_want_to_bind_a_key_to_lock_my_screen.2C_how_do_I_do_it.3F)

Follow the above guide to add Lock Screen icon to your Menu and then you can increase the time (Blank After) to 60 mins or more and whenever you want to use the Screensaver, either to press Super Key + L OR Click on Lock Screen icon.


> I think the problem is all the mentioned software are designed to work with gnome screensaver and know many people or distributions are using xscreensaver.

If you are sure about that OR you want to check whether it's true or not, I suggest to install GNOME Screensaver and give it a try. Don't let anything to hold/block you from trying :)
This is what I do to learn more about Linux.

Thank you!

---

### Post by esbrinartot on 2011-12-03
Well,

What I've done is create a launcher and put in in the desktop. The launcher execute next command:

xscreensaver-command -exit

The deactivates the xscreensaver deamon.

To restart the deamon I create a shortcut to the desktop. That's the best solution I've found. (Not so nice idea but functional)

To check if the problem is caused by software I'm using is design to work with gnome-screensaver I will test once I have running a virtual machine. When I have time I will try it.

---

### Post by amjjawad on 2011-12-03
> **esbrinartot said:**
> Well,

What I've done is create a launcher and put in in the desktop. The launcher execute next command:

xscreensaver-command -exit

The deactivates the xscreensaver deamon.

To restart the deamon I create a shortcut to the desktop. That's the best solution I've found. (Not so nice idea but functional)


This is not the best solution. Not trying to insist to use my suggestion but you don't really have to stop and re-run the same process. Anyway, use whatever works for you :)

---

### Post by esbrinartot on 2011-12-06
> **amjjawad said:**
> This is not the best solution. Not trying to insist to use my suggestion but you don't really have to stop and re-run the same process. Anyway, use whatever works for you :)
Hi, I want to give further information about the solution I proposed.

What I proposed doesn't work. So don't try it.

The solution I propose is fine but notice now I can use caffein and I prefer caffein rather the lock screen icon.

Why know I can use caffein?

Because now I use metacity instead of openbox. So caffein doesn't  work with open box.

Another positive point of metacity is:

Wiith openbox the letters in the windows or the browser got half erased. Now with metacity works perfect. Another positive point is that metacity is also so light. 

So if you belong to the team of lubuntu developers take in to account my comments if you think are worthy.

Please also notice that would be great that ubuntu had xcompmgr by default with openbox.

When I have time I will install lubuntu in a virtual machine and I will install gnome screensaver instead x-screemsaver.

---

### Post by amjjawad on 2011-12-08
Hi,

I'm a member of Lubuntu Family but not a developer at all :)

For me, I have no problems with Lubuntu. It's a great but yes, users need sometime until they get familiar with it beside it lacks to lots of useful documentation IMHO and this is what I'm working on. I'm trying to write a FULL Guide for beginners. This guide should be more than enough to cover everything that a beginner might need without the extra tweak and stuff, just the basic necessary stuff :)

A general advice: use whatever works for you. Use google or [www.googlubuntu.com](www.googlubuntu.com) to find what you need.

---


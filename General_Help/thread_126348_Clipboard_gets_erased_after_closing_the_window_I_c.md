---
title: "Clipboard gets erased after closing the window I copied from"
date: 2006-02-06
forum: General Help
---

### Post by louis_nichols on 2006-02-06
Hi!

I noticed this some time ago, but didn't think it would be so annoying. But I can't stand it anymore. I don't know when it started happening or why.

I sometimes open a piece of text in some app just to copy some of it to the clipboard, then immediatelly close the app, with the intention to paste the text. But it will no longer be on the clipboard and IT'S DRIVNG ME CRAZY!! having to re-open the same stuff again. It will happen within the same app, but different tabs, for example in gaim: if I open a conversation to copy the last lines and then close the tab to paste the text to another conversation.

I have no idea how the clipboard works in Gnome, so please tell me if you need the contents of some config file or anything. I don't know where to start.

---

### Post by quonsar on 2006-02-06
coming from windows, i also found this annoying. however, this seems to be the way it works in gnome. 

the solution is simplicity itself: stop closing the apps before pasting. :rolleyes:

---

### Post by magnusbb on 2006-02-06
This also annoyed me, but my solution is to use the KDE clipboard in GNOME - it is possible, and it works very well. Go to System -> Preferences -> Sessions. Click on the tab "Startup programs" and on "Add". Input the command "klipper". The next time you log in to GNOME, the KDE clipboard will take care of your copy/paste activities, and it's represented with its own icon in the notification area of your panel.

Of course, this solution requires that KDE is installed on your Ubuntu system (not by default). If you want a basic KDE system, just do a "apt-get install kubuntu".

---

### Post by elzed on 2006-02-06
You don't have to install KDE to solve this problem!

The "gnome-clipboard-daemon" will solve this.

You can download it here: [http://members.chello.nl/~h.lai/gnome-clipboard-daemon/](http://members.chello.nl/~h.lai/gnome-clipboard-daemon/)

There is no installation procedure, just run ./gnome-clipboard-deamon

---

### Post by quonsar on 2006-02-06
[QUOTE=elzed]You don't have to install KDE to solve this problem!

The "gnome-clipboard-daemon" will solve this.

You can download it here: [http://members.chello.nl/~h.lai/gnome-clipboard-daemon/](http://members.chello.nl/~h.lai/gnome-clipboard-daemon/)

There is no installation procedure, just run ./gnome-clipboard-deamon[/QUOTE]


VERY cool! thanks elzed!!!!  :mrgreen:

---

### Post by ronmarley1 on 2006-02-06
I downloaded the tarball, extracted it and tried to run it using ./gnome-clipboard-deamon and all I get is a blinking cursor.  It doesn't seem to be running.  Any ideaas?

---

### Post by dcstar on 2006-02-06
[QUOTE=ronmarley1]I downloaded the tarball, extracted it and tried to run it using ./gnome-clipboard-deamon and all I get is a blinking cursor.  It doesn't seem to be running.  Any ideaas?[/QUOTE]
Put it in System-Preferences-Sessions-Startup Programs

---

### Post by louis_nichols on 2006-02-06
See? This is why I ike Ubuntu: there's a solution for almost everything. :)

Are you sure that what I wrote here is the default way for Ubuntu? I seem to remember it wasn't like this at first (but it might be because I come after a pretty long history with KDE)... Anyway, great ideas you posted! I would love to use klipper, but I'm having these prpblems, with the system hanging when I logout and I have a hunch it might be because of apps like kGet and Krusader, which I leave open. So I wanna try to go without k apps for a while.

---


---
title: "How to disable gdm and run a single gui app"
date: 2010-01-15
forum: General Help
---

### Post by brain!ac on 2010-01-15
Hi

First of all i would like to say my first Hello to you guys .

And my issue is ,i disabled the gdm from RC start-up scripts so now my ubuntu will boot only in text-mode (terminal) ,but what i need to know is how can i run a single application for ex. Firefox in gui mode ,by keeping gdm disabled ,i tried using startx but it did not solved my issue .

Best on advance

---

### Post by wojox on 2010-01-15
If you don't enable gdm then x-windows never gets invoked so you won't be able to start any gui applications. If you need a text based web browser try:

```
w3m -v http://www.google.com
```

---

### Post by brain!ac on 2010-01-15
> **wojox said:**
> If you don't enable gdm then x-windows never gets invoked so you won't be able to start any gui applications. If you need a text based web browser try:

```
w3m -v http://www.google.com
```

Hi ,

Thanks for reply ,but im thinking about any Application Firefox was an example ,becuase what if i need only VLC or Mplayer fullscreen to run on VGA Output instead of gdm .

---

### Post by Locutus_of_Borg on 2010-01-15
what error is 'startx' giving you?


you will need to run X to run a gui application, but you could use mplayer, for example, on the framebuffer


another option if you dont want to use gdm, is to use qingy as the login manager

---

### Post by brain!ac on 2010-01-19
Thanks on reply ,

I think i was bad in explanation ,the idea is to create a StandAlone OS with an SWF app. (i thought to play it by browser because most of OS provides an internet browser) ,but whatever it can be played by another app. 

When user connects it`s PC where Ubuntu is installed ,it will load system components ,and when the boot is finished than on PC Display will be that SWF App without the mouse cursor or Desktop components .

---

### Post by KeyserSoze93 on 2010-01-19
Try adding the following to /etc/rc.local (BEFORE the line which says exit 0):

```
su YOU -c "xinit -- firefox"&
```

This should make the system start X windows as your user (where YOU is your username), and invoke firefox.

This doesn't work perfectly, since without a GUI there is nothing to give the window title bars etc. so you can't resize it.

However, for something like fullscreen mplayer, it should be OK.

---

### Post by lewisforlife on 2010-01-19
See this thread: [http://ubuntuforums.org/showthread.php?t=1345861](http://ubuntuforums.org/showthread.php?t=1345861)
It should really help you out.

You will really want to use a Window Manager, so that you can control whether firefox, or other programs that you load are full screen or not.  If you do not use a window manager, there is no way to tell it how big to make your windows.  There are some really basic windows managers that you can use (not desktop environments like gnome).

---

### Post by brain!ac on 2010-01-20
Hi guys 

I solved the case by ussing xinit command .

First of all i`ve disabled gdm so my uBuntu will boot only on txt mode ,than when it will check start-up scripts at rc.local it will load a command which is used for firefox and ffplay .

```
xinit /usr/bin/firefox width-200 height-200
```
```
xinit /usr/bin/ffplay -fs /home/User/desktop/Desktop/video1.mp4 
```

So thanks to all ,and best regards .

---

### Post by fathead12 on 2011-05-25
Hello,

I am trying to do exactlythis on 11.04
Can you please provide detailed istructions?

how do I disable gdm?
how do I set up firefox to autolaunch in fullscreen mode-no status bar /navbar/ or anything else 

I want the user to not be able to do anything in fireox. It will launch to a citrix client login page-thats it

---


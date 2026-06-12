---
title: "is it possible to play video directly inside desktop?"
date: 2010-03-30
forum: General Help
---

### Post by gfunkera on 2010-03-30
i want to watch music videos, etc but i want them to play (not in a window) inside the desktop like in a predefined area... is this possible?

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
Anything is possible. With music you can use conky but I'm not sure how you would embed video into the desktop. I'm sure there are ways to do it though.

Edit: On jaunty I found a program to make your background a video but there was no sound. It was mainly just for animated backgrounds. I did play kung fu movies on it when I was working on my command line which is painted to the desktop and transparent.

---

### Post by kokkus on 2010-03-30
You mean as a desktop background? coz yup that is possible.

First lets grab some essential building libraries via the terminal: Applications->Accessories->Terminal
sudo apt-get install build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev cvs
Now lets Install xwinwrap:
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
cd xwinwrap
make
sudo cp xwinwrap /usr/bin

Now lets start our video/movie as the Desktop Wallpaper!
First find a video/movie you would like to set as your backround and issue this command:
xwinwrap -ni -fs -s -st -sp -b -nf -- mplayer -wid WID -nosound "videofile.Xvid.avi" -loop 0

Now everything should be working fine, if you would like sound, remove -nosound

You can also display Screensavers as your background:
nice -n 15 ./xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/lib/xscreensaver/glmatrix -root -window-id WID



I used .avi as an example but offcourse you can use playlist files instead.
Good luck.

---

### Post by gfunkera on 2010-03-30
absolutely WONDERFUL! thank you so much!

---


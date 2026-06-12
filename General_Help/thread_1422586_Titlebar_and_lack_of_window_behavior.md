---
title: "Titlebar and lack of window behavior"
date: 2010-03-05
forum: General Help
---

### Post by buntu_hugenewbie11 on 2010-03-05
I recently upgraded my ubuntu hardy 64 bit.
I use kde 3.5 and do not have any desktop effects.
I do not use compiz or anything like that.
For somereason none of my application windows have title bars.
I cannot move application around and to close them or minimize I must either go to the taskbar and right click or go to file and close.
This is the most irritating behavior I have ever come across as I work on many applications at the sametime and move windows around and minimize and close them using the taskbar.
Please someone let me know how I can get the windows behavior of my windows back.
Help me.

---

### Post by Intrepid Ibex on 2010-03-05
So you don't have window bars. There are usually insane bugs when upgrading from older distros to newer ones but I didn't understand the part where you said you were using kde 3.5.

It doesn't come with Karmic... did you upgrade _to_ hardy of _from_ it?

Kwin (the window manager in KDE) should defonitely come out with the other KDE stuff - I guess your configurations just ain't working. You can try moving out ~/.kde* stuff to e.g. ~/.kde*-backup and try logging in again.

Most likely the kde 3.5 confs won't work with kde 4.4 (if I understood your problem correctly).

---

### Post by buntu_hugenewbie11 on 2010-03-05
I am not using Karmic.
I am using Hardy. I do not use KDE 4 instead I use KDE 3.5
I found a way to bring back toolbars.
in the terminal
sudo metacity --replace

Unfortunately I need to run it on each start up, but at least everything works now.

---

### Post by Intrepid Ibex on 2010-03-06
you don't need to do that with sudo and kde uses kwin instead of metacity.
did you try my suggestion of moving out the old settings?

You can also install fusion-icon and change the window manager with that but first you should try whether "kwin --replace" even does a thing. If it doesn't - either your settings won't work with kde 3.5 or you don't have kwin.

---

### Post by buntu_hugenewbie11 on 2010-03-09
Actually kwin --replace makes one of my desktops unusable.
I have separate X-Screens and one monitor's desktop stops responding.
metacity --replace actually brings back the normal behavior.
And yes I know I am using kde and that it should not work this way.
The hassle is that I have to do it on each startup.
As for my upgrade procedure:
apt-get update
apt-get upgrade
apt-get dist-upgrade.

I am using Hardy because supposedly it should be less buggy given the LTS label.
It's too bad the LTS stands for "Likely Tricky Situations"

---


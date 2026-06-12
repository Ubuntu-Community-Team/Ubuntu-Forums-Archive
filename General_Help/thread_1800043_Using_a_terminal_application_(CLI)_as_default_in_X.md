---
title: "Using a terminal application (CLI) as default in Xubuntu"
date: 2011-07-08
forum: General Help
---

### Post by nmatavka on 2011-07-08
I do a lot of torrenting on my xubuntu box, and ever since my introduction to computers, I have become attracted to the command-line way of doing things.  My default editor is vi, my default torrent programme is rtorrent, my default gopher client is lynx... you get the idea.  My web browsing, and sometimes also my file browsing, however, is always in graphical mode.

As you know, downloading a torrent involves downloading a small file with the extension .torrent.  When I clicked on this .torrent file, although I have rtorrent installed, Transmission showed up.  Not to insult the Transmission guys, but compared to an ncurses-based torrent client, Transmission is just too bloated.  Anyhow, I right-clicked on the file, Open With Other Application, etc.

Into the box that showed up, I typed /usr/bin/rtorrent (the path to my favourite torrent client), and clicked OK.  I double-clicked on the torrent file again, and nothing.  Transmission didn't show up, but neither did my terminal client.  I'm sick of having to go to the Applications menu and firing up the Terminal to torrent a file.  I'd like to have the Terminal open up with rtorrent as soon as I double click the file.

How do I do this?  Don't tell me to read the ******* manual, because I did... can't find anything on this topic.

---

### Post by searchfgold6789 on 2011-07-08
There should be a check box with "Run in Terminal" written on it at the window that allows you to select the other application you want to use.

---

### Post by WorMzy on 2011-07-08
You need to open a terminal, then make the terminal open the right application, then make the application read the file.

To do this, make a script with the following content:
```
#!/bin/bash

terminal -x rtorrent $@
```

make it executable, then, in your file browser, right-click a torrent, and choose "open with other application". Set the application to the script you just made.

Voila.

---

### Post by nmatavka on 2011-07-08
There is no "Run in Terminal" check box; you must have Xfce confused with GNOME, where such a check box exists, although it seemingly also doesn't work.

I tried the shell script idea; somehow, that doesn't work either.

---

### Post by WorMzy on 2011-07-08
Do you use a different terminal emulator? I thought "terminal" was the default on XFCE, but perhaps you're using something else?

Modify the script to suit your needs. For example, if you use urxvt, use
```
urxvt -e rtorrent $@
```

for sakura, use
```
sakura -e rtorrent $@
```

etc.

You'll have to check which flag your terminal emulator uses to execute commands -- terminal uses -x, urxvt uses -e, and sakura can use either, but only -e seems to work for me.

---

### Post by nmatavka on 2011-07-09
Thanks so much!  Xfce does in fact use terminal, but I decided to download sakura, a terminal app I'm familiar with, and go from there.  Using the example provided, I was able to fashion a shell script that did in fact work.

---

### Post by andrew.46 on 2011-07-09
Mind you the easiest way is to set rtorrent to watch a specific location and then simply dump your torrent files in there. On my own system I use $HOME/.rtorrent/ for this:

```

schedule = watch_directory,5,5,load_start=/home/andrew/.rtorrent/*.torrent

```

This removes the use of the mouse from what is essentially a commandline program :).

---


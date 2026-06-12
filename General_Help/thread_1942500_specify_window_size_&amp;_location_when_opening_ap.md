---
title: "specify window size &amp; location when opening ap from command line, possible?"
date: 2012-03-17
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-03-17
Is there any general way to specify the size and location of window to open an ap with in the same command that opens the ap? By general I mean a nomenclature/syntax that would be the same regardless of the ap being opened. Something that could be prepended or appended to the command used to open the ap. For instance, something like:
gedit --window-size=800x100 --window-location=x,y
Failing a general syntax, is there something specific for gedit?

I boot in Maverick to get anything real done, but I have an Oneiric with Mate partition I'm tweaking so an answer in terms of either would be appreciated.

---

### Post by Habitual on 2012-03-17
devilspie in the repos should help nicely.

---

### Post by rg4w on 2012-03-18
wmctrl may help.  You can find it in the Software Center - docs here:
[http://spiralofhope.wordpress.com/2010/02/03/wmctrl-user-documentation/](http://spiralofhope.wordpress.com/2010/02/03/wmctrl-user-documentation/)

---

### Post by Dreamer Fithp Apprentice on 2012-03-18
Thank you, both.  I'll play with both programs a bit. Wmctrl looks a little more promising at the moment as it looks like I can use it to create a script to open an instance of gedit and resize the window to spec automatically. Gnome-terminal can be opened in a window of specified dimensions and location with a switch after the gnome-terminal command. I could wish all programs had such a feature.

---

### Post by stinkeye on 2012-03-18
Hi again
If you just want to resize an active window after it has been loaded
you can use something like this.
```
wmctrl -r :ACTIVE: -e 0,[COLOR="Magenta"]100,300[/COLOR],[COLOR="DarkOrange"]890,560[/COLOR]
```
[COLOR="Magenta"]100,300[/COLOR]= window position x,y
[COLOR="#ff8c00"]890,560[/COLOR]= window size x,y
change to whatever.

Rather than set to a keyboard shortcut I like to use easystroke mouse
gestures to set a gesture to run the command.
The wmctrl command works on the focused window so by performing the gesture in the window you want to resize it gives it focus then runs the command.

---

### Post by HiImTye on 2012-03-18
I'd use wmctrl, making sure to add a sleep between it (to give the window time to actually open) i.e.
```
program && sleep 5 && wmctrl -r :ACTIVE: -e 0,x_pos,y_pos,x_size,y_size
```

---

### Post by Dreamer Fithp Apprentice on 2012-03-24
Thanks, Stinkeye; HiImTye,

Yep, wmctrl seems to be just the ticket. I'm going to find lot of uses for this.  I'm marking this solved.

---


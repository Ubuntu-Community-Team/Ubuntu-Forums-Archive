---
title: "Bad performance with games"
date: 2006-03-24
forum: General Help
---

### Post by Jeff Eklund on 2006-03-24
[FONT=Lucida Sans Unicode]Hi!
I do play a game or two sometimes as recreation but the game performance in KDE is not what i could wish for. Most games run laggy and are unresponsive. The strange thing is that running games, on the same computer, in Gnome or Xfce gives me a much nicer experience. 
Most of the games i am trying to run use SDL (apart from some emulator, which I'm not sure of what they use). The computer is a 6 month old Acer Aspire with a gig RAM, 1.5 ghz Pentium Celeron and the crappiest video card made in the history of computers. The video card hasn't got any 3D hardware acceleration nor anything fancy; it's only 32 megs, but the games I'm trying to run aren't large games. I'm trying to run OpenTTD, Freeciv or similar, 2D, games.

Since the games run smoother when using Gnome or Xfce I gather it's a problem with KDE. When KDE is resting, without any applications open, it uses ~2% of the cpu and ~180 MB of RAM. With most of my standar applications running in the background (mail, some karambra, aggregator, clipboard program and so on) about 9-12% of the cpu is used and about 250 MB of ram. Gnome, without anything open, uses about 4% of the cpu and 230 MB of RAM.

What settings could I have set wrong? What could I do to improve my gaming performance using KDE?[/FONT]

---

### Post by der_joachim on 2006-03-24
There is a wiki somewhere on the Kubuntu site, which can help you improve Kubuntu performance. I have it in my bookmarks, but currently I am on my GFs laptop. Bad girlfriend! No cookie! :)

Even after tweaking Kubuntu, I still detect a slight performance problem in KDE. I've reduced memory consumption to a mere 90 megs (that includes some SuperKaramba widgets). Even then, I sometimes find that gaming is more choppy than in Xfce. Perhaps it has something to do with a KDE service?

---

### Post by Jeff Eklund on 2006-03-24
[quote=der_joachim]Perhaps it has something to do with a KDE service?[/quote]Yes, i'm thinking in the lines of that too. As my problem seems mostly related to SDL-games (albeit I haven't played much non-SDL games); could it be something with KDEs handling of such layer APIs as SDL?

---

### Post by der_joachim on 2006-03-25
Back on my own PC again. [Here]("https://wiki.kubuntu.org/KubuntuOptimization")'s the link to the Wiki I mentioned in an earlier post. I do not know anything about SDL/KDE interoperability.

---

### Post by z-vet on 2006-03-25
You can easily run games without KDE, but i'm afraid it works only for Linux native games (these running without emulators). I can post a little howto on how to do it if someone interested.

---

### Post by Jeff Eklund on 2006-03-25
[QUOTE=z-vet]You can easily run games without KDE, but i'm afraid it works only for Linux native games (these running without emulators). I can post a little howto on how to do it if someone interested.[/QUOTE]
Please do.

---

### Post by z-vet on 2006-03-25
Open a terminal emulator and do:
```
sudo cp /etc/X11/default-display-manager /etc/X11/default-display-manager.orig
sudo nano /etc/X11/default-display-manager
``` 
This file contains only one line: 
```
/usr/bin/kdm
```
Delete this line and save a file.
Find out what is your game's executable and remember it's full path. In my case it's /usr/local/games/ut2003/ut2003, yours may be different.
Now close KDE and reboot (reboot needed just once for the changes to take effect). When the system boots up you will stay in text-only mode with login prompt. Login with your username and pass. To start X do:
```
startx &
```
To start a game do:
```
startx -e /path/to/your_game_executable
```
Enjoy.
BASH will remember this command, so you don't need to type it in each time you want to start a game, just use standard up-arrow to list previous commands.
When the game is closed, you stay in X session. Kill it with Ctrl-Alt-Backspace to get to prompt again. Then ```
startx &
``` for KDE.
In case you did not like it and want to rollback, it's simple: 
```
sudo rm -f /etc/X11/default-display-manager
sudo cp /etc/X11/default-display-manager.orig /etc/X11/default-display-manager
```
Reboot.
Hope it helps...

---


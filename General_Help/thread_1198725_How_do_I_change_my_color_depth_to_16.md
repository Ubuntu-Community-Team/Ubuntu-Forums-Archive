---
title: "How do I change my color depth to 16?"
date: 2009-06-27
forum: General Help
---

### Post by Zorgoth on 2009-06-27
The title pretty much says it all.  There doesn't appear to be a DefaultDepth option in /etc/X11/xorg.conf.

---

### Post by starcraft.man on 2009-06-27
Why would you want to go back to 16 bit color depth? Is there a problem? Please elaborate.

---

### Post by Zorgoth on 2009-06-27
I was wanting to do it because I had a game that crashed in wine, and in the error was something about not being able to reset the color depth to 16.

---

### Post by starcraft.man on 2009-06-27
That's an old game then. I don't think that's a problem with your set colordepth. Just like on Windows, Wine should be able to I believe reset the color to what it needs to to play the game. It's also noteworthy that WINE isn't perfect, it might just a problem with the implementation of WINE.

What's the name of the game? I'd look for it in the [appDB]("http://appdb.winehq.org/") and see how it's rated to run. Search in the top right.

---

### Post by Zorgoth on 2009-06-27
The game is Majesty - Gold Edition.  Note that I know nothing about WINE.  Here is a link to the thread I made about it:

[http://ubuntuforums.org/showthread.php?t=1198729](http://ubuntuforums.org/showthread.php?t=1198729)

---

### Post by starcraft.man on 2009-06-27
> **Zorgoth said:**
> The game is Majesty - Gold Edition.  Note that I know nothing about WINE.  Here is a link to the thread I made about it:

[http://ubuntuforums.org/showthread.php?t=1198729](http://ubuntuforums.org/showthread.php?t=1198729)

The game doesn't seem to run very well in WINE. [Link]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13827&iTestingId=39017").

I'm afraid this might just not work in WINE. I can't help you beyond that, guess you'll have to wait for someone a bit more experienced with WINE.

---


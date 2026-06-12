---
title: "LIRC bindings for Totem and others?..."
date: 2006-04-12
forum: General Help
---

### Post by encompass on 2006-04-12
I want to control my Totem Player and other programs like xmms and rhythmbox...
What bindings do I need for them to work properly with my remote...  I think it has something to do with my .lircrc file in my home directory... I have set it up to wirk with mplay just fine but that is because mplayer has a nice list of the bindings.  But none of the other programs do.  Or if they do, I would love to know them.  Thanks for the help..
quick note... I am using totem-xine and lirc is working just fine

---

### Post by mirkov on 2006-04-12
For xmms, you'll need lirc plugin. I've attached my .lircrc file, and it works for xine, mplayer, xmms and mythtv. You would have to change keys to match the ones of your remote.

---

### Post by encompass on 2006-04-13
Thank for the file... it will get me started... bummer on not having the list for totem... I thouhgt maybe totem xine but it doesn't seem to work with the xine bindings.  I can't even see it in the man pages or their website.  Thanks for your help dude...8)
NOTE... I have decided to start looking at the code of totem itself and came across this...
[http://cvs.gnome.org/viewcvs/totem/src/totem-remote.c?rev=1.7&view=markup]("http://cvs.gnome.org/viewcvs/totem/src/totem-remote.c?rev=1.7&view=markup")
From there I made this... <clippy>:-D Thanks for everyone's help. I also found out that rhythmbox will be having lirc support in there next release... home dapper gets a hand on it.

---

### Post by SIZABANTU on 2008-03-10
thanks for the file very handy :P

---


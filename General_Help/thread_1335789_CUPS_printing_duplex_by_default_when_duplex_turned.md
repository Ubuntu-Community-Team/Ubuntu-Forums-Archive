---
title: "CUPS printing duplex by default when duplex turned off [karmic]"
date: 2009-11-23
forum: General Help
---

### Post by ajmcello on 2009-11-23
I'm using karmic koala and have cups installed. All of my printers (about 5 of them) are printing double sided, even though under print options I have it disabled under cups. Things printed fine in earlier releases....

Using lp/lpr -o sides=one-sided fixes the problem, but does anybody have an idea whats causing this? 

Could it be a filter setting somewhere?


Thanks..

---

### Post by phthomas on 2009-12-05
I'm in the same boat. If the printer has a duplexer, CUPS prints in duplex mode by default.

---

### Post by bmcm on 2009-12-16
I have this problem also, and it is really very very irritating - a very serious regression ...

---

### Post by joelpedersen on 2009-12-22
Ditto, I am having the same problem.

---

### Post by joelpedersen on 2009-12-22
Actually, Documents printed under Open Office print without duplex, documents in evince and okular print in duplex (except when they are exported from Open Office) regardless of settings.  Strange.  Will keep poking around.  J

---

### Post by sybille on 2010-01-28
Hello, all.

I seem to have solved this problem, which only existed for one user on my setup, by deleting (renaming) the following file:
```
~/.cups/lpoptions
```(That's the text file named "lpoptions" in the hidden .cups folder in the user's home directory.)

The lpoptions file only contained a parameter for duplex printing, nothing else. Removing the file did not change anything else in the printer configuration.

I don't know which application added the lpoptions file, so I suppose this is only a work-around. But it does seem to have worked for me.

---

### Post by craq on 2010-02-05
Thanks, that solved my problem too =)

It would be nice to have GUI access to this though - either with System settings/Printer Configuration (to set a default) or somewhere in the print dialog (to override the default)

---

### Post by sybille on 2010-02-05
> **craq said:**
> It would be nice to have GUI access to this though - either with System settings/Printer Configuration (to set a default) or somewhere in the print dialog (to override the default)

The file isn't created by default - if you create a new user, there is no .cups folder. So I'd think that it's a matter of figuring out which program creates the user-specific lpoptions file.

I poked around a bit with the various applications (the gnome/gtk+ dialog, the cups web configuration, KDE settings, and some other things), and never found anything that created an lpotions file to store the settings I'd changed. I basically gave up on that, if only because I've been using the user directory in question for quite a while and on more that one distro, so I essentially decided to assume that it was something an application (or I myself) set up at some earlier point. That's not a satisfying resolution, though.

---

### Post by tracyandskye on 2010-04-08
I have this same situation with evince printing duplex, but there is no hidden .cups folder in my home directory.  Any other tips?

---


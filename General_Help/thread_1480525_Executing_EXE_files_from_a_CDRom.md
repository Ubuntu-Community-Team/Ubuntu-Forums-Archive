---
title: "Executing EXE files from a CDRom"
date: 2010-05-11
forum: General Help
---

### Post by jazzon on 2010-05-11
I am not exactly new to linux or to Ubuntu, and I cannot seem to find what I need to in either these forums, Ubuntu help, or various Man pages.

Issue:
When I insert a CD it automounts correctly, but I cannot Use the "Open with Wine" option (even after configuring wine to recognize the executable) due to a "trust" issue within Ubuntu.  I have learned that this "trust" is simply the executable bit, but I obviously cannot change that bit on a read only medium.  

The software requires the CD at both install and run time, so I cannot use a separately mounted ISO.

Somewhere there must be a setting where I can turn off the "*require trust flag*" which I assume must exist.  Any ideas as to where this might be, and / or how I do this?

---

### Post by bredman on 2010-05-11
I recommend that you try the Wine forum.

[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by jazzon on 2010-05-11
I started there.  There have been several requests there to solve the issue, but no working responses yet.  Since the issue is rooted in either the mounting protocols, Gnome, or some portion there of (Nautilus perhaps) I chose to post here.  

In addition, i have many other softwares that I wish to run from CDRom and prior to 10.4 was able to but now i cannot.

---

### Post by semafor on 2010-05-12
I guess Nautilus requires this, and that's a very good thing.

You can though just bypass nautilus by opening a terminal and

```

$ cd /media/cdrom0
$ wine Setup.exe

```

---

### Post by Mark Phelps on 2010-05-12
Wine is not the miracle cure some tout it to be -- it only runs SOME MS Windows apps.  Since you have "many" you want to run, save yourself a lot of time and grief by going to the WineHQ site linked below and searching for the "softwares" you want to run:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

Anything that's not listed, or has a rating less than Gold, is most likely NOT going to run -- no matter what you do in Wine.

---

### Post by jazzon on 2010-05-17
@semafor
  Been using linux for several years off and on...duh...command line...shoulda thought of that myself.  Getting to GUI bound I guess.  Thanks for the reminder.

@mark
  The "many" refers to packages on cdrom I would like to run from cdrom.  Mostly linux native.  The wine stuff is for my kids to play.  

So my wine issue is solved.  I thank you all for the help there.

If anyone knows how to alter the Nautilus issue though, more help there would still be appreciated.

---


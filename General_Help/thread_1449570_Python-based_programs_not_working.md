---
title: "Python-based programs not working"
date: 2010-04-08
forum: General Help
---

### Post by Nopantsman on 2010-04-08
Hello everyone!

I've been using Ubuntu 9.10 fairly regularly on my home computer for a week or two now, dual-booting it with Windows 7.  So far I've been quite happy with it, but yesterday something odd happened.  I decided to copy all the music I had stored on the Windows partition over to the Ubuntu file system so that I could listen to it there.  I have about 16 gigs of music mostly in .mp3 format, so I put the folder on an external hard drive, then logged into Ubuntu and copied it back from the external drive to my Music file. 

Once the transfer was done, I opened the Music file and double-clicked on one of the .mp3s at random to play it.  When I did this, a window popped up and the first half-second or so of the track played, and then the window closed and it stopped.  This happened once or twice more with different .mp3s.  The window didn't last long enough for me to get a good idea of what program it was for, but I assume it was Totem, which I hadn't yet run since installing Ubuntu, because according to the Properties->Open With tab of any .mp3 file, that's the default program to use to open .mp3s.  

Attempting to run Totem from the Applications menu gives the same result, I later found.  Attempting to run Totem from a terminal gave the following error: 

andrew@Lovelace-Linux:~$ totem

** (totem:2323): WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault

Then, several other programs began having similar issues immediately after I first tried to play a .mp3 yesterday.  Specifically, Rhythmbox - which I also hadn't used before, and next tried to use to play the music - will not start at all.  Running it from the terminal gives:

andrew@Lovelace-Linux:~$ rhythmbox

** (rhythmbox:2338): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:2338): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:2338): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault

Note that pygtk is again referenced.  The weirdest part is that other program that's having this issue, an IM client called emesene, is one that I had been using just fine, without issue, for several sessions previous.  Since trying to play that .mp3, it now won't run at all.  I tried removing and re-installing emesene, to no avail.  Running it from the Terminal gives:

andrew@Lovelace-Linux:~$ emesene
Traceback (most recent call last):
  File "/usr/share/emesene/Controller.py", line 21, in <module>
    import gtk
ImportError: No module named gtk

This time the missing module is gtk, but I know that emesene is written in Python, which the earlier "pygtk" is perhaps a reference to.  Thus, the connecting thread between all these programs, as near as I can tell, is Python.

Does anyone know what might have happened, and how I can fix it?

EDIT: just noticed that part of one transcript was turned into smilies.

---

### Post by Chronon on 2010-04-08
Was/is pygtk installed?

---

### Post by Nopantsman on 2010-04-08
According to "help('modules')", no, it isn't.  Not that that's a surprise, given the error messages Totem and Rhythmbox were giving.  What I'm wondering is why it isn't installed - surely a module essential to several pieces of included software would be included with the default installation.  Indeed, the fact that a previously working program is now broken suggests that pygtk (and gtk) were somehow removed.

How would I go about reinstalling this module, and how might it have been removed in the first place?

---

### Post by Chronon on 2010-04-08
You can use Synaptic or Software Center to install packages.  I'm not sure why it wasn't installed if you have packages that require it.  This should be handled by the package management system.

Maybe someone with a keener insight into your problem will stop by.

---

### Post by Nopantsman on 2010-04-09
I've tried using Synaptic, but this is a missing module, not a package (not that I could tell you what the difference is), and I can't seem to find any packages in Synaptic that seem to be the right thing.  Pygtk doesn't seem to have a package that Synaptic knows about.

If I can't figure this out, I may just switch back to Windows entirely, at least until I get a chance to do a fresh install of Ubuntu.

---

### Post by Chronon on 2010-04-09
The pygtk warning might be a red herring.  I have python-gtk2 but not pygtk and rhythmbox works on my netbook with 9.10.  (pygtk is a source package used to build python-gtk2 and several other packages.)

You can try 
```
sudo apt-get -f install
```
in terminal and see if it tries to fix any broken packages.

You can also try fixing broken packages in Synaptic via the Edit menu (it should do the same as the above command).

---

### Post by Nopantsman on 2010-04-09
Thanks for the suggestion.  Unfortunately, neither the command nor Synaptic's "fix broken packages" tried to repair anything.  I also tried using Synaptic to reinstall python-gtk2, but it didn't help.

I am one sad penguin.

---

### Post by Chronon on 2010-04-09
This topic seems similar:
[http://www.uluga.ubuntuforums.org/showthread.php?t=1438507](http://www.uluga.ubuntuforums.org/showthread.php?t=1438507)

Someone reports the same rhythmbox errors.  See if the command in comment #3 helps you.

---

### Post by Nopantsman on 2010-04-09
Thanks again.  Sadly, still no dice.

---

### Post by Chronon on 2010-04-09
Dang.  I'm about out of ideas.  Sorry.

---

### Post by Nopantsman on 2010-04-16
Bump!  Can anyone help me?! :(

---

### Post by Nopantsman on 2010-04-17
Bumping one last time.  If anyone has any ideas, I'd love to hear them.

---

### Post by Bachstelze on 2010-04-17
Just reinstall pygtk. ;) It *is* a separate package in Ubuntu (python-gtk2).

---

### Post by louis--taylor on 2010-04-17
Try:
```
sudo apt-get install python2.5 python-gtk2 python-gnome2
python-glade2
```Not sure if that will work but worth a try :)

or, 
```
sudo apt-get --reinstall install python2.5 python-gtk2 python-gnome2
python-glade2
```

---

### Post by Nopantsman on 2010-04-17
Thanks louis, but that didn't work either.

---

### Post by gordintoronto on 2010-04-17
Install Audacious. To make it the default for playing MP3s, right-click in Nautilus, select "properties," and one of the properties is the default program.

---

### Post by Nopantsman on 2010-04-17
> **gordintoronto said:**
> Install Audacious. To make it the default for playing MP3s, right-click in Nautilus, select "properties," and one of the properties is the default program.
I appreciate the suggestion, but the lack of the ability to play audio isn't really my problem.  (edit) VLC still works, and audio programs aren't the only ones that have stopped working.

---

### Post by louis--taylor on 2010-04-17
try:
```
sudo dpkg -r python-gtk2 python-gnome2
python-glade2
```and *then* run the commands I said up there /\

Or have a look at [http://tinyurl.com/y68qoge](http://tinyurl.com/y68qoge) or something along those lines...

---

### Post by Nopantsman on 2010-04-17
Hm.  That command spits out a long string of messages detailing which programs depend on those packages, then says that they were not removed.  Here's what it told me:

```
$ sudo dpkg -r python-gtk2 python-gnome2 python-glade2
[sudo] password for andrew: 
dpkg: dependency problems prevent removal of python-gtk2:
 software-properties-gtk depends on python-gtk2.
 usb-creator-gtk depends on python-gtk2 (>= 2.12).
 computer-janitor-gtk depends on python-gtk2.
 python-desktopcouch-records depends on python-gtk2.
 gnome-about depends on python-gtk2.
 onboard depends on python-gtk2.
 python-desktopcouch depends on python-gtk2.
 python-notify depends on python-gtk2 (>= 2.10); however:
  Package python-gtk2 is to be removed.
 python-aptdaemon-gtk depends on python-gtk2.
 totem-plugins depends on python-gtk2 (>= 2.13).
 gdebi depends on python-gtk2 (>= 2.6.3-2).
 emesene depends on python-gtk2 (>= 2.10).
 python-rsvg depends on python-gtk2.
 python-gtksourceview2 depends on python-gtk2 (>= 2.8.0).
 python-gtksourceview2 depends on python2.5-gtk2; however:
  Package python2.5-gtk2 is not installed.
  Package python-gtk2 which provides python2.5-gtk2 is to be removed.
 python-gtksourceview2 depends on python2.6-gtk2; however:
  Package python2.6-gtk2 is not installed.
  Package python-gtk2 which provides python2.6-gtk2 is to be removed.
 python-gnomekeyring depends on python-gtk2.
 python-webkit depends on python-gtk2.
 glchess depends on python-gtk2 (>= 2.10.0).
 gnome-codec-install depends on python-gtk2 (>= 2.10.1).
 checkbox-gtk depends on python-gtk2.
 gnome-orca depends on python-gtk2 (>= 2.10).
 python-vte depends on python-gtk2.
 ubuntuone-client-gnome depends on python-gtk2 (>= 2.10).
 alacarte depends on python-gtk2 (>= 2.13.0).
 python-gmenu depends on python-gtk2.
 python-gtkhtml2 depends on python-gtk2.
 python-sexy depends on python-gtk2 (>= 2.6.2).
 gnome-sudoku depends on python-gtk2 (>= 2.10.0).
 rhythmbox depends on python-gtk2 (>= 2.10); however:
  Package python-gtk2 is to be removed.
 software-center depends on python-gtk2.
 gedit depends on python-gtk2 (>= 2.12.0); however:
  Package python-gtk2 is to be removed.
 desktopcouch depends on python-gtk2.
 apport-gtk depends on python-gtk2 (>= 2.12).
 system-config-printer-gnome depends on python-gtk2.
 python-gnomeapplet depends on python-gtk2.
 language-selector depends on python-gtk2.
 python-ibus depends on python-gtk2.
 apturl depends on python-gtk2 (>= 2.6.3-2).
 gimp depends on python-gtk2 (>= 2.8.0).
 python-gtksourceview2 depends on python-gtk2 (>= 2.8.0).
 python-gtksourceview2 depends on python2.5-gtk2; however:
  Package python2.5-gtk2 is not installed.
  Package python-gtk2 which provides python2.5-gtk2 is to be removed.
 python-gtksourceview2 depends on python2.6-gtk2; however:
  Package python2.6-gtk2 is not installed.
  Package python-gtk2 which provides python2.6-gtk2 is to be removed.
 python-gtksourceview2 depends on python-gtk2 (>= 2.8.0).
 python-gtksourceview2 depends on python2.5-gtk2; however:
  Package python2.5-gtk2 is not installed.
  Package python-gtk2 which provides python2.5-gtk2 is to be removed.
 python-gtksourceview2 depends on python2.6-gtk2; however:
  Package python2.6-gtk2 is not installed.
  Package python-gtk2 which provides python2.6-gtk2 is to be removed.
dpkg: error processing python-gtk2 (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of python-gnome2:
 usb-creator-gtk depends on python-gnome2.
 gnome-about depends on python-gnome2.
 python-pyatspi depends on python-gnome2.
 gnome-orca depends on python-gnome2 (>= 2.6.2).
 rhythmbox depends on python-gnome2 (>= 2.18); however:
  Package python-gnome2 is to be removed.
 system-config-printer-gnome depends on python-gnome2.
dpkg: error processing python-gnome2 (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of python-glade2:
 software-properties-gtk depends on python-glade2.
 computer-janitor-gtk depends on python-glade2.
 checkbox-gtk depends on python-glade2.
 ibus depends on python-glade2.
 system-config-printer-gnome depends on python-glade2.
 apturl depends on python-glade2 (>= 2.6.3-2).
dpkg: error processing python-glade2 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 python-gtk2
 python-gnome2
 python-glade2
andrew@Lovelace-Linux:~$ sudo apt-get install python2.5 python-gtk2 python-gnome2 python-glade2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python2.5 is already the newest version.
python-gtk2 is already the newest version.
python-gnome2 is already the newest version.
python-glade2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
```

---


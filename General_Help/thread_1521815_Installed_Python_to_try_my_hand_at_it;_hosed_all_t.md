---
title: "Installed Python to try my hand at it; hosed all the Python apps on my system."
date: 2010-07-01
forum: General Help
---

### Post by snurfle on 2010-07-01
Apologies if this is double-posted...
I tried to post it in the "Programming" section, but for some reason it is not allowing me to post, so I will try here...

Yes, I did read the FAQ...

I have been a VB programmer for years, a Linux user for 5 years, and have been dabbling in GAMBAS for about a year.
I decided to try my hand at Python the other day...
I downloaded 2.6.5 from python.org, and installed it on my machine (Lucid running on a Dell Inspiron B120, no dual boot, just a straight up Linux machine).
I played around with the tutorials on the python site; tried the "Hello World" app, a few math functions and some string functions. All seemed well.
I decided to play a sudoku before bed, and for some reason the program would not launch... just the spinning "waiting" cursor which would then disappear after about 10 seconds.
Hmmmm.
I rebooted my machine this morning after a kernel update, and now...

No desktop icons at all
I cannot launch nautilus either from menus or from the command line
Most of the apps in AWN are not working
Sudoku and Chess do not launch
I do not know what else is broken; but the AWN apps and the 2 games are written in python, which leads me to believe that installing Python on my system somehow hosed the applications which use Python...

I tried reinstalling sudoku just to see if that would help out... but it did not.

My system is essentially unusable at this point other than a few applications... (Chrome, for one!)...

Any idea how to proceed from here?

Thanks.

---

### Post by oldfred on 2010-07-01
Phthon 2.6.4 is the standard version inside 9.10 which I am on right now. Almost the entire system runs on python and if you uninstall it your system will not work.

I would try to reinstall the desktop if you can get to a command line.

apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

You could just try 
sudo apt-get install python
or
sudo apt-get install --reinstall python


The installed python package is linked to python folder so the link may be broken or set to your new version which is not set up correctly?

---

### Post by snurfle on 2010-07-01
wow... good timing!
I didnt realize that the python programming interface was already installed, and nothing at python.org indicated that i already had the functionality as part of lucid (shouldnt that be in big flashing lights?)
I posted this thread 3 different times this morning, but for some reason it just never appeared that i had posted it at all, then i spent an hour trying to get logged back in to the forums, but i kept getting a "not authorized" message... finally got fed up with the whole mess and walked away for a few hours...
just got back and tried asking the question on the python irc channel, and here is the reply i got...

> as root or via sudo run this command:
rm -rf /usr/local/lib/python2.6 /usr/local/include/python2.6 /usr/local/bin/python 

Then run hash -r and logout

in your shell you might run hash -r once too, but after that you'll all fixed up
copy and paste that rm command EXACTLY like it is or bad things could happen

I rebooted, and everything appears to be fine!

After rebooting is when I got your reply... Thx for the assist!  :)

---


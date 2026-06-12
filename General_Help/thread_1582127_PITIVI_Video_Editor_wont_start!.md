---
title: "PITIVI Video Editor wont start!"
date: 2010-09-26
forum: General Help
---

### Post by Vigh on 2010-09-26
this was an ia32libs problem, now fixed in latest updates

Hi, tried to remove and purge and reinstall through terminal. No success.

PITIVI is installed but when I click on the launcher in the applications menu nothing happens. 

Regards

Ant

---

### Post by 3rdalbum on 2010-09-26
> **Vigh said:**
> Hi, tried to remove and purge and reinstall through terminal. No success.

Did you try removing Pitivi's preferences files? They are in ~/.config/pitivi and ~/.pitivi. Removing a package will still retain its per-user settings files, which can sometimes cause crashes if they are corrupt.

> PITIVI is installed but when I click on the launcher in the applications menu nothing happens.

Do you get an error message if you run Pitivi from the terminal? (literally, type 'pitivi' into the terminal to run it)

I had a similar problem after I installed RGBA (transparency) on my system. Pitivi must be added to your RGBA blacklist. If running Pitivi from the terminal says "X error", then you should either disable RGBA or add Pitivi to the RGBA blacklist.

---

### Post by Vigh on 2010-09-26
Says PyGTK could not be found! "No module named pygtk'

I did install python2.4 recently as i have a program that isn't supported by the new version 2.6/2.8, would that have anything to do with the error? Although python 2.8 should still be running along side 2.4.

---

### Post by Vigh on 2010-09-26
Okay now skype is not loading either, when I run skype in terminal it comes up with a similar warning- GTK WARNING!

---

### Post by bharathwaaj on 2010-11-02
Latest python is required and it is taking the old version. Assuming yours is installed in /usr/local/bin.

```
sudo mv /usr/local/bin/python /usr/local/bin/pythonorig
```Now it will start taking the latest installed python.

If you want to use python2.4 use the command

```
 > python2.4 application.py 
```

when running applications which depend on it.

---

### Post by omelette on 2010-11-06
This has got to be the buggiest piece of s/w in existence!  Installed via Ubuntu's software Manager, it worked but I could not get it to 'render' videos - no error message, nothing, it just sits there!  I therefore removed it and reinstalled the most up-to-date 'stable' version - and I experienced what's being reported here - now it won't even run!

Undeterred, I tried installing it on my laptop which runs Fedora.  Hurray, it runs!  My joy was sort-lived though.  For starters, clicking the Play/Pause button doesn't show the button alternating between the two modes, though it does work - intermittent and a somewhat trivial complaint I admit.  Much more serious, it seems easy to cause the whole app to lock up just by playing with the video-playback buttons.  Maddeningly, every time you click the 'Render' button, all of the selected settings are lost and must by set again, every-time! The Rendering itself (the most important part) is unbelievably flaky - occasionally it works, more often than not it doesn't!  When it doesn't there is no clue from the program itself that there is anything wrong, the only way is to keep an eye on System Monitor's CPU-load to see if there is actually any rendering taking place!  Very often, it will start to render but does only a few frames before stopping and just sitting there, again with no suggestion that anything is wrong.

What I can't figure out is why has Ubuntu started including something this flaky by default with the OS.  Though I never used it much, the video editor 'Lives' performed much much better, so would be a far better choice.  It doesn't reflect well on the OS itself to be including applications that perform this poorly...

---

### Post by Vigh on 2010-11-06
All good now, no problems, I wiped my HDD and did a fresh buntu install, reason why it wasn't starting for me was I was running python 2.4 and GTK1.2 instead of the latest version to get an old version of audacity to work with JACK which is now not an issue at all as I'm going to run the audio software on a virtual machine in the background. 

Ant :-)

---


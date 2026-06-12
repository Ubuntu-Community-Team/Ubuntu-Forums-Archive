---
title: "Repair unfinished install in Software Center"
date: 2009-10-30
forum: General Help
---

### Post by OleR on 2009-10-30
Hey everyone, 

I tried to install eclipse using the software center. Somewhere in the middle of the download, the system crashed because I was fiddling around somewhere else. When I rebooted, software center indicates eclipse as installed. I tried to launch it, which does not work (of course - the download was not finished). I looked for a reinstall or repair option - no luck. I thus decided to remove eclipse using software center again which worked. When I then tried to reinstall, the progress bar moves suspiciously quick. I still can't launch (as if it reinstalled the incomplete download). What can I do to really start over?

Cheers
Ole

---

### Post by nothingspecial on 2009-10-30
In your menu go accessories > terminal and type


```
sudo apt-get install -f
```

You`ll have to type your password but you won`t see it.

Post back if that doesn`t work

---

### Post by Earl_Maroon on 2009-10-30
Try```
sudo dpkg -a --reconfigure
```

---

### Post by OleR on 2009-11-05
Thanks for your replies. Unfortunately it did not work. I have the german version so I rougly translate what I got:

sudo apt-get install -f

...
The following packages were installed automatically and are not longer needed:
  eclipse-rcp libswt-gtk-3.5-jni java-common libaccess-bridge-java-jni
  libaccess-bridge-java icedtea-6-jre-cacao eclipse-platform-data
  libequinox-osgi-java default-jre openjdk-6-jre-headless tzdata-java
  openjdk-6-jre libjline-java openjdk-6-jre-lib rhino default-jre-headless
  libswt-gtk-3.5-java ca-certificates-java
Use »apt-get autoremove« to remove them.
0 updated, 0 newly installed, 0 to remove and 3 not updated.

After that, I could again use software center to install eclipse, but it would do the same as before: Quickly telling me its installed but then not working.

I then tried 

sudo dpkg -a --reconfigure

which would simply tell me the option reconfigure does not exist. The --help message does not mention anything the like either.

Any other suggestions?

---

### Post by pastalavista on 2009-11-05
> **Earl_Maroon said:**
> Try```
sudo dpkg -a --reconfigure
```

The code should be```
sudo dpkg-reconfigure -a
```
it could take a while..

---

### Post by OleR on 2009-11-05
I now did the simplest of all solutions: I removed eclipse using the software center, and then installed it using aptitude - runs perfect. Doesn't really explain why I didn't get it to work with software center, but at least its all working now.

---

### Post by nipunshakya on 2011-09-07
> **OleR said:**
> I now did the simplest of all solutions: I removed eclipse using the software center, and then installed it using aptitude - runs perfect. Doesn't really explain why I didn't get it to work with software center, but at least its all working now.


Sometimes, things that seem complex work out pretty well with simple solutions...:)

---


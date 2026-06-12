---
title: "Google Earth Fonts VERY Ugly"
date: 2011-06-01
forum: General Help
---

### Post by WildZontar on 2011-06-01
I'm having a problem with a new installation of Google Earth on Ubuntu 11.04. The fonts look VERY ugly. Is there something I'm supposed to do or install? I already have ttf-mscorefonts installed or whatever it was.


[IMG]http://db.tt/rMOgz1x[/IMG]

---

### Post by linuxinstalledfromhdd on 2011-06-01
Uninstall it and reinstall it from the Google Earth PPA repository like this:

[http://cinderbox.net/2011/05/11/how-to-install-google-earth-on-ubuntu-11-04-natty-narwhal-ppa/](http://cinderbox.net/2011/05/11/how-to-install-google-earth-on-ubuntu-11-04-natty-narwhal-ppa/)

---

### Post by WildZontar on 2011-06-01
Did it. No change.

---

### Post by linuxinstalledfromhdd on 2011-06-01
You needed to use a walkthrough when you installed your version of Ubuntu.

You forgot to install:

sudo apt-get install ttf-mscorefonts-installer

Try using a walkthrough or guide to make sure you have everything installed on your system you are going to need probably. 

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

Here is one for the older version 10.10:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by AlphaLexman on 2011-06-01
See this fix, worked for me on 9.10.
[Google Earth Menu's & Text Oversized in Linux Ubuntu 9.10]("http://www.google.com/support/forum/p/earth/thread?tid=078d0b530dd9254e&hl=en")

---

### Post by WildZontar on 2011-06-01
This did not work for me either. I recieved an error about libraries when attempting to load.

I will use windows in my dualboot to use GE instead.

---

### Post by AlphaLexman on 2011-06-01
Please post the error you received.

---

### Post by nerdy_kid on 2011-06-01
try:

```


export LD_PRELOAD=/usr/lib/libfreeimage.so.3

LD_LIBRARY_PATH=/usr/lib:.:$LD_LIBRARY_PATH /opt/google/earth/free/googleearth-bin "$@"


```

try each line separately in a terminal.  If it works, then I'll tell you how to make it permanent.

---

### Post by linuxinstalledfromhdd on 2011-06-01
> **WildZontar said:**
> This did not work for me either. I recieved an error about libraries when attempting to load.

I will use windows in my dualboot to use GE instead.

Wow. Did you uninstall it before you tried to fix it? Did you use the PPA I gave you? 

Did you install the stable one from the PPA? 

Make sure you check out the walkthrough I sent you.  Goodluck.

---

### Post by sundar_ima on 2011-06-03
Here is the solution.

Do all with sudo:
1) go to /opt/google/earth/free
2) rm -rf libcurl.so.4 libGLU.so.1 libnss_mdns4_minimal.so.2 libQtCore.so.4 libQtGui.so.4 libQtNetwork.so.4 libQtWebKit.so.4 # we will use system libraries instead of these ones
3) edit googleearth, add line "export LD_PRELOAD=libfreeimage.so.3" before line 'LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH ./googleearth-bin "$@"'
4) copy libfreeimage.so.3 and plugins/ from [http://goo.gl/GxLQw](http://goo.gl/GxLQw) (and libphonon.so.4, if running on x86_64) to /opt/google/earth/free

Solution was found on this page
[http://www.google.com.tw/support/forum/p/earth/thread?tid=3fe67ea84f63bcd8&hl=en](http://www.google.com.tw/support/forum/p/earth/thread?tid=3fe67ea84f63bcd8&hl=en)

---

### Post by linuxinstalledfromhdd on 2011-06-03
Uninstall any googleearth you have on your system from synaptic package manager. Right click on it and select "completely remove from system".

In synaptic go to 'Settings', 'Repositories', 'Other Software', and enable the partner and independent repositories by clicking their checkboxes. Close out of synaptic. 

In terminal run:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ttf-mscorefonts-installer

```In terminal run:

```

wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb http://dl.google.com/linux/earth/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt-get update
sudo apt-get upgrade

```And then run this in terminal:

```
sudo apt-get install google-earth-stable lsb-core ia32-libs
```

---

### Post by nerdy_kid on 2011-06-03
> **sundar_ima said:**
> Here is the solution.

Do all with sudo:
1) go to /opt/google/earth/free
2) rm -rf libcurl.so.4 libGLU.so.1 libnss_mdns4_minimal.so.2 libQtCore.so.4 libQtGui.so.4 libQtNetwork.so.4 libQtWebKit.so.4 # we will use system libraries instead of these ones
3) edit googleearth, add line "export LD_PRELOAD=libfreeimage.so.3" before line 'LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH ./googleearth-bin "$@"'
4) copy libfreeimage.so.3 and plugins/ from [http://goo.gl/GxLQw](http://goo.gl/GxLQw) (and libphonon.so.4, if running on x86_64) to /opt/google/earth/free

Solution was found on this page
[http://www.google.com.tw/support/forum/p/earth/thread?tid=3fe67ea84f63bcd8&hl=en](http://www.google.com.tw/support/forum/p/earth/thread?tid=3fe67ea84f63bcd8&hl=en)

I've tried rming the custom libraries but it caused a seg fault for me before, maybe that is fixed now though.

---

### Post by Reeman on 2011-07-14
The fix mentioned in post #10 is finally one that seems to work. Using system font rendering rather than msttf is really the only sensible answer. I set up my nvidia control to anti-alias for lcd and wow does googleearth ever snap and look good at the same time. :rolleyes: Must have been an actual google linux coder that figured that one out...without seeing the original code it would have been nothing better than a guessing game!

---


---
title: "getting adobe to work properly"
date: 2010-05-05
forum: General Help
---

### Post by mick463 on 2010-05-05
Hi i have just installed 10.04 64 bit onto my computer.I then used the command 
sudo apt-get install ubuntu-restricted-extras  to install adobe flash it seemed to work untill i went to use the play button in the window.It will not allow me to use the buttons in the window to play or pause etc,i tried to use a different site (cisco.netacad.net)which requires flash and all works well until i try to select a chapter or launch anything.I am at a loss some one told me it might be a javascript problem in firefox is this tru PLEASE HELP i have to read my cisco chapters and i cant afford windows and i like this ubuntu release.Thankyou in advance.

---

### Post by no2498 on 2010-05-05
do a search for 64 bit flash
it is diff than the 1 you have installed 

hope this helps

---

### Post by cdenley on 2010-05-05
I had this problem as well until I installed the 64-bit flash pre-release.
```

sudo apt-get remove flashplugin-installer
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
mkdir ~/.mozilla/plugins
cd ~/.mozilla/plugins
tar xzfv ~/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz

```
restart firefox

Ubuntu still uses a wrapper for the 32-bit flash plugin, which apparently has some issues.

---

### Post by mick463 on 2010-05-08
Hi did what you said and now i have you tube working properly but  firefox crashes at the login screen of cisco.netacad.net and  google chrome works fine with everything.Am at a loss i know it is a browser issue but have no idea what it is.If anyone knows how to fix this i would realy like to know.Thank you.

---

### Post by phpadik on 2010-05-08
You might want to try this out. [http://conradmiguel.com/install-flash-player-10-on-ubuntu-10-04-64-bit-lucid-lynx](http://conradmiguel.com/install-flash-player-10-on-ubuntu-10-04-64-bit-lucid-lynx)

---

### Post by mick463 on 2010-05-08
Thank you but firefox is still crashing at the cisco.netacad.net site.It gets to the login screen where i put in my username and password then the browser just shuts down.

---

### Post by lidex on 2010-05-08
You may have conflicting plugins. Try this in a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
```

Now go here and download flash-installer:
[http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")

---

### Post by mick463 on 2010-05-09
thanks for the effort but it did not make any difference at all

---

### Post by mscout2004 on 2010-05-09
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591) 64bit flash updated

---

### Post by mick463 on 2010-05-09
i did the $ cat /proc/cpuinfo | grep lahf_lm and got no output which according to the site means that i have an older cpu which i do (pentium 4)will try the fix when i get back from my mothers (mothers day in aus)and i will let you know how i go and thank you for all your help.

---


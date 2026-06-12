---
title: "Restore login page icon in Lucid"
date: 2010-05-04
forum: General Help
---

### Post by bigwoof on 2010-05-04
Hi there,

I have just upgraded from Karmic to Lucid and have an issue with the login screen.  It defaulted to show the edubuntu logo.  this is probably because I tested the edubuntu packages on my system and it thought it was a edubuntu system.  

I went into 
/usr/share/pixmaps/splash 
and replaced the edubuntu-splash.png file with the Ubuntu logo png (i renamed the file).

Unfortunately this did not work and now I have a login screen with a "no image" icon.

Anybody have some thoughts to restore this?

Cheers

Phil

---

### Post by dino99 on 2010-05-04
gconf-cleaner

then reset your png

---

### Post by warfacegod on 2010-05-04
Use Synaptic to Reinstall usplash-theme-ubuntu

---

### Post by bigwoof on 2010-05-04
dino99 - I installed and ran gconf-cleaner, but I am unsure how to reset the png as the method I tried didnt seem to work, please can you explain how i should do this.

warfacegod - I went into synaptic usplash-theme-ubuntu was not installed, when I tried to maek it for installation it said that it conflicted with a number of packages already installed and that they would need to be removed, so I didnt proceed.

Cheers

Phil

---

### Post by WorMzy on 2010-05-04
> **warfacegod said:**
> Use Synaptic to Reinstall usplash-theme-ubuntu

Lucid doesn't use usplash, and this is a login screen query..? :S

I haven't tried this myself, but does [this link]("http://laptopny.us/ubuntu-tips/how-to-change-login-screen-background-on-lucid-lynx-ubuntu-10-04") help?

---

### Post by bigwoof on 2010-05-05
Hi WorMzy,

I tried that earlier and was able to change the background however it did not help with the icon :(

Cheers

Phil

---

### Post by bigwoof on 2010-05-10
Bump

---

### Post by warfacegod on 2010-05-11
I don't know if this works in Lucid. Its excellent for Karmic.

[http://ubuntuforums.org/showthread.php?t=1358026]("http://ubuntuforums.org/showthread.php?t=1358026")

---

### Post by bigwoof on 2010-05-11
Hi warfacegod,

I tried the tool you suggested but it gave no option to change the Icon (otherwise it is a cool tool).  If I get desperate enough I can create my own Icon set to replace the "no Graphic" icon with an ubuntu icon and apply the icon set to the login page only with the tool.  A bit of a hack but it may work.  

Cheers

Phil

---

### Post by bigwoof on 2010-05-16
If anybody is interested, I solved the issue. Well kind of...
I reconfigured the login screen to use a different icon set then I replaced the image-missing.svg file with the ubuntu logo svg, and now it looks new and shiny.  I will probably do a fresh install next release 

Cheers

Phil

---

### Post by Ichido on 2010-05-18
To change the Login Logo and/or the Background, use Ubuntu-tweak which you get from Synaptic Package Manager!
Tweak does more than just the Login Screen.

---

### Post by warfacegod on 2010-05-18
Unless its a recent edition Ubuntu Tweak isn't available in Synaptic. Excellent tool, I use it myself.

---

### Post by Ichido on 2010-05-18
I installed ubuntu-tweak from Synaptic just yesterday.
You can also get it at:
[http://www.getdeb.net/updates/ubuntu/10.04/?page=3](http://www.getdeb.net/updates/ubuntu/10.04/?page=3)

---

### Post by warfacegod on 2010-05-18
This must be new for 10.04 because, to be certain, I uninstalled it from my 9.10 and looked for it in Synaptic. Definitely not there.

It is also, by the way, available on Ubuntu Tweak's main page.

---

### Post by bigwoof on 2010-05-18
Thank you. 

I already had tweak installed but I didnt know of this feature.  Thanks It has solved my problem :)

and it is more elegant than my hack.

Cheers

Phil

---

### Post by warfacegod on 2010-05-20
@ichido: I just booted into my 10.04 install and checked Synaptic. no Ubuntu Tweak. I'm guessing you got it, through Synaptic, by having a PPA enabled.

---


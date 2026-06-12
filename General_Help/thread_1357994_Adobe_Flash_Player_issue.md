---
title: "Adobe Flash Player issue"
date: 2009-12-17
forum: General Help
---

### Post by cjwescott on 2009-12-17
I am trying to view a video on youtube through firebox and the need to download the latest flash player pops up.  I have 10.42.34 already installed and it is asking me to install that same version.

All was fine just the other day and now this.

Any ideas?

Chris

---

### Post by ean5533 on 2009-12-17
> **cjwescott said:**
> I am trying to view a video on youtube through firebox and the need to download the latest flash player pops up.  I have 10.42.34 already installed and it is asking me to install that same version.

All was fine just the other day and now this.

Any ideas?

Chris

Type the following into the address bar and hit enter:

```
about:plugins
```

Find where it says "Shockwave Flash" and post what version it is.

Also, are you on 64-bit or 32-bit Ubuntu?

---

### Post by cjwescott on 2009-12-17
It says the following:

File name:  npwrapper.libflashplayer.so Shockwave Flash 10.0 r42I am running 64 bit.

---

### Post by ean5533 on 2009-12-17
> **cjwescott said:**
> It says the following:

File name:  npwrapper.libflashplayer.so Shockwave Flash 10.0 r42I am running 64 bit.
That's the right version, and firefox definitely acknowledges that it exists. Let's just try a basic uninstall and reinstall. Shut down firefox and all other running web browsers and run this in a terminal:

```
sudo apt-get update && sudo apt-get purge flashplugin-nonfree nspluginwrapper flashplugin-installer && sudo apt-get install flashplugin-nonfree
```

Say yes when it prompts you to delete flash and then yes when it asks you to reinstall. Load up firefox and check to make sure flash still shows up in about:config afterwards. Then, load up a fresh youtube video and see how it goes.

---

### Post by cjwescott on 2009-12-17
I determined the culprit.

I installed the plugin Noscript the other day.  It apparently is preventing the flashplayer from being recognized.  One I uninstalled, and only if I uninstalled does everything go back to normal.

thx for the help. 

Edit: Man you sure know your command line.  How long have you been using Ubuntu?

Chris

---


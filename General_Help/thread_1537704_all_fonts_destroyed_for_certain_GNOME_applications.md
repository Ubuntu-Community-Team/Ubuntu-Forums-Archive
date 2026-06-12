---
title: "all fonts destroyed for certain GNOME applications"
date: 2010-07-23
forum: General Help
---

### Post by gtmarks on 2010-07-23
After building pango-1.28.1 and cairo-1.8.10 from source in an unsuccessful attempt to build graveman-0.3.12-5 (due to inability to configure gtk+-2.20.1), various GNOME applications display empty boxes where text should be.  Three screenshots to illustrate (for Rhythmbox, System->Preferences->Appearance dialogue box, and  System->Preferences->Sound dialogue box) are posted at:

  [http://gmarks.co.cc/Screenshot-0.png](http://gmarks.co.cc/Screenshot-0.png)
  [http://gmarks.co.cc/Screenshot-1.png](http://gmarks.co.cc/Screenshot-1.png)
  [http://gmarks.co.cc/Screenshot-2.png](http://gmarks.co.cc/Screenshot-2.png)

Can anyone help suggest how to fix this mess?

---

### Post by gtmarks on 2010-07-24
Note: after reboot, problem is much worse--even affects login screen.  Updated screenshot (URLs above) to reflect exacerbated problem.  Any solution will have to be via command line, since I can only use the affected computer via ssh.  Current problem seems similar to that described here:

  [http://www.linuxquestions.org/questions/linux-general-1/system-fonts-are-gone-146824/](http://www.linuxquestions.org/questions/linux-general-1/system-fonts-are-gone-146824/)

(which, disconcertingly, has not been resolved in the last six years).  The packages listed there bear some similarities to those I attempted to install.  In my case: gtk+-2.20.1 failed to install, pango-1.28.1 installed, atk-1.30.0 installed (in each case from source).

---

### Post by pzkfw on 2010-07-24
Try using apt-get to completely remove and install GNOME.

```
apt-get remove --purge gnome-desktop; apt-get install gnome-desktop
```

---

### Post by gtmarks on 2010-07-24
Thank you for the suggestion.  I assume you meant:

```

sudo apt-get remove --purge gnome-desktop-environment
sudo apt-get install gnome-desktop-environment

```(There does not seem to be a package gnome-desktop.)  Unfortunately, after trying the above commands and restarting, the problem remains, with no change.

---

### Post by gtmarks on 2010-08-03
The denouement can be found here:

[HTML]http://www.linuxquestions.org/questions/linux-desktop-74/all-fonts-destroyed-for-certain-ubuntu-gnome-applications-821807/[/HTML]

---


---
title: "Firefox 3.5 64 bit can't play flash"
date: 2009-07-21
forum: General Help
---

### Post by AceMilo on 2009-07-21
I was running firefox 3 and flash was fine and updated today to 3.5 via ubuntuzilla.  The install went fine and firefox works fine, except flash.  I tried the guide here and it didn't work:

[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

No matter what I do I can't seem to get it working.  When I go to sites like youtube I get this error: "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player."

Any help is appreciated.

---

### Post by Rob_H on 2009-07-21
I'm not sure about the installation from Ubuntuzilla, but I can confirm that the 64-bit Flash pre-release works fine with the **firefox-3.5** package from the Ubuntu Jaunty repository. I'm watching Hulu right now as I type this. Just make sure the **libflashplayer.so** file exists under **~/.mozilla/plugins**. Good luck!

---

### Post by AceMilo on 2009-07-21
Rob yes I tried that, doesn't work.  The 3.5 in the repo is beta, at least for me, and still says shriecto or whatever it's called.  I made the plugins dir and put the file in there, doesn't work.  I uninstalled 3.5 and I'm back on 3 from the repo and flash is fine for now, but I really want 3.5.

---

### Post by Rob_H on 2009-07-21
The **firefox-3.5** package is not beta. It doesn't have the Firefox branding--apparently a conscious decision to differentiate it from the officially supported version--but it is, in fact, 3.5.1 as of now.

In any case, perhaps there is more than one pre-release version of 64-bit Flash out there. The md5sum of my copy is 1957a3414dfbfe5f7de000ae72da4cb6 and in the **about: plugins** page in Firefox, it identifies itself as 10.0 r22.

---

### Post by AceMilo on 2009-07-21
I installed shiretoko and it is indeed updated and flash does work.  It's kind of annoying to have a blue icon but whatever, it works.  Thanks.

---

### Post by Rob_H on 2009-07-22
Glad it worked. Perhaps the Ubuntuzilla version is not looking for plugins at that location. If you want to go back to it, you could try copying the library to its shared plugins directory (probably "<firefox_install_dir>/plugins").

On the other hand, the package from the repos seems to work well. You can always change the icon/name in the menu and point the "firefox" symlink to "firefox-3.5". Then it's almost the same.

---

### Post by nanotube on 2009-07-22
Hi
ubuntuzilla installs the mozilla build, which is 32bit, so you have to manually take 32bit flash plugin and stick it into the plugins directory. 

See this thread for more details:
[http://ubuntuforums.org/showthread.php?t=1175961](http://ubuntuforums.org/showthread.php?t=1175961)

consider also using the firefox PPA, which will get you a 64bit testing build from the ubuntu mozilla team.

---


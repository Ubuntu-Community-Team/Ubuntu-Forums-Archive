---
title: "Freezing on ubuntu logo page"
date: 2009-09-29
forum: General Help
---

### Post by thedoctor81877 on 2009-09-29
I restarted my netbook, & when it came back up, it froze on the intro page (the one w/ the ubuntu logo), & I haven't been able to get it to come back up. I restarted again & hit esc, & did a recovery mode, then entered normal mode, but it started up in the command line. When I go to restart, it just takes me back to the command line, same for shut down - & when I manually power down, it freezes up again. Any help??? BTW, I am using Karmic Koala Alpha 6.

-Michael


And now, I cannot even mount a USB stick to re-install UNR 9.04. What gives???

---

### Post by samthehobbit on 2009-09-29
Hi Michael,

I had a similar problem today. The (temp) fix for that was to let it boot until it appeared to have hung, then switch to tty1, login and 'sudo restart gdm'.

Hope that helps.
- Sam

---

### Post by sandpvrr on 2009-09-30
Hello All, 
         Had the same issue - I switch to xterm instead of Gnome and with a network cable plugged in I was able to run sudo apt-get update and sudo apt-get upgrade
          Immediately an update was installed to the splash screen and my machine booted normally into Gnome again. I did notice a lack of sound card support (Eee PC 900A - 2 GB ram - 4GB SSD) but a partial upgrade was also immediately offered through Update Manager once Gnome booted. Installing that now.
          -Joey

---

### Post by sandpvrr on 2009-09-30
Hello Again,
      Took a while, but the partial upgrade completed and magically my sound card started working again. WLAN card still working and all appears to be good. I'm no developer, but I'd suspect I got an updated soundcard driver then upgraded the kernel which supported it. 
       Enjoy! 
       -Joey

---


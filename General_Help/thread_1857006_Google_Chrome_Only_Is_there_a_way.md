---
title: "Google Chrome Only? Is there a way?"
date: 2011-10-09
forum: General Help
---

### Post by jwhitney83 on 2011-10-09
Is there a way to have Google chrome installed only? When I uninstall Firefox it install chromium, and visa-versa.

Is it at all possible to have Google chrome only?

---

### Post by jonkiribati on 2011-10-09
you can create a bash script to do that if you'd like.

---

### Post by IWantFroyo on 2011-10-09
Google Chrome isn't recognized as a browser. I can't really help you get it to be recognized as one.

However, Chromium is the same thing as Chrome, so you can use that.

Or you can just tell Chrome not to bother you about default browsers, and have two browsers on your system (which is usually a good idea, in case one bombs).

---

### Post by snowpine on 2011-10-09
What is the benefit to uninstalling Firefox, I'm curious?

---

### Post by jwhitney83 on 2011-10-09
> **snowpine said:**
> What is the benefit to uninstalling Firefox, I'm curious?

Don't like it and don't use it. Prefer Google Chrome.

---

### Post by jwhitney83 on 2011-10-09
> **jonkiribati said:**
> you can create a bash script to do that if you'd like.

How would I go about doing this? is there already one in existence?

---

### Post by pr3zident on 2011-10-09
> **jwhitney83 said:**
> How would I go about doing this? is there already one in existence?

Try this website for installing Google chrome - [http://blog.sudobits.com/2011/04/23/how-to-install-google-chrome-on-ubuntu-11-04/](http://blog.sudobits.com/2011/04/23/how-to-install-google-chrome-on-ubuntu-11-04/)

---

### Post by jwhitney83 on 2011-10-09
> **pr3zident said:**
> Try this website for installing Google chrome - [http://blog.sudobits.com/2011/04/23/how-to-install-google-chrome-on-ubuntu-11-04/](http://blog.sudobits.com/2011/04/23/how-to-install-google-chrome-on-ubuntu-11-04/)

I already have Google chrome installed, its the uninstalling Firefox and chromium part that I need to figure out. I want Google chrome installed only.

---

### Post by jwhitney83 on 2011-10-09
bump

---

### Post by hollowsyndicate on 2011-10-09
do u have firefox or chromium installed atm?

---

### Post by jwhitney83 on 2011-10-09
> **hollowsyndicate said:**
> do u have firefox or chromium installed atm?

Yes chromium, there is no choice its one or the other. I wanted to uninstall them both and have Google Chrome only.

---

### Post by hollowsyndicate on 2011-10-09
> **jwhitney83 said:**
> Yes chromium, there is no choice its one or the other. I wanted to uninstall them both and have Google Chrome only.

u can do it. i did it with 11.04 but its kinda complicated. do u want google chrome only that much?

---

### Post by jwhitney83 on 2011-10-09
> **hollowsyndicate said:**
> u can do it. i did it with 11.04 but its kinda complicated. do u want google chrome only that much?

I like minimum, if I don't use it. I see no need for it to be installed. How did you do it?

---

### Post by VinDSL on 2011-10-09
If it was me, I'd open Synaptic, do a search for chromium OR firefox, and completely remove them that way. ;)


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-9-oct-2011(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-9-oct-2011.png")[/INDENT]

---

### Post by jwhitney83 on 2011-10-09
> **hollowsyndicate said:**
> u can do it. i did it with 11.04 but its kinda complicated. do u want google chrome only that much?

hollowsyndicate solved the problem here is the procedure:

Firefox:
sudo apt-get install firefox
sudo apt-get autoremove && sudo apt-get autoclean
open software sources untick everything in the 1st n 2nd tab
sudo apt-get purge firefox

Chromium:
sudo apt-get install chromium-browser
sudo apt-get autoremove && sudo apt-get autoclean
open software sources untick everything in the 1st n 2nd tab
sudo apt-get purge chromium-browser

SOLVED Thanks to hollowsyndicate.

---


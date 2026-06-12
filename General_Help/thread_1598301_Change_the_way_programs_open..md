---
title: "Change the way programs open."
date: 2010-10-16
forum: General Help
---

### Post by jameshampshire on 2010-10-16
How do i change preferred things like say on kubuntu and i use msn and i click the email button which should do what it does on ubuntu and open a new tab with mozilla.
But on this it opens with konqueror instead of mozilla and i want to change that.

---

### Post by gnush on 2010-10-16
Does Preferred Applications exist in the settings menu in Kubuntu?

---

### Post by jameshampshire on 2010-10-16
Nah it doesn't I'm still looking but can't find anything.

---

### Post by jameshampshire on 2010-10-18
bump

---

### Post by schnelle on 2010-10-18
System settings>Default Applications>Web browser and choose firefox.

---

### Post by jameshampshire on 2010-10-18
Already tried that.
Emesene still opens with konqueror and not mozilla.
On Ubuntu it opens perfect with mozilla.
Still bumping for help.

---

### Post by Zorael on 2010-10-18
You can set default applications in two places, and it's really up to each program to decide which to listen to. One is in System Settings -> Default Application. Technically *all* KDE programs should prefer that way.

The other is by setting the **x-www-browser** *alternative* to whatever browser you prefer.

```
$ **sudo update-alternatives --config x-www-browser**
There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                       Priority   Status
------------------------------------------------------------
* 0            /usr/bin/chromium-browser   40        auto mode
  1            /usr/bin/chromium-browser   40        manual mode
  2            /usr/bin/rekonq             40        manual mode

Press enter to keep the current choice[*], or type selection number:
```
I don't have Firefox installed so it's not listed for me. But run that command ('**sudo update-alternatives --config x-www-browser**') and see what it says.

---


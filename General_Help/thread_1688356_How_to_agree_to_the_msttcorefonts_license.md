---
title: "How to agree to the msttcorefonts license?"
date: 2011-02-15
forum: General Help
---

### Post by InquisitiveErin on 2011-02-15
OK, so I noticed that my Microsoft fonts had disappeared in OpenOffice (although they worked fine a couple weeks ago). I tried to install msttcorefonts several times, only to find that it was already installed. I then did some searching around and discovered that the only file in my msttcorefonts directory was a readme that said this:

> License refused.

Please reinstall the ttf-mscorefonts-installer package, e.g. via
 apt-get install --reinstall ttf-mscorefonts-installer
to get prompted for the license again.So, I typed that into the terminal:

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```and now this has happened:

[IMG]http://i1212.photobucket.com/albums/cc447/emmy-91/pckgconfig.png[/IMG]
 
I may be completely terminal-retarded, but how do I agree? Clicking on that box does nothing, and I can't type anything, even when I maximize the terminal window to fill the whole screen. Thanks in advance. :)

---

### Post by howefield on 2011-02-15
Use the tab key to highlight the OK button, and press enter.

---

### Post by InquisitiveErin on 2011-02-15
Amazing that I couldn't figure that out myself. :roll: Got all my MS fonts now. Thanks!

---


---
title: "VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (r"
date: 2011-11-02
forum: General Help
---

### Post by MonocleMike2 on 2011-11-02
mike@mikelap:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)

At the moment my system (11.10) is using the default driver and does not detect the display type.  It works OK.  Is there a specific driver for this card and will it work?  Will it provide anything better?  I use the machine for browsing the web and watching videos.  I don't play games.
If I decide to try a new driver, how do I get back to the current system if it breaks it?

---

### Post by dcstar on 2011-11-02
> **MonocleMike2 said:**
> mike@mikelap:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)

At the moment my system (11.10) is using the default driver and does not detect the display type.  It works OK.  Is there a specific driver for this card and will it work?  Will it provide anything better?  I use the machine for browsing the web and watching videos.  I don't play games.
If I decide to try a new driver, how do I get back to the current system if it breaks it?

Via Unichrome video drivers have been a problem in Linux since forever, basically.

You can try and search out if anything has changed, but I gave up on 'em about 6 years ago and solved my problem by purchasing a cheap Nvidia video card.

---

### Post by MonocleMike2 on 2011-11-02
Thanks for the advice.  I can't change the card as it is a laptop and everything is built in very tightly.

---


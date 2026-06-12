---
title: "Flash not playing well in FF"
date: 2009-12-02
forum: General Help
---

### Post by keithclark on 2009-12-02
I don't seem to be able to get Flash to work well in FF 3.5.  Sometimes it works, other times not.  When a web page that has Flash is loaded, I see an "F", then a "Play Arrow".  When I hit the play arrow the flash media will play.  Very annoying.  In maps.google.ca, I cannot get the street view to work.  I get the F and then the play arrow, but when I press the play arrow all I get is a black window where the street view should be.

Ideas?

Keith

---

### Post by fluffman86 on 2009-12-02
Did you install flashplugin-installer or some other flash player?  Do you have any extensions (like flashblock) that could be causing the problem?

---

### Post by wojox on 2009-12-02
This should help [URL="http://ubuntuforums.org/showthread.php?t=1193567"] Firefox optimization and troubleshooting thread
[/URL]

---

### Post by keithclark on 2009-12-02
> **wojox said:**
> This should help [URL="http://ubuntuforums.org/showthread.php?t=1193567"] Firefox optimization and troubleshooting thread
[/URL]

Excellent!  This seems to have worked for me:

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

Thanks for the reference.

Keith

---


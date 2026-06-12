---
title: "Can't listen to internet radio"
date: 2010-07-24
forum: General Help
---

### Post by NeverHide on 2010-07-24
I went on radio's web site to listen to it when i hit the link to listen to i get an error saying i don't have the required plugin and an option to search.I searched and i got this message

---

### Post by geoffjay on 2010-07-24
Possible solution at [http://ubuntuforums.org/showthread.php?t=1137833](http://ubuntuforums.org/showthread.php?t=1137833)

---

### Post by NeverHide on 2010-07-26
I did what was suggested on that thread but unfortunately nothing changed :(
Thnx for the efford anyway :)

---

### Post by geoffjay on 2010-07-26
What program/radio station are you trying? Let me know and I'll give it a try.

---

### Post by NeverHide on 2010-07-27
This is the the site [http://www.kiss.gr/](http://www.kiss.gr/) the link to listen is the "Listen Live"  ,upper left side of the side between the headphones.
It opens a new window for the player and the url of it ends with .jsp
Don't know if that helps,feel free to check it out

---

### Post by geoffjay on 2010-07-27
Loads fine for me. Verify that you have the following installed

- flash (you can test your version by searching "flash test" in google and visit the Adobe test page)
- ubuntu-restricted-extras
- gstreamer0.10-plugins-good
- gstreamer0.10-plugins-bad
- gstreamer0.10-plugins-ugly

I don't think I've really installed anything for audio other than those seeing as this is a work computer. Also, the browser that I'm using is the development version of Google's Chrome from the PPA that can be enabled in ubuntu-tweak.

---

### Post by NeverHide on 2010-07-30
> **geoffjay said:**
> Loads fine for me. Verify that you have the following installed

- flash (you can test your version by searching "flash test" in google and visit the Adobe test page)
- ubuntu-restricted-extras
- gstreamer0.10-plugins-good
- gstreamer0.10-plugins-bad
- gstreamer0.10-plugins-ugly

I don't think I've really installed anything for audio other than those seeing as this is a work computer. Also, the browser that I'm using is the development version of Google's Chrome from the PPA that can be enabled in ubuntu-tweak.

That did the trick my friend \\:D/
Thank you very much :D :D :D

---


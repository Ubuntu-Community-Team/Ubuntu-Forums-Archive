---
title: "Webcam Recording Program That Detects Motion?"
date: 2010-09-17
forum: General Help
---

### Post by warmnscsi on 2010-09-17
Is there a program for linux that will start recording video from my webcam when it detects motion? If so where can I download it? Thanks.

---

### Post by Aearenda on 2010-09-17
Yep, there's one called "motion" and it's available for Ubuntu via your favourite package manager. But it's managed from the command line,there's no GUI.

---

### Post by warmnscsi on 2010-09-17
> **Aearenda said:**
> Yep, there's one called "motion" and it's available via your favourite package manager. But it's managed from the command line,there's no GUI.

Ah I just ran it and it started taking a billion pictures. I closed the terminal but I'm pretty sure it's still running.  I can't find any tut's online since "motion" is a pretty generic name. I tried "motion man" to find a manual and it's just spitting out a bunch of errors. Help?

---

### Post by Aearenda on 2010-09-17
I don't have it installed at the moment, I used it a couple of years ago. Try ```
motion --help
```or```
man motion
```

:-) If you don't change the default config file it sets up a local web server which lets you see the pictures it takes using a browser. The config file has a lot of comments in it, so it should be reasonably straightforward to get it to do what you want.

---

### Post by Aearenda on 2010-09-17
I just found the [home page for motion]("http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome") - that should help!

---

### Post by no2498 on 2010-09-18
wxcam say's it has motion
i think the program wxcam needs to be open to use it
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---


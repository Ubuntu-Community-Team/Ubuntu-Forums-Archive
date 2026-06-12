---
title: "Transmission, can't find settings.json"
date: 2010-10-25
forum: General Help
---

### Post by p2ranger on 2010-10-25
After upgrading a couple of months ago from Ubuntu server 9.04 to 10.04, transmission stopped working. I have since removed it and reinstalled. It is running as I can start and stop the daemon. However, I can't locate the settings.json file so I can get into it in the browser. The version running is 1.93. I tried searching in multiple directories and even searched using:
```
sudo find / -iname settings.json
```
Nothing came up.

I stopped the daemon and created the file in /etc/transmission-daemon/settings.json with the contents of my old file I had saved elsewhere. Restarted the daemon and I still get the 404 error.

I was suspicious the last step wouldn't work as I was of the opinion that transmission is supposed to generate its own default settings.json file.

What am I doing wrong?

Thanks for any help

Jason

---

### Post by p2ranger on 2010-10-26
Well, I don't know what the problem was, but I updated to the latest transmission, 2.11 and it works now.

Jason

---

### Post by tje210 on 2012-12-02
i've found the same problem.  running the gui version of transmission (transmission-gtk) has generated the settings.json, but that's the only way i've seen to generate it.  when i install and just run transmission-cli, i have to run transmission-gtk one time (and while i'm in there, i edit my preferences just how i want them), and then the settings.json shows up.  alternately, of course, i can just import it from a different computer.

---

### Post by wildmanne39 on 2012-12-02
Old thread closed.

---


---
title: "libstdc++.so.6  BIG PROBLEM"
date: 2010-09-08
forum: General Help
---

### Post by dlawler on 2010-09-08
So, while fooling around with dolphin, i was looking into a problem with libstdc++.so.6 and pulled a really dumb terminal command. basically i think it was something along the lines of:


> sudo mv libgcc_s.so.1 libgcc_s.so.1.orig

so now, nothing's opening. luckily i had chrome open and of course the terminals running, but EVERYTHING on my computer refuses to open and outputs this from the terminal:


> me:~$ firefox
/usr/lib/firefox-3.0.11/firefox: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

another:


> daniel@daniel-laptop:~$ audacity
audacity: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

so basically, i'm sitting at a starbucks with a damned computer and need help FAST...

thanks in advance

---

### Post by mc4man on 2010-09-08
try 
```
sudo apt-get install --reinstall libstdc++6 libgcc1
```

otherwise post what release of ubuntu you're using, nothing mentioned previously

Edit
or if you can open a terminal (konsole), then ck. your history (arrow up or enter history and try reversing the mv whatever it actually was

---

### Post by dlawler on 2010-09-08
ok, well, basically, aptitude wasn't working, and things looked grim. I ended up having to leave the starbucks and regretfully shut down my computer. upon rebooting, though, I got a command line. found the problem, and then booted up a live disc and copied the right files over.

I guess i literally had just added .orig at the end of a file that didn't need to be that way... so, simple fix. Thanks all!

---


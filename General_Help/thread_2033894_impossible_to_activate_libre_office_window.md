---
title: "impossible to activate libre office window"
date: 2012-07-27
forum: General Help
---

### Post by Gingalone on 2012-07-27
Today I opened a Libre Office (LO) Writer document (.odt) and then I opened a LO Calc file (.ods). I got both icons active on Unity launcher, BUT when I had the Calc window on foreground (whole screen) and clicked on Writer icon on launcher nothing happened. The same doing Alt-tab: the Writer icon was there but no way to get the Writer window opened (or back on foreground). The only way I found to see the Writer window back was to click on Window menu in Calc and then choosing the Writer file in the pop down menu...
That's a very strange behaviour (and "a bit" disappointing!).
Thanks for any help!

---

### Post by daslinkard on 2012-07-30
After rebooting your machine is this problem still persisting?

---

### Post by Gingalone on 2012-08-08
> **daslinkard said:**
> After rebooting your machine is this problem still persisting?

yes, the problem is still there, even today, after a week long vacation...

---

### Post by Gingalone on 2012-08-08
The described behaviour took place with Ubuntu 2D.
With normal Ubuntu it looks there is no compatibility between Libre Office (LO) and Unity: when a LO window is active it's not possible to switch to it with alt-tab (no LO icon); in Unity launcher the LO icon is present but NOT active, so, if the LO window is minimized, I have no way to get it back on the screen.

Am I the only Ubuntu 12.04 user to experience this anomaly?:confused:

Thanks for help!

---

### Post by nicocarbone on 2012-08-09
I am having the same problem. And we are not the only ones. There is a "new" bug report about it: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1027000]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1027000")

Please, mark it as affecting you too so it gets some attention.

---

### Post by Gingalone on 2012-08-10
> **nicocarbone said:**
> I am having the same problem. And we are not the only ones. There is a "new" bug report about it: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1027000]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1027000")

Please, mark it as affecting you too so it gets some attention.

OK, done that...
Hopefully someone will take care of this bug!

---

### Post by azangru on 2012-08-26
I [complained]("http://ubuntuforums.org/showthread.php?t=2027606") about this bug here on the forums, and one suggestion was to install the global menu for LibreOffice (lo-menubar). I haven't tested it yet, but you may give it a try.

---

### Post by RomanIvanov on 2012-09-04
```
sudo apt-get install lo-menubar
```

and restart worked for me. Thanks A lot.

---


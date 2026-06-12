---
title: "Speed up 10-04 Boot"
date: 2010-05-01
forum: General Help
---

### Post by JugglinPhil on 2010-05-01
I just found this tutorial, and I was wondering if this was actually anything serious:

[http://www.aroundtheweb.info/2010/04/how-tospeed-up-ubuntu-1004-lucid-lynx.html](http://www.aroundtheweb.info/2010/04/how-tospeed-up-ubuntu-1004-lucid-lynx.html)

If it is, it does not seem to work, pressing "e" while booting does not do anything.
Any ideas on this?

---

### Post by JugglinPhil on 2010-05-02
Bump

---

### Post by JugglinPhil on 2010-05-02
Anybody?

---

### Post by bowens44 on 2010-05-02
yeah because 30 secends to boot is waaayyyyyy toooooo long

---

### Post by mugetsu37 on 2010-05-02
It worked before: [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263). If it's not working for you the e at boot may have been deprecated in Lucid and someone just posted it again for Lucid, assuming it would be the same.

---

### Post by JugglinPhil on 2010-05-02
> **bowens44 said:**
> yeah because 30 secends to boot is waaayyyyyy toooooo long
If you can't contribute to the topic just keep it to yourself.

---

### Post by adibogos89 on 2010-06-06
You have to hold 'Shift' before the boot screen shows because the Grub boot list has been hidden to speed up things even more.

After that, select your active kernel from the list and press 'E' to edit it.

---

### Post by east375 on 2010-06-06
You may change /etc/default/grub
Find the line GRUB_CMDLINE_LINUX_DEFAULT, add 'profile' to the end of line. This will look now something like
"quiet splash nomodeset **profile**"
Save your changes and run "sudo update-grub"

---

### Post by JugglinPhil on 2010-06-07
> **adibogos89 said:**
> You have to hold 'Shift' before the boot screen shows because the Grub boot list has been hidden to speed up things even more.

After that, select your active kernel from the list and press 'E' to edit it.
Okay thanks I can access the menu now, however after pressing 'e' there is no entry that starts with 'kernel' as described in the tutorial..

---

### Post by Paddy Landau on 2010-06-07
Do you have a particularly slow boot? My Lucid takes under 30 seconds.

I saw something about a profile during my last Lucid installation; I suspect that Lucid does it automatically.

---

### Post by ShadowDragon on 2010-06-07
> **JugglinPhil said:**
> I just found this tutorial, and I was wondering if this was actually anything serious:
[...]


Well, this actually already happens out of the box. In short, [ureadahead](http://ubuntuforums.org/showthread.php?t=1434502) "profiles" your entire boot process and keeps a record of which files are accessed during boot. The next boot it will read these files in an optimized way and caches them in your RAM memory, resulting in a quicker access. Every time you install a package which will be needed during boot, ureadahead will automatically profile your next boot. The tutorial only explains how you can profile manually.

I hope this explanation helped you :)

---

### Post by JugglinPhil on 2010-06-07
No I don't, it is about 30 something seconds as well.
I was just curious if you could push it a bit further..

---

### Post by ShadowDragon on 2010-06-07
If you want to analyse your boot-process try to make a bootchart-picture to find some possible bottlenecks.

Installation: ```
sudo aptitude install pybootchartgui bootchart
```
Images can be found in "/var/log/bootchart/[computername]-[timestamp].png

---

### Post by JugglinPhil on 2010-06-07
> **ShadowDragon said:**
> Well, this actually already happens out of the box.
All right, thanks for the explanation. Makes sense after all. :)

---

### Post by ShadowDragon on 2010-06-07
Glad I could help :) Do you need more help or can we [mark this one as solved](http://ubuntuforums.org/solved.php?do=marksolved&t=1468195)?

---

### Post by dcstar on 2010-06-08
> **Paddy Landau said:**
> Do you have a particularly slow boot? My Lucid takes under 30 seconds.
.......

Mine takes a second to load **burg** (graphical Grub2) after the BIOS screen, then about 3 seconds after starting to boot sequence to give me a login screen.

Once logged in it loads Firefox, Evolution, Pan and a few other utilities and panel applets in about 5 seconds.

Having Ubuntu installed on a SSD certainly makes all things quicker at start up.....   :popcorn:

---


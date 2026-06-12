---
title: "Problem with keyboard layout switcher"
date: 2010-09-08
forum: General Help
---

### Post by stee1rat on 2010-09-08
This is a really weird problem. I have no idea what is the reason. 

I have ubuntu 10.10 beta 1 on my computer, and i have 2 layouts - russian and english. So, when i start my computer it works fine for a while, but after some time my layout swither start to work very strange. It's switching the keyboard layout while i'm typing! So the final text becomes a mess. And i have to restart my computer to fix this problem.

Any one have an idea what's going on with my ubuntu?

---

### Post by stee1rat on 2010-09-11
Does anyone have an answer? I just got the same issue on my netbook's ubuntu netbook remix 10.10 beta 1.. Looks like a bug or something.

---

### Post by ru_adima on 2010-09-12
I have same problem with Russian and USA keyboard layout. Ubuntu Beta 10.10

---

### Post by mohd995 on 2010-09-14
the same problem here with arabic and english layouts

---

### Post by konart on 2010-09-14
Same here. Russian + English

---

### Post by DsXack on 2010-09-15
yes.... i have this bag with rus+usa layounts too...

---

### Post by mohd995 on 2010-09-15
has not been fixed here with this morning update

---

### Post by ru_adima on 2010-09-18
may be there is solution. i turn off plugin `keyboard` for gnome_settings_daemon. Go to Applications - System Tools - Configuration Editor, find section /apps/gnome_settings_daemon/keyboard, uncheck "Active"

---

### Post by mohd995 on 2010-09-21
that is what i have done so far and it works fine
go to the keyboard preferences>> layouts >> options>> key(s) to change layouts... and disable the the keys
if you want change the layout go to the panel and change it manually form there

it works with me so far
i hope this will be fixed with the future updates

---

### Post by SiegHard on 2010-10-03
Same here in RC realise  with LTU <> US Layouts ;D

---

### Post by 21h on 2010-10-04
same problem
usa+rus

no idea how to fix this

---

### Post by cserpentis on 2010-10-04
Same story. As a temporary solution have to turn on the keyboard plugin after boot and then turn it off (so that the hotkeys work, despite whe indicator being broken). So the oldie, but goodie IT support favourite: "Hello, have you tried turning it on and off again?" still works. Quite sad to see Ubuntu include untested and obviously broken software into release, especially, when better, more stable alternatives (that are standart in Gnome) are available.

---

### Post by Gladk on 2010-10-05
Same problem for me, USA+RUS+UKR

---

### Post by phoenix49 on 2010-10-06
Problem still exists, is there any bug report related to this problem?

UPD: There's bug report already created. 
[https://bugs.launchpad.net/gnome-settings-daemon/+bug/625793](https://bugs.launchpad.net/gnome-settings-daemon/+bug/625793)

---

### Post by k7rata121 on 2010-10-07
same here (ar,usa)

---

### Post by mahdif62 on 2010-10-09
Same problem here. USA and Iranian keyboard layout.  Ubuntu 10.10 RC. This is a very annoying bug.

---

### Post by mahdif62 on 2010-10-09
I filed the bug in Launchpad: [http://ubuntuforums.org/showthread.php?t=1570776](http://ubuntuforums.org/showthread.php?t=1570776)
Please go there and comment so that the problem may be fixed sooner.

---

### Post by Yumi on 2010-10-09
No problem with me any more. An update maybe a week ago fixed it for me and also introduced a new icon for the bottom bar.

Michael

---

### Post by Gladk on 2010-10-09
I still have it.

---

### Post by tapin13 on 2010-10-12
the same. ubuntu 10.10
i'm really disappointed! :mad:

---

### Post by phoenix49 on 2010-10-13
Bug is fixed, and is now in proposed update repository. It will soon land in normal update repo

---

### Post by cserpentis on 2010-10-13
Confirmed. Now if only there was a way to take that useless keyboard icon out of the indicator…

---


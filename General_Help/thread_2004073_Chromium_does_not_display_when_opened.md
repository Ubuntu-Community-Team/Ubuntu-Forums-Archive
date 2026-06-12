---
title: "Chromium does not display when opened"
date: 2012-06-15
forum: General Help
---

### Post by CaptainMark on 2012-06-15
Sometimes when I open Chromium it does not display anything. I know it opened because it appears in the window list (cinnamon) but I have to click the window list first to minimise it then again to maximise chromium and it will reappear, has anyone experienced anything similar to this (im not sure if it appears in the launcher if you are using unity)

Regards 
Mark

---

### Post by CaptainMark on 2012-06-18
Bump anyone?

---

### Post by vasa1 on 2012-06-18
Could be a bug in Cinnamon? I don't think there's any problem with Chromium, per se.

---

### Post by CaptainMark on 2012-06-19
well ill check it by switching to unity for a few days

---

### Post by vasa1 on 2012-06-19
If the problem persists, you may consider setting up a new profile, at least temporarily. Assuming that Chromium uses the same path as Chrome, with **no** Chromium process running, you could rename [FONT="Courier New"]/home/your_name/.config/google-chrome/Default[/FONT] to Default.bak. Then, when you start Chromium, it will create a new [FONT="Courier New"]Default[/FONT] untainted by cookies, extensions, cache, etc.

---

### Post by CaptainMark on 2012-06-20
my profile is definitely not the problem as this has be ongoing for some time and my profile will have been deleted several times since it first occurred for various reasons

---

### Post by vasa1 on 2012-06-20
> **CaptainMark said:**
> my profile is definitely not the problem as this has be ongoing for some time and my profile will have been deleted several times since it first occurred for various reasons
Have you enabled any stuff in about:flags?

---

### Post by CaptainMark on 2012-06-20
no none, this does seem to be specific to cinnamon at the moment, its not present in unity i may have to spend a few days with gnome-shell to see if its a bug specific to mutter, and by relation in muffin (cinnamon) as unity does use these packages it would seem probable

---

### Post by vasa1 on 2012-06-20
> **CaptainMark said:**
> ... i may have to spend a few days with gnome-shell ...
Or just try Xfce.

---

### Post by mlaitinen on 2012-07-03
I have exactly the same problem in Linux Mint 13 (with Cinnamon). My Chromium version is: 18.0.1025.151 (Developer Build 130497 Linux) Built on Ubuntu 12.04, running on LinuxMint 13

Usually I don't see Chromium at the beginning, but a moment ago it appeared in the upper left corner in the size of a stamp. I could see my start page and some very very small text. After I clicked it in the window list twice (minimize and maximize), it opened properly.

---

### Post by CaptainMark on 2012-07-04
I have issued a bug report via github here [https://github.com/linuxmint/Cinnamon/issues/869](https://github.com/linuxmint/Cinnamon/issues/869) please sign in/up to github and post your +1's

---


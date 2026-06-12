---
title: "Stuck on loading screen after removing KDE"
date: 2011-01-18
forum: General Help
---

### Post by Mudwreck on 2011-01-18
I installed KDE but decided to remove it after a while as I wasn't using it and its application were redundant on my Gnome desktop. I followed Psychocats' guide for "pure Ubuntu" but after rebooting, Ubuntu just hangs on the loading screen (or during 'checking battery state').

I tried booting in recovery mode but I'm unable to navigate the menu: when I press a direction key it alternates between the menu and the Ubuntu loading screen. Several other keys do the same thing, while the rest do nothing.

Any help would be much appreciated.

---

### Post by todak on 2011-01-18
Copy and paste this into a terminal ```
sudo update-alternatives --config gdm
``` Choose the number that has 'gdm'.

 Then enter ```
sudo apt-get remove kdm
```

---

### Post by Mudwreck on 2011-01-18
The problem is I can't access a terminal. When I boot in recovery mode, I can't navigate the menu by pressing the arrow keys, instead, they function as the return key and continue to regular boot.

---

### Post by ububaba on 2011-01-18
> **Mudwreck said:**
> The problem is I can't access a terminal. When I boot in recovery mode, I can't navigate the menu by pressing the arrow keys, instead, they function as the return key and continue to regular boot.

Had similar problem with my desktop but could solve it by taking these steps. 

- Put the power off.

- W ith the help of motherboard manual, located a jumper which I had
   to change by inserting on some other pins.

- Then removed the battery for about ten seconds, then put it back.

- Jumper as well back to the original position.

- Readied it for repowering it by putting the power cable back. 

- At the restart kept the shift key down till I was in BIOS.

- Set time and date to synchronise. 

Problem solved. Though I have other problems which cannot be 
solved by clearing CMOS.

---

### Post by Mudwreck on 2011-01-20
I reset the CMOS but still no luck.

---

### Post by pxs096320 on 2011-06-21
bunp....I too have a similar problem...  You can check my thread titled "[B]ubuntu does not boot up stuck at logo with blinking process bar" 

[/B]You can use the link below
[B][http://ubuntuforums.org/showthread.php?t=1787975](http://ubuntuforums.org/showthread.php?t=1787975)
[/B]

---


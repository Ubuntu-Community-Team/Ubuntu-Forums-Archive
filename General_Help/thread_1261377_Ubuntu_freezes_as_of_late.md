---
title: "Ubuntu freezes as of late"
date: 2009-09-08
forum: General Help
---

### Post by TheHimself on 2009-09-08
I have a Ideapad S10 with Jaunty on it. It's been twice that it freezes in last two days. How can I find the source of the problem?

---

### Post by SoftwareExplorer on 2009-09-08
Is there a common thing that happens around when it freezes? 
Second, is the HDD useage light on when it freezes?
Does your mouse still move when it's frozen?
Does anything happen if you do Ctrl + Alt + F3?
What about Ctrl + Alt + Del?

---

### Post by TheHimself on 2009-09-09
Is there a common thing that happens around when it freezes? 

No, once it happened when I fired up rhythmbox and again when I was editing a document in Kile. Mouse cursor moves but can't do anything. I can do a few things using keyboard like turning off the monitor but that's mostly it. Even the laptop dis not go to sleep when I closed its lid.

Can system log reveal anything?

---

### Post by SoftwareExplorer on 2009-09-11
I don't know about the system log, but you might be able to make a way to get yourself out of such freezes. Try this ```
sudo apt-get install dontzap&&sudo dontzap --disable
```
That will make it so that when you press Ctrl + Alt + Backspace it will restart the GUI, which might work to get you out of these freezes. Hopefully someone who knows about the system log will also reply so that you can get to the root of the problem.

---

### Post by TheHimself on 2009-09-11
Are you sure the name is correct? Package can't be found.

---

### Post by NoaHall on 2009-09-11
```
sudo apt-get install dontzap && dontzap --disable
```

Or just do "alt + k + printscreen" It's the same as the old "ctrl + alt + backspace"

---

### Post by TheHimself on 2009-09-11
Does this just restore the Ctrl+Alt+Backspace shortcut which has been disabled in Jaunty? This can be done using Keyboard Shortcuts as well.

---

### Post by SoftwareExplorer on 2009-09-11
> **TheHimself said:**
> Does this just restore the Ctrl+Alt+Backspace shortcut which has been disabled in Jaunty? This can be done using Keyboard Shortcuts as well.

Yes it does. As far as the package name, I think I have it correct.
> sudo apt-get install dontzap          (09-11 16:30:23)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dontzap is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtk1.2 libclutter-0.8-0 libglib1.2ldbl libgtk1.2-common
  libclutter-gtk-0.8-0 libtorrent-rasterbar4 libvlccore0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


---


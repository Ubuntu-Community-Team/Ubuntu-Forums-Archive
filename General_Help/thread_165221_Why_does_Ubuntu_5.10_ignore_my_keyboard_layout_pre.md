---
title: "Why does Ubuntu 5.10 ignore my keyboard layout preference?"
date: 2006-04-24
forum: General Help
---

### Post by 1002285 on 2006-04-24
I use Ubuntu 5.10 and have only got it working with Estonian layout a couple of times. Sometimes it understands that I want it, but mostly it does not. And even if it does, it goes back to the wrong (US, I guess) layout after the next restart. If I cannot solve this, I should go back to Windows probably.
What I have done is that I have tried the keyboard layout preferences (with Estonian both default and not default) and marked writing aids (kirjutamise abivahendid) for Estonian in language settings. I have yet not understood why it started working for me a couple of times and why it did not work in all other occasions.

---

### Post by dg_w on 2006-04-24
Are both you xserver and Gnome set to the correct layout ?

sudo gedit /etc/X11/xorg.conf

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
       ** Option          "XkbLayout"     "gb"**


In gnome:
Preferances \ Keyboard.
Remove all languages, except the layout you want ..
(and make sure keyboard model is correct)

Hope this helps

---

### Post by 1002285 on 2006-04-24
I dont even know anything about xorg, but that might not be the problem, as I found a possible solution from this forum (titled estonian keyboard). But I do not even understan why I cannot do anything - for instance I am not able to make new folders or copy necessary deb or sh files to existing folders - I get an error that I do not have rights to write in one or another folder.
I should probably just look for other threads that have this subject.
Thanks.

---

### Post by dg_w on 2006-04-25
As a user in Ubuntu you will not be able to copy items into system folders..

Just your home directory..

To create a new folder you can read \ write to in the main file system
From command line
sudo mkdir /folder_name
sudo chmod 777 /folder_name

Or to use existing folders
sudp cp filename /folder

Hope that helps

---


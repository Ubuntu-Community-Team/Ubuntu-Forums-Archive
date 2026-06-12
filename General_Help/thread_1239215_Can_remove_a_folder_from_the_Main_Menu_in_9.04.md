---
title: "Can remove a folder from the Main Menu in 9.04"
date: 2009-08-13
forum: General Help
---

### Post by starr0stealer on 2009-08-13
Hello fellow linux brothers.
I am having some issues getting my (Wine) from to be removed after uninstall. I have an attached screen shot of where I am trying to remove it at. I click delete and nothing happens.

I have cleared everything that said WINE in the folder
/home/MYYOURUSER/.local/share/applications

I will be putting wine back on, I am just a perfectionist

---

### Post by coldReactive on 2009-08-13
Did you remove it from add/remove or from terminal using **sudo apt-get purge wine**?

---

### Post by wojox on 2009-08-13
Click the very top Applications and delete from there.

---

### Post by starr0stealer on 2009-08-13
I used the Synaptic package manager to remove.

I ran that command, it removed the folders inside (wine-wine) but not the folder its self.

I have tried clicking the delete from the top most layer, nothing happens when I do that.

---

### Post by P4man on 2009-08-13
Then just uncheck it (from the top level), so its no longer visible :)

---

### Post by michy99 on 2009-08-13
The wine menu entries are stored at /home/YOUR_USERNAME/.local/share/applications/wine. If you delete them from there, they will be gone from the menu.

---

### Post by starr0stealer on 2009-08-13
Unchecking it isn't enough for me. Leaves data integerty. And a unclean house. I have completely removed Wine. And that folder no longer exist, but it still is found in the menu.

---

### Post by michy99 on 2009-08-13
Did you read my post right above your last reply? Open a terminal and enter:```
rm -r ~/.local/share/applications/wine
```

---

### Post by starr0stealer on 2009-08-13
yes, there was nothing found.

I went ahead and installed Wine again. Now the menu option is gone.
And I can't find where it installed it. And it didnt show up in the menu at all.

---

### Post by michy99 on 2009-08-13
Maybe it is there, but unchecked.

---

### Post by starr0stealer on 2009-08-13
No it is not unchecked, I have tried searching for 'wine' in command line. Nothing found. 

I have tried installing it a few different times. nothing change so far.

I'm about to say screw it and redo the OS install.

Sadness.

---


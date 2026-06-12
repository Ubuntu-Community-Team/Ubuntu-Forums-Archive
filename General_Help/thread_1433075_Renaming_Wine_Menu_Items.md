---
title: "Renaming Wine Menu Items"
date: 2010-03-18
forum: General Help
---

### Post by MadDawg010 on 2010-03-18
Alright, after trying to organize shortcuts in Wine's menu (which did not work), I ended up hitting the 'Revert' button, which changed the names of most of the folders:

[Screenshot]("http://s199.photobucket.com/albums/aa174/MadDawg001/?action=view&current=Screenshot-6_2.png")

As you've probably guessed, I want to remove "wine-Programs-" from the beginning of the folder names. I've tried using the menu editor to do this, but the 'Properties' button does not seem to work on anything I did not create myself. How do I go about editing the names?

I would also like to know how to move the MS Office shortcuts into a custom folder/menu. They refuse to drag into any folder I make.

---

### Post by mastermindg on 2010-03-18
Menu editing is still something that is a pain in Linux. FreeDekstop uses xml to generate menu's and it's a pain to update these. As far as I know there is no way to copy/paste menu items. I ended up having to create NEW items from scratch.

Just copy the path to an already existing link, i.e. env WINEPREFIX="/home/user/.wine" wine "C:\Program Files\AmiBroker\Broker.exe". Replace user with your username and the path after wine with the path to the app.

Good luck!

---

### Post by MadDawg010 on 2010-03-18
Cool, thanks for the info.

---


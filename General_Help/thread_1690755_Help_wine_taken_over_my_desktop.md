---
title: "Help wine taken over my desktop"
date: 2011-02-18
forum: General Help
---

### Post by TurtleKing on 2011-02-18
My most important problem is that wine has taken over the places menu on my top panel. Everytime I try to click on one of the folders it comes up with the typical wine window saying error could not find file or folder. In addition, ever since I tried to install Enemy Territory Quake Wars (horrible idea) with wine an annoying black rectangle has appeared in the center on the bottom of the desktop (only there on ubuntu) and wont go away. I tried unistalling and removing any trace of enemy territory quake wars, and I tried uninstalling wine via terminal, but according to terminal wine is not installed. However, I see it listed under the application menu in the top panel as well as deleting the .wine file from the home folder via terminal, but to no success.

I really don't want to have reinstalled ubuntu again just to get rid of this annoying rectangle and get everything back to normal, so someone please help me get my ubuntu back to normal before this disaster.:(

---

### Post by Bigtime_Scrub on 2011-02-18
I don't know what that black rectangle is but if you want to restore Gnome back to default press Alt-F2 and enter in the box
```
 gnome-terminal 
``` Then press run. 

In the terminal

```
  rm -rf .gnome .gnome2 .gconf .gconfd .metacity 
``` and press enter.

Restart from terminal with 

```
 sudo shutdown -r now 
```

or you can log out and then back in and it should be restored to default. 


You can uninstall wine from Synaptic Packages Manager. 

Remove Wine from the menu entry 

```
 rm -rf ~/.local/share/applications/wine* 
```


Hope this helps.

---

### Post by TurtleKing on 2011-02-18
Thanks, the actual black rectangle came from having compiz disabled with cairo-dock. For some reason, I guess the desktop did that on its own as I don't recall turning it off recently. As for the Places menu being controlled by Wine, no more. I went through computer and checked the home folder properties and opened it with "openfolder". However, I still for the likes of me can't get rid of wine from ubuntu. At least I got my desktop back to normal. Anyways, I will leave this open in case anyone wants to help me get rid of it since I am kind of scared of its power now. lol

---

### Post by TurtleKing on 2011-02-18
Opps didn't read completly your post. Got rid of it now. Hopefully it wont comeback that creepy software. lol Solved.

---


---
title: "How to add my favorite places as a quicklist in my home's icon in Unity?"
date: 2011-10-19
forum: General Help
---

### Post by hojjat on 2011-10-19
The answer used to be this: [http://askubuntu.com/questions/35024/how-to-add-my-favorite-places-as-a-quicklist-in-my-homes-icon-in-unity](http://askubuntu.com/questions/35024/how-to-add-my-favorite-places-as-a-quicklist-in-my-homes-icon-in-unity)

However, it doesn't work with Ubuntu 11.10 anymore. Once you follow that procedure, the custom locations are correctly added to the quicklist. However, when you click on them, a new icon appears in the launcher (a second home button). Is there a fix for that?

---

### Post by hojjat on 2011-10-27
Bump?

---

### Post by Steeperton on 2011-10-28
Mine was working fine with the quicklists until yesterday. I'm guessing Unity was updated. Now even clicking "Home Folder" launches a 2nd icon on the launcher. 

No idea how to fix though...

Edit: someone's bugged it though: [https://bugs.launchpad.net/unity/+bug/881235](https://bugs.launchpad.net/unity/+bug/881235)

---

### Post by mc4man on 2011-10-28
Still works fine here but was able to recreate in a new user & then fix. 

Hopefully your custom nautilus-home.desktop doesn't look like the one posted in bug, it's mis-constructed, the last 6 lines should be above the X-Ayatana-Desktop-Shortcuts=.... line 
(maybe it was mis-posted
Edit:
while I wouldn't put those lines at the end the bigger issue may be this line, if you have it then delete it completely from your custom nautilus-home.desktop, log out/in & see
> OnlyShowIn=GNOME;Unity;

Does your '2nd' icon show as "Files"?
Re-edit: commented what I see as the issue in bug..

---

### Post by Steeperton on 2011-10-30
> **mc4man said:**
> Still works fine here but was able to recreate in a new user & then fix. 

Hopefully your custom nautilus-home.desktop doesn't look like the one posted in bug, it's mis-constructed, the last 6 lines should be above the X-Ayatana-Desktop-Shortcuts=.... line 
(maybe it was mis-posted
Edit:
while I wouldn't put those lines at the end the bigger issue may be this line, if you have it then delete it completely from your custom nautilus-home.desktop, log out/in & see


Does your '2nd' icon show as "Files"?
Re-edit: commented what I see as the issue in bug..

Thanks Mc4man (have also commented in the bug) - yes, removing "OnlyShowIn" line, and it behaves properly.

---

### Post by hojjat on 2011-11-01
Removing the OnlyShowIn part fixed it for me as well.

---

### Post by stinkeye on 2011-11-17
Thanks mc4man,
Fixed here as well.
=D>

---


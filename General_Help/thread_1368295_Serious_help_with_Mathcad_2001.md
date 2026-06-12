---
title: "Serious help with Mathcad 2001"
date: 2009-12-30
forum: General Help
---

### Post by rasmus91 on 2009-12-30
Hi

Okay guys, i know there are a million posts about this allready, but i think i've used several hours trying to find a solution. and i only found one complete guide which was not usable at all for me.

So, what I'd like to know is: Isn't there anybody at all who has succesfully installed Mathcad on wine?

Were talking mathcad 2001 here, and for once the installer seems to work, but when it prepares the install process it gives the following message:

1155: File E:\MATHCAD\Mathcad 2001 professional.msi not found.

Sadly i'm stuck on windows 7 until i find a way of making this work.

Please help.

Thanks you for your time.

Cheers, Rasmus.

---

### Post by rasmus91 on 2009-12-30
Okay, i got it running by copying my from my windows installation. but upon start up it says: "Failed to create function manager"

which basically means it won't be able to do any calculations.

Any have a idea?

---

### Post by taurus on 2009-12-30
Here's a link for you.  2001 version is rated as garbage!

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1402](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1402)

Here's the whole list.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=263](http://appdb.winehq.org/objectManager.php?sClass=application&iId=263)

---

### Post by rasmus91 on 2009-12-30
Sorry dude but thats like the first place i looked... I just got beyond anything i could find in any guide on the internet, i need this last bit, and no one knows how this is done...

It's just that i need this program for school, and really need it... I just don't want to use windows.

But it's just that there really isn't any equal opensource mathcad solution available, i've tried several different, but none work quite as well... :'(

Installed in Virtual box XP

---

### Post by BFris on 2011-03-18
MathCAD is a great program. And maybe by now Wine is good enough to handle the older versions. If you start your MathCAD from a command prompt, sometimes you can get some good clues on which dlls are having problems. Then you tell Wine to use the native version of those dlls. 

CompPad has a slightly better price (free) and can be used on all platforms. Functionality wise, it's quite similar to MathCAD
  [LIST]
[*]natural math notation
[*]units
[*]gentle learning curve
[*]easy to use graphs
[/LIST]
It's still rough around the edges but usable enough for me to use in my work.

---

### Post by waterfish on 2011-08-02
Ubuntu 11.04, Wine 1.3
Update all necessary components using winetricks
Installing mathcad using wine 1.3 is trouble free. It works with some misgivings: the math region is blackened making editing totally off. Refreshing by scrolling to other pages and back works. But the text region (change the font to different color) can be edited.

---


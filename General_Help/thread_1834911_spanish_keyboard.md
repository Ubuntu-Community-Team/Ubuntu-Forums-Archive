---
title: "spanish keyboard"
date: 2011-08-28
forum: General Help
---

### Post by jeremybentham on 2011-08-28
I have lubuntu on my little acer aspire netbook which I am v happy with except there doesnt seem to be anyway of adding different keyboard layouts -is there something I can get or do to add spanish keyboard?

---

### Post by whatthefunk on 2011-08-28
Try this in a terminal:

```
sudo setxkbmap -layout es
```

---

### Post by jeremybentham on 2011-08-29
Thanks whatthefunk.
This has worked in that it has changed my keyboard to spanish.
Presumably 

sudo setxkbmap -layout en

will change back to english?

I was hoping there would be a way like with normal ubuntu to have es or en on toolbar and change with a mouseclick.

Cheers

---

### Post by jeremybentham on 2011-08-29
ah sudo setxkbmap -layout en

does not work so how do I switch back?!

---

### Post by whatthefunk on 2011-08-29
Ahhh...you probably want ibus.  I havent done this in a long while so this may not be the exact order, but it goes something like this:

-Go to Menu > System Tools> Language Support

-Under the Language tab, on the bottom, it says Keyboard Method Input System.  Change this to ibus.

-You also may have to install Spanish...you can do that from the Language Support window as well.

-Now you should be able to go to Menu > Preferences > Keyboard Input Methods

-From there, you can go to the Input Method tab and change your input method to Spanish.  Under the General tab, you can do things like tell ibus to have an icon in the panel or assign it a hotkey for easy switching.

Like I said, I havent done this in a long time so cant remember exactly how I did it.  If you play around with it, Im sure you can figure it out.

After you get it up and running, you have to go to Menu > Preferences > Desktop Session Settings and check ibus to get it to run on startup.  If its not in the menu, post back here and we can help get it going at startup in other ways.

---

### Post by whatthefunk on 2011-08-29
> **jeremybentham said:**
> ah sudo setxkbmap -layout en

does not work so how do I switch back?!

```
sudo setxkbmap us
```

Does that work?

---

### Post by jeremybentham on 2011-08-30
y

---

### Post by jeremybentham on 2011-08-30
> **whatthefunk said:**
> 
-Go to Menu > System Tools> Language Support

-Under the Language tab, on the bottom, it says Keyboard Method Input System.  Change this to ibus.

on my display Method Input System.cannot be changed -clicking on it does nothing even though an information box opens mentioning ibus.

Anyway I can make changes to keyboard at Menu > Preferences > Keyboard Input Methods
I don't know why I hadn't noticed this before

thanks for helping whatthefunk

---


---
title: "Changing keyboard layout on Ubuntu Server"
date: 2011-07-09
forum: General Help
---

### Post by Lagrima on 2011-07-09
I decided to give Linux another chance and installed Ubuntu Server. During the setup, I was asked about my keyboard layout in a rather cumbersome way. I remember answering a number of questions and even having to type a few keys so that Ubuntu could *guess* the layout, rather than just letting me select "Swedish". But that's okay; Ubuntu guessed right and suggested me to use to Swedish layout.

After setup I was still left with some standard US layout. This deserves ranting about. I may have expected to run into some show-stopper this time too, but I never expected it to be something as *fundamental* as getting the keyboard layout right!

Anyway, I googled and found the same suggested answer in many places:
```

sudo dpkg-reconfigure console-setup
```

I ran it a few times now (selecting UTF-8 and Latin1 mostly), but it makes no difference. There is no setting for keyboard layout there, so I don't see why it would work. Are all server admins expected to get a US keyboard or what?

---

### Post by seawolf167 on 2011-07-09
If you know your keyboard layout you should be able to set it with *setxkbmap*

```
man setxkbmap
```

---


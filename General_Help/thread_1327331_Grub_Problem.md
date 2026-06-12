---
title: "Grub Problem"
date: 2009-11-15
forum: General Help
---

### Post by JustMarius on 2009-11-15
hi guys i just decided to install windows xp along my ubuntu so i just resized my ubuntu partition with gparter live cd to make space for windows after that i instaled windows xp everithing worked fine so so i just reboted my sistem and sice it was loading directly to windows i reinstaled my grub but now grub shows just ubuntu T.T anione now's how to make grub show and give me acces to both systems and im not so good with linux comands 

Ps didnt now were to put this topic so i chosed general 

Ty for the help

---

### Post by Lateralis on 2009-11-15
In the first instance you can try updating grub.  In the comamnd line (Applications -> Accessories -> Terminal) type:

```

sudo update-grub

```

This will hopefully pick up your Windows XP partition, add an entry to the grub menu and everything should be fine.  

If that doesn't work, we'll need to manually edit grub to add a Win XP entry to the menu.  For that we'll need to know what version of grub you are running (typing *grub --version* into the command line will tell you) and you'll need to post the output of 

```

sudo fdisk -l

```

where the last character is a lowercase "L" and not a one (1), and

```

cat /boot/grub/menu.lst

```

---

### Post by JustMarius on 2009-11-15
[LEFT]The first command worked and im using grub 1.97beta4 thank you alot 

ty ty ty u saved me there thoth il need to reinstal everithing T.T



ty ty ty :)
[/LEFT]

---

### Post by Lateralis on 2009-11-15
Hehe.  You're of course welcome!  

If you could mark this thread as* [SOLVED]* by using the thread tools located above your first post, that would be grand!

---


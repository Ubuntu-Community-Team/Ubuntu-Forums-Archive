---
title: "USB Autorun?"
date: 2010-05-17
forum: General Help
---

### Post by drewsus on 2010-05-17
Hello all!

So, I was wondering about autorun and USB drives. 
Is there a way to run some sort of script from the USB drive when it is inserted? 

What I am wanting to do is add this to an external drive that has all my movies. My intent is to run a portable version of XBMC Media Centre when the USB is inserted into the computer. 
Its easy to do for windows, but I can't find the method for Linux/Ubuntu.

Any help would be wonderfunk!
Drewsus

ps- I would like to not have to modify the system, only the USB, if possible.

---

### Post by drewsus on 2010-05-17
bump for the evening crowd...

---

### Post by Directive 4 on 2010-05-17
hi!

so you need to make a executable text file (with gedit and chmod +x)

here's a** simple** one i use(it lives on the usb drive and works with windows)


[B][autorun] 
icon=Icon.ico[/B]

this calls up a picture (icon.ico) which is show on the desktop for the folder.

good luck!

---

### Post by drewsus on 2010-05-17
does it have to be named something specific like for Windows it would be autorun.inf (iirc)?

edit: I must have missed where you said this works for windows...
Thanks anyway :)

So is there a solution to this for Linux?

---

### Post by Directive 4 on 2010-05-18
yea, this works for linux and windows

so i guess you could mess about and try to get other commands to run.. 

i thing all you need is 
[B][autorun]

[/B]the any command you want, 
just make sure it's on the first level of the usb stick

---

### Post by Jim Danner on 2010-05-18
Hm... this didn't work for me with the instructions you gave, but it does if you *name* the file **autorun** and construct it as a typical shell script. For instance, if the contents of autorun are```
#!/bin/bash
gcalctool

```when you insert the drive you get asked (twice) whether you want to run that, and then it starts the Calculator.

---

### Post by davavanstone on 2010-07-20
did anyone get anywhere with this?

---

### Post by drewsus on 2010-07-24
> **davavanstone said:**
> did anyone get anywhere with this?

Yes, precisely as Jim Danner says above! 
Works like a charm. 
I will make this as solved now, as I should have before. 

Drew
ps- Thanks Dannerman

---


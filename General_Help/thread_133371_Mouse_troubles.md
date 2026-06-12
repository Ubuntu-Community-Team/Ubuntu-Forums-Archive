---
title: "Mouse troubles"
date: 2006-02-20
forum: General Help
---

### Post by kc0rtg on 2006-02-20
I recently got my ubuntu live cd.  I was all excited so i popped in the live cd and waited.  After all the loading and things, i see my cursor and i am ready to dive in and mess with things.  Well, my mouse doesnt work!  So, i turn off the computer and try my other mouse.  Same thing happens!  Well i tried on 2 different machines and no luck.


The mice are...

MICRO innovations PD450P Optical PS/2 Mouse
CIRQUE Power Cat GDB450 Touchpad Serial Port Mouse

I am new to the linux scene and i am excited to mess around with things. I have only used linux once or twice at a friends house (dam small linux) 

I would appreciate any help.

---

### Post by xmastree on 2006-02-20
Well, I can't imagine why your PS/2 mouse doesn't work, but I know from experience that serial mice aren't detected, and you have to manually edit the xorg.conf file.
See this thread:
[http://www.ubuntuforums.org/showthread.php?p=604061#post604061](http://www.ubuntuforums.org/showthread.php?p=604061#post604061)
for advice on how to do that.

---

### Post by kc0rtg on 2006-02-20
Thank you xmastree for the reply, i have asked for help on the beginners forum on how to acess the terminal with no mouse.  Hopefully your fix will work for me :D

---

### Post by kc0rtg on 2006-02-22
Okay, i have folowed the directions you gave.  But instead of gedit i used nano.  I found the section and i changed 
```
"/dev/input/mice"
```
with
```
"/dev/ttyS0"
```

and then i replaced
```
"ImPS/2"
```
with
```
"Microsoft"
```

After spending lots of time making sure i didnt spell anything wrong or use wrong characters i tried 
```
"/dev/ttyS1"
```
instead of
```
"/dev/ttyS0"
```

I am using the live CD by the way.  And i choose to save my changes everytime i finish with nano.  But when i return to my desktop i still have no mouse movement.  I planned on installing ubuntu to my hard drive, but if it doesnt work with either of my mice i dont know what im going to do.  Anything else i should try?

---

### Post by xmastree on 2006-02-23
Did you restart the x server after making the changes? It only reads that file as it starts. Change it back to /dev/ttyS0 (for com1) save the file then press ctrl-alt-backspace to restart the desktop.

---

### Post by kc0rtg on 2006-02-23
Thank you very much xmastree sir!  My mouse now works flawlessly.  I really appreciate your help. 

:-D

EDIT:Oh, and i knew nothing about restarting the x server.  But as soon as it finished loading everything was perfect.  I will probably install ubuntu to my hard drive in a few hours.

---

### Post by xmastree on 2006-02-23
[QUOTE=kc0rtg]Thank you very much xmastree sir![/quote]You're welcome. :D 
> My mouse now works flawlessly. **Great!**\\:D/ 

> I will probably install ubuntu to my hard drive in a few hours.Good luck.

Although the PS2 mouse is still a mystery... :-k  It's probably a better mouse too.

---


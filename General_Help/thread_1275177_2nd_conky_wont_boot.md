---
title: "2nd conky wont boot"
date: 2009-09-25
forum: General Help
---

### Post by trstncmpbll on 2009-09-25
im trying to run a second conky and i named it .conkyrc2 but it wont boot. i know im missing something but not sure what
Any ideas?
thanks

---

### Post by Liolikas on 2009-09-25
conky -c .conkyrc1 && conky -c .conkyrc2

---

### Post by m_duck on 2009-09-25
You need to tell conky where the second config file is. Running *conky* will make conky look for ~/.conkyrc and or /etc/conky.conf. To make the second one run you need to use the *-c* switch to tell it where the other configuration file is.

To make them both start at the same time, run the command:```
conky & conky -c ~/.conkyrc2
```The first one will run your regular conky at ~/.conkyrc and the second will run the other.

EDIT: I'm not sure if it is always the case but on my computer, if I run the command given by Liolikas, the first conky will open and the second will not appear until the first is closed. That may just be for me though.

---

### Post by trstncmpbll on 2009-09-25
thanks for the tips but when i run it that way they flicker back and forth, all im trying to do is have me second conky be a log of all my computers activity. is there any way i can have one conky be displayed in 2 places on my screen or any other ideas to stop the flicker

---

### Post by Liolikas on 2009-09-25
There is option to reduce it. Do not remember well just look google or .config examples of others.

---

### Post by trstncmpbll on 2009-09-25
well heres my pic to kind of understand whats going on. on the top right under my panel i want a second conky or a second different part of my other conky to display different info
[IMG]http://img.photobucket.com/albums/v610/trstncmpbll/screen.jpg[/IMG]

---

### Post by trstncmpbll on 2009-09-25
ok so i have everything going the way i want it to but now how do i get .conkyrc2 to start when the computer boots automatically. because of right now i have to run "conky & conky -c ~/.conkyrc2" to boot both of them

---

### Post by Liolikas on 2009-09-25
System->Preferences->More Preferences->Sessions

---

### Post by trstncmpbll on 2009-09-25
didnt work i tried to put in all these things, .conkyrc2, conky & conky -c ~/.conkyrc2.

but i also use openbox and enter it with ubuntu tweak

---

### Post by trstncmpbll on 2009-09-25
got it upder .config openbox services.sh

---

### Post by blur xc on 2009-09-25
I have a .startconky script, and I had to add a sleep 5 (I think, don't recall the exact number) before starting the 2nd conky.

BM

---


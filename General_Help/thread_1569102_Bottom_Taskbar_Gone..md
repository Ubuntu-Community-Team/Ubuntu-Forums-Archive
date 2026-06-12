---
title: "Bottom Taskbar Gone."
date: 2010-09-06
forum: General Help
---

### Post by jameshampshire on 2010-09-06
i tried to install some widgets that screwed up.
i then accidentally deleted the whole bottom taskbar and cannot get it back now.
plasma commands and kicker commands arent doing anything, let alone working.
i installed whatever was the new version of kubuntu over the top of ubuntu lucid 10.04
can someone help

---

### Post by DemonBob on 2010-09-06
You could reset your kde settings completely. You will have to set up backgrounds and such again. 

```
sudo rm -fR ~/.kde
```

Reboot.

---

### Post by jameshampshire on 2010-09-06
hey mate that command didn't do anything.
nothing bad showed up in terminal but it didn't give me the taskbar back.

---

### Post by jameshampshire on 2010-09-06
oh sorry didnt reboot hang on

---

### Post by jameshampshire on 2010-09-06
nah it didnt work man.

---

### Post by DemonBob on 2010-09-06
Try, i just googled, and it looks like some distro's save kde conf files under kde4, instead of kde

```
sudo mv ~/.kde4 ~/old.kde4
```

Reboot.

---

### Post by jameshampshire on 2010-09-06
james@james-desktop:~$ sudo mv ~/.kde4 ~/old.kde4
[sudo] password for james: 
mv: cannot stat `/home/james/.kde4': No such file or directory
james@james-desktop:~$ 

i love ubuntu and kubuntu but it seems i spend more of my time fixing problems then enjoying the operating system and every time i google answers that are relevant to my problem and terminal it i get either unknown command or the commands just flat out don't work.

this is very frustrating.

---

### Post by jameshampshire on 2010-09-06
i know im NOT meant to bump so frequently.
but shits gone bad.
requesting urgent help.

---

### Post by jameshampshire on 2010-09-06
ok i see the taskbar but its screwed up.
all the stuff isn't on it any more the way it was.
how does one restore kubuntu to how should i say "factory settings" to the original state it was in when i first installed it.

---

### Post by jameshampshire on 2010-09-06
Figured it out.
When I said I lost the task bar it was hiding in the corner at the top left of the screen.
I had to drag that task bar across to the middle at very top of the page.
I then left it there right clicked on the right top corner options menu for adding panels and such, went add new panel which gave me a new panel (for some reason I could only add a new panel to the bottom by dragging the original across to the middle when it was hiding in the corner, for some reason it wouldn't let me?) I then pulled the new panel to the bottom entered what demonbob said which is below of this post, deleted the old panel and restarted. it restored to "factory install default" like I first installed Kubuntu. (like reinstalling Kubuntu completely) thanks guys.


sudo rm -fR ~/.kde

---


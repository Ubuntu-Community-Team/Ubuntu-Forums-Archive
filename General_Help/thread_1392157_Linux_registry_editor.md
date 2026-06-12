---
title: "Linux registry editor"
date: 2010-01-27
forum: General Help
---

### Post by musdem on 2010-01-27
A long time ago I was trying to find a way to have the computer icon, the home icon, and the trash icon on my desktop in Ubuntu (like in windows), I got them on fine. When I put them on I used some program that was already on Ubuntu, the guide I used told me it was the equivalent of the registry editor in windows. Now I want to get on this program again to see what I can do, does anyone kn ow what it is? Thanks.

---

### Post by Leppie on 2010-01-27
i think you're looking for gconf-editor:
```
sudo apt-get install gconf-editor
```

---

### Post by Arand on 2010-01-27
And on any normal install of ubuntu gconf-editor is already present, hence the command should suffice:```
gconf-editor
```
 - Arand

---

### Post by Leppie on 2010-01-27
> **Arand said:**
> And on any normal install of ubuntu gconf-editor is already present
lol - i've never used it... good to know, tx :)

---

### Post by musdem on 2010-01-28
Thanks, can you tell me what I could do with it?

---

### Post by t4thfavor on 2010-01-28
It's a settings editor for gnome, you can edit almost any setting with it.

---

### Post by scouser73 on 2010-01-28
> **musdem said:**
> Thanks, can you tell me what I could do with it?

In Gconf-Editor click on **Apps** > **Nautilus** > **Desktop** & tick the boxes for the icons that you wish to be displayed.

---

### Post by musdem on 2010-01-28
Thanks is there anyway to start it without the terminal?

---

### Post by howefield on 2010-01-28
Go to System > Preferences > Main Menu and click on System Tools in the left hand window pane and place a check mark in the box beside Configuration Editor in the right hand window pane.

It'll then show up in your Applications > System Tools menu.

---

### Post by musdem on 2010-01-28
Ok thanks for the help.

---


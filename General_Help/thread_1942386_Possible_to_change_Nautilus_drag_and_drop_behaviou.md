---
title: "Possible to change Nautilus drag and drop behaviour?"
date: 2012-03-17
forum: General Help
---

### Post by tcmct on 2012-03-17
As the title suggests I was wondering how, if possible, to change to behaviour of the drag and drop in nautilus? I'm dual booting Ubuntu 11.10 and Windows Vista, and I have most of my files stored on the Windows partition (for easy of access between OS's). Now within Ubuntu when I drag and drop files between directories it's like a cut and paste action, but moving files from my Ubuntu partition to the Windows side it acts as a copy and paste, leaving the original file for me to delete. I would like to change this so wherever I move my file it won't leave the original. I am comfortable using terminal but not very experienced with it, and already am aware of the "mv" command within terminal. I just prefer the gui.  Any help would be greatly appreciated. Thank you!

---

### Post by coffeecat on 2012-03-17
You can achieve exactly what you want with keyboard shortcuts. The important thing to remember is that the default behaviour for a drag and drop **within** a partition is a move, whereas a default drag and drop behaviour **between** partitions is a copy - both of which you have discovered. One partition does not have to be a Windows one. Any two partitions will see a copy rather than move with drag and drop.

However, you can modify this behaviour by holding down either the shift or the ctrl key when dragging and dropping.

shift = move
ctrl = copy

Obviously, holding shift when dragging and dropping between folders in one partition is superfluous, but doesn't affect the result. Similarly with ctrl and different partitions

Have a try with the various combinations.

---

### Post by tcmct on 2012-03-17
Thank you for the fast response! The keyboard shortcuts will/do work. Is is possible though to change the mouse gesture by itself to default to always cut and paste? Maybe an internal file that could be edited?

---

### Post by coffeecat on 2012-03-17
> **tcmct said:**
> Thank you for the fast response! The keyboard shortcuts will/do work. Is is possible though to change the mouse gesture by itself to default to always cut and paste? Maybe an internal file that could be edited?

That's an interesting question and I don't know the answer - perhaps someone else does.

For what it's worth, the reason I've never looked for an answer is that I don't 100% trust automatic file moves (what you call cut and paste) between physical locations. Why? I've seen them go wrong with data loss. Which is why I prefer to copy and then delete the originals after I am sure that the copy has finished successfully.

---

### Post by XiaolinDraconis on 2012-10-02
> **coffeecat said:**
> That's an interesting question and I don't know the answer - perhaps someone else does.

For what it's worth, the reason I've never looked for an answer is that I don't 100% trust automatic file moves (what you call cut and paste) between physical locations. Why? I've seen them go wrong with data loss. Which is why I prefer to copy and then delete the originals after I am sure that the copy has finished successfully.

Amen to that. As I just made a huge mistake with dragging and dropping to Dropbox and lost hours of scripting in Conky.

---


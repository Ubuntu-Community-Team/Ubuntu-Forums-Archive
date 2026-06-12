---
title: "Confirm delete action"
date: 2012-05-11
forum: General Help
---

### Post by samwillc on 2012-05-11
Hi everyone,

Still playing with my new ubuntu 12.04 install, love it so far, think it's great!

Is there a way that when I press delete key for example, on a file or folder, instead of just deleting, I can confirm the action first (like in windows)?

Thanks.

Sam

---

### Post by forrestcupp on 2012-05-11
Open up Nautilus, the file browser, and go to Edit-Preferences, and click the Behavior tab. At the bottom, there is a checkbox that is probably already checked that says "Ask before emptying the Trash or deleting files". It won't ask you before you move something to Trash because if you make a mistake, you can just go to the Trash can and restore it. But it *will* ask you before you empty the trash, or actually delete the file.

If you want to have an option to really delete files, check the box under that that says "Include a Delete command that bypasses Trash". If you do that, and choose to delete a file, it will ask you first.

---

### Post by samwillc on 2012-05-11
Hi thanks,

The behaviour I am expecting (although I can live without) is:

File > press delete - do you want to delete this file? Yes/no
If yes > moves to trash

I have checked both boxes in behaviour tab and nothing has changed. Pressing delete on a file doesn't give a message box, it just moves to trash like it did before the box was checked.

Do I need a restart to action the changes?

Sam.

**edit**

Right clicking on the file and selecting delete: do you really want to delete file? pop up (as expected)
Pressing delete KEY on the file - no pop up (??)

Strange.

---

### Post by papibe on 2012-05-11
> **samwillc said:**
> Right clicking on the file and selecting delete: do you really want to delete file? pop up (as expected)
Pressing delete KEY on the file - no pop up (??)

Just note that 'Right Click -> delete' doesn't send the file to the Trash, it just delete it forever, thus the warning (as described on Preferences).

Regards.

---

### Post by samwillc on 2012-05-11
Hi thanks, but I expected the same behaviour whether right click -> delete OR pressing Del key.

Surely they should do the same thing.

Sam.

**edit** ok I think I get it. Include delete command means delete will appear in the menu after right click. Uncheck that box and it's not there.

I am just used to windows where you get a warning before you move to trash. I'm sure I'll get over it!

---

### Post by forrestcupp on 2012-05-11
> **samwillc said:**
> Hi thanks, but I expected the same behaviour whether right click -> delete OR pressing Del key.

Surely they should do the same thing.

Sam.

**edit** ok I think I get it. Include delete command means delete will appear in the menu after right click. Uncheck that box and it's not there.

I am just used to windows where you get a warning before you move to trash. I'm sure I'll get over it!
One possible solution for you is to press Shift+Delete. That is the keyboard shortcut to delete a file, bypassing the Trash. If you do that, it will be the same as right-clicking and choosing Delete, and it will ask you to confirm.

There are ways to change the keyboard shortcut so that just pressing the Delete key will be for a real file delete, but that takes more work. It's possible to do that, if you want to, though.

A lot of people have requested for Nautilus to ask for confirmation to Move to Trash, but they have never added that functionality.

---

### Post by samwillc on 2012-05-12
Ah, ok thanks.

Now I know the functionality is not there, that's all I needed.

Sam.

---


---
title: "OpenOffice Calc: Delete key annoyance"
date: 2010-02-04
forum: General Help
---

### Post by chewearn on 2010-02-04
In OpenOffice Calc, when you pressed Delete key, this dialogbox pops up:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=145952&stc=1&d=1265276523[/IMG]

How do I tell it to stop asking me, and use "Delete all" option every time?

---

Thank you for your kind assistance.

---

[SIZE=4][COLOR=Red]**And yes, I know if you press Backspace key, it will delete the content immediately, and does not ask with this dialogbox.  But Backspace key does not delete any custom Formats on the cell.**[/COLOR][/SIZE]

E.g. if I have set the cell to Bold and red font, Backspace key does not remove the Bold and red font formating.

---

---

### Post by chewearn on 2010-02-05
bump (in the night)

---

### Post by lotharmat on 2010-02-05
I have had a look through the options exhaustively and cannot find any setting to do what you want.

---

### Post by chewearn on 2010-02-05
Thanks for replying.  I tried once again to solve this problem, did a couple of Google searches.  And I found a workaround.

[SIZE=4][B][COLOR=Red]Instead of delete, I just need to "Cut" the cell (i.e. Shift+Del).
That would remove everything for the cell.
And then, I reassign keyboard shortcut "Delete" to mean "Edit > Cut".[/COLOR][/B][/SIZE]

---

### Post by StuartN on 2010-02-05
> **chewearn said:**
> Instead of delete, I just need to "Cut" the cell (i.e. Shift+Del).   That would remove everything for the cell.  And then, I reassign keyboard shortcut "Delete" to mean "Edit > Cut".

Pressing Backspace deletes without opening a dialog. Although you have now edited the original post to say you knew this.

---

### Post by chewearn on 2010-02-05
> **StuartN said:**
> Pressing Backspace deletes without opening a dialog.

Yes, and if you read my first post, you would know that I did knew about Backspace, and that Backspace does not do the job I wanted.

---

### Post by rossmoore on 2010-02-05
This may or may not be quite what you're after:
Click Tools->Customize...
Under the Keyboard tab you can specify what action you want Calc to take when you hit the Delete key. The UI of that Customize control takes a bit of getting used to - basically you choose the Delete key from the list in the top box, then the action you want to be taken in the 3 boxes below, then hit modify. "Delete Contents" is what happens when hit the Backspace key, so you could assign that. If that isn't quite what you want, you could probably write a macro and assign it to that key...

---


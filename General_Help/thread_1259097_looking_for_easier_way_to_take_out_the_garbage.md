---
title: "looking for easier way to take out the garbage"
date: 2009-09-05
forum: General Help
---

### Post by driven1 on 2009-09-05
I hate that every time I want to delete a file, I must put it in the trash, then either open the trash or right-click it command it to empty, then confirm that yes, I really do want to take out the garbage. It seems to me that in an earlier version of Ubuntu, i found a way to turn off the warnings, but I can't remember where. I do seem to recall that I stumbled across it somewhere unexpected. Also, under MAC OS X, I could use key combinations to send items to the trash and delete them, all without annoying dialog boxes. Is there a set keyboard command, if not can I create one? Thanks for making my home folder a cleaner place.

---

### Post by relay_man on 2009-09-05
If the file is in your home folder then, 

From the command line:

rm *filename*

If the file is in a subfolder in your home folder, then 

cd /*folder name*

then

rm *filename*



rm means remove...forever
If you aren't absolutely sure, ask someone before you hit <enter>.

---

### Post by sethhikari on 2009-09-05
Shift+del Instantly deletes a file

---

### Post by peakpc on 2009-09-06
Right mouse on file in file bowser, select delete from the drop down list, and then delete button. the file will be gone.

---

### Post by 3rdalbum on 2009-09-06
> **peakpc said:**
> Right mouse on file in file bowser, select delete from the drop down list, and then delete button. the file will be gone.

You have to enable that from gconf-editor first:

Run this command:

```
gconf-editor
```

In the Gconf Editor, open up Apps > Nautilus > Preferences and click the "Enable Delete" checkbox.

---

### Post by driven1 on 2009-09-06
Thanks, I forgot all about ```
gconf-editor
```

I found the option to turn off the warning. That's exactly what I needed.

---

### Post by aysiu on 2009-09-06
In Nautilus (the file browser), go to Edit > Preferences > Behavior > Trash

Make sure *Ask before emptying the Trash or deleting files* is unchecked/unticked.

Then, the next time you want to delete a file straight away, press Shift-Delete.

---

### Post by driven1 on 2009-09-07
Thanks again, everyone. Those were the exact tips I needed. I am a switcher, from OS X to Ubuntu. It has been an interesting year with ups and downs, but I don't intend on going back.

---


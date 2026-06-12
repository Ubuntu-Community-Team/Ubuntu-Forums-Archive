---
title: "deleted files"
date: 2010-03-10
forum: General Help
---

### Post by nischalinn on 2010-03-10
How to recover deleted files in Ubuntu when I did Shift+Delete?

---

### Post by Kevbert on 2010-03-10
Providing the files are in the wastebasket, left click on it (in bottom right-hand corner assuming you're using Ubuntu). Select and highlight the files you want, then right-click at select Restore from the menu that appears.

---

### Post by geirha on 2010-03-10
It depends on the filesystem. Undeleting is impossible on ext3/4 filesystems, though you might be able to recover the data contained in the file. See [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by howefield on 2010-03-10
> **Kevbert said:**
> Providing the files are in the wastebasket, left click on it

Doesn't shift-delete bypass the waste basket ? That's the reason for the combo.

---

### Post by Roasted on 2010-03-10
> **howefield said:**
> Doesn't shift-delete bypass the waste basket ? That's the reason for the combo.

This is correct. Shift + Delete = permanent delete instantly. No files get transferred to the trash when you use this method.

As far as I know, you'll have to look into some sort of file recovery program. There's many out there (I believe PhotoRec is one) but I haven't used any to offer more help. Look into that avenue though...

---

### Post by Kevbert on 2010-03-10
Tried it in Nautilus on 9.04/ext3 and text files were sent to wastebasket. Did this prior to posting #2. Is that a problem/bug ?

---

### Post by Roasted on 2010-03-10
> **Kevbert said:**
> Tried it in Nautilus on 9.04/ext3 and text files were sent to wastebasket. Did this prior to posting #2. Is that a problem/bug ?

Might be. Running 9.10 and when I delete a text file, it deletes with zero warning and goes to the trash. If I shift + delete, I get a warning that I'm about to permanently delete the file. If I shift + delete, it doesn't go to trash and permanently vanishes.

---

### Post by Kevbert on 2010-03-11
Tried again (several times) and this time I get the expected behaviour. Not sure how I was able to shift+delete and get multiple files to go to wastebasket. :confused:

---

### Post by Roasted on 2010-03-11
Not to question your keystrokes, but are you sure you're holding down shift, and then with shift still held down, pressing delete??

---


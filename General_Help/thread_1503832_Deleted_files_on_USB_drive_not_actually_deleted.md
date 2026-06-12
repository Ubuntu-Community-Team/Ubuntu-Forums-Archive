---
title: "Deleted files on USB drive not actually deleted"
date: 2010-06-07
forum: General Help
---

### Post by JlyGrnMigt on 2010-06-07
I searched the forum with various terms and didn't find anything, so my apologies if this is a common and/or newbie problem.

It seems that when I have a USB drive plugged in to switch the files around, those that I delete are still taking up space.  I first noticed it with a Chinese MP3 player and thought it was the player being crappy.  I could still play all the songs that were supposedly gone.  Today, I noticed it with a little thumb drive that I've had for years.  I plugged it into my husband's computer running winXP, and the files showed up in a weird, unusable form.  I was able to delete them for real. 

Is this just a formatting issue?  Thanks.

---

### Post by God Of Atheism on 2010-06-07
I've noticed this as well, what does delete them is just deleting the ./thrash folder on the usb device (make sure you can see hidden files).

---

### Post by JlyGrnMigt on 2010-06-07
I will try that now.  Thanks!

---

### Post by Chesamo on 2010-06-07
Hit Ctrl+H to view hidden files (or ls -a in the Terminal). Shift+Delete will remove the folder without sending it to the Trash.

---

### Post by arubislander on 2010-06-07
Even after the files have ended up in the trash, if you choose Empty Trash before unmounting the USB drive the files will be really gone.

---


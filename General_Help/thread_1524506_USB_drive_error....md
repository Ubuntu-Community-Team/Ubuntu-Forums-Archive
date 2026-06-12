---
title: "USB drive error...???"
date: 2010-07-05
forum: General Help
---

### Post by robertcoulson on 2010-07-05
Can not access USB drive anymore...Get error as per attachment...Can anyone help...!!!
Robert

---

### Post by grindboy on 2010-07-05
Might help:
[http://ubuntuforums.org/showthread.php?t=1437631](http://ubuntuforums.org/showthread.php?t=1437631)

---

### Post by robertcoulson on 2010-07-05
Hi Grindboy....Tried your link but got this error in the terminal...see attachment...I am lost.
Robert

---

### Post by robertcoulson on 2010-07-05
Thanks for your help Grindboy...Think I will just re-install 10.04 and hopefully that will correct my problem.
Robert

---

### Post by Penguin Guy on 2010-07-05
Looks like you made a typo - it should be **/dev**, not **/deb**.

---

### Post by robertcoulson on 2010-07-05
WOW...Typo error where...???...I haven't typed anything yet...???
Robert

---

### Post by robertcoulson on 2010-07-05
Oh....I see what you mean, the web page I copied from had a typo error...Will try again.
Robert

---

### Post by robertcoulson on 2010-07-05
Oh well..still get roughly the same error except for "bad magic number"...???????????????????????????????????????
Robert

---

### Post by MooPi on 2010-07-05
Why would you need to reinstall over a bad USB drive?
It may be better to try to delete the partition table on the drive then create a new partition table and format again. Much less trouble than reinstalling.

---

### Post by robertcoulson on 2010-07-05
I would..But my daughter's wedding pictures are on it...Hope the USB drive isn't bad...I have dual boot with XP..Maybe I should see if XP will recognize it first.
Robert

---

### Post by MooPi on 2010-07-05
Try this before you go and use windows.
```
sudo fdisk -l
```
Post the results back here please.

---

### Post by robertcoulson on 2010-07-05
tried it and got this return in the terminal...But still can't access USB.
Robert

---

### Post by MooPi on 2010-07-05
You will need to boot into windows to attempt ckeckdisk. The e2fdisk is best dealing with native linux file systems and yours is a fat32. Linux has utilities for fat32 but I would suggest first to correct with a checkdisk. If you plug the drive in before boot Windows may check it automatically.

---

### Post by robertcoulson on 2010-07-05
Ok..Will try that..thanks.
Robert

---


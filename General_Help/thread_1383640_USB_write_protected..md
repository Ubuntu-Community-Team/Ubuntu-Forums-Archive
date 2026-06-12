---
title: "USB write protected."
date: 2010-01-17
forum: General Help
---

### Post by Dracar on 2010-01-17
OK, ive tried my hand and failed. My friend was using my computer nad he didnt safely remove his USB MP3 and now it is write protected. Ive tried windows diskpart (nothing), ive tried fsck ("disk maybe in use?"), i tried to format(write protected)ive tried otehr USB slots and other computers. This has happened to me sooo many times and i can never find a damn thing about it, can some one tell me how to fix this??? There has to be a simple fix as it is such a simple issue, an issue any one who has used windows for 90% of their computing history could make.
Thanks, Tony.

---

### Post by gabo.cr on 2010-01-17
Did you try as root?

```
sudo -s
```

Then remove the files:

> rm -R /media/USB/folders

USB is the name of your USB drive and "folders" the ones that you want to delete.

BE EXTRA CAREFUL, WORKING AS ROOT CAN BE DANGEROUS !

---

### Post by Dracar on 2010-01-17
yea ive tried it as root. doesnt work on windows computers either.

---

### Post by gabo.cr on 2010-01-17
The USB drive seems to be damaged.
Unless anybody else knows a solution...

---

### Post by Leppie on 2010-01-17
as it doesn't seem to be something in the os, what's the make and model of the mp3 player?

---

### Post by warfacegod on 2010-01-17
Removing an USB without unmounting has the potential to corrupt files. Have you tried to plug it back into your machine and unmounting it properly?

---


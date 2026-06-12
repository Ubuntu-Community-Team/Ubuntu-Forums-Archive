---
title: "Progress bar then goes to recovery text mode??"
date: 2009-12-09
forum: General Help
---

### Post by Bucky Ball on 2009-12-09
Hi all,

Odd one. I only get to work with this machine once every six months so hoping I can fix this quickly. Have looked in the logs but can find nothing suspicious and it might be nothing, just a tweak. Hoping someone might be able to shed some light ...

Problem is when I boot into a regular Ubuntu 8.04 kernel (not recovery) I get the progress bar for longer than I would imagine (in comparison to my three machines 750Kms away!) then it hits a text based boot. I see no obvious errors as the info flashes by. The machine then hits the login screen and everything is as normal. Shuts down fine with the progress bar going the other way. 

This is not a major issue. The machine works perfectly (as far as I can tell) in every other respect. Just totally curious as to why this is happening. It is my mother-in-law's machine which I built almost a year ago. She loves it and Ubuntu but is a user only and not into tweaking so I am just wanting to make it as user-friendly an experience as possible, as I have from the start. 

Footnote: I see the machine once every six months or so but that is all that is needed. My mother-in-law is not exactly a tweaker or coding guru so nothing ever breaks. I just tune things up a bit, help her with any questions she has (although that hasn't been many over the past 8 months or so),  and give her a few tips. She finds it easier than windows, which she used for years, and does not even have it installed on this machine. 

Hoping someone can let me know how to get an attractive progress bar boot rather than slipping to the text. Cheers. :)

---

### Post by JBAlaska on 2009-12-09
Try this in a terminal:
```
gksu gedit /boot/grub/menu.lst
```

Then look for a similar entry to this (Your kernel will be different)
```
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f **ro quiet splash**
```

If these **ro quiet splash** are not at the end, add them and save.
If they are there you might have a filesystem error and need to just FSCK it..

---

### Post by Bucky Ball on 2009-12-09
Yep, **ro quiet splash **is there. Still investigating but not getting far.

---


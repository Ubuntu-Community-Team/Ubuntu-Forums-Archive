---
title: "Help with restoring Evolution mailbox"
date: 2011-07-04
forum: General Help
---

### Post by hogar_pg on 2011-07-04
It seems that one in a while I just have to have a MAJOR issue with my Ubuntu desktop. 2-3 days ago, I was prompted to do (if I recall correctly) "version upgrade" on my 11.04 64-bit Ubuntu. As any average unsuspecting user, I clicked on OK and left it for updating.

After the update was over, I restarted the computer and was unable to boot since. After several tries, using failsafe option, I booted into X but unfortunately did not backed up my email. 

After some googling, I obviously did something very wrong as I am unable to start X in any way, so I decide to reinstall Ubuntu and to install 10.04 LTS.

Problem is that I can't find my emails from old hard drive now. I tried in ~/.evolution and ~/.gconf/apps/evolution, but no success. By coping those two folders I retrieved only server settings, but no email and no  contacts. Can anyone help? Thanks!

---

### Post by e79 on 2011-07-04
It probably won't help much but in Natty, the evolution folder you are seeking for (with mails and contacts at it seems) is under :

```
~/.local/share/evolution
```I don't know though if retrieving those files/folders would help you to restore Evolution as it was (always exported/backed up mine).

---

### Post by hogar_pg on 2011-07-04
Thanks a lot. Copying ```
~/.local/share/evolution/mail/local
``` from 11.04 folder to ```
~/.evolution/mail/local
``` on 10.04 folder did the trick for the emails. Could not find the combination that would save the address book, but that is my least worry. Thanks again!

---

### Post by e79 on 2011-07-04
I'm glad you could at least get all your emails back and it's a good thing to kow it works ! I'll keep searching for your contacts issue and let you know if I find anything; maybe someone else could hop in and help you with this last bit !

Regards

---

### Post by hogar_pg on 2011-07-04
No need, it is only a few most frequent addresses that I can very easily put into address book again. (and I erased the HDD after retrieving the emails) :D

You helped a LOT! Thanks again!

---

### Post by e79 on 2011-07-04
Oki if you say so :p

Best Regards

---


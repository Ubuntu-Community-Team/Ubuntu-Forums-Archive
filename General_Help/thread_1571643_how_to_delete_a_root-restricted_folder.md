---
title: "how to delete a root-restricted folder"
date: 2010-09-09
forum: General Help
---

### Post by SanguineTeddy on 2010-09-09
Hello everybody! To keep things (relatively) brief, I now use Pinguy OS (not sure if you're familiar with it, but it's basically ubuntu for lazy people - lots of goodies are installed and ready-to-use from the moment you start using it, but nothing major...think of the restricted extras, wine, etc). And, yes, it's ubuntu 10.4.

The reason I'm writing in is because I backed up my information from 10.4 to an external hard drive before I switched to pinguy using sbackup. Once I installed pinguy, I made sure to download sbackup and hit restore. So far, all fine and dandy, except when it restored my information, it extracted all the information to a new folder in /home, which is root-restricted, so I can't even access it normally. I got annoyed, and just manually extracted the music and documents (which were the only things I really cared about anyway), and now I'd like to delete the 15 or so gigabytes just sitting on my computer, taking up space. 

The folder being root, I couldn't just drag it to the wastebasket. so I started terminal, entered root, typed rm /home/tmpuWiQlI (the folder in question), only to be told it's a directory and can't delete it! What gives?? Also, if anybody could suggest any way to delete the folder, I'd be very grateful.

Thanks!

---

### Post by Noz3001 on 2010-09-09
```
sudo rm -r /directory

```

---

### Post by SanguineTeddy on 2010-09-09
worked like a charm - thank you very much!

---

### Post by NearlyALaugh on 2010-09-09
Just be careful with **rm -r** as root.

---

### Post by garvinrick4 on 2010-09-10
I imagine a user can use GUI if they choose to.

ALT/F2 and type in gksudo nautilus then you can navigate to directory and toss them while in root nautilus.

---

### Post by pinguy on 2010-09-10
With Pinguy OS you could of just right clicked in the folder went to "scripts" > "root-nautilus-here" and this would of gave you root access allowing you to delete the folders.

---

### Post by tomsfeenie on 2012-02-14
Thank you, worked just as expected.

---


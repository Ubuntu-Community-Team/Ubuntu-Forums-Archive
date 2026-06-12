---
title: "Removing LUKS from an ubuntu install"
date: 2011-11-10
forum: General Help
---

### Post by renegadeandy on 2011-11-10
Hey guys.

I want to remove LUKS drive encryption from my system so that I can easily repartition the drive. I could add LUKS back after I have doen the work.

Can somebody please tell me how to do this?

---

### Post by whitethorn on 2011-11-10
So you have partitions set up and you want to remove the encryption then repartition and encrypt again?

It's not possible to just remove encryption and still have all your data intact. You have to backup everything on the partition somewhere else then manipulate the *empty* partitions however you want. Then you can encrypt everything again and copy the data back. 

I would do all of this from a Live CD, before you start repartitioning make sure you have everything backed up. Mount your disk rsync the data to an external harddrive, or another disk. Make your changes, rsync the data back.

Oh and before you do anything, make sure you back up your data :)

---


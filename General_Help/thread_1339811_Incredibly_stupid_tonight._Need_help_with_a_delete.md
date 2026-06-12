---
title: "Incredibly stupid tonight. Need help with a deleted folder."
date: 2009-11-27
forum: General Help
---

### Post by agim on 2009-11-27
Okay, so I have a partition where I keep lots of random stuff, old /home folders, pics, things like that. The partition itself was an old ubuntu partition, so its set up like a regular install, with the filesystem, and everything was in the home folder. I was cleaning it up, I was using Nautilus as a super user (I know, I know, dumbest thing I have ever done. I am truly ashamed.) and when I was checking the size of the file, accidentally deleted the damn thing. I unmounted to partition, so I didn't write over anything, and I am now hoping to get that folder back.

Gparted is still reading the partition as full, and when I tried to unmount from with nautilus, a dialog popped up that asked me if I wanted to empty the trash to retrieve hd space. I said no.

I really, really hope someone can help me find my 10 or so lost GB of saved data from the last 3 years.

Thanks Everyone.

---

### Post by scouser73 on 2009-11-27
Have you checked the recycle bin, if it's there then just restore it.

---

### Post by agim on 2009-11-27
Where is the file address for the recycle bin?

---

### Post by agim on 2009-11-27
Remember, i have no home folder. On that partition.

---

### Post by lisati on 2009-11-27
Look for a trash can icon at the bottom right of your screen.

---

### Post by agim on 2009-11-27
No, its not there. I deleted something from another partition, not from my current partition. Such things aren't usually kept in the current home recycle bin.

---

### Post by raktarok on 2009-11-27
**Don't give up, this may save you!**
Mount that partition again and do a ctrl+h at the outermost folder, ie if you mounted it at /media/DATA then at DATA. There should be afolder called .Trash-1000. All your files should be there, since you never deleted them permanently.

---

### Post by agim on 2009-11-27
You are the man! Files saves. Holy damn, so many family pictures and personal projects.
Thanks so much!

---

### Post by raktarok on 2009-11-27
you did a very wise thing when you said no when you were asked to delete the trash! since it was not mounted when you checked your trash earlier, it did not show up. be careful from now on though, especially while doing stuff as superuser. Remember, with great power comes great responsibility! :)

---

### Post by iponeverything on 2009-11-28
It is also a good time to remind you that you need to put a copy of your valuable data on separate drive and keep that drive in place place where it won't be subject to the same adverse conditions that might affect the original drive (flood, fire, theft, etc) Drive failure is not uncommon either..

---

### Post by agim on 2009-11-28
That's actually what I was doing. I was erasing things I didn't need so it would fit on my drive. Maybe its just time to get a bigger external hd.

---


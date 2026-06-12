---
title: "Could Duel Booting cause suspend problems??"
date: 2011-07-30
forum: General Help
---

### Post by redFlameStar on 2011-07-30
I've tried a few times (duel booting) to move fully over to ubuntu but for some reason suspend never works. My life style it's big enought pain to move back to Win7. I'm just wondering if duel booting would or may cause Ubuntu to not be able to suspend?? Any thoughts would be neat.
THANKS

---

### Post by garvinrick4 on 2011-07-30
No Ubuntu is on one partition and windows is on another. Unless you have a Wubi install which is in a folder inside of Windows.

---

### Post by Mark Phelps on 2011-07-30
To answer your original question -- most certainly YES!!

But ... where I've seen this happen is where folks did the following:
1) Suspended MS Windows
2) Rebooted, but into Ubuntu, this time
3) Made changes to files in the MS Windows partition (I know -- really BAD idea, but folks will do anything these days)
4) Suspended Ubuntu
5) Rebooted but this time, started MS Windows -- and discovered that the file system had problems and/or their file changes were gone.

So, as long as you ALWAYS boot back into the same OS that you suspended, you should have no problems.

---

### Post by Shehab Ahmed on 2011-07-30
i agree with 
 				 				[garvinrick4]("http://ubuntuforums.org/member.php?u=899097")

---


---
title: "Hard drive went blank!"
date: 2010-06-17
forum: General Help
---

### Post by russki_drewski on 2010-06-17
Okay, so I have this external drive that is formated as an ext3 (maybe ext4, not sure). I was using the latest ubuntu liveCD to access it one day and then the next thing I knew the contents of the drive disappeared and it only shows a lost&found folder. What happened?!

I've run testdisk on it and it didn't recover anything.

I've run photorec for about 20-30 min and it didn't find a single file. (I know photorec needs several hours to run, but I figured it would find at least a couple of files within that time so I could check it.)

Any ideas on what the heck happened? Any ideas on what to do to recover my data? 

Should I run a disc analysis tool like SpinRite to see if the drive is going bad? It doesn't seem like its going bad to me. Its only a few months old.

Hey, thanks for any help guys. Ubuntu forums rock!

---

### Post by dabl on 2010-06-17
If there is not a damaged filesystem (as revealed by a fsck), and/or if testdisk and GParted show the space as unused, except for the Lost&Found folder, then one would have to conclude that either all data were deleted, or else the partition got reformatted.

---

### Post by russki_drewski on 2010-06-29
So I tried some stuff on this drive that I have. It reports that part of the disc is occupied, but it doesn't show anything of course. 

I ran photorec on the drive and it came up with only 4 meaningless files.

Now, I'm not sure if the drive was formatted with ext3 or ext4. Would that make a difference to photorec on how it analyzed the disc and searched for files? Would it make a difference to testdisk?

Any ideas or input would be greatly appreciated. I would really like to recover this drive if I can!

Thx * 10^6
russki_drewski

---

### Post by russki_drewski on 2010-06-30
Anyone?

---

### Post by russki_drewski on 2010-07-02
So, am I plum out of luck on this one?

Would it make any difference if the drive was formatted to ext3 or ext4?

Do testdisk and photorec support ext4?

Any insight is appreciated.

Thx!

---

### Post by russki_drewski on 2010-07-06
Wow, I'm sorry to say I'm a little disappointed with the forum on this one. Not in that my problem hasn't been resolved, but that there has been so little feed back and ideas given on what to do here.

Is there no one that has an idea of what to do or what might have happened?

---


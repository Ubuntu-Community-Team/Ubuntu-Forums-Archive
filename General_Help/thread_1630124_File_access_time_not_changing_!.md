---
title: "File access time not changing ?!?"
date: 2010-11-24
forum: General Help
---

### Post by ianc1 on 2010-11-24
I am trying to modify the file access time in a Python routine I have.  I have I believe the correct code for this but have a greater issue.  Looking at a random file in my home directory I can see it was last accessed yesterday (I didn't open this file yesterday) so it was presumably my virus scan.  No problem there.  Now I have opened the file today, rescanned the file for viruses and read the file in Python and the file access time remains the same!

I have checked the access time by right clicking on the file and choosing Properties, using "ls -lu", and using os.stat(path) in Python.

I'm confused.

Any ideas, please.

---

### Post by DaleyB on 2010-11-24
If you do a "touch" on the file does it update the timestamp? And if so could you make a system call from within the Python procedure in order to update the timestamp on the file?

D

---

### Post by ianc1 on 2010-11-24
Thanks D.  Touch filepath does update the access time to the time I "touched" the file.  So the access time is changing.  Any ideas why the other file operations had not changed the file access time.  I had even logged out and restarted in a vain hope that that would update all the access times.

---

### Post by biggerben on 2010-11-24
you don't by any chance have noatime in the /etc/fstab?

---

### Post by ianc1 on 2010-11-24
Unfortunately my etc/fstab file, which is 14 lines in length and remains unchanged by me since installation of 10.10 does not contain noatime.

---

### Post by dcstar on 2010-11-25
> **ianc1 said:**
> I am trying to modify the file access time in a Python routine I have.  I have I believe the correct code for this but have a greater issue.  Looking at a random file in my home directory I can see it was last accessed yesterday (I didn't open this file yesterday) so it was presumably my virus scan.  No problem there.  Now I have opened the file today, rescanned the file for viruses and read the file in Python and the file access time remains the same!

I have checked the access time by right clicking on the file and choosing Properties, using "ls -lu", and using os.stat(path) in Python.

I'm confused.

Any ideas, please.

I suspect that you need the "atime" option in your fstab as "noatime" may well be set as default nowdays.

---

### Post by asmoore82 on 2010-11-25
> **dcstar said:**
> I suspect that you need the "atime" option in your fstab as "noatime" may well be set as default nowdays.

I heard a while back that "noatime" was to become the default...
But I just tested this on my 10.04 laptop and atime is still functional.

I'm actually going to turn this off immediately,
I would suggest re-engineering your python code to rely on something else.

`touch` updates the file modification time which also is guaranteed to update atime.
Can you just use mtime?

---

### Post by ianc1 on 2010-11-25
Thanks asmoore82.  What is the benefit of noatime apart from less disk wear?  Also whats relatime?

None of my mount points have atime or noatime as an option although /home which is ext4 has defaults as the option.  Unsure what this is some googling to do.  I'm still confused about what, why and when file access times change as yesterday no matter what I did the access times only updated on touch.  Otherwise they still said last accessed the day before when I ran a virus check.  Yet a virus check yesterday didn't update the access time.

Regarding the Python code I was not trying to write a script to update the access time rather to correct the access time after hashing and copying a file I wanted the atime back as it was.

Ian

---

### Post by dcstar on 2010-11-26
> **ianc1 said:**
> 
........
Regarding the Python code I was not trying to write a script to update the access time rather to correct the access time after hashing and copying a file I wanted the atime back as it was.

Ian

Then spend 30 seconds editing your fstab file and your problem should be solved.

---

### Post by ianc1 on 2010-11-26
> **dcstar said:**
> Then spend 30 seconds editing your fstab file and your problem should be solved.

I agree that this is an easy option particularly know I understand more about ftstab and its options (relatively new to this Linux lark).  However, I would still like to get to the bottom of while the file access time or atime does not seem to reflect the file open/read time.

---

### Post by asmoore82 on 2010-11-26
> **ianc1 said:**
> Thanks asmoore82.  What is the benefit of noatime apart from less disk wear?  Also whats relatime?"relatime" is the good one! Thanks for the reminder!
It's no such much about disk wear as it is about efficiency. Disk writes are naturally slower than reads but keeping up with atime turns every read into a read AND a write.

---


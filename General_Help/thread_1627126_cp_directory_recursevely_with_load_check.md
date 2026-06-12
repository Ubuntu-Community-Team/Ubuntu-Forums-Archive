---
title: "cp directory recursevely with load check"
date: 2010-11-21
forum: General Help
---

### Post by henkas on 2010-11-21
Hello,

Could you possibly give me a clue on how the bash script should look to copy huge directory with multiple sub-folders to a new place place while checking load and stopping for several seconds if load reached lets say 3 or 4 ? 

I only know the simple command cp -r /dir/allfiles /dir/newplace

However would like to copy over 30 000 files which will cause me a high load. 
Thank you for your thoughts.

---

### Post by gorfou on 2010-11-21
you don't define exactly do you want to do. Is it load on your processing resources or disk space.

If it's the first, you may try to lower the priority of your cp process : see the 
nice 
command.

For the latter, you may check beforehand disk usage using
df -h
and the size of the directory you want to move with 
du -h 
(use -s to limit the output at a summary, and -h option is to print sizes in human readable sizes, instead of in KB)

---

### Post by henkas on 2010-11-21
What I need exactly is to copy 10 000 files from directory /old to directory /new 
I want to copy all files as it is, however copying so many files would cause huge server load. That is why I would like to check server load ever file copied and if load is over 4, sleep for 30 seconds, then continue. 

Do you know how that would look like?

---


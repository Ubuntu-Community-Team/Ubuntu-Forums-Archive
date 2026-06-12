---
title: "Error in Intel Debugger IDB while debugging fortran code"
date: 2011-08-09
forum: General Help
---

### Post by fallschirmjaeger on 2011-08-09
I have an issue. I compiled my fortran code with the following command
$ ifort -mcmodel medium -shared-intel xyz.f   (i use extra arguments to increase the stack)

it compiles well and gives our a.out

now when I call idb 

$ idb a.out  

the GUI opens but there is an error - Error: could not start debugee
                                                                                                         could not start process for a.out
                                                                                                        No image loaded....Recovering..... 

Can anyone tell the problem ? ... when i compile my code without  additional memory allocation as stated above ..everything works ...but  not after that...... would be grateful if someone can shed some light

---

### Post by Myoldmopar on 2011-08-23
Hey just to let you and everyone else know, I encountered this same exact problem.  I was running ifort with debug symbols generated, optimization off, etc.  It built fine, and actually I was able to debug fine in idb.  

Then one day I got a new machine..decided to use the secondary hard drive to store my development work.  idb was then installed on the file system of disk 0, dev work on a partition on disk 1.  Eclipse was also installed on the file system of disk 0.  I used eclipse to build the project and it built fine, but it wouldn't debug.  I noticed it wasn't executable either...odd...it had been working great on my previous machine with nearly identical setup.

I moved the build back to the main file system partition with everything else, rebuilt, and voila it worked perfect.  idb can happily debug now.  I'm guessing it has to do with the development partition being NTFS (it is shared storage between my windows and ubuntu partitions), but I didn't have time to investigate further yet.

Good luck everyone!

---


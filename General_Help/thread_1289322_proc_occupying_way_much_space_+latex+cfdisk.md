---
title: "/proc occupying way much space +latex+cfdisk"
date: 2009-10-12
forum: General Help
---

### Post by jayeshbhat55 on 2009-10-12
I got 3 problems

My ubuntu amd64 is totally up to date with all the packages n updates. I have installed matlab r2008b n virtual box ose with win xp32bit as my VM. 

1) I had allocated 14.7 GB to ubuntu and now its 88% full!! (12.8GB). The only heavy file in there is matlab which is occupying about 3  GB. how come linux is occupying so much space. my /proc folder is 5GB in size.! is it normal?

2) Now wen I want to edit my ubuntu partition, cf disk is giving an error : 
FATAL ERROR: cannot open disk drive 
Press any key to exit cfdisk
What is the workaround for this? what are the other ways of partitioning?

3) I am working as an RA and I require latex to edit n type papers. I have never used latex before. texlive-full is a whoppin 700MB n then 1.1GB of HDD space. Do i need entire latex or texlive-latex-base(137 MB) will do.?   

Thanx

---

### Post by lensman3 on 2009-10-12
The files in /proc are nothing more than hooks into the running kernel.  They don't take up any real disk space.  

If you do "du /proc" from a command line you will see that the files occupy zero space.  The large file "/proc/kcore" is a mapping of the current running kernel and all subprocess.

---


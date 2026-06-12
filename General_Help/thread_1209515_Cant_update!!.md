---
title: "Cant update!!"
date: 2009-07-10
forum: General Help
---

### Post by Joselito84 on 2009-07-10
hey people, havnt logged into ubuntu for a while, i thought i would to get all the updates for it guess what? i cant!! this is what i get:

jose@Joselito:~$ sudo apt-get update
E: Type '--2009-04-14' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
jose@Joselito:~$ sudo apt-get upgrade
E: Type '--2009-04-14' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
jose@Joselito:~$ 


any ideas?

---

### Post by michy99 on 2009-07-10
You have a messed up file. If you post the output of this command I will tell you how to fix it.```
cat /etc/apt/sources.list.d/winehq.list
```

---

### Post by Joselito84 on 2009-07-10
hmmm dont think this is right but here is what i got...

jose@Joselito:~$ cat /etc/apt/sources.list.d/winehq.list
--2009-04-14 17:43:15--  [http://wine.budgetdedicated.com/apt/sources.list.s/intrepid.list](http://wine.budgetdedicated.com/apt/sources.list.s/intrepid.list)
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-04-14 17:43:16 ERROR 404: Not Found.

jose@Joselito:~$

---

### Post by csabo2 on 2009-07-10
well the 404 suggests that the directory or file that the list is going for is no longer valid. check with wine and make sure they havent updated that file, they may have moved stuff around :)

---

### Post by michy99 on 2009-07-10
You should just delete that file and then update.```
sudo rm /etc/apt/sources.list.d/winehq.list
sudo apt-get update
```Tell me if you get any errors.

---

### Post by SeanJStrand on 2009-07-10
Thanks for telling us all but I installed new version to day, updated and BANG!
RETURN TO STARTING POINT or RELOAD?

The error comment i got was:
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'
Thus lads in the UP-DATE DEPARTMENT PLEASE HAVE A GOOD LOOK then Please can you fix , resolve or replace.
Thanks  SEanS ( a 2 week old new-boy! )

---

### Post by Joselito84 on 2009-07-10
all sorted!!
heres what i did:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list](http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/winehq.list

and its all working again!!

thanks heaps for your help!!

---

### Post by Joselito84 on 2009-07-10
now the question is... should i update to 9.04?....

---

### Post by michy99 on 2009-07-10
> **SeanJStrand said:**
> Thanks for telling us all but I installed new version to day, updated and BANG!
RETURN TO STARTING POINT or RELOAD?

The error comment i got was:
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'
Thus lads in the UP-DATE DEPARTMENT PLEASE HAVE A GOOD LOOK then Please can you fix , resolve or replace.
Thanks  SEanS ( a 2 week old new-boy! )

It is better to start your own thread than to jump in the middle of someone elses, but try this:```
sudo rm /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-amd64_Packages
sudo apt-get update
```

---

### Post by SeanJStrand on 2009-07-10
> **michy99 said:**
> It is better to start your own thread than to jump in the middle of someone elses, but try this:```
sudo rm /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-amd64_Packages
sudo apt-get update
```


Thanks lads for all your responses, but they don't seem to work so well in that I now see:

 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 112kB in 0s (155kB/s)                 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
root@luka64:/lib# 

This I am still stuck in it!

---

### Post by SeanJStrand on 2009-07-10
> **Joselito84 said:**
> hey people, havnt logged into ubuntu for a while, i thought i would to get all the updates for it guess what? i cant!! this is what i get:

jose@Joselito:~$ sudo apt-get update
E: Type '--2009-04-14' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
jose@Joselito:~$ sudo apt-get upgrade
E: Type '--2009-04-14' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
jose@Joselito:~$ 


any ideas?


Hay: V. Sorry that I seem to have jumped into your thread.  -- a New Boy problem.
 Rgds SEanS

---

### Post by Joselito84 on 2009-07-10
hey, maybe try this one:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Jaunty (9.04):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list](http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/winehq.list


see how ya go mate!

---


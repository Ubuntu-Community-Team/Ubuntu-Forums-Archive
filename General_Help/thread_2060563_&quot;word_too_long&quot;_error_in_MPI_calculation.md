---
title: "&quot;word too long&quot; error in MPI calculation"
date: 2012-09-20
forum: General Help
---

### Post by dancoz87 on 2012-09-20
hello everybody
i use AVL Fire 2011 (CFD) on Ubuntu 12 and when I try to start a simulation  using all 4 of the CPUs (default settings) I get an error from the shell  where Fire is running. After typing my password (it is needed to  connect to myaccount@127.0.1.1) i can read:

[FONT=Lucida Console]fire_cmd@myaccount: Word too long.
Word too long.
Word too long.
MPI Application rank 0 exited before MPI_Init() with status 1
mpirun: broken pipe[/FONT]

Has anybody ever had this problem?
Thank you for your help

---

### Post by drmrgd on 2012-09-20
I might be way off here, but the very first thing that comes to mind is an architecture issue.  It is possible that you're running a 32-bit application on a 64-bit system, hence the word too long error?  Double check the architecture matches.  Also, if you can't get a 64-bit version of the software, installing the ia32-libs pacakge in the repos might get you the libraries you need.

[https://launchpad.net/ubuntu/+source/ia32-libs](https://launchpad.net/ubuntu/+source/ia32-libs)

If I'm way off in my assessment, just ignore this!

Hope that helps!

---

### Post by dancoz87 on 2012-09-20
my system is 32bit, i'm sure of that.
the simulation works if I use just one processor and I don't think that it would be possible if I installed a wrong version of the program.
however, thank you for ur help, drmrgd!

---

### Post by Bucky Ball on 2012-09-20
You have a 32bit quad-core or am I missing something?

[QUOTE=dancoz87]when I try to start a simulation  using all 4 of the CPUs[/QUOTE]

---

### Post by dancoz87 on 2012-09-20
> **Bucky Ball said:**
> You have a 32bit quad-core or am I missing something?

That's right! I have an Intel quad core processor

---

### Post by Bucky Ball on 2012-09-20
As I understand that would then be a 64bit processor.

[QUOTE=dancoz87]my system is 32bit, i'm sure of that.[/QUOTE]

---

### Post by dancoz87 on 2012-09-21
I've just come to know (by typing lscpu) that my Intel Core2 Quad CPU has two operating modes:

$ lscpu
Architecture: i686
CPU op-mode(s): 32-bit, 64-bit
...

Is the installation of 32-bit OS and software correct, then?

---

### Post by drmrgd on 2012-09-21
You can be running 32-bit Ubuntu on a 64-bit CPU.  So, even though you have a 64-bit capable processor, if you installed 32-bit Ubuntu, then your architecture (and essentially all of the system wide libraries you have) will reflect that.  So, your statement about being sure you have a 32-bit system may well be correct.  That seems to be verified by the "Architecture" bit of the lscpu command you ran.  You can also verify this by running:

```
uname -a
```

That will spit out all of the system details (in one line) related to the version of Ubuntu you have installed.  On my system, I see 'x86_64 GNU/Linux' which tells me I'm running the 64-bit version. 

That all being said, I'm not sure what the error means in that case.  The converse of my original idea crossed my mind (i.e. you have a 64-bit installation on a 32-bit system).  But, I would imagine that the program would have not even compiled if this was the case.  I tried to find and install the program myself to see if I could figure it out, but didn't have much time and was a little confused on which packages to get - plus it looked like it isn't free.

Especially if you paid for the software, you may have to contact the vendor to see if this is an error they're aware of and how they would suggest you get around it.  This software seems so specialized, you may have a tough time getting the answer here, although we're happy to help if we can figure it out!

---

### Post by dancoz87 on 2012-09-21
Thank you for ur efforts, drmrgd.
The software isn't free at all, the university paid for that but since i am running this sw on Ubuntu (for the sake of simplicity), while they recommend RedHat, i can't get any help from the vendor to solve this problem.

However, this is what i get running *uname -a*
```
Linux <myname> 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:!9:09 UTC 2012 i686 i686 i386 GNU/Linux
```

I've been searching for a log file showing me what happens with more details, but i can't find it in /var/log nor in the folder of the software.

---

### Post by Bucky Ball on 2012-09-21
64bit = use a 64bit OS and take advantage of your hardware. Yes, you can run a 32bit OS, but why would you want to? 64bit with 32bit dependencies installed and you can run 32 and  64bit apps ...

Majority of apps available in 64bit anyhow. For quad-core you might need 64bit. Try it and see if it makes any difference (from a livecd then on another partition if you want to keep fiddling with this install).

---

### Post by dancoz87 on 2012-09-21
> **Bucky Ball said:**
> 64bit = use a 64bit OS and take advantage of your hardware. Yes, you can run a 32bit OS, but why would you want to? 64bit with 32bit dependencies installed and you can run 32 and  64bit apps ...

Majority of apps available in 64bit anyhow. For quad-core you might need 64bit. Try it and see if it makes any difference (from a livecd then on another partition if you want to keep fiddling with this install).

It wasn't me who chose the OS, since the machine belongs to my university; 64 bit is better than 32, of course, but will it make any difference about this problem with MPI calculation?
I'll try to upgrade to the Ubuntu 64bit version.
Thanks!

---


---
title: "Install/update error"
date: 2010-10-13
forum: General Help
---

### Post by anonomo on 2010-10-13
Hello:)
BIG issue

can't install new software, update, autoremove, anything at all

at some point whether in terminal, synaptic or software center it will tell me
```

dpkg: parse error, in file '/var/lib/dpkg/available' near line 10152:
 newline in field name `[main]'
E: Sub-process /usr/bin/dpkg returned an error code (2)
```the dpkg/available file line 10152 seems rather harmless

> This             package             contains             various             fonts             from             dustismo.com             licensed             under             
                              
            the             GPL.             possibly a more suspicious looking thing about this file is that all the packages are written
> Architecture: AMD64(i forget the exact processor on this machine but its Intel)
could that be causing the problem?
(but i've been succesfully updating and installing b4 now)

Running
Ubuntu Studio lynx / Win7

Software? Hardware? Too much coffee?
seriously i have no clues any leads much appreciated,
got some urgent video work to do:P

---

### Post by tommcd on 2010-10-14
> **anonomo said:**
> 
can't install new software, update, autoremove, anything at all
dpkg: parse error, in file '/var/lib/dpkg/available' near line 10152:
Try renaming the */var/lib/dpkg/available* file to */var/lib/dpkg/available.bak* and then run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
 and see if that fixes it.
> **anonomo said:**
> 
possibly a more suspicious looking thing about this file is that all the packages are written
Architecture: AMD64 
What version of Ubuntu (32bit or 64bit) did did you install? If you don't know you can find out by running:
```
uname -a
```
It should list either i686 (32bit) or x86_64 (64bit).
> **anonomo said:**
> 
(i forget the exact processor on this machine but its Intel)
could that be causing the problem?
To find out if you have a 64bit CPU run:
```
cat /proc/cpuinfo
```
If you have a 64bit CPU you will see something like this in the **flags** line:
```
flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt **lm** 3dnowext 3dnow up rep_good extd_apicid pni lahf_lm

```
The key thing to look for in the flags line is **lm**. That indicates a 64bit CPU. It may also show something like this, which is more obvious:
```
model name: AMD Athlon(tm) 64 Processor 3200+
```

Also, somewhere in Windows7 it probably lists whether it is 32bit or 64bit, as well as info about you CPU.

---

### Post by anonomo on 2010-10-14
hey tommcd thanks heaps for helping

so i rename the file
*/var/lib/dpkg/available* file to */var/lib/dpkg/available.bak*  

but then trying to dist-upgrade we get the problem that it looks for the file and it isnt  there
```

Preconfiguring packages ...
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

sorry ive no idea how to tell it where to look:(


my processor is Intel Core i5 M 520 
yep its a 64 bit processor
(was a stab in the dark that perhaps AMD architecture was a problem as with mac os x)

os is Ubuntu Studio 10.04
or uname -a will tell you
> Linux ubuntu 2.6.32-24-preempt #42-Ubuntu SMP PREEMPT Fri Aug 20 16:53:41 UTC 2010 x86_64 GNU/Linux

---

### Post by tommcd on 2010-10-15
> **anonomo said:**
> 
so i rename the file
*/var/lib/dpkg/available* file to */var/lib/dpkg/available.bak*  
but then trying to dist-upgrade we get the problem that it looks for the file and it isnt  there

OK, Then just rename */var/lib/dpkg/available.bak*, to */var/lib/dpkg/available*, as it was originally.
Then run *sudo apt-get update* again.
I think I may have found an answer. See this:
[https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)
So then try running:
```
sudo dpkg --clear-avail && sudo apt-get update
```
as it says there. Then see if you can install updates and other programs. Let me know if this works.

Your CPU is 64bit, and your output from *uname -a* indicates you are running 64bit Ubuntu. So that is fine. You can use 32bit or 64bit distros with a 64bit CPU. So there is no problem there.

---

### Post by anonomo on 2010-10-15
:popcorn:
WOO

yep it works 

actually i just discovered the same answer on another thread
just:

sudo dpkg --clear-avail

in other words just delete everything in the dpkg/available file

and dist-upgrade re-writes it

nice!


wow thanks heaps for helping - if you werent there i would have thought i was just going crazy by myself:P

---

### Post by tommcd on 2010-10-15
Well, I didn't expect it would be fixed so quickly!
Glad I could be of some help. Have fun with Ubuntu!

---

### Post by tommcd on 2010-10-16
> **sudha100 said:**
>  so i rename the file
*/var/lib/dpkg/available* file to */var/lib/dpkg/available.bak*  

but then trying to dist-upgrade we get the problem that it looks for the file and it isnt  there ...

If you have not seen it already, see my follow up in post #4 in this thread.
Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by tommcd on 2010-10-16
> **Sam1Parker said:**
> 
  M USING UBUNTU OP 
   BUT HOW CAN UPDATE MY OP PLZ TELL ME

No need for all caps here. 
And can you *please* manage to write in complete, and (hopefully!!) coherent sentences please!

Can you possibly provide more info???
What version of Ubuntu did you install???
Is this a Wubi install?? Or did you do a real linux install to a dedicated partition on your hard drive???
Are you able to successfully boot to the Ubuntu desktop???
Can you open a terminal (applications > accessories > terminal) and run these commands:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
And post the output here.

Here is a great site for getting started with Ubuntu:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
And get the *free!!!* Ubuntu manual here:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
And welcome to the Ubuntu forums!

---


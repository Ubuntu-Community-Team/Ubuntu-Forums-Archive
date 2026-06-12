---
title: "Does my system monitor look right?"
date: 2010-12-12
forum: General Help
---

### Post by David_UK on 2010-12-12
I have a 4 week old fresh install of Ubuntu 10.04.  Pentium 4, 1G RAM, plenty of space on HDD, 2G swap.

After boot up, system monitor shows memory usage steady at 600MB.  This is with nothing other than the OS running.  Under 'processes' tab, about 10 entries use 1-5MB, but nothing major.

It seems a very high memory usage - any thoughts?

Thanks

---

### Post by Spyderkid on 2010-12-12
go to system> preferences >start-up applications

and disable anything un-needed for example bluetooth, remote desktop things like that. it might help

go to processes at system monitor and scroll down and have a look for some applications/processes that are running and report anything strange. only 1 or two should be running at 2-5% cpu

---

### Post by QLee on 2010-12-12
> **David_UK said:**
> I have a 4 week old fresh install of Ubuntu 10.04.  Pentium 4, 1G RAM, plenty of space on HDD, 2G swap.

After boot up, system monitor shows memory usage steady at 600MB.  This is with nothing other than the OS running.  Under 'processes' tab, about 10 entries use 1-5MB, but nothing major.

It seems a very high memory usage - any thoughts?

Thanks

Since you have been a user since 2006, you should already know this. However, I understand my unrealistic expectations of "shoulds" for other people. I'm pretty hard on myself with "shoulds".

[Edit] I agree with Spyderkid that you could not start any applications you don't need.

Enter the command, free -m, in a terminal window. That will show you memory usage in MB (-m). You will see a figure for cached memory, that is used to allow your system to respond faster in case it needs something it has already read from disk because RAM is faster than disk reading. That is a good way to use memory, it will be used for something else when and if needed. I think the cache includes write cached data too, but I'm not absolutely sure of that.

[Edit] The commands, ps aux, and, top, might also be helpful. Sometimes firefox uses a lot of memory.

Sorry, I initially mis-read, now I see you have nothing else running.

You can probably find out lots more about memory usage with a search engine, once you have determined what is using it.

I apologise for so many edits, I'm presently trying to do too many things at once.

---

### Post by bkratz on 2010-12-12
> **David_UK said:**
> I have a 4 week old fresh install of Ubuntu 10.04.  Pentium 4, 1G RAM, plenty of space on HDD, 2G swap.

After boot up, system monitor shows memory usage steady at 600MB.  This is with nothing other than the OS running.  Under 'processes' tab, about 10 entries use 1-5MB, but nothing major.

It seems a very high memory usage - any thoughts?

Thanks

system monitor is really hard to understand what it is saying ( at least for me) there are threads around that describe it's use, but it you install htop it is more understandable.

---

### Post by David_UK on 2010-12-14
> **Spyderkid said:**
> disable anything un-needed for example bluetooth, remote desktop things like that.

go to processes at system monitor and scroll down and have a look for some applications/processes that are running and report anything strange. only 1 or two should be running at 2-5% cpu
Ok, the attached image shows my system monitor ordered by memory usage.

> **QLee said:**
> Since you have been a user since 2006, you should already know this. However, I understand my unrealistic expectations of "shoulds" for other people. I'm pretty hard on myself with "shoulds".
QLee, I don't really follow what you mean by this.  I've struggled on and off for several distros trying to make sense of out of date tutorials and wildly differing advice.  I think I'm pretty typical of a casual user wanting to join the Ubuntu world but constantly struggling to do so.  If I "should" have got to grips with it by now, then I apologise for being so thick.


> **QLee said:**
> Enter the command, free -m, in a terminal window.
Ok, here it is.  Hopefully it means something useful to you.  It's with firefox running but nothing else.

             total       used       free     shared    buffers     cached
Mem:          1002        959         42          0        142        154
-/+ buffers/cache:        662        340
Swap:         2047         40       2006

---

### Post by David_UK on 2010-12-14
> **bkratz said:**
> install htop it is more understandable.

Ok, thanks now we're getting somewhere.  (see attached screeshot). There are a whole load of entries relating to AVG antivirus (I followed a walkthrough to install this as I use Ubuntu for my emails, but the process did not go as described and it appeared not to install at all).

---

### Post by David_UK on 2010-12-16
Thanks bkratz, you helped me solve this.
Removing unwanted startup items decreased the memory usage by about 20M, but once I saw in htop how much memory AVG was using, I uninstalled it from Synaptic and after a reboot memory usage settled at about 150M - much more what I would expect from this desktop install of ubuntu.

---

### Post by migs73 on 2010-12-16
See here; 

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

This also explains why people can get in a panic about RAM usage.

EIT: Not that you were in a panic!!! i am just dramatising the issue (see the webpage!!)

---


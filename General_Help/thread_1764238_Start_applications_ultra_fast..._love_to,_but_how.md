---
title: "Start applications ultra fast... love to, but how?"
date: 2011-05-21
forum: General Help
---

### Post by the8thstar on 2011-05-21
Hello,

There are a few applications that we always use at home on the computer: Firefox, Skype, MS Office (through Wine 1.3).

Usually, the first time we start any of these, the computer will 'think' for about 3 to 20 seconds before loading the application we want. If we close and reload them, the 'thinking' time is much shorter.

So, I am looking for a way to have these applications preloaded in memory when Ubuntu starts to save the 'thinking' time and have firefox, skype or MS Office load almost instantly from RAM.

What should I do to achieve these results? I heard of RAM disk, but I don't know how to load the applications to the RAM disk everytime the computer starts.

I also wonder if I should add the apps to the Startup session list. Would that load the apps into memory for faster access?

Thanks for your help in finding the best tweak!

---

### Post by oldos2er on 2011-05-21
You can certainly add apps to 'Startup', at the expense of having a slightly longer login time while they load.

Look at the package 'preload,' here is its description:

 Description: adaptive readahead daemon
 preload monitors applications that users run, and by analyzing this data,
 predicts what applications users might run, and fetches those binaries and
 their dependencies into memory for faster startup times. 
 
 Note that installing preload will not make your system boot faster and that
 preload is a daemon that runs with root priviledges.
Homepage: [http://sourceforge.net/projects/preload](http://sourceforge.net/projects/preload)

---

### Post by satanselbow on 2011-05-21
hmmmm... I wonder where M$ got the idea of "prefetching" from then... :popcorn:

---

### Post by the8thstar on 2011-05-21
> **oldos2er said:**
> You can certainly add apps to 'Startup', at the expense of having a slightly longer login time while they load.

Look at the package 'preload,' here is its description:

 Description: adaptive readahead daemon
 preload monitors applications that users run, and by analyzing this data,
 predicts what applications users might run, and fetches those binaries and
 their dependencies into memory for faster startup times. 
 
 Note that installing preload will not make your system boot faster and that
 preload is a daemon that runs with root priviledges.
Homepage: [http://sourceforge.net/projects/preload](http://sourceforge.net/projects/preload)

Thanks, I will try the startup way; using preload never made any difference, it just loaded the OS more slowly...

---

### Post by meloade on 2011-05-21
Use an SSD. That's what I do, It's pretty much like a hard drive made of ram, except it's 60GB.

---

### Post by the8thstar on 2011-05-21
> **meloade said:**
> Use an SSD. That's what I do, It's pretty much like a hard drive made of ram, except it's 60GB.

I know what an SSD is. And it's a significant expense too! Way too much for me at the moment anyway, so I'd like to try and use what I have :-)

---

### Post by the8thstar on 2011-05-22
I wonder if there is a way to start the applications in a minimized mode when you put them in startup applications?

---

### Post by blueridgedog on 2011-05-22
> **meloade said:**
> Use an SSD. That's what I do, It's pretty much like a hard drive made of ram, except it's 60GB.

If his system is taking 3 to 20 seconds to load some basic applications, it bet his hardware is not in keeping with what a user would have if they were in the market for and SSD.

---

### Post by blueridgedog on 2011-05-22
> **the8thstar said:**
> I wonder if there is a way to start the applications in a minimized mode when you put them in startup applications?

Perhaps this?

[http://ubuntuforums.org/showthread.php?t=687273](http://ubuntuforums.org/showthread.php?t=687273)

---

### Post by lmn. on 2011-05-22
there may be some linux overclocking tools around if you are desperate to squeeze out some extra power.

Puppy Linux could be an option to boot into when you need to get something done fast.

---

### Post by Larkspur on 2011-05-22
> **the8thstar said:**
> I wonder if there is a way to start the applications in a minimized mode when you put them in startup applications?

Some do allow this as an option to their launch command, some don't.  Check the man page for the programs you want to do this for, to see if they support this.  Another way around this - the one I use for Evolution - is to have Compiz open them on a workspace I don't use until I need them. To do this, go to ccsm>Place Windows>Fixed Window Placement>Windows With A Fixed Viewport and add your program.

---


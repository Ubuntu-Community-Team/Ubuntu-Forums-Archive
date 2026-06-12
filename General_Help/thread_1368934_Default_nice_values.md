---
title: "Default nice values"
date: 2009-12-31
forum: General Help
---

### Post by MrZehl on 2009-12-31
I use LottaNZB to download from usenet. LottaNZB is a GUI for HellaNZB. HellaNZB downloads all files and calls par2 and unrar and leaves just the files you want. Easy. But.. when I download a big file, like a DVD image, and the download is finished the processing begins. And this will sometimes sloooooooow down my computer. Sometimes it's frozen.

When it's frozen I'll have to wait. When it's not frozen but just slow I can change the priority of the processen and give them a higher nice value, which is in fact a lower priority.

Now my question: can I somewhere set a default value for processen that must always be low priority, like 7zip, unrar, par2, hellanzb?
So I don't mean starting unrar with 'nice unrar 10' , because I want unrar low priority whenever it's started by any program or by myself. 
So can I set a default priority for a certain program?

Or another option: which processes I have to give a lower nice value, thus higher priority, to prevent my system to freeze.
Which processes are responsible for screenupdating and mouse interaction?

---

### Post by xifer on 2009-12-31
> **MrZehl said:**
> can I somewhere set a default value for processen that must always be low priority, like 7zip, unrar, par2, hellanzb?


locate the executable, rename it for example  nice_unrar

```

which unrar
mv /usr/bin/unrar /usr/bin/nice_unrar

```create a shell script for example /usr/bin/unrar as


```

nice -20 /usr/bin/nice_unrar

```

---

### Post by rnerwein on 2009-12-31
high - i thing your problem has nothing to do with process priority (i'am sure). whats happen when your downloaded files (i bet this are big files) are proccesed the system will start havey caching and you will run into a shortness of memory. the system monitor which comes with the system don't show you the cache and buffercache. use vmstat -n 2 see the usage of them (vmstat has to run in a shell window).
there are a couple of tuning parameters available to manupulate the behavior of swaping and caching. see /proc/sys/vm (try: swapiness=20, dirty_ratio=15,dirty_background_ratio = 10) - see man 5 proc. and remember - to play this parameters can also slow down your system - or make it faster. ciao richi

---

### Post by MrZehl on 2010-01-01
> **xifer said:**
> locate the executable, rename it for example  nice_unrar

```

which unrar
mv /usr/bin/unrar /usr/bin/nice_unrar

```create a shell script for example /usr/bin/unrar as


```

nice -20 /usr/bin/nice_unrar

```
Nice idea, but it will not work after update. So I created /usr/local/bin/unrar

```

#! /bin/bash
/usr/bin/nice -20 /usr/bin/`basename $0` "$@"

```

It includes the arguments and reads the filename so the same file I could save as 7z and par2. For hellanzb I had to changed the full paths in the hellanzb.conf. When I start par from nautilus it goes automagicly right. It does the trick, but didn't solve the problem.
Strange, but I really needed to use the full path to nice.

> 
high - i thing your problem has nothing to do with process priority (i'am sure). whats happen when your downloaded files (i bet this are big files) are proccesed the system will start havey caching and you will run into a shortness of memory. the system monitor which comes with the system don't show you the cache and buffercache. use vmstat -n 2 see the usage of them (vmstat has to run in a shell window).
there are a couple of tuning parameters available to manupulate the behavior of swaping and caching. see /proc/sys/vm (try: swapiness=20, dirty_ratio=15,dirty_background_ratio = 10) - see man 5 proc. and remember - to play this parameters can also slow down your system - or make it faster. ciao richi

Well I try this. Last time my system was a bit slow, but not yet extremely I got this values from vmstat -n 

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1 11  51488  62004  30136 999040    0    3   578   811  444  495  6  2 86  7

I added 
vm.swappiness=20
vm.dirty_ratio=15
vm.dirty_background_ratio = 10

to /etc/sysctl.conf

The default values were swappiness=60, dirty_ratio=20 ,dirty_background_ratio = 10. So the dirty_background_ratio hasn't changed for now. I'll reboot and will post new result when the next big download is ready.

---

### Post by MrZehl on 2010-01-01
Wow!

With the next heavy processing job. The output of vmstat was

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1  7   1132  16496  25020 1022348    0    0  1814   224  244  299  4  1 88  7

Comparable with before but my system still is responsive. Of course I have to use these settings for a while to be sure but  it seems that adjusting that new values worked very fine. Thanks.

---


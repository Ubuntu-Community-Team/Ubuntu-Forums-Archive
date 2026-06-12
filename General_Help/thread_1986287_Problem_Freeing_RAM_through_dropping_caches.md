---
title: "Problem Freeing RAM through dropping caches"
date: 2012-05-24
forum: General Help
---

### Post by lemonoid on 2012-05-24
I really need to free up some RAM and although I've been using Ubuntu a while, other than closing programs, the only way I've found to free RAM is by dropping caches. I will list the command below. Two different sources have recommended the exact same method, but I keep getting told permission denied. I logged into root and I'm still having problems. If anyone knows another way to free up RAM, as in what significant memory-consuming programs I can kill and an easy way to do it. But here is the command

I have to pass a number (1-3) using echo depending on which caches I want to drop, but I will just use an example.

echo 1 > proc/sys/vm/drop_caches


btw I need two GB RAM, and although I have 4GB available memory (actually only 3.8 ) right now my free -m shows me 889MB.  And the thing is I will need to free the RAM at a certain time. I'm making a custom ROM build for Android, and at the very end of the build when the package is being signed, it needs 2GB RAM to sign it (that's the easiest way).
Thanks!:confused:

---

### Post by pbrane on 2012-05-24
you should be able to
```

sudo su
// enter your password, then enter
sync; echo 1 > proc/sys/vm/drop_caches

```

And you may want to echo 3 to drop everything from cache instead of just pagecache. I assume you have tried building the ROM and it fails during the signing process complaining about memory?

EDIT: the above commands don't complain about permissions but they don't actually seem to do anything either.

for me 
```

sudo sync;
sudo sysctl -w vm.drop_caches=3

```
worked.

---

### Post by matt_symes on 2012-05-24
Hi

It should drop the caches when you need the memory.

You can check the actual amount of memory used with the free command.

Here is mine.

```
matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-3.7
 % free -m
             total       used       free     shared    buffers     cached
Mem:          2758       2595        162          0         60        416
-/+ buffers/cache:       **2119**        638
Swap:        10001       1771       8230
matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-3.7
 % 

```

The actual result you are interested in is highlighted in bold above.

To answer your question though

```
echo 1 | sudo tee proc/sys/vm/drop_caches
```

or 

```
sudo bash -c "echo 1 > proc/sys/vm/drop_caches"
```

or 

```
sudo -i
```

and run the command or....

Kind regards

---

### Post by ajgreeny on 2012-05-24
Are you sure you are interpreting the **free -m** output properly, and that you understand the manner in which Linux manages ram.

Sorry if you know this already, but my output for free -m is
```
total       used       free     shared    buffers     cached
Mem:          2012        876       1136          0         98        406
[COLOR=Red]-/+ buffers/cache:        370       1642[/COLOR]
Swap:         2047          0       2047
```
The important figures are those in red, which show that there is actually 1642 M of my 2G of ram that is available and 370 which is being used and not available.

Linux does not empty ram until it is needed again, but that does not mean that all of the used ram that is full of data is unavailable.

---

### Post by matt_symes on 2012-05-24
.

---

### Post by lemonoid on 2012-05-24
thank you all for your replies. this is what I ended up doing to get it to work.

sudo -v
password

sudo echo 3 /proc/sys/vm/drop_caches


I had just originally tried sudo in front of echo, and then tried logging into su and then trying echo without sudo in front of it, I figured out I have to do both, but I will try all of your methods. For some reason my signing process still was complaining about free RAM even though I cleared it up to 3.2GB, so I am trying a new method, editing the common.py file that sets the signing process to 2048m, I am instead changing it to 1024m. and if that doesn't work I'm changing to 512m. I believe I will save all of your methods in a file, because although I've been using Linux for over a year, I still have a lot to learn so I am building a resource with a bunch of 'tutorial' style files.

and to ajgreeny, in reference to looking at the wrong line instead of -/+ buffers I was originally looking at the wrong line but I figured it out right after I posted this, but I looked at the right line and I was short before I dropped those caches. I also have another question. Does setting the niceness of a process affect the RAM? I know what it does is setting priority, but if a service has a low priority (high niceness), does that mean that it will get killed easier and free my RAM? if so I was wondering if there is any way I could set the niceness of some services I don't need while compiling my ROM to drop the service, and instead bump the priority of my make to a higher priority? i hope that makes sense...

---


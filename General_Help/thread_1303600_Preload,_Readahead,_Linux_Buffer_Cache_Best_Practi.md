---
title: "Preload, Readahead, Linux Buffer Cache: Best Practices?"
date: 2009-10-28
forum: General Help
---

### Post by ricojonah on 2009-10-28
**I realized my initial post was a little too long-winded, so here's what I was wondering in a nutshell:**

For a desktop user, is there any difference between using preload vs readahead (or vice-versa) for better performance? 

Is it a waste of time to install preload along with readahead on the same system (because of the redundancy)?

Is there a way to monitor how the cache for either of these is being used?

Anyone's suggestions or experience is greatly appreciated. Thanks!


*Here's the long-winded version of the same questions I asked:*

I recently discovered that Ubuntu installs with the readahead daemon by default, which appears to improve desktop performance by reducing the loading time of boot files and user applications. A separate available utiliy, called preload, essentially does the same thing through a somewhat different method. The intended result is that a desktop system gathers commonly used content stored on the hard drive (applications like Firefox, and frequently accessed files) and stores it all in unused memory, allowing your system to load these things much faster.

The benefits that readahead and/or preload provide are absolutely great--the performance improvement is very noticable for most of my typical desktop usage Firefox, Miro, OpenOffice, and Virtualbox VMs all fully load in 1/2 the time they used to). But I was wondering if anyone has an answer to any of my questions (or if anyone else has wondered the same thing):

1) How might I monitor the amount of (otherwise) free memory that readahead and preload are using to cache everything? Anything from either the terminal or the GUI would definitely be appreciated! 

2) Somewhat related to the fist Q: I've noticed that Gnome-panel's System Monitor applet has a memory usage monitor that also displays the size of *some type of* memory cache. Is this the memory cache of the Linux kernel's memory buffer, readahead, preload, or something else?

3) Being in the last few days of its Beta status, I've noticed that Ubuntu 9.10 Karmic uses sreadahead instead of readahead (good move for netbook users!), and that, often after installing applications from the terminal, I see this particular line during the output:
```
sreadahead will be reprofiled on next reboot

```
Does this mean that manually re-profiling readahead/sreadahead (to improve boot times) is no longer necessary, or have I just not been paying much attention to my lovable little terminal?

4) This one might sound a little silly, but what's *really* the difference between (s)readahead and preload nowadays? From what I've understood, preload was more adaptive (smarter about deciding what to cache) than readahead, but with all of the recent changes to readahead, I'm not so sure.

5) If preload and readahead, serve similar purposes (they all store disk contents in RAM for faster access and reduced disk I/O), doesn't installing & utilize more than one of these result in a lot of wasteful redundancy? By redundancy, here's what I mean: If preload is storing a memory cache while readahead is storing its own separate one at the same time, aren't both deamons potentially caching the same content? That would mean they are wasting free memory on caching the same thing twice, and reducing the amount of further-available memory for caching more information. 

 


I know that's a lot of questions for one thread, but anyone's experiences or wisdom would be greatly appreciated!

---

### Post by Diskdoc on 2009-11-04
This is interesting for me as well. I know there is a bug concerning sreadahead but I don't really understand it:

[https://bugs.launchpad.net/ubuntu/karmic/+source/sreadahead/+bug/432089](https://bugs.launchpad.net/ubuntu/karmic/+source/sreadahead/+bug/432089)

---

### Post by yaztromo on 2009-11-05
I was under the impression that sreadahead was just to speed up karmic boot times and not for preloading desktop apps. Is this right?

> 
sreadahead is a daemon that reads data sequential by use from disk. It does
this by retrieving the read order (in timestamp format) from an actual boot
sequence and storing a list of data that was read during that boot sequence in a flat database. 
 
On the next boot this file can be used to load all the data described in the database into memory and in order of use. 
 
sreadahead requires a kernel patch included in the Ubuntu kernel.


I am interested myself in how karmic seems to give better desktop app loading times than jaunty after being loaded once. Initial load times for apps still seem slow but subsequent loads definitely beat jaunty.

Regarding preload: I installed it on a jaunty desktop and it never seemed to make any difference.

---

### Post by lswb on 2009-11-05
IMHO readahead is better for decreasing boot time, as the same files must always be read, and there is no need for the adaptive and predictive features of preload. preload I believe is better suited to aid in quicker loading of desktop applications once boot is completed.

I experimented with preload in my hardy installation. I can't quantify it but I believe it somewhat speeds up loading of the desktop and definitely decreases initial load time of large frequently used apps like firefox. I didn't consider it enough of a benefit to install it when I started running 9.04 though.

Both readahead and preload may have different results depending on your system, e.g. which services run, commonly used applications, amount of memory available for caching, etc. The only way to be sure is to time things on your particular system.

Currently I usually boot into 9.04. I use the profile boot option to rebuild the readahead list when I think things have changed enough to warrant, and have a slightly modified init script that uses separate readahead lists depending on which kernel is being used. (I am experimenting with different kernels and intel drivers so this benefits me, but most users probably wouldn't need it) 

I also do readahead on the gnome desktop. I found that this almost cut in half desktop startup time for me after logging in.
[http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651) explains this. Note the comments about sreadahead used in 9.10 vs readahead of earlier versions. I have no experience with sreadahead.

---


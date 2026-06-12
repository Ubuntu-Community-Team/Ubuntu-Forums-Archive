---
title: "Ubuntu Software Center Closed Unexpectedly"
date: 2011-03-24
forum: General Help
---

### Post by joehoward on 2011-03-24
Hi Everyone,
Whenever I try to run the Ubuntu Software Center, a message comes up saying "Sorry, Ubuntu Software Center closed unexpectedly".  I also tried using the Synaptic Package Manager program instead, but it gives an error message saying:
```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

```
When I run software-center from terminal, I get the same messages with more stuff listed afterward, most likely from the above error.

Since my filesystem gets corrupted often, I ran fsck -C on my home partition.  It found and fixed many problems, including a number of corrupted places.  It did not fix the Software Center problem, though.

Extra Info:
I am running Ubuntu 10.10 on a school-owned netbook off a persistent-installed 8gb flash drive.  I used a Ubuntu 9.10 boot disk to check the home partition on the flash drive.

Thanks

---

### Post by oldos2er on 2011-03-24
Try this solution given in a similar thread: [http://ubuntuforums.org/showthread.php?t=1651765](http://ubuntuforums.org/showthread.php?t=1651765)

---

### Post by joehoward on 2011-03-25
oldos2er,

I tried the instructions at the other thread
> Open up /var/lib/apt/lists from your root partition and delete the file named us.archive.ubuntu.com_ubuntu_dists_maverick_main_b inary-i386_Packages and try apt-get update again.

I don't seem to have a "lists" directory at that location.
:confused:

---

### Post by oldos2er on 2011-03-25
> **joehoward said:**
> I don't seem to have a "lists" directory at that location.

Sure? What's the output of **ls /var/lib/apt** ?

---

### Post by joehoward on 2011-03-25
Thanks for helping
The ls outputs:
```
cdroms.list cdroms.list~ extended_states [COLOR="RoyalBlue"]keyrings lists mirrors periodic[/COLOR]
```

(The text is in the color it appeared in the terminal)

---

### Post by oldos2er on 2011-03-25
> **joehoward said:**
> Thanks for helping
The ls outputs:
```
cdroms.list cdroms.list~ extended_states [COLOR="RoyalBlue"]keyrings [COLOR="Red"]lists[/COLOR] mirrors periodic[/COLOR]
```


The 'lists' directory is in red.

---

### Post by joehoward on 2011-03-25
Wow.  I must have been in the wrong directory at first. #-o  Sorry.

Now that I figured out how to get where I'm supposed to be, the solution at the other thread worked.  Thanks for your help and patience.

---

### Post by oldos2er on 2011-03-26
You're welcome. Glad you got it sorted out.

---

### Post by bogdarnet on 2013-02-09
Getting this problem in PRECISE... should we delete the precise main binary i386 lists file?

---

### Post by wildmanne39 on 2013-02-10
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


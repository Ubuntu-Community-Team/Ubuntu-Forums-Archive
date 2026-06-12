---
title: "folding at home getting Segmentation fault under 10.10"
date: 2010-10-12
forum: General Help
---

### Post by markp1989 on 2010-10-12
just done a fresh install of 10.10 on my desktop, and im having trouble folding. 

i installed using [http://folding.stanford.edu/English/LinSMPGuide](http://folding.stanford.edu/English/LinSMPGuide) like i normaly do , but this time i get a seg fault 

```

mark@mark-desktop:~/folding$ ./fah6 -smp -verbosity 9

Note: Please read the license agreement (fah6 -license). Further 
use of this software requires that you have read and accepted this agreement.

8 cores detected


--- Opening Log file [October 12 22:44:22 UTC] 


# Linux SMP Console Edition ###################################################
###############################################################################

                       Folding@Home Client Version 6.29

                          http://folding.stanford.edu

###############################################################################
###############################################################################

Launch directory: /home/mark/folding
Executable: ./fah6
Arguments: -smp -verbosity 9 

[22:44:22] - Ask before connecting: No
[22:44:22] - User name: markp1989 (Team 32)
[22:44:22] - User ID not found locally
[22:44:22] + Requesting User ID from server
[22:44:22] - Getting ID from AS: 
[22:44:22] Connecting to http://assign.stanford.edu:8080/
Segmentation fault

any help?

thanks, mark 
mark@mark-desktop:~/folding$ 

```

---

### Post by bford16 on 2010-10-12
Here, too.

Dual-core amd 2.6Ghz with kernel 2.6.35-22-generic

Using command ./fah6 -configonly

Complete error is:
../sysdeps/unix/sysv/linux/getpagesize.c:32: __getpagesize: Assertion `_rtld_global_ro._dl_pagesize != 0' failed.
Segmentation fault.

---

### Post by windracer01 on 2010-10-13
+1. Found this reported here as well:

[http://en.fah-addict.net/news/news-0-299+folding-home-and-ubuntu-10-10-a-rocky-start.php](http://en.fah-addict.net/news/news-0-299+folding-home-and-ubuntu-10-10-a-rocky-start.php)

---

### Post by windracer01 on 2010-11-09
I installed and configured nscd (details in the updated post I linked to above) and that worked for me.

---

### Post by markp1989 on 2010-11-12
> **windracer01 said:**
> +1. Found this reported here as well:

[http://en.fah-addict.net/news/news-0-299+folding-home-and-ubuntu-10-10-a-rocky-start.php](http://en.fah-addict.net/news/news-0-299+folding-home-and-ubuntu-10-10-a-rocky-start.php)

that worked for me aswell, Thanks :)

---

### Post by windracer01 on 2010-11-23
Well, it's not a perfect fix. I found my folding service had stopped a few days ago. I found this in FAHlog.txt:

```
[05:34:21] Completed 210000 out of 250000 steps  (84%)
[05:39:22] Timered checkpoint triggered.
[05:44:23] Timered checkpoint triggered.
[05:48:37] CoreStatus = 8B (139)
[05:48:37] Client-core communications error: ERROR 0x8b
[05:48:37] This is a sign of more serious problems, shutting down.

```

I restarted the service and it seemed to pick up where it left off, but you might want to keep an eye on your own folding progress ...

---


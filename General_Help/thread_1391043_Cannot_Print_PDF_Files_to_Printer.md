---
title: "Cannot Print PDF Files to Printer"
date: 2010-01-26
forum: General Help
---

### Post by gruntlips_ on 2010-01-26
I cannot print pdf files. I click print in evince everything seems ok but nothing comes out on the printer. I receive no error. I have a HP printer (LasterJet 3005n) attached over a network. I am running 9.10 on a Dell Optiplex. I did not have this problem in 9.04. I had this problem immediately after I did a fresh install of 9.10. I can print open office documents without any problem, just not pdfs. I have the same problem with my serval laptop (also running 9.10). Any help would be appreciated.

Thanks,

- gl

---

### Post by gruntlips_ on 2010-01-26
Well, I guess this problem is the same as in the post below. There does not appear to be a good solution. Not being able to print a pdf to an HP printer is a pretty ridiculous shortcoming for ubuntu's evince in the workplace.

[http://ubuntuforums.org/showthread.php?t=1386107&highlight=Print+PDF+Files+Printer](http://ubuntuforums.org/showthread.php?t=1386107&highlight=Print+PDF+Files+Printer)

---

### Post by Chronon on 2010-01-26
> **gruntlips_ said:**
> Well, I guess this problem is the same as in the post below. There does not appear to be a good solution. Not being able to print a pdf to an HP printer is a pretty ridiculous shortcoming for ubuntu's evince in the workplace.

[http://ubuntuforums.org/showthread.php?t=1386107&highlight=Print+PDF+Files+Printer](http://ubuntuforums.org/showthread.php?t=1386107&highlight=Print+PDF+Files+Printer)

Have you made sure it is reported on launchpad?  This is the best thing users can do to improve Ubuntu: Provide feedback to the devs.  You can sometimes find and help test preliminary fixes for such bugs there too.

---

### Post by gruntlips_ on 2010-01-26
Yes, it appears that this might be the post on launchpad and the issue is with libcairo not evince. However, I cannot find the libcairo fix/update on this post and I have no idea how to install it.

[https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/227186](https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/227186)

---

### Post by Chronon on 2010-01-26
That one looks a bit old.  This one looks a bit more promising, I think.

[https://bugs.launchpad.net/ubuntu/karmic/+source/cairo/+bug/419143](https://bugs.launchpad.net/ubuntu/karmic/+source/cairo/+bug/419143)

There's a bit of back and forth between that one and #443026

It seems this bug doesn't affect Okular, so you could use that if the other workarounds posted in those tasks don't work for you.

---

### Post by gruntlips_ on 2010-01-27
Thanks Chronon!

So I have added the ppa to my sources.list file and imported the signed key. How do I actually find and use the fixed cairo packages from this PPA? I typed sudo apt-get update and nothing new showed up to install. I searched for the package "cairo" in synaptic and it did not appear. I know this question is idiotic, but please bear with my idiocy.

Thanks,

- gl

---

### Post by Chronon on 2010-01-27
Reading the most recent comments it appears that the version from that PPA was pushed out to the main repositories (I believe this is the meaning of "Fix Released".  It appears that this updated version (I think it's actually called libcairo2) does not fix all such problems for people, but does fix a subset of printing problems.

Till Kamppeter says this in comment #109
> 
It seems that the fix in Cairo solves the "0a" problem of the original poster (embedded fonts), but there are also other "0a" problems which are not covered (other embedded binary data, like pictures or so).

So we can approve the Cairo fix to at least help the users who cannot print files with embedded fonts, but we need to get Cairo completely fixed to cover all "0a" cases.


Since the updated Cairo version doesn't fix the problem for you, it might be worth trying Mark Eddington's workaround in comment #89 (print to a new PDF using cups-pdf, then print that with evince).  If this is too troublesome you could try okular instead of evince.

---

### Post by gruntlips_ on 2010-01-27
Thanks again Chronon. I am sifting through many pdfs daily so I will use okular (which appears to work fine). I wondered about that too - when a fix became part of the main repository. Hopefully, the other OA problems in Cairo will be fixed at some point.

- gl

---

### Post by Chronon on 2010-01-28
Cheers.  :)

I'm sure a fix will be released when they isolate the cause of the remaining problems.

---


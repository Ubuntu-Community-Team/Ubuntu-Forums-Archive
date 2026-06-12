---
title: "Missing GRUB Files in Natty Narwhal (11.04)"
date: 2011-01-14
forum: General Help
---

### Post by jcracken on 2011-01-14
I am a noob to Ubuntu, so I might just be doing something wrong. A couple months ago, I created a dual boot between Windows 7 and Ubuntu 10.04 using wubi. I then upgraded to 10.10. What would usually happen is I would start up my laptop and it'll go to the Windows boot manager, letting me choose between Windows 7 and Ubuntu. If I would choose Ubuntu, it would go to a GRUB boot manager. It would let me choose between several different ways to boot Ubuntu, mainly that there were different options that were all the same except they had different numbers in the name, i.e. Ubuntu, whatever, 14.33.22.19.25 or something like that. A couple weeks ago, I updated to 11.04. At first it worked good, but then a couple days later I updated a bunch of packages. It tried to CAT a GRUB file and failed. It gave me an error code, but I ignored it. Yesterday, I updated again, but since last time failed, it told me to do a partial upgrade. This I did, and it was successful. But now, everytime I go to GRUB and try to select any of the options, it tells me "Error: File not Found" and I cannot boot into Ubuntu. There are recovery versions for each choice, and using these I can boot into Ubuntu in low graphics mode and I can also get to a command line prompt. What can I do to fix this?

---

### Post by Habeouscorpus on 2011-01-14
Have you tried reinstalling grub or running "sudo grub-update"?

P.S: You posted this thread about 5 times in a row... wonky internet?

---

### Post by efflandt on 2011-01-14
Until Natty is released (months from now) there is a different forum for that [http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

So you should post Natty questions to that forum, or lurk in it to check for any issues.  A sticky in that forum also explains what to do about "partial" updates, which can break things if you blindly do them.

You should only run a development version if you understand that there may be bugs, things may not work at times, and you may need to reinstall.  It is even riskier running a Wubi version when a regular install is not sorted out yet.

---


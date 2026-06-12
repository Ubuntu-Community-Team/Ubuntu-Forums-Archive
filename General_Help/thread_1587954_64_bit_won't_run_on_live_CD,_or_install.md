---
title: "64 bit won't run on live CD, or install"
date: 2010-10-04
forum: General Help
---

### Post by ked on 2010-10-04
I've got a brand new HP EliteBook 2540p and the 64 bit version of 10.04 won't run from the live CD or install. I only get to choose language and then make a choice from the next menu. Then the screen go black and the CD stop spinning after a while. Anyone else experienced similar behavior?

Cheers,
Ked

---

### Post by ivanovnegro on 2010-10-04
Did you check the md5 sum?
Maybe your CD is corrupted.

---

### Post by ked on 2010-10-04
> **ivanovnegro said:**
> Did you check the md5 sum?
Maybe your CD is corrupted.

Must admit I did not, mostly because I'm not sure how to do it. If I run
"md5sum" on the downloaded ISO, I get 4bc6827198b3b3825e1db5cb256eeece
But but how do I find the md5 sum on the CD?

Thanx in advance
Ked

---

### Post by Quackers on 2010-10-04
There is a page on the Ubuntu site that gives the checksums, I believe.
Is it possible that you downloaded the alternate cd?

---

### Post by ivanovnegro on 2010-10-04
> **ked said:**
> Must admit I did not, mostly because I'm not sure how to do it. If I run
"md5sum" on the downloaded ISO, I get 4bc6827198b3b3825e1db5cb256eeece
But but how do I find the md5 sum on the CD?

Thanx in advance
Ked

Ok, here is a [Link]("https://help.ubuntu.com/community/UbuntuHashes") with the md5sums. I hope it helps.

---

### Post by Quackers on 2010-10-04
I can't see that checksum anywhere (including Maverick Meerkat) :-(

---

### Post by ked on 2010-10-04
> **ivanovnegro said:**
> Ok, here is a [Link]("https://help.ubuntu.com/community/UbuntuHashes") with the md5sums. I hope it helps.

The md5 sum is ok, and the disc is also ok (found out how to check) so I think the burner may have burned to fast. Had a problem with that before. I'll try to re-burn the image at a slower speed.

Thanx,
Ked

---

### Post by ivanovnegro on 2010-10-04
> **ked said:**
> The md5 sum is ok, and the disc is also ok (found out how to check) so I think the burner may have burned to fast. Had a problem with that before. I'll try to re-burn the image at a slower speed.

Thanx,
Ked

Thats good to hear. So burn it again with lower speed, thats the best idea.
How often I burned with maximum and had problems.
I hope its only this detail, very often it is.

---

### Post by ked on 2010-10-05
> **ivanovnegro said:**
> Thats good to hear. So burn it again with lower speed, thats the best idea.
How often I burned with maximum and had problems.
I hope its only this detail, very often it is.

Hmmm... Ubuntu refuse to install or run the live CD. It has got a flash mem HD, could that be a problem?

Ked

---

### Post by TNT1 on 2010-10-05
Are you sure it's a 64bit processor?

---

### Post by vinan on 2010-10-05
[COLOR=black][FONT=Verdana]I have experienced similar issue with HP machines, don no why[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Try to boot from USB stick, by using Unetbootin, to make u r pen bootable[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Or use an external CD/DVD drive.-[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]  [/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
/vinan

---

### Post by ivanovnegro on 2010-10-05
> **ked said:**
> Hmmm... Ubuntu refuse to install or run the live CD. It has got a flash mem HD, could that be a problem?

Ked

Really, I dont know and yes be sure to have a 64bit processor.
What OS you have at the moment installed?
Karmic?

---

### Post by migs73 on 2010-10-05
If you are not sure if your CPU is 64bit capable, but are running Ubuntu/Linux, put this into terminal
```
cat /proc/cpuinfo | grep flags
```

If the output contains 'lm' in the groups of letters, then it is. If not you'll need to try the 32bit version.
If you can only use 32bit but have more than 3.5GB RAM, Ubuntu should be clever enough to download the PAE kernel which will allow that.

---

### Post by akvik on 2010-11-13
Hi,

maybe this thread is outdated now that 10.10 is around, but did you fix it? It worked for me when I used Startup Disk Creator in ubuntu to burn the .iso disk but not when I did it in Windows with unetbootin. If I remember correctly this also applies to 10.10.

---


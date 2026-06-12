---
title: "Compiz no longer working"
date: 2010-03-18
forum: General Help
---

### Post by bcvery on 2010-03-18
Hi all,

I'm pretty new to Ubuntu, have got 9.10 64-bit.  I have been using some of the compiz effects now for just over a week with no problems.  but yesterday they stopped working for what seems to be no reason.  I have the recommended nVidia driver installed, here is my graphics card from lspci:
```
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)

```

I right clicked on my desktop, and went to 'Change Destop background', then visual effects.  This has been set to None.  I cannot change this to Normal or extra, as I get an error saying
```
Desktop effects could not be enabled
```

I have followed another thread which explained how to unistall and reinstall compiz, but it did nothing.

Please help!

Thanks, bcvery

---

### Post by ibuclaw on 2010-03-18
Try running this script:
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

And post the output here.

Regards
Iain

---

### Post by bcvery on 2010-03-18
```
 More than one running X server detected -- sorry, the script can not handle that.
 Aborting.

```

Cheers, bcvery

---

### Post by bcvery on 2010-03-19
I have reinstalled Ubuntu 9.10 64-bit (for a number of reasons), and now have compiz running OK on twinview (from nVidia settings).  I have found a new problem, which is windows no long stay on my second screen, but after I've moved them there, they snap back to primary monitor.  I've found one other thread with this problem:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8992209#post8992209](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8992209#post8992209)
But there is no help there as of yet :(

Thanks, bcvery

---

### Post by bcvery on 2010-03-19
Solved, the problem was 'wobbly windows' apparently.

Thanks for the help,
bcvery

---

### Post by SagnaB on 2010-04-01
I now have similar problem.

Compiz WAS working quite well, with NO problems at all. Then today all of a sudden, it's as though compiz and my NVIDIA driver are not installed...

Here is the compiz-check output:
```

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G73 [GeForce 7600 GS] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```Any ideas?
As I said before, It was all working very well, no problems at all; compiz, Nv driver, desktop cube visual effects etc... But just today, nothing.
I have tried rebooting several times, completely un-installing compiz then reinstalling it, rebooting. It doesn't seem to help.

---


---
title: "kernel building"
date: 2012-10-07
forum: General Help
---

### Post by unibroker on 2012-10-07
I am following a tutorial written in May, 2012 for building a kernel.  I currently have a version installed that is more current than that used in the tutorial.  I noticed that the second step in the procedure is ```
wget http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.2.17.tar.bz2
```is an older version.  Will I encounter problems?  My purpose is one of learning more about linux and maybe as a side benefit making a kernel that is more efficient.  Thanks in advance.

---

### Post by Doug S on 2012-10-07
It should be O.K. to use the older kernel, depending on what has changed.
Why don't you just change that one step to get the current (for the 3.2 series) linux-3.2.30.tar.bz2 instead.
If you go to [http://www.kernel.org/](http://www.kernel.org/) the current stable kernels are listed, with links to the source code.

---

### Post by LiamOS on 2012-10-07
I'd recommend trying out the 3.6 release. It's just recently come out.
You could also try 3.5.5. 

I like new kernels.

---

### Post by unibroker on 2012-10-07
Thanks for the replies.  I will give my kernel a unique name.  Will it appear in the grub menu so that if there is an issue I can switch to my current one?

---

### Post by Doug S on 2012-10-07
> **unibroker said:**
> Thanks for the replies. I will give my kernel a unique name. Will it appear in the grub menu so that if there is an issue I can switch to my current one?
Yes, it should. And definately give yourself the option to go back. I also like to increase the time that the grub menu is displayed to be sure I have time to see it:```
GRUB_TIMEOUT=10
```

---

### Post by unibroker on 2012-10-07
I extracted the kernel with the final 2 lines of output being ```
tar: cd: Not found in archive
tar: Exiting with failure status due to previous errors

```.

This is what I've done so far.
Step 1```
sudo apt-get install git-core libncurses5 libncurses5-dev libelf-dev asciidoc binutils-dev linux-source qt3-dev-tools libqt3-mt-dev libncurses5 libncurses5-dev fakeroot build-essential crash kexec-tools makedumpfile kernel-wedge kernel-package
```
Step 2```
wget http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.5.5.tar.bz2
```
Step 3```
tar -xjvf linux-3.5.5.tar.bz2 cd linux-3.5.5/
```

Is there something I need to address before going on?

---

### Post by Doug S on 2012-10-07
I think you are O.K. This:```
tar -xjvf linux-3.5.5.tar.bz2 cd linux-3.5.5/
```Should be this:```
tar -xjvf linux-3.5.5.tar.bz2
cd linux-3.5.5
```And I think, but did not test it myself, that is why you got the error you listed.
 
Edit: By the way, the current stable 3.5 series kernel is 3.5.6 (Oh, ... but I think that might just be as of not long ago. I see there is a 3.6.1 now also)

---

### Post by unibroker on 2012-10-07
In the configuration, under General Setup, Kernel Compression Mode has Gzip selected but the kernel I downloaded was of .bz2.  Will that present a conflict if I don't select Bzip2?

---

### Post by unibroker on 2012-10-07
I did get a successful build and installation of the 3.5.5 kernel. However, when I did boot into it I had the same resolution problems that I had in testing the early Quantal kernels.  It probably has to do with my nvidia graphics chip as it was with Quantal.  I am puzzled by the fact that in one of the steps I followed was code to mirror my current settings.

---


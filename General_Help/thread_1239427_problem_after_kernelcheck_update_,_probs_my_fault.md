---
title: "problem after kernelcheck update , probs my fault"
date: 2009-08-13
forum: General Help
---

### Post by mathyou on 2009-08-13
Hi,
I wanted to get my webcam working and after some googling the solution seemed to be to use kernelcheck to update the kernel, as in this [post]("http://ubuntuforums.org/showthread.php?t=885795&highlight=vx-1000&page=7"). Not sure what I did wrong but now when I boot into ubuntu it gets to the loading screen, then when the loading bar is full it goes to a complete mess. I think it is something to do with graphics drivers but I am not very knowledgable and could do with someone to point me in the right direction. 

Is it rescue-able?

I'm using Jaunty, and have an ATI HD4850.

Writing this from windows...

---

### Post by SPr on 2009-08-13
Do you mean this post? [http://ubuntuforums.org/showpost.php?p=7352750&postcount=65](http://ubuntuforums.org/showpost.php?p=7352750&postcount=65) You'll have to install new drivers to match the kernel.

```
uname -r
``` will show which kernel is installed. Did the new kernel download from the Ubuntu repos? If so then:
```

aptitude update
aptitude safe-upgrade

```
will do it for you.

If the kernel came from somewhere else (I've never heard of kernel check) then you may have to install using the manufacturer's own driver (if they produce one - I use nVidia and don't know much about ATI).

---

### Post by mathyou on 2009-08-13
Yep that is the post I meant. I think kernelcheck updates to the latest kernel, which is not in the ubuntu repos. Unfortunately I must have done something wrong. Even if I choose a different kernel from the boot menu, I get to the same point and then it crashes. The kernel is 2.6.30.4 

As I said, I think the problem is with graphics drivers, I'm just not sure how to fix it. Any solution will probably have to be by using the command line only, in recovery mode as it crashes beyond that. Is there a way to reenable/reinstall my proprietary driver from the command line?

cheers,
m

---

### Post by SPr on 2009-08-13
Sadly I can't help you with installing ATI drivers I only know how to do it from the repos or by using the nVidia method (nVidia user here). Hopefully someone else will know how to do it.

TBH I'm not sure why the other kernels won't work; did kernelcheck install anything other than a new kernel?

I'm sure you already now this ;) but installing a kernel from anywhere else except the official repos can lead to trouble and the person in that post really shouldn't have suggested it as a fix even if it worked for him/her. BTW I'd be interested t know if s/he is now having trouble because of it.

Edit: You could always compile your own kernel; at least it would be built to run on your PC ;)

---

### Post by mathyou on 2009-08-13
You're probably right, I knew it was a bit risky. Thanks, maybe someone will know how to enable the ATI drivers.

---


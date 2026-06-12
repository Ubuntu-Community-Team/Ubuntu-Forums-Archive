---
title: "what is kernel installation?"
date: 2012-03-02
forum: General Help
---

### Post by c2tarun on 2012-03-02
Hi friends,

I was reading a book on linux kernel development. In the first chapter it is teaching me how to install a kernel.
I am not getting this point. 
What does it mean by to install a kernel?
I already have linux installed in my machine. 
What will happen if I install new kernel? 
On rebooting do I get the option of switching b/w the two kernel's?

Or is it like chroot, I install it then lock myself in it and then do all the operations?

---

### Post by elliotn on 2012-03-02
> **c2tarun said:**
> Hi friends,

I was reading a book on linux kernel development. In the first chapter it is teaching me how to install a kernel.
I am not getting this point. 
What does it mean by to install a kernel?
I already have linux installed in my machine. 
What will happen if I install new kernel? 
On rebooting do I get the option of switching b/w the two kernel's?

Or is it like chroot, I install it then lock myself in it and then do all the operations?

yes if you install a new kernel it will appear in grub and you can choose to boot on one of them. ubuntu provide already compiled kernels modified to work well will ubuntu

---

### Post by Khayyam on 2012-03-02
The analogy is this: 

Linux (the kernel proper) is the "OS", what you have installed is a "userland" with applications, commands, and user interfaces. The "OS" provides a means of linking the hardware to "userland".

So, to have the kernel sources and to be able to build your own, means that you can effect this "link" in the form of "drivers" (for specific hardware that perhaps your current kernel doesn't support, or have included), remove un-necessary drivers, etc, etc.

You probably don't want to do this, most "Linux" users don't, but the sources are available for you to do so. It's that simple.

best ... khay

---

### Post by 1clue on 2012-03-02
The kernel is not the operating system.

Linux is the kernel, nothing else.  Your "Linux" distribution (probably Ubuntu given the nature of this forum :)  ) consists of the kernel and a bunch of software, most of which is Open Source but some might not be.

The kernel is a layer of software that provides a common API to access whatever hardware you have.  It consists of device drivers (video cards, network cards, CPU features, etc), protocol support (like advanced networking features, support for filesystem types), memory management, and a bunch of other similar things.

Note that a lot of those features I mentioned can have "userland" components.  Generally the userland components configure the kernel features, but in some cases the userland component is actually a core part of the feature.

The kernel provides a place for your operating system to "stand."  You have libraries which are compiled for your platform that use the kernel features to access your hardware.  There are services which use those libraries to provide things like file sharing.

Finally, your applications (like Firefox) use services and libraries to do whatever you use the libraries on.

---

### Post by 1clue on 2012-03-02
Oh yeah...the point.

So the reason you might want to install a different kernel.

Here are some:
[LIST=1]
[*]There might be a security flaw or bug which is fixed in the new version.
[*]There might be a feature you want which is unavailable in your current kernel but available in the new one.  Like advanced networking.
[*]There might be a feature in your current kernel which is available but you don't want it to be.
[*]You might be playing with your kernel to see what features you might want or not want.
[/LIST]

Seriously, compiling your kernel can provide months of free entertainment and education.

Always keep a working kernel installed as the default kernel.  That lets you "undo" without a lot of hoop-jumping.

---

### Post by c2tarun on 2012-03-02
> **1clue said:**
> Oh yeah...the point.
 
So the reason you might want to install a different kernel.
 

Here are some:[LIST=1]
[*]There might be a security flaw or bug which is fixed in the new version.
[*]There might be a feature you want which is unavailable in your current kernel but available in the new one. Like advanced networking.
[*]There might be a feature in your current kernel which is available but you don't want it to be.
[*]**You might be playing with your kernel to see what features you might want or not want.**
[/LIST]
Seriously, compiling your kernel can provide months of free entertainment and education.
 
Always keep a working kernel installed as the default kernel. That lets you "undo" without a lot of hoop-jumping.
 
I'll go with the fourth reason, and might be one day I may make my career in kernel development :)
and I am not playing with my kernel, I pulled the latest stable version from [www.kernel.org]("http://www.kernel.org") and I am trying to break it make it or whatever you say :) . I have one stable kernel installed with the Ubuntu and Iam not going to touch it right now :)

---

### Post by Khayyam on 2012-03-02
> **1clue said:**
> The kernel is not the operating system. Linux is the kernel, nothing else.

No, you are incorrect. The idea that "userland" is the "operating system" (as a user "operates" it) is something of a new invention that came about with the advent of "personal computing", GUI's, etc. When people "checked email" they "used email", they didn't use "Unics" (the OS on which the mail system run on) and the habit of calling the user interface the "OS" kinda developed from there.

Now we are all used to calling "userland" the "OS", and I'm more than happy to go along with the convention, however, "userland" is more an "interface" than the method by which the computer operates, which is why "userland" can be identical on any number of OSes (think of Linux, *BSD, etc).

This is why I wrote "Linux (the kernel proper) is the OS", because **it** does the actual "operating", "userland" is provided with the kernels "OS" facilities and interfaces with the user.

If you read the "[Linux Kernel](http://en.wikipedia.org/wiki/Linux_kernel)", [operating system kernel](http://en.wikipedia.org/wiki/Operating_system_kernel), and [Linux](http://en.wikipedia.org/wiki/Linux) entries on wikipedia, you will see how the terminology has developed as they now speak of an "operating system kernel" (which is "Linux") and a "unix like operating system", but again, the terminology is meerly being tweeked to bring it more in line with common usage. In the 70's and 80's the "OS" would have been a distant abstraction for users. They would have "used email", "used a terminal", or "used the computer" (via a tty or tellytype).

best ... khay

---

### Post by 1clue on 2012-03-02
A user operates the operating system?  No.

[http://lmgtfy.com/?q=computer+operating+system+definition](http://lmgtfy.com/?q=computer+operating+system+definition)

The operating system is the software abstraction layer which is "operated" by userland applications, which are in turn "operated" by a user at some level up the chain.  Drivers are generally considered to be parts of the operating system and they *sometimes* can run in userland (which is unprivileged execution mode and non-kernel memory on the computer, not something a user does).

glibc is an example of a userland library which is NOT generally considered part of the operating system and is used to enable applications which use it to run on any operating system to which glibc has been ported.  glibc IS part of an abstraction layer.

End-user applications such al Libre Office use standard libraries to run, and those libraries make porting much easier.

When you compile the kernel a lot of this becomes clear, because you generally sit there and read through the help for anything you don't understand.  The kernel sometimes calls unprivileged code, but only in limited context.

---

### Post by Khayyam on 2012-03-02
> **1clue said:**
> A user operates the operating system?  No.

Please read what I wrote: "**The idea that "userland" is the "operating system" (as a user "operates"  it) is something of a new invention that came about with the advent of  "personal computing", GUI's, etc.**"

So, am I in disagreement here?

> **1clue said:**
> The operating system is the software abstraction layer which is "operated" by userland applications, which are in turn "operated" by a user at some level up the chain.  Drivers are generally considered to be parts of the operating system and they *sometimes* can run in userland (which is unprivileged execution mode and non-kernel memory on the computer, not something a user does).

Where has anything I've written contradicted this? The "OS" (proper) is the "[operating system kernel]("http://en.wikipedia.org/wiki/Linux") and, as you say, "not something a user does", but common parlance is that the "OS" is something the "user operates". I was making that very point when trying to show how the idea developed from the "use" of an "application" in "userland".

> **1clue said:**
> glibc is an example of a userland library which is NOT generally considered part of the operating system and is used to enable applications which use it to run on any operating system to which glibc has been ported.  glibc IS part of an abstraction layer.

Sorry? I don't think we are in disagreement about anything here, and I'm not sure what point you're trying to make with the above.

> **1clue said:**
> End-user applications such al Libre Office use standard libraries to run, and those libraries make porting much easier.

Fact ... but unrelated.

> **1clue said:**
> When you compile the kernel a lot of this becomes clear, because you generally sit there and read through the help for anything you don't understand.  The kernel sometimes calls unprivileged code, but only in limited context.

Anecdotal, factual ... but unrelated

oh, and thanks for the link to google ... I wasn't aware that such a facility existed.

best .. khay

---


---
title: "Ubuntu kernel selection + updates"
date: 2006-07-01
forum: General Help
---

### Post by xenomorph99 on 2006-07-01
Hi,

First time around I installed Ubuntu I managed to get the K7 kernel (which is correct) somewhere along the line but I can't remember when or how it happened.

I've just installed Ubuntu on another machine, which is also AMD Athlon (k7) and it has installed the -386 kernel as default. So, I did an apt-get install etc and fetched the latest k7 kernel for the machine and rebooted.

Now, in the auto update, I'm being asked if I want to install the latest 386 kernel. So, there are two things:
a. Why ask me if i want the latest 386 kernel when I have booted using k7?
b. Is the 386 kernel somehow 'later' than the k7 kernel *I just fetched*?

Also, is there a correct sequence for installing etc from scratch.

e.g. 
a. Install ubuntu
b. Install right kernel
c. Install updates minus the -386 items
d. Run easyubuntu and get correct packages..

etc

?

Ta.
Xeno

---

### Post by az on 2006-07-01
To install the k7 kernel, you install linux-k7 (and get the kernel and associated packages)

That in of itself does not remove the linux-386 package, nor the kernel(s) that are already installed on your system.  Since they are there, the package manager will update them too.  To prevent that you can just remove the linux-image-386 packages and their dependencies.

---

### Post by xenomorph99 on 2006-07-01
Hi,

Thanks - I sort of expected it to 'swap it' all by itself but I can understand why that might not be the best action. 

I'll remove them....

When I 'remove them via synaptic', will that also modify the grub bootloader menu?

Also, if I use synaptic to remove the 386 kernel items, it automatically forces me to install the later version of the 386 kernel. It's not very intuitive, is it?

Ta.
Xeno

---

### Post by az on 2006-07-01
[QUOTE=xenomorph99]

When I 'remove them via synaptic', will that also modify the grub bootloader menu?
[/QUOTE]

Yes.
[QUOTE=xenomorph99]
Also, if I use synaptic to remove the 386 kernel items, it automatically forces me to install the later version of the 386 kernel. It's not very intuitive, is it?

Ta.
Xeno[/QUOTE]
You are not removing all the linux-386 packages, then.  You need to get rid of all of them.  You can do this by removing al the linux-image-386-xxxxx packages, that wil in turn remove linux-386.

---

### Post by xenomorph99 on 2006-07-02
Hi,

I selected all the 386 items for removal but synaptic always ended up deciding to download the later 386 kernel (which, in the end, I did). When I tried to remove THAT kernel, it did without further hassle.

I seem to now have the correct kernel and the grub menu appears correct.

Ta,
Xeno

---


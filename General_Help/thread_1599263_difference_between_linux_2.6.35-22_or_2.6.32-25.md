---
title: "difference between linux 2.6.35-22 or 2.6.32-25?"
date: 2010-10-17
forum: General Help
---

### Post by arnetheman on 2010-10-17
I am an Ubuntu noob and i recently upgraded from 10.04 to 10.10.

After I upgraded from 10.04 to 10.10 I can choose between the following OS's when turning on my computer (see picture):
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=172656&d=1287342272[/IMG]

What is the difference between linux 2.6.35-22 and 2.6.32-25?
The  2.6.35-22 option froze once on login, I have never experienced any trouble with the 2.6.32-25 option.

So what is the difference between the two? Do i need both? If not, which one should I remove and how?

---

### Post by Hippytaff on 2010-10-17
These are different kernels - the code which contains modules (drivers) that talk to the hardware on your pc and the programs that run, like a middle man...they also control memory assignment and input output...ness. if one causes issues use the other one...it's best to keep at least two so that when new kernel upgrades are downloaded you always have a working one to revert to in situations like this :-)

[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel) for more reading :-)

---

### Post by arnetheman on 2010-10-17
thanx!

---

### Post by bakegoodz on 2010-10-17
They are supposed to bug fixes in Ubuntu's implementation of the Linux Kernel. They could come from of bug reports of certain hardware not working like it should. I assume that the kernel module settings get tweaked or something. Also the official Linux kernel team puts out fixes for specific version such as going from 2.6.35.1 to 2.6.35.2  I bet those make there way into the Ubuntu kernel too.

---

### Post by Hippytaff on 2010-10-17
> **bakegoodz said:**
> They are supposed to bug fixes in Ubuntu's implementation of the Linux Kernel. They could come from of bug reports of certain hardware not working like it should. I assume that the kernel module settings get tweaked or something. Also the official Linux kernel team puts out fixes for specific version such as going from 2.6.35.1 to 2.6.35.2  I bet those make there way into the Ubuntu kernel too.

From what I've read, the ubuntu devs get the kernel from the debian upstream, and tweak the kernels, but yes it's all about fixing bugs and hardware compatability as far as I know

---

### Post by Toz on 2010-10-17
Kernel changelog can be viewed by typing:

> gunzip -c /usr/share/doc/linux-headers-2.6.35-22-generic/changelog.Debian.gz | more

in a terminal window. (Remember to replace '2.6.35-22-generic' with your specific kernel)

---

### Post by Hippytaff on 2010-10-17
> **Toz said:**
> Kernel changelog can be viewed by typing:



in a terminal window. (Remember to replace '2.6.35-22-generic' with your specific kernel)
wow...thats fantastic...one for the Tomboy Notes :-)

---


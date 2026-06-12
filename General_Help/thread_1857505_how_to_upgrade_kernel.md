---
title: "how to upgrade kernel?"
date: 2011-10-10
forum: General Help
---

### Post by einstein**-7 on 2011-10-10
Can someone please tell me how to get synaptic to show newer and older kernels particularly 2.6.39-0 for ubuntu 11.04 i'm using 64bit.:confused:

---

### Post by snowpine on 2011-10-10
Use your Update Manager or the following terminal commands to get the latest supported kernel (for 11.04 this will be 2.6.38 ):

```
sudo apt-get update 
sudo apt-get dist-upgrade
```

If you want to install an unsupported kernel then you have options, probably the easiest is the [Ubuntu Kernel PPA]("https://launchpad.net/~kernel-ppa/+archive/ppa") and the obvious is [kernel.org]("http://kernel.org")

---

### Post by mikejonesey on 2011-10-10
hello einstien, e=mc hammered...

you can't they are not available like that... you can compile and build your own... there are a few tutorials on the net but you risk frying your pc if somting is not setup right...

---

### Post by einstein**-7 on 2011-10-10
> **snowpine said:**
> Use your Update Manager or the following terminal commands to get the latest supported kernel (for 11.04 this will be 2.6.38 ):

```
sudo apt-get update 
sudo apt-get dist-upgrade
```If you want to install an unsupported kernel then you have options, probably the easiest is the [Ubuntu Kernel PPA]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa") and the obvious is [kernel.org]("http://kernel.org")

how would i add the kernel ppa to synaptic's repository list?:confused:

---

### Post by snowpine on 2011-10-10
> **einstein**-7 said:**
> how would i add the kernel ppa to synaptic's repository list?:confused:

The instructions are on the page I linked to. Are you sure you're ready to run an unsupported kernel? What specific problems are you having with the supported kernel?

---

### Post by Zill on 2011-10-10
> **einstein**-7 said:**
> how would i add the kernel ppa to synaptic's repository list?:confused:
With all due respect, if you need to ask this question you *really* shouldn't attempt to do it.

---

### Post by garvinrick4 on 2011-10-10
#This is not in repos for natty 2.6.39 if you want it do this below:
To remove a kernel type the kernel number in synaptic search window;
Kernels installed:
```
grep menuentry /boot/grub/grub.cfg
```Here is 2.6.39 imagine you want it for some reason not explained.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-oneiric/")
Take all three.
all.deb
then 64 bit headers
then 64 bit image
Download the 3 of them then click on them in same order as given and they will install through ubuntu software center.
If wants module-init-tools upgraded also: Lower left of page 64 bit in .deb install same download and
click on will install through Ubuntu software center.
[amd64 build : 3.13-1ubuntu1 : &#8220;module-init-tools&#8221; package : Ubuntu]("https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1/+build/2555500")

---

### Post by einstein**-7 on 2011-10-11
> **snowpine said:**
> The instructions are on the page I linked to. Are you sure you're ready to run an unsupported kernel? What specific problems are you having with the supported kernel?

Sorry i used the terminal instructions and they worked but hadn't found the instructions for adding the ppa to the sources file.  I installed them as 'garvinrick4' suggested and all seemed to work fine - also added the ppa so synaptic can find new kernels in the future.
As for the reason, this thread explains [http://ubuntuforums.org/showthread.php?t=1750000&highlight=natty+mem+leak](http://ubuntuforums.org/showthread.php?t=1750000&highlight=natty+mem+leak)
I'm using for graphical applications and this problem makes the system useless.  As far as unsupported kernels - why not? especially when the stable supported ones have stupid problems.:lolflag:

---

### Post by einstein**-7 on 2011-10-11
Thanks all!:p

---

### Post by snowpine on 2011-10-11
> **einstein**-7 said:**
> As for the reason, this thread explains [http://ubuntuforums.org/showthread.php?t=1750000&highlight=natty+mem+leak](http://ubuntuforums.org/showthread.php?t=1750000&highlight=natty+mem+leak)

I think you misunderstood that thread. It is about a memory leak in Compiz, completely unrelated to the kernel. If you're having that problem then try disabling Compiz, just like the thread says...

---


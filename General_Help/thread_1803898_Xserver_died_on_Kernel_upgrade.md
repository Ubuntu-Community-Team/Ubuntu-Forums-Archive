---
title: "Xserver died on Kernel upgrade"
date: 2011-07-14
forum: General Help
---

### Post by CattyNebulart on 2011-07-14
When booting to kernel 2.6.38-10 I get an error about it not being able to load the nvidia drivers/kernel module. 2.6.38-8 works fine. Actually I do not even get the error unless I run 'startx' but instead have to hunt through the logs for it.

I do not even get the usual low resolution mode, just the text terminal so this is an serious issue especially since grub no longer prompts at startup for alternate boot options. :( Probably the worst change in Ubuntu since it makes it much harder to recover from something like this.

I think it might be due to the GTX 460 card I have, I noticed other people have had the same issue in the past with this card.

Nvidia drivers installed from the kubuntu repository version 4.1.0 NVIDIA 270.41.06.

How do I fix the drivers, or alternately what is the change in the grub menu to change the defaulted booted kernel?

---

### Post by idoitprone on 2011-07-14
well....did you load the nvidia kernel module after you upgraded the kernel. Every time you update the kernel, you will also need to install the nvidia module

---

### Post by CattyNebulart on 2011-07-14
As per my understanding apt should take care of all of that without interference from the user. Since this isn't the case something is wrong either with the apt dependencies, the nvidia driver or my system.

If there are certain manual steps that should be taken please enlighten me as to what they are, I am sure this will help other people who run into the same problem.

---

### Post by idoitprone on 2011-07-14
> **CattyNebulart said:**
> As per my understanding apt should take care of all of that without interference from the user. Since this isn't the case something is wrong either with the apt dependencies, the nvidia driver or my system.

If there are certain manual steps that should be taken please enlighten me as to what they are, I am sure this will help other people who run into the same problem.

No no no. It is not the problem with the dependencies, but problem with nvidia itself. It is a closed source priopriotory driver and that cause issues itself. Apt frontend of dpkg does try it best to reinsure the depencies, but close source drivers do not play nice sometimes and does not load when there is a kernel update
here is a thread with the same kind of problem. This is not an unusual issue
[http://lwn.net/Articles/287056/]("http://ubuntuforums.org/showthread.php?t=15538")

try this command on the broken gui kernel

```
sudo modprobe nvidi<tab>
```Please: note, I never used an nvidia card with linux, so I do not know what is the name of the kernel module. I am telling the to use tab to find the correct module

If you want proof
type

```
lsmod | grep -i nvidia
```on both kernels. One should return the module, the other should not have it.

If it still does not work. You need a new nvidia driver since it is incompatible with the kernel you just installed. This is why developers kidda hate closed source kernel.
[http://kerneltrap.org/Linux/Position_Statement_on_Linux_Kernel_Modules]("http://www.osnews.com/story/1990/Kernel_Devs:_Closed_Source_Modules_Harmful_and_Undesirable")
In some cases you might have to recompile. Who know what nvidia did to their drivers. Try to find the lastest drivers on nvidia website and follow their instructions.
try to look at this forum if you have to install the nvidia kernel from their website
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

### Post by yokums on 2011-07-14
Have the exact same problem.  While I agree with CattyNebulart that this should be handled and I thought it was starting with 11.04, idoitprone is correct.  I had to download and rebuild the driver from Nvidia to get this working.

---

### Post by szal on 2011-07-14
Strange&#8230; I didn&#8217;t have any such issue; I just rebooted into the new kernel, and everything was fine. I even checked to see what driver was being used. Granted, I use the NVIDIA 275.09.07 from Roberto Ferramosca&#8217;s LffL PPA, but the handling shouldn&#8217;t be any different with the stock NVIDIA 270 driver.

***[Edit]*** CattyNebulart and yokums: Please check that you have **dkms** installed, then try [COLOR=Blue]**sudo apt-get install --reinstall linux-generic**[COLOR=Black], that should take care of the kernel modules (not only graphics drivers, but also things like the VirtualBox kernel module).[/COLOR][/COLOR]

---

### Post by CattyNebulart on 2011-07-18
> **szal said:**
> try [COLOR=Blue]**sudo apt-get install --reinstall linux-generic**[/COLOR]

I tried it from the working kernel and rebooted, that didn't work.

I also checked out idoitprone suggestion, and the kernerl with a broken nvidia indeed does not have the nvidia module when I do lsmod. In fact the borked kernel has a lot less modules.

As I don't reboot all that often I will just change grub for now, the next kernel update should hopefully fix it anyway.

Thanks for your help, feel free to keep adding to this thread as other people have the same problem.

---


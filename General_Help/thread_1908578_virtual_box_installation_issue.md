---
title: "virtual box installation issue"
date: 2012-01-13
forum: General Help
---

### Post by helyos on 2012-01-13
Hi there, 

I have ubuntu 10.04. I try to install virtual box. I run

sudo /etc/init.d/vboxdrv setup

it gives me :

```
 * Stopping VirtualBox kernel modules                                                                                                                            Opening /proc/modules: No such file or directory
Opening /proc/modules: No such file or directory
Opening /proc/modules: No such file or directory
                                                                                                                                                          [ OK ]
 * Uninstalling old VirtualBox DKMS kernel modules                                                                                                        [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                                                                                                   
Error! Your kernel headers for kernel 2.6.38.2-grsec-xxxx-grs-ipv6-32 cannot be found at
/lib/modules/2.6.38.2-grsec-xxxx-grs-ipv6-32/build or /lib/modules/2.6.38.2-grsec-xxxx-grs-ipv6-32/source.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                                                                                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

```

If i try:


sudo apt-get install linux-headers-$(uname -r)
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.38.2-grsec-xxxx-grs-ipv6-32
```


The log file is:
```
Uninstalling modules from DKMS
  removing old DKMS module vboxhost version  4.1.8

------------------------------
Deleting module version: 4.1.8
completely from the DKMS tree.
------------------------------
Done.
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/4.1.8/source ->
                 /usr/src/vboxhost-4.1.8

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.38.2-grsec-xxxx-grs-ipv6-32 package.
Failed to install using DKMS, attempting to install without
Makefile:172: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.
```
Cam you help me? thanx

---

### Post by lechien73 on 2012-01-13
Is this a plain vanilla install of Ubuntu 10.04? Your kernel looks very strange - I've only seen that type of kernel once before and that was in a co-located server environment.

You'll need a standard Ubuntu kernel before you can compile the Virtualbox kernel driver against it.

---

### Post by helyos on 2012-01-13
Ubuntu was pre-installed on the environment.
So any sugestions on how should i get a "normal" version of kernel?

---

### Post by Synoc on 2012-01-13
> **helyos said:**
> Ubuntu was pre-installed on the environment.
So any sugestions on how should i get a "normal" version of kernel?

if it is a production server, MY suggestion is don't try to change the kernel, if someone went to the trouble to use a non-standard kernel, it's for a reason.

You might be better off trying a different computer. What type of computer is it currently on?

---

### Post by guestolo on 2012-01-14
Why not directly download the .deb file from virtualbox and install it
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)
Afterwards, install Extension pack 
I've never had a problem with Virtualbox

Running Ubuntu 11.10 operating system
VM's>>Windows XP sp3
Ubuntu 10.04  and Linux Mint

---

### Post by helyos on 2012-01-14
> **guestolo said:**
> Why not directly download the .deb file from virtualbox and install it
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)


This is the way how i installed it. There were no errors at installation, but when i create and start a new virtual machine, it gives me the error.

@Synoc this is my guess too.

Maybe there is an alternative to virtualbox for ubuntu 10.04?

---

### Post by Bobhuber on 2012-01-14
> **helyos said:**
> This is the way how i installed it. There were no errors at installation, but when i create and start a new virtual machine, it gives me the error.

@Synoc this is my guess too.

Maybe there is an alternative to virtualbox for ubuntu 10.04?
Virtualbox is looking for the Kernel Header information which under a normal install it would find automatically with DKMS.
However if someone compiled and installed a Kernel specific to there needs (very easy and common thing to do) and then REMOVED the source code from the directory it was compiled or moved it elsewhere VBOX can't find the header information it needs to recompile the header info it needs to run.
Solution > If there are no special needs that you know of you can use Synaptic package manager and install the most recent Standard Kernel files for 10.04 . It should update the system files and allow you to install VB without any problem. This may indeed work depending on what updates have occured since the system was installed.
LEAVE THE CUSTOM KERNEL INSTALLED untill you are sure there are no problems. You can select which version to boot from via the grub boot menu. There are 3 files you need to install. Maybe someone running 10.04 will be kind enough to give you the names of the files you need.

---

### Post by Cheesemill on 2012-01-14
What hardware are you running on?

The only time I've seen a kernel resembling this was on a VPS from Linode.

You're not trying to install VirtualBox on a virtual machine are you?

---

### Post by helyos on 2012-01-14
It is a dedicated server from ovh. 
At the end i think i will leave the kernel how is it because i can't have any downtime and maybe i will install virtual box on other machine. Maybe if i will put a new kernel will not function properly with the server's hardware.

Thanks for your help.

---


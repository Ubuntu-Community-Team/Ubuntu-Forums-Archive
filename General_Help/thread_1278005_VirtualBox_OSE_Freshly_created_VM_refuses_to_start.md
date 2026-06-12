---
title: "VirtualBox OSE: Freshly created VM refuses to start"
date: 2009-09-29
forum: General Help
---

### Post by anthony62490 on 2009-09-29
Just installed virtualbox-ose a few hours ago. I'm trying to install a virtual copy of XP. Installation and VM creation worked just fine, but when I push the start button, I get two error messages, one after the other:
> 
Failed to open a session for the virtual machine Windows XP.
--------------------------------------------------
Virtual machine 'Windows XP' has terminated unexpectedly during startup.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component:   Machine
Interface:   IMachine {ea6fb7ea-1993-4642-b113-f29eb39e0df0}


Followed by:
> VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908 )

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

So running the command brings up this output:

> anthony@anthony-desktop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for anthony: 
sudo: /etc/init.d/vboxdrv: command not found

Sure enough, upon checking the file, there is no file called "vboxdrv"

Now when I run VBox in the terminal, I get a very interesting message:
> anthony@anthony-desktop:~$ virtualbox
WARNING: The character device /dev/vboxdrv does not exist.
Please install the virtualbox-ose-source package and the appropriate headers, most likely  linux-headers-generic.

You will not be able to start VMs until this problem is fixed.

---------------------------------------------
---------------------------------------------
Now what I gather from this is that a file was skipped when I installed Vbox and that I can get this file by installing the source package and copying the file. The problem is, upon checking Synaptic, I see that I already have these two packages. I've got to say that I'm at a loss here. Do you have any ideas for what I am supposed to do next?

EDIT: I found a file called vboxdrv at /var/lib/dkms/ (screenshot included)
It doesn't look as though it has been compiled however. I'm a bit unsure what to do with it. 
If I am going in the wrong direction with this idea, please tell me.

---

### Post by Darkwing-Duck on 2009-09-29
I don't know a lot about VB but, Here is a guide that is very complete. Hope this can help you.

[http://gwos.org/udsf/doku.php/software:virtualbox](http://gwos.org/udsf/doku.php/software:virtualbox)

---

### Post by fuzzyk.k on 2009-09-29
have you tired running ```
 modprobe vboxdrv
``` ?

---

### Post by anthony62490 on 2009-09-29
> **fuzzyk.k said:**
> have you tired running "modprobe vboxdrv"

anthony@anthony-desktop:~$ modprobe vboxdrv
FATAL: Module vboxdrv not found.

---

### Post by P4man on 2009-09-29
There should be a "/etc/init.d/vboxdrv" (at least there is on my install). I suggest you try reinstalling virtualbox.

---

### Post by anthony62490 on 2009-09-29
> **P4man said:**
> There should be a "/etc/init.d/vboxdrv" (at least there is on my install). I suggest you try reinstalling virtualbox.

Uninstalled virtualbox-ose and virtualbox-ose-source and reinstalled them. No change. Vboxdrv still does not exist. I also tried to compile the source files for vboxdrv, but no luck there either. the thing just won't compile.

---

### Post by P4man on 2009-09-30
dont try compiling it from source. 
Perhaps try removing it again, and install "virtualbox-3.0 " ?

---

### Post by anthony62490 on 2009-09-30
> **P4man said:**
> dont try compiling it from source. 
Perhaps try removing it again, and install "virtualbox-3.0 " ?

Ok, did not work. It was not included in Synaptic, so I found a [.deb package]("http://www.virtualbox.org/wiki/Linux_Downloads") (i386)for jaunty. I installed it, but nothing appeared to change. The terminal command "virtualbox-3.0" doesn't exist, and there is no entry for virtualbox in the Applications menu, so I tried to add it to Synaptic.

I ran the following commands:
```
sudo gedit /etc/apt/sources.list

//and added to the list:

deb http://download.virtualbox.org/virtualbox/debian jaunty non-free

//followed by:

wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

//

sudo aptitude update

//

sudo aptitude install virtualbox-3.0 dkms
```

At this point, I think I should have seen a configuration window, but I got nothing. The terminal output was as follows:

> anthony@anthony-desktop:~$ sudo aptitude install virtualbox-3.0 dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages will be REMOVED:
  libadplug0c2a{u} 
0 packages upgraded, 0 newly installed, 1 to remove and 15 not upgraded.
Need to get 0B of archives. After unpacking 455kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 161024 files and directories currently installed.)
Removing libadplug0c2a ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done


I must say, I'm a touch on the confused side here. Interestingly enough, I now have the vboxdrv file. Got any ideas?

---

### Post by P4man on 2009-09-30
installing the .deb and then installing the same thing through synaptic is what happened. Looks ok to me. now try running that 

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by anthony62490 on 2009-09-30
> **P4man said:**
> installing the .deb and then installing the same thing through synaptic is what happened. Looks ok to me. now try running that 

sudo /etc/init.d/vboxdrv setup

Ok, that didn't do very much.

```
anthony@anthony-desktop:~$ sudo /ect/init.d/vboxdrv setup
[sudo] password for anthony: 
sudo: /ect/init.d/vboxdrv: command not found

```

---

### Post by anthony62490 on 2009-09-30
Woah, woah. Hold everything. After I ran the last command, I checked my files again. This time I found "Sun VirtualBox" under the System Tools tab. That wasn't there before. I started it up and ran the command again.

```
anthony@anthony-desktop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for anthony:
 * Stopping VirtualBox kernel module
 *  done.
 * Recompiling Virtual Box kernel module
 * Look at /var/log/vbox-install.log to find out what went wrong
anthony@anthony-desktop:~$

```

And in vbox-install.log:

> Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/3.0.6/source ->
                 /usr/src/vboxdrv-3.0.6

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.28-11-generic cannot be found at
/lib/modules/2.6.28-11-generic/build or /lib/modules/2.6.28-11-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:147: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

It does more than it did last time, but I think I am still missing a file.

---

### Post by anthony62490 on 2009-10-01
I get the impression that this is just one or two commands from being fixed, but honestly, I'm not sure what to do next.

---

### Post by anthony62490 on 2009-10-02
OK, Im not sure how or why it happened, but Vbox is finally behaving! I just reset the computer and as it was rebooting, it ran a script that recompiled the Vbox kernel. I guess installing version 3.0 was what did it. Thank you all very much for helping mr out and being patient. 

I now have a working copy of Windows XP running under Ubuntu (hah!).

---


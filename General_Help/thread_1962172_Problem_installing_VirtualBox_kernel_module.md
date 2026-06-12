---
title: "Problem installing VirtualBox kernel module"
date: 2012-04-20
forum: General Help
---

### Post by Xandaros on 2012-04-20
Hey there,
I was unsure where to post this, but since so many factors come together, I decided to post it here.

First of all, I am using Ubuntu 11.10 Oneiric Ocelot. I upgraded from Ubuntu 11.04 Natty Narwhal, which was the first install.

Also, Linux version is 2.6.38-11-generic and it seems it was compiled with gcc 4.5.2.
(I am just trying to provide as much information as possible here :D)

When I first tried installing virtualbox today, it failed because it could not find the kernel headers. It was a bit of a hassle to install them, because I had to grab them from a lucid package.

Trying to install vbox again, these are parts of the install log that might be of interest:
> [...]
virtualbox (4.1.2-dfsg-1ubuntu1) wird eingerichtet ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
[...]

DKMS: install Completed.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * modprobe vboxdrv failed. Please use 'dmesg' to find out why
                                                                         [fail]I did as I was told and ran "dmesg | grep vboxdrv". This is the output:
> [   22.869308] vboxdrv: Found 4 processor cores.
[   22.869561] vboxdrv: fAsync=0 offMin=0x498 offMax=0x14b8
[   22.869626] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.869628] vboxdrv: Successfully loaded version 4.1.12 (interface 0x00190000).
[22377.802708] vboxdrv: disagrees about version of symbol module_layout
[22581.929389] vboxdrv: disagrees about version of symbol module_layout
[22821.807936] vboxdrv: disagrees about version of symbol module_layout
[23234.387832] vboxdrv: disagrees about version of symbol module_layout
[23688.004080] vboxdrv: disagrees about version of symbol module_layoutTrying to install the module manually with modprobe gave me this output:
> FATAL: Error inserting vboxdrv (/lib/modules/2.6.38-11-generic/updates/dkms/vboxdrv.ko): Invalid module formatI thought that I might be using a wrong version of gcc so I changed gcc from gcc-4.6 to gcc-4.5, but the problem persists.

I did everything I could think of / find via google.
I've got no remaining ideas on what's causing this, the module just doesn't want to be installed.

I was using virtualbox on natty without problems, so it's not a hardware problem.

Now, all those guys that might have an idea on what's happening:
Where is the problem or what shall I do to find the problem?

Edit:
In the first log it says "wird eingerichtet". It is german for "is being installed"

---

### Post by SeijiSensei on 2012-04-20
Are you sure you have linux-headers-2.6.38-11-generic installed as well?  How many different kernel versions do you have?  You might try cleaning out the stale ones from /boot, /boot/grub/grub.cfg, and /lib/modules.

Another thing to try is running 
```
sudo /etc/init.d/vboxdrv setup
```
though I'm guessing you'll get the same mismatch errors. Doesn't hurt to try, though.

Also did you install VBox using the Oracle repository as described [here](https://www.virtualbox.org/wiki/Linux_Downloads)?  Browse down to the part about "Debian-based distributions" and follow the instructions to add the repository.  I've found this the best method to insure everything matches up correctly when a new VirtualBox version is released.

---

### Post by Xandaros on 2012-04-20
Oh, forgot to mention that. I tried to execute that script, but it doesn't exist.
Thanks for giving me the hint about kernel versions. I just checked and saw that I got a 3.0 kernel, too.

I wonder why it didn't set GRUB up to use it, though...

Well, I'll boot that up and try again

---

### Post by Xandaros on 2012-04-20
After finally figuring out how to boot the 3.0 kernel, it seems to work.
I wonder why it doesn't show up in GRUB, though... It's in the menu.lst...
Oh well, I'll fix that some other time. I'm fine with typing a few commands to boot it for now :D

Thanks for the help!

And uhm... how do you mark a thread as solved?

---


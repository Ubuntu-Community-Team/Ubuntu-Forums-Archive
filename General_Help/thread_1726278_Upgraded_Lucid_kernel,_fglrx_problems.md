---
title: "Upgraded Lucid kernel, fglrx problems"
date: 2011-04-10
forum: General Help
---

### Post by Chowchilla on 2011-04-10
Hello all,

In upgrading Lucid's default kernel (2.6.32-30) to a more recent one (2.6-35-22), fglrx has gone awry. I performed the upgrade via Synaptic and went away from the computer for a short while. On return, despite the new kernel seemingly installed problem free, I had a crash report waiting for me in the notification area. It mentioned that fglrx had failed to install correctly. (I already had fglrx installed and working problem free, I assume kernel upgrade triggers reinstallation.)

I then attempted to reinstall it via System > Admin > Hardware drivers, however this too led to an installation error. I then decided to try completely removing it to start over, and so removed fglrx and associated packages via Synaptic.

On restart (booting into newer kernel) I received an error about there being graphical errors and Ubuntu running in basic graphical mode. I selected the option to load default config settings (or something...) and then selected "restart X". I then got back into the OS proper, albeit with windows not appearing in correct position and scrolling happening very slowly.

I now want to reinstall fglrx, but the Hardware drivers option is missing in the menu and I am unsure about trying via Synaptic, lest I cause further mess. Any help would be greatly appeciated!


UPDATE:

I tried to install fglrx again via Synpatic but it lists the old kernel (which I removed) as a dependency, but since I need fglrx for my current kernel I did not install this. So what should I try now?

UPDATE 2:

Realised that "Hardware drivers" missing was due to me carelessly removing jockey package when I was trying to remove fglrx earlier. So I reinstalled it and tried to install fglrx using it, but I received the error "SystemError: installArchive()" (or similar). Again, I had to remove the broken fglrx package(s) that jockey installed. It also installed the old kernel, which I removed again. So it would seem that regardless of the error encountered, the fglrx would not be compatible for my kernel.

---

### Post by b0b138 on 2011-04-10
Assuming it works the same as nvidia drivers, the video drivers module has to be recompiled with the new kernel. dkms should take care of this automatically. In your case, you also need the kernel headers, these are required for compiling. The 2.6.35 kernel is backported to lucid from maverick, so the packages you need are the kernel, linux-image-generic-lts-backport-maverick. And the headers, linux-headers-generic-lts-backport-maverick.

Im guessing you need the headers so the video driver module can be compiled against the new kernel.

---

### Post by Yellow Pasque on 2011-04-11
The fglrx package included with Lucid probably depends explicitly on the Lucid kernel. Install Catalyst manually: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)

---

### Post by Chowchilla on 2011-04-11
Tried following the solution offered [here]("http://www.mydailytechtips.com/2010/09/how-to-fix-fglrx-error-after-upgrading.html") but no joy. Still getting error when installing new kernel. I guess dkms cannot apply driver to new kernel.

After a good night's rest I shall try your advice, Temujin. Removing fglrx, installing new kernel, removing old kernel and then manually installing driver via instructions in your link may very well work. I think you may be correct that Lucid's fglrx packaged is dependent on the Lucid kernel.

If that fails I'll go with your recommendation, b0b138. Although I guess I should install the [kernel via this ppa?]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa")

Will let you know if I strike gold.

---

### Post by b0b138 on 2011-04-11
The backported maverick kernel is fine, no need to use the one from the kernel ppa. The how to you linked looks right, but you've got to have the headers installed for the module to compile.

---


---
title: "How to install Firefox 32-bit under Ubuntu 64-bit ?"
date: 2012-09-10
forum: General Help
---

### Post by ThrashManiac on 2012-09-10
Hi everyone, 

can someone please guide me through: 

1. remove existing installation of Firefox and all the connected plugins, like Adobe Flash  

2. building deb-package of i686-version of Firefox 

3. installation of i686 FF package and Adobe Flash of the same arch 

4. keeping installed package up to date

---

### Post by coldcritter64 on 2012-09-10
I just looked in Synaptic, if you have the multiarch-support, ia32-libs-multiarch:i386 and ia32-libs packages installed, there is a package called firefox:i386. You should be able to install firefox:i386 from there and use it. I don't think it is necessary to remove the existing one though as you indicate you plan to do. It should run as a separate application, there is also a flashplugin-installer:i386. All updating should occur as it normally would using this.

Note I haven't used the 32bit version of firefox this way so don't know how good it is. I've only ever run the 32bit version in a chroot environment (with schroot/dchroot) and only up until about 10.04, after that my method of chroot setting up became extremely difficult to get working.

Someone else with knowledge of this will need to give you some pointers, or until then you may wish to search up on multiarch and how it is used. Cheers and good luck.

---

### Post by ThrashManiac on 2012-09-10
> **coldcritter64 said:**
> I just looked in Synaptic, if you have the multiarch-support, ia32-libs-multiarch:i386 and ia32-libs packages installed, there is a package called firefox:i386. You should be able to install firefox:i386 from there and use it. I don't think it is necessary to remove the existing one though as you indicate you plan to do. It should run as a separate application, there is also a flashplugin-installer:i386. All updating should occur as it normally would using this.

Note I haven't used the 32bit version of firefox this way so don't know how good it is. I've only ever run the 32bit version in a chroot environment (with schroot/dchroot) and only up until about 10.04, after that my method of chroot setting up became extremely difficult to get working.

Someone else with knowledge of this will need to give you some pointers, or until then you may wish to search up on multiarch and how it is used. Cheers and good luck.

In you opinion, what's the best way? To add architecture (which can screw up the whole package manager) or to use chroot (which is pretty tricky to configure, afaik)?

---

### Post by coldcritter64 on 2012-09-10
The 3 packages in the first paragraph that I mentioned seem to be installed by default here (on 11.10) , I think probably the best way to go is with the package manager and multiarch, provided it is stable/usable (wait for further opinion on that - I haven't used it, but noted the firefox:i386 package in the repos).

I lost the ability to set up my chroots about or just after 10.04, I think it was when a lot of services running on the system were changed from init to upstart (or something named like that). Using chroots for running 32 bit apps is the very old way of doing things, seems like ia32libs and/or multiarch is the way things are done nowadays.

As for > (which is pretty tricky to configure, afaik)more like a sheer nightmare at times, particularly with bind mounting my home directory and storage volumes. Very nearly lost all my media and actually lost all my system [s]icons[/s] fonts on removing the chroot file system while it was still bind mounted to the 64 bit file system. Can get very dangerous to your data if you're not careful. I wouldn't even post my old instructions here because of what can happen ;).

---

### Post by ThrashManiac on 2012-09-10
> **coldcritter64 said:**
> As for more like a sheer nightmare at times, particularly with bind mounting my home directory and storage volumes. Very nearly lost all my media and actually lost all my system icons on removing the chroot file system while it was still bind mounted to the 64 bit file system. Can get very dangerous to your data if you're not careful. I wouldn't even post my old instructions here because of what can happen ;).

Thanks for the advice! :lol:

---

### Post by coldcritter64 on 2012-09-10
> **ThrashManiac said:**
> ... :lol:I wasn't doing that at the time :lolflag:, more like crying with terror, it was the quickest I've ever hit the ctrl + c key combination after using the "sudo rm" command. Too late (after about a fraction of a second), the interace fonts were all reduced to little blank rectangles. Luckily my media was saved in time. Phewww, what a relief !!! I didn't even mind having to reinstall the main OS.

One app I did run with ia32libs  (Nero 3 32bit deb installer) could at the time be installed pretty simply with the "dpkg" command and the "--force-architecture" switch. Hope the multiarch works for you, to do so with the package manager would be great.

---

### Post by ThrashManiac on 2012-09-10
I will try that today, in the evening. We'll see :-)

---

### Post by ThrashManiac on 2012-09-11
Well, I did the next thing: 

[INDENT]1. goto Synaptic and select arch i386 
2. install ia32-libs-multiarch:i386 
3. goto arch amd64 
4. install ia32-libs:amd64
5. goto arch i386 
6. install firefox:i386[/INDENT] 

I  think I did wrong, number 4 should be before 2 imho, because number 2 shown me some errors for lib sql-something. 

Adoe Flash package didn't install, so I had to do it manually: 
Adobe Flash 32-bit version (install_flash_player_11_linux.i386.tar.gz): 
[INDENT]cp libflashlayer.so ~/.mozilla/plugins
sudo cp -r usr/* /usr[/INDENT]

The only thing doesn't work: after download, when I click on "Open file location" Firefox cannot find the file manager (Nautilus 3.4.2). 

How do I fix it?

---

### Post by ThrashManiac on 2012-09-11
Setting up file manager was pretty easy (standard graphical dialog of firefox). The only question about that is - why the hell firefox doesn't use it out of the box??!

---


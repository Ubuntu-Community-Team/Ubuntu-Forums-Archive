---
title: "Installing packages without sudo access."
date: 2010-11-24
forum: General Help
---

### Post by chrisgregg on 2010-11-24
I do a lot of testing and developing on an Ubuntu machine at my university, and I don't have sudo access to the machine.  It hasn't been a problem so far because the tools I've needed have been installed.

However, I have to build OpenCV, which has a lot of dependencies, some of which (notably, libbz2-dev) aren't installed.

I have access to localtmp on the local drive, and of course my own home folder (which is on NFS).  Is there a way for me to install a local version of the tools I need using apt-get without sudo access?  If not, is there another way to install them?  I've been using CMAKE_INSTALL_PREFIX=/localtmp for some builds, but I'm not sure if this is the way to go, or if there is a better way.  Thanks!

tl;dr Is there a way to install applications locally without the ability to sudo?

---

### Post by pricetech on 2010-11-24
The short answer is ask someone at the university.  The obviously didn't give ordinary users sudo rights for a reason.

I'm sure if you have a legitimate reason to have the stuff you want to install, it will be installed for you.

---

### Post by elgordo123 on 2010-11-24
If they dont want to install all of those packages for you, maybe you can ask if they can put virtualbox on there?  Then you can run a VM and put whatever you want on it.

---

### Post by karlwbloedorn on 2010-11-24
See if u can boot into single user mode from grub if they havent locked it down.
Otherwise if you can build all of the dependencies and add em to your path (and however you add library paths) then build the thing you want id think that would work...

I will look into it more

Edit: so far one place to look is the LD_LIBRARY_PATH environment variable

---

### Post by Rubi1200 on 2010-11-24
Personally, I have to go with what pricetech already said; if you do not have sudo access, there is a good reason.

If you are involved in legitimate academic activities, ask the relevant people to install what you need.

Otherwise, you are in breach not only of the code of conduct on this forum, but also your university's regulations.

---

### Post by chrisgregg on 2010-11-24
Thanks for the responses.  I ended up figuring out how to compile what I needed by judicious use of the "prefix=" flag for cmake and make, and setting the proper LD_LIBRARY_PATH environment variables, etc.  Unfortunately, the VM is out because I'm doing research on GPGPU processing and I need access to the GPU hardware at a relatively low level.

As for not having sudo access -- it has to do with the fact that the IT folks want to be in complete control of the machines for updates, etc.  I get it, but at least I have full access to the machine on my desk.  Thanks again.

---


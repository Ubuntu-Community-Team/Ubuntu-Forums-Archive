---
title: "size of kernel sources"
date: 2012-01-04
forum: General Help
---

### Post by pindar on 2012-01-04
Hi, 

I have a graphics card which needs the 3.2 kernel to work properly. The kernel compiles fine, yet there is a thing I don't understand. When I download and expand the archive of 3.2-rc7 from kernel.org, I get a directory of about 550 MB. However, after compiling the kernel and making a deb file with this command

fakeroot make-kpkg --initrd kernel_image kernel_headers

the source directory is a whopping 7.9 G! Now I understand that the directory will be somewhat larger after compilation, but this seems a tad excessive. I have tried on a fresh install, and I've encountered the same phenomenon. Can anybody explain what's going on here? Thanks!

---

### Post by Bobhuber on 2012-01-04
> **pindar said:**
> Hi, 

I have a graphics card which needs the 3.2 kernel to work properly. The kernel compiles fine, yet there is a thing I don't understand. When I download and expand the archive of 3.2-rc7 from kernel.org, I get a directory of about 550 MB. However, after compiling the kernel and making a deb file with this command

fakeroot make-kpkg --initrd kernel_image kernel_headers

the source directory is a whopping 7.9 G! Now I understand that the directory will be somewhat larger after compilation, but this seems a tad excessive. I have tried on a fresh install, and I've encountered the same phenomenon. Can anybody explain what's going on here? Thanks!
Your most likely compiling the kernel with debug info which you can disable before the compile .
[]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

---

### Post by pindar on 2012-01-05
> **Bobhuber said:**
> Your most likely compiling the kernel with debug info which you can disable before the compile .
[]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")
Thanks a lot, I think you've nailed it. I had overlooked this sentence in the wiki: "Note that Ubuntu kernels build with debugging information on, which makes the resulting kernel modules (*.ko files) much larger than they would otherwise be."

---

### Post by xyzzyman on 2012-01-05
If you're using Oneiric there is a PPA that backports the 3.2 precise kernels to 11.10. Currently it's RC7 but should be 3.2 final in a day or two:

```
sudo apt-add-repository ppa:ptn107/ppa
sudo apt-get update
sudo apt-get upgrade

```
Or if you want to compile on your own, [https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-7.13](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-7.13) has the 3.2 tarball with all the ubuntu goodness like the ASPM power fixes that won't be in mainline until 3.3, the ureadahead patch, etc... (Note that this link will soon be changing once it's rebased to 3.2 final in the next day or so, and the page will show the change)

I've got my 3.2 kernel (With custom dsdt, compiled for core2 and my drivers in the kernel instead of modules, everything i don't need stripped out, governor defaulted to 'conservative', 1000hz as my Windows VM's work smoother, etc.) down to 9.1MB deb for linux-image down from 36MB's for defaults. initrd dropped from 19.6MB to 7.3MB's also.

---

### Post by pindar on 2012-01-05
> **xyzzyman said:**
> If you're using Oneiric there is a PPA that backports the 3.2 precise kernels to 11.10. Currently it's RC7 but should be 3.2 final in a day or two:

```
sudo apt-add-repository ppa:ptn107/ppa
sudo apt-get update
sudo apt-get upgrade

```
Or if you want to compile on your own, [https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-7.13](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-7.13) has the 3.2 tarball with all the ubuntu goodness like the ASPM power fixes that won't be in mainline until 3.3, the ureadahead patch, etc... (Note that this link will soon be changing once it's rebased to 3.2 final in the next day or so, and the page will show the change)

I've got my 3.2 kernel (With custom dsdt, compiled for core2 and my drivers in the kernel instead of modules, everything i don't need stripped out, governor defaulted to 'conservative', 1000hz as my Windows VM's work smoother, etc.) down to 9.1MB deb for linux-image down from 36MB's for defaults. initrd dropped from 19.6MB to 7.3MB's also.
Ah great, I'll wait for final then and install the backport. My setup (UEFI boot with radeon card) used to need a kernel patch until early versions of 3.2rc, but as of rc7, it's in the kernel, so this will hopefully work! Thanks a lot.

---


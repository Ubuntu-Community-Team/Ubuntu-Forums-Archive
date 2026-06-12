---
title: "Kernel 2.6.33"
date: 2010-02-10
forum: General Help
---

### Post by noops on 2010-02-10
I am curious if there is currently an easy way to install the 2.6.33 kernel in Ubuntu. I'd rather not need to recompile it from the source myself. Is there a repository that might contain this?

---

### Post by bjorkiii on 2010-02-10
Not being funny but if you have to ask how to do this you shouldnt be doing it :p

---

### Post by adam814 on 2010-02-10
The short answer is yes you can.  You can download a kernel package here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

The complete answer is maybe.  Those kernels don't have all the Ubuntu patches, so you can't use them if you need AppArmor or the nfs-kernel-server.  They're also compiled with a 100MHz timer frequency (optimized for servers).  Of course they also aren't officially supported or recommended for production environments, especially since the earliest 2.6.33 could make it into an Ubuntu release is for 10.10.

I'd personally wait *at least* until 2.6.33 has a stable release.  Release Candidate kernels sometimes have major bugs up to and including corrupting your filesystems, especially if you're using one that isn't very mature in the development cycle (like btrfs now or ext4 a few kernels back).

So while you can do it, it may or may not be acceptable for your environment and YMMV.  Good Luck.

---

### Post by noops on 2010-02-10
Thank you for an actual answer. Bjorks answer is, unfortunately, what I have come to expect from the linux community.

---

### Post by n0dix on 2010-02-10
If you want experimenting, go ahead, but you should have a minor knowledge in the case broke the system.

---

### Post by Richard1979 on 2010-02-10
I'd advise backing up /boot just in case.
If it does go wrong, I expect you know how to use the Live CD to mount your disks and reverse the operation.

---

### Post by noops on 2010-02-11
I ended up compiling from source instead of using the packages mentioned above.

If anyone else ends up compiling 2.6.33 be aware that some things have changed. You would need the kernel-package 12.032 installed or the build will fail. You can find this in the lucid package repository.

The make-kpkg included in Ubuntu 9.10 will not compile the 2.6.33 kernel.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=561569]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=561569")

---

### Post by n0dix on 2010-02-11
> **noops said:**
> I ended up compiling from source instead of using the packages mentioned above.

If anyone else ends up compiling 2.6.33 be aware that some things have changed. You would need the kernel-package 12.032 installed or the build will fail. You can find this in the lucid package repository.

The make-kpkg included in Ubuntu 9.10 will not compile the 2.6.33 kernel.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=561569]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=561569")

It's good to know. Post any bug, if is have it.

---

### Post by Satoru-san on 2010-02-11
Just curious why do you feel you need to upgrade your kernel?

I am still using the .31 kernel and I probably wont upgrade it untill emerge breaks. Haveing a newer kernel just means that it supports the newest hardware, if you have an old machine, it doesnt matter if you have an old kernel.

---

### Post by noops on 2010-02-11
> **Satoru-san said:**
> Just curious why do you feel you need to upgrade your kernel?

I am still using the .31 kernel and I probably wont upgrade it untill emerge breaks. Haveing a newer kernel just means that it supports the newest hardware, if you have an old machine, it doesnt matter if you have an old kernel.Development.

---


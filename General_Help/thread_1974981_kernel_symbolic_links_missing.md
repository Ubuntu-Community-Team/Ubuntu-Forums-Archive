---
title: "kernel symbolic links missing"
date: 2012-05-06
forum: General Help
---

### Post by Binary-Synapse on 2012-05-06
Hello.
I'm using Ubuntu 11.10 and I'm trying to compile kernel 3.4-rc5 to support some new hardware on a recent netbook I got.
 
Compile process:
cd /usr/src/linux-3.4-rc5/
sudo make nconfig
sudo make-kpkg clean
sudo CONCURRENCY_LEVEL=4 fakeroot make-kpkg --initrd --revision=3.4.custom kernel_image kernel_headers
 
Note: I used sudo because I was inside /usr/src/, otherwise I think I should not use it, since the compile process does not need too much privileges, right?
 
After the 3 hour process terminates, when I try to install the kernel, I get:
```

etc...
 
Hmm. There is a symbolic link /lib/modules/3.4.0-rc5/build
However, I can not read it: No such file or directory
Therefore, I am deleting /lib/modules/3.4.0-rc5/build
 
 
Hmm. The package shipped with a symbolic link /lib/modules/3.4.0-rc5/source
However, I can not read the target: No such file or directory
Therefore, I am deleting /lib/modules/3.4.0-rc5/source
 
etc.........
```
 
Why is that happening?
Is it serious? How can I correct it?
 
And also... should I just compile the kernel in my home directory? That way I wouldn't need sudo or root privileges, right? Would it be safer?
 
Note: The new compiled kernel boots perfectly and supports the new hardware, but I was just curious about the symbolic links section.
 
Can someone help?
 
Thank you.

---

### Post by Binary-Synapse on 2012-05-13
No one has a clue?
 
Thank you.

---

### Post by bodhi.zazen on 2012-05-13
You first need to configure your kernel

```
make menuconfig
```

Then compile

```
make -j5
```

Then install, either manually or automatically

```
make install
```

See [http://bodhizazen.net/Tutorials/kernel](http://bodhizazen.net/Tutorials/kernel)

IMO making a .deb for your kernel is a bit over kill.

---

### Post by Binary-Synapse on 2012-05-13
Hello bodhi.zazen
 
 
My compile process was:
cd /usr/src/linux-3.4-rc5/
sudo make nconfig
sudo make-kpkg clean
sudo CONCURRENCY_LEVEL=4 fakeroot make-kpkg --initrd --revision=3.4.custom kernel_image kernel_headers
 
Making the deb files was a necessary step since the kernel and the headers will be distributed among many different remote computers (for many different clients).
 
When I compile the kernel for myself only, I sometimes take your suggestion (which is in fact the same as the _official kernel sources instruction file_).
 
I think the only problem with that approach is distribution amongst different computers, right? And I really need that, in this case.
But please correct me if I'm wrong...
 
Thank you

---

### Post by bodhi.zazen on 2012-05-13
I am not sure why you are having a problem.

A .deb would be ideal obviously.

If that fails, you could distribute the compiled kernel and modules as a tar ball.

You just package up the kernel, config, and system map from /boot , include the modules (/usr/lib/modules/3.4.0-rc5).

You then extract the tar ball and update grub. Not really that much more complex then a .deb (two commands, extract the tar ball and update grub).

---


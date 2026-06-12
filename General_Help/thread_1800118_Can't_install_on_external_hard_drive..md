---
title: "Can't install on external hard drive."
date: 2011-07-08
forum: General Help
---

### Post by expunk on 2011-07-08
So I just finished installing Ubuntu on my 500 GB HDD. Everything works fine. 
I am able to boot into and use Ubuntu. However, when I booted into Windows, my HDD wasn't getting detected.

I want to be able to access my HDD in Windows as well as run Ubuntu from it. How do I go about this? 

Thanks in advance.

---

### Post by _Narcisse_ on 2011-07-08
Hello expunk, and welcome to the forums. :)

From your title I get that you installed Ubuntu on an external HDD. If that's the case, I've never done this so I can't be of much help.
However, I don't know which install method you used but I think Ubuntu 11.04 uses the Ext4 filesystem by default, which is not readable under Windows without special drivers. Such drivers can be found [here]("http://www.ext2fsd.com/") or [here]("http://www.fs-driver.org/") for example. But be careful about stability and compatibility. A quick Google search might bring some more options.

That being said, I don't know what kind of setup you want, but it might be a better idea to create a separate partition (for your /home folder for example) on your HDD using the FAT filesystem, which is compatible with both Ubuntu and Windows.

Feel free to clarify and I'll try to help.

Cheers

---

### Post by lmarmisa on 2011-07-08
Windows is not able to read the Ubuntu file-systems ext3/etx4. So, if during the installation you have selected the full external drive for Ubuntu, Windows will be not able to read it. You do not need 500 Gbytes for Ubuntu. 20-50 Gbytes would be enough for the Ubuntu root partition. You will need a swap partition with the same size of your RAM too. Finally I recommend to define a huge NTFS partition in your external hard drive. The size of this NTFS partition would be about 450 Gbytes.

---

### Post by wildmanne39 on 2011-07-08
> **expunk said:**
> So I just finished installing Ubuntu on my 500 GB HDD. Everything works fine. 
I am able to boot into and use Ubuntu. However, when I booted into Windows, my HDD wasn't getting detected.

I want to be able to access my HDD in Windows as well as run Ubuntu from it. How do I go about this? 

Thanks in advance.
Hi, here is a link so windows can read ubuntu file system, I have never used it but I have read that it works.
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---


---
title: "Windows Partition"
date: 2011-08-02
forum: General Help
---

### Post by Fustigate on 2011-08-02
Hi. 

I installed Ubuntu on the same drive as Windows, so I got both Windows and Ubuntu.

When I'm on Ubuntu  I'd like to see my documents from Windows.
When I click Windows 7 (My Windows drive) I get some files which aren't what I need, see attachment.  I've been trying this for a while, I'm new to Ubuntu and I'm finding out some things. Thanks in advance.

---

### Post by Fustigate on 2011-08-02
Anyone?

---

### Post by dino99 on 2011-08-02
to make a real install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)


ntfsprogs & ntfs-3g on ubuntu give you access to ntfs partitions/files

sudo synaptic

---

### Post by Mark Phelps on 2011-08-02
> **Fustigate said:**
> Anyone?

Either you installed inside an MS Windows partition (using Wubi) or you create an empty space and install to a partition in that space using the Ubuntu installer.

HOW you then go about seeing your Win7 partition depends critically on WHICH version of install you did.

So, which was it?

---

### Post by Rubi1200 on 2011-08-02
Hi and welcome to the forums Fustigate :-)

You can find your files like this:

The Windows partition where you installed Wubi is available as /host  within Ubuntu (Places > Computer > File System > Host) All the other partitions will be available under Places > Removable Media 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Good luck and enjoy Ubuntu!

---


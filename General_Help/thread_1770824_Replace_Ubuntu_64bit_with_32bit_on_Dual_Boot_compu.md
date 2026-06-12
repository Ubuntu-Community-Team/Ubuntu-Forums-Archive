---
title: "Replace Ubuntu 64bit with 32bit on Dual Boot computer"
date: 2011-05-29
forum: General Help
---

### Post by 8jwong14 on 2011-05-29
Hi.  I helped my friend install Ubuntu on his computer.  Now he dual boots Ubuntu 64 bit and Windows 7.  However, he has lag with 64 bit so I want to install 32 bit Ubuntu instead.  How should I go about this?  Should I delete the Ubuntu partition from Windows 7 then install Ubuntu 32 bit?

---

### Post by jocko on 2011-05-29
> **8jwong14 said:**
> Hi.  I helped my friend install Ubuntu on his computer.  Now he dual boots Ubuntu 64 bit and Windows 7.  However, he has lag with 64 bit so I want to install 32 bit Ubuntu instead.  How should I go about this?  Should I delete the Ubuntu partition from Windows 7 then install Ubuntu 32 bit?
That should work, or just format the partition from the ubuntu installer.
But why do you think replacing 64 bit with 32 bit will do any good? On 64 bit hardware, a 64 bit OS will perform better than a 32 bit one.

---

### Post by oldfred on 2011-05-29
As a general thing do not use windows to edit Linux partitions. Some windows tools have been know to modify the partition table incorrectly creating problems. Use windows tools for windows and Linux tools for Linux.

But you can just use manual install ("Something Else" in Natty) and just choose to reformat the existing partition and set it as / (root). It will find swap automatically. If you have a separate /home choose it but be sure NOT to FORMAT it.

But I have to agree, the 64 bit will be faster for just about everything if you have over 2GB of RAM. You may just need some configuration settings. Whether the 32bit defaults to a better setting is not likely but possible.

Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Essentially says if you can use the 64bit kernel you should.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
Advantages and Disadvantages of 64bit. (Plus install Guides) from 2008
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)
Benchmarks Performance on 9.04
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)
Bug report on Text reads "not recommended" for 64-bit
[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

---

### Post by jerome1232 on 2011-05-29
> **jocko said:**
> 
But why do you think replacing 64 bit with 32 bit will do any good? On 64 bit hardware, a 64 bit OS will perform better than a 32 bit one.

Reiterating, I believe you should look elsewhere for his slowness, what are the specs of the computer? What hardware does it have (particularly the video card and ram)
Also are the video drivers properly installed and working? Is this a true dual boot or Wubi install?

---

### Post by 8jwong14 on 2011-05-29
> **jerome1232 said:**
> Reiterating, I believe you should look elsewhere for his slowness, what are the specs of the computer? What hardware does it have (particularly the video card and ram)
Also are the video drivers properly installed and working? Is this a true dual boot or Wubi install?
On my friends computer, using 64 bit causes lag while using 32 bit fixes it.  HE has 4 GB of memory.

---

### Post by linuxinstalledfromhdd on 2011-05-29
I love 32-bit. That's what I use, and I installed the PAE kernel to expand my RAM memory sticks too.  That's important to install as well.

---


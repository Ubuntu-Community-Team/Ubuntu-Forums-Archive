---
title: "Possible to copy physical hard drive to virtual?"
date: 2012-01-20
forum: General Help
---

### Post by kemtnbkr on 2012-01-20
Hi, short background story:

My friend just bought a '94 Camaro as a project; the guy he bought it from gave him a laptop full of tuning software, but it is older.  The battery has basically no life, and it is on an IDE hard drive.

I had a IDE/ USB converter laying around, and I used dd to copy the entire hard drive to my laptop.  

So, would it be at all possible to boot this hard drive image using VirtualBox?  (WinXP is the OS on the laptop).  I'm guessing it's not easy to do, because I couldn't find anything about it with Google.  The desired partition is the first; there are also a few linux partitions on the laptop which don't have any necessary software, so I also copied over only the first partition (I'm returning the HD itself tomorrow, so I figured I'd do both to make sure).

I already tried just saving the image as a .vhd and .vdi, but VirtualBox wouldn't accept either of them as a pre-existing VHD (kinda thought that wouldn't work, but gave it a shot anyways).

Any suggestions would be appreciated; I have basically no experience with virtual machines. Thanks in advance.

---

### Post by dcstar on 2012-01-20
> **kemtnbkr said:**
> 
..........
Any suggestions would be appreciated; I have basically no experience with virtual machines. Thanks in advance.

Go to the Virtualization forum and read the sticky posts at the top for pointers.

---

### Post by C.S.Cameron on 2012-01-20
An XP install will only work on the motherboard it was first installed on.
I don't think it will run on another computer,  physical or virtual.

There are programs that will copy installed programs from one XP install to another.

---

### Post by kemtnbkr on 2012-01-20
> **C.S.Cameron said:**
> An XP install will only work on the motherboard it was first installed on.

Good point, I guess I didn't think that through very thoroughly :o

I keep forgetting about all the stupid limitations of paid software, its been a while since I've used windows.  

But, I guess that answers my question, so I'll mark the thread as solved.  Thanks to both for your speedy responses!

---

### Post by haqking on 2012-01-20
clone your physical with clonezilla and then clone it into the virtual machine.

Job Done.

Cheers

---

### Post by dcstar on 2012-01-20
> **C.S.Cameron said:**
> An XP install will only work on the motherboard it was first installed on.


Rubbish, the utilities that places like VMware provide take the different hardware environment into account, and there are instructions available on the web showing how you set up a "vanilla" hardware profile to be able to move existing Windows installations to different platforms.

This sort of thing has been done thousands of times. The threads in the Virtualization forum go into more detail.

---

### Post by C.S.Cameron on 2012-01-20
> **dcstar said:**
> Rubbish, the utilities that places like VMware provide take the different hardware environment into account, and there are instructions available on the web showing how you set up a "vanilla" hardware profile to be able to move existing Windows installations to different platforms.

This sort of thing has been done thousands of times. The threads in the Virtualization forum go into more detail.

Thanks David:
Sounds like I stand corrected.
To avoid needing to browse the 120 posts you refer to:

[http://ubuntuforums.org/showpost.php?p=6122463&postcount=6](http://ubuntuforums.org/showpost.php?p=6122463&postcount=6)

---

### Post by kemtnbkr on 2012-01-21
Thanks C.S.Cameron for the link, I don't have time to try it out, but I'll try it out soon and see if I can get it working.

Looks like that should cover it... I'll post if I encounter errors, but if there's a thread that covers it, I should be able to follow along well enough.

---


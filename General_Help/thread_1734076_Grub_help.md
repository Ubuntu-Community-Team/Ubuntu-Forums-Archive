---
title: "Grub help"
date: 2011-04-19
forum: General Help
---

### Post by r0llingthund on 2011-04-19
So I had this Idea that I would be able to dual boot in my laptop (I know very innovative <-- that was sarcasm). But instead of partitioning the hard drive in my laptop I have a external Hard drive (meaning 2 hard drives). I would have one OS on my laptop's HDD and another on my external HDD.

So is there a way to have grub let me choose from what Hard Drive I want to boot from. I am thinking I can not, but I do hope I am wrong.

---

### Post by grahammechanical on 2011-04-19
I am no expert but I have seen many replies to this question and the answer is yes. Are we to assume that Ubuntu will be on the external hard drive? If so then I think that you must make sure that Grub is installed on the Internal drive otherwise you will not be able to boot the OS on that internal drive if you unplug the external drive. The install process of Ubuntu will also install Grub, which in turn will search for any other OS because this is what it is designed to do. It will then create a menu which you will see at boot time and you will have about 10 seconds to choose which OS to load.

Regards.

P.S. Hard drives or partitions they are all the same to Linux. They are all called partitions.

---

### Post by lmarmisa on 2011-04-19
I do not know if your plan is to install a dual boot system with Windows and Ubuntu or two Linux distros. I think the answer to your question would be different depending on the case.

---


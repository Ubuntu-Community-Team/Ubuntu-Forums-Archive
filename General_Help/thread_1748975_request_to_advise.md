---
title: "request to advise"
date: 2011-05-04
forum: General Help
---

### Post by grahammechanical on 2011-05-04
The question is this: Is the CPU 64bit? If it is not then you must stay with a 32bit operating system. A 64bit OS will only work on a 64bit CPU. Whereas, a 32bit OS will work on both 32bit and 64bit CPUs. This is why the website recommends the 32bit OS install. That way nobody complains that the OS does not work and that it broke their computer.

If you have a 64bit CPU then you can install the 64bit OS. I have. It works great.

Backup your data first. Do you have a separate /home partition or a /home folder in the one Ubuntu partition. If  you do not have a separate /home partition then there is a lot more work to change from 32bit to 64bit than simply reinstalling  the OS.

Regards.

---

### Post by grahammechanical on 2011-05-06
I have tried going to the Dell website to find out what CPU is used in the optiplex GX520 but I have been unable to find out that information.

Do you have a user guide for the computer? Does it give you some specifications? Do you see any information about the CPU? If you know the type of CPU then you can search the maker's website for information about that CPU.

For example, my CPU is an Intel Core 2 Duo. On the website I find a link that tells me that all Core 2 Duo CPUs are have 64bit architecture. You need to find out some information like that.

Computer processors work by carrying out instructions that are in digital format (a sequence of zeros and ones). Each of these zeros and ones are called a bit. A group of bits is called a word. The width of each word, the number of bits in each group is limited by the design of the Central Processing Unit (CPU). Early CPUs were 8bit. They could compute instructions one at a time that were 8 bits wide or had a total 8 bits of information in the form of zeros and ones.

Over time CPUs have been developed to use 16bit instructions, 32bit and now 64bit instructions. The wider the words, the greater the information that could be processed in the same time. So, a 64bit CPU would process information faster than a 32bit CPU even though both were running at the same speed.

For years it did not matter much whether the CPU was 32bit or 64bit because we only had 32bit operating systems to use on them. That has changed. Microsoft and the Linux developers have produced 64bit operating systems. So, before installing a 64bit operating system a home user needs to know if the CPU is 64bit or 32bit.

Do you have a Windows operating system installed? Is it described as a 64bit operating system? If so then you can install 64bit Ubuntu.

I hope this helps. To fully understand about CPUs and bits a person would need to do a lot more research than I can remember in this little review. I am sorry.

Regards.

---

### Post by Thewhistlingwind on 2011-05-07
More practical advice is that to get specs on your hardware (particularly your CPU architecture.) you can try the following:

1. Hardware listing in system monitor
2. cat /proc/cpuinfo
3. Labels and documentation that came with your computer. (On laptops from the vista era, they commonly advertise their CPU architecture on the casing with a sticker.)

You did say you were running ubuntu already, right?

Regardless, you can always just burn a CD and stick it in. AFAIK it won't let you boot a live 64 bit install without a 64 bit processor. 

Good luck.

---

### Post by mcduck on 2011-05-10
According to Wikipedia, [OptiPlex GX520]("http://en.wikipedia.org/wiki/Dell_OptiPlex") comes with a Pentium 4, Pentium D or Celeron processor, none of which are 64-bit processors. So go for the 32-bit Ubuntu.

---


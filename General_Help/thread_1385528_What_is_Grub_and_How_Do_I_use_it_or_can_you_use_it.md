---
title: "What is Grub and How Do I use it or can you use it?"
date: 2010-01-19
forum: General Help
---

### Post by tgaston34 on 2010-01-19
Hi I am a newbie to Ubuntu Linux and I like the operating system, but need some help and was told to look at Grub and I have no clue what Grub is or what it does. I installed Ubuntu as a dual boot with Vista and it installed version 14 then a week or so later updated to 17. I don't think I needed them both refrenced in my boot menu I would like to use the current one and delete the first one. How do I do this? and Where do I go to learn how to do this so I have clear and understandable directions? Thanks for your help Tony](*,)

---

### Post by synapsys on 2010-01-19
Grub is a 'bootloader' It is best explained here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by JiuJitsu500 on 2010-01-19
GRUB is your bootloader for Ubuntu, much like Windows BOOT.INI or NTLDR. The old kernel versions (14 as you're saying, 17 is current) love to stick around the menu there.

[http://ubuntuforums.org/showthread.php?t=1349693](http://ubuntuforums.org/showthread.php?t=1349693)

Try here, it's the terminal's craziness, but it works. Did you use Wubi to dual-bot by the way? I tried it on vista and 7 without luck at first....

Oh, and I tink bashing your face into brick walls is not very good for your health... but I'm not a doctor :o

---

### Post by stoneage on 2010-01-19
Those are kernel versions. It is normally a good idea to keep at least one spare. If an update breaks something you could boot from the previous kernel version and repair the problem.

---

### Post by drs305 on 2010-01-19
Tgaston34,

Welcome to Ubuntu and the Ubuntu forums.

Often users keep at least two kernels available on the Grub menu - the most recent one, and an older one which they know has worked in the past. This allows the user to "fall back" to a previous kernel should the new one not get along with something in the system.

While two kernels is often recommended, if newer kernels are released you will see this list grow, and it's not necessary to keep them all. For Grub legacy (0.97) there was an excellent GUI tool for hiding older kernels. For Grub 2 (1.97~beta or later) StartUp-Manager doesn't work quite as well. However, in the guide on SUM there is a section on how to remove older kernels.

You can read about it in the following link; near the end is a section "Removing Older Kernels". The short story is you can remove them via Synaptic or a nice tool called Ubuntu Tweak. Both methods are described.
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---


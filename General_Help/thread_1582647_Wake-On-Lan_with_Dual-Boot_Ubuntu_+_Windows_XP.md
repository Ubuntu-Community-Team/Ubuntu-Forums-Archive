---
title: "Wake-On-Lan with Dual-Boot Ubuntu + Windows XP"
date: 2010-09-26
forum: General Help
---

### Post by pseudosudo on 2010-09-26
Hello everyone!

I'm in a unique situation here and I've decided to try and find a solution from the community rather than continue searching for the answer on Google. I've been searching for over 3 hours and I haven't found any relevant information.

Here's the situation:

I have ubuntu and Windows XP set up for dual boot on my system. Both Operating systems are working fine. My system is set up to Wake-On-Lan because I'm not usually at home so I RDP into my Windows XP OS from the internet after I wake it up. 

What I want to be able to do is to select which operating system I want to use remotely. In other words, I want to be able switch between ubuntu and Windows XP through a remote connection. I know that you can not switch operating systems remotely when your system is booting so I figured the best way to do this is by changing the default OS in the boot menu.

The best method I could think of for my situation is to somehow get ubuntu on the Windows XP Bootloader, use the Windows XP Bootloader instead of Grub2, then when I want to alternate operating systems I would just need to edit the boot.ini which is accessible from both ubuntu and Windows.

Problem is that I can't find any information on how to do that neither. However, there are many threads saying how the Windows XP Bootloader can't load ubuntu.

So I'm stuck here and I would really appreciate it if someone could help me out.
Thanks in advance!

---

### Post by zzztownsend on 2010-09-28
I'm afraid I have no idea how to solve the problem directly, but you could easily run XP virtualised inside ubuntu, which may give you the functionality you want. 

I suggest Virtualbox.org 'Personal Use & Evaluation (PUEL)' version, which supports RDP if you like using that. Can be run headless and doesn't seem to use too many resources provided you've got a decent amount of RAM

---

### Post by pseudosudo on 2010-09-28
Hey,

Thanks for the suggestion zzztownsend. Sounds like a great program and I would definitely be using it if my computer wasn't so old. My computer is only a P4 2.0Ghz with 512 MB of RAM and I doubt these specs would be enough to run a virtual environment. Correct me if I'm wrong. Thanks for the suggestion though!

Are there anymore ideas out there??

---


---
title: "Which distro for i7"
date: 2010-09-14
forum: General Help
---

### Post by susanto on 2010-09-14
I would like to install ubuntu on my i7 system.
The machine will be used as workstation, not as server.
I read that Ubuntu-64 desktop is not suggested for daily use.
I am confused, is the system is not stable for daily use?
Or ubuntu is not suitable for i7?
If not, can anybody suggested which distro is better?
The machine is mostly used for heavy computation, 
and I need X.
Can anybody help?
Thanks.

---

### Post by Jesus_Valdez on 2010-09-14
I have been using Ubuntu-64 for my laptop for years and I have never had a problem.

Whoever tell you that is not stable is lying.

---

### Post by uRock on 2010-09-14
[s]It is stable, as long as you like glitchy flash and programs that have to be run in 32bit vboxes.[/s]

For everyday use 64bit will do. Just don't expect much.

---

### Post by Jesus_Valdez on 2010-09-14
Probably I'm doing something wrong because I don't have problems with flash.

---

### Post by uRock on 2010-09-14
> **Jesus_Valdez said:**
> Probably I'm doing something wrong because I don't have problems with flash.
You are one of the lucky ones. I tried several methods listed on the forums and they all failed. As for 32bit, runs just as fast with no problems and I don't have to run vboxes for simple applications anymore. All is good now. 

OP, give 64bit a shot, if it just doesn't work, then falling back to 32bit is easy.

BTW, I am not sure how much RAM you have, but with the 32bit PAE kernel installed, you can use up to 2GB per process.

---

### Post by Jesus_Valdez on 2010-09-14
What do you mean by "32 bit vboxes#?

---

### Post by uRock on 2010-09-14
> **Jesus_Valdez said:**
> What do you mean by "32 bit vboxes#?Self answering question? VBoxes with 32bit ubuntu.

---

### Post by Jesus_Valdez on 2010-09-14
I'm intrigued, what software require that?

---

### Post by uRock on 2010-09-14
> **Jesus_Valdez said:**
> I'm intrigued, what software require that?
Feel free to scan my posting history as they most likely do not apply to the OP.

---

### Post by susanto on 2010-09-15
I am going to use i7 with 6G RAM.
I am just confused with recommendation on ubuntu download page,
64bit ubuntu desktop is not for everyday use. While installing 
server is probably less useful to me. 
Thanks for the comment, I am going to give it ago.

---

### Post by SavageWolf on 2010-09-15
I've been using 64bit Ubuntu for a while now, and I am a flash gamer (or whatever). I installed flashplugin-installer (or whatever), which seems to have installed "npviewer.bin", it seems to work well bar the occasional crash and high CPU usage.

But the Load Average Average (?) seems to have dropped from ~4-5 to less than 2 (quad core), and I would recommend it!

---

### Post by 98cwitr on 2010-09-15
> **Jesus_Valdez said:**
> I'm intrigued, what software require that?

he's talking about running virtual machines from VirtualBox (virtualbox.org)...you'd want a lot of ram depending on your needs and quantity of vm's you set up. Otherwise, even 4GB of ram is completely overkill for Ubuntu in a home/office environment.

If you've got 6GB and a 32-bit OS, use the other two as a RAMDisk...offload all your cache and /tmp dir into it everytime :)

---

### Post by Irony on 2010-09-15
64 bit works fine on i5 and is stable.

I also run virtualbox for Windows 7, I run wine (the latest version handles 32 and 64 bit apps).

I have 2GB of ram.

---

### Post by syncmasterpt on 2010-09-15
> **susanto said:**
> I am going to use i7 with 6G RAM.
I am just confused with recommendation on ubuntu download page,
64bit ubuntu desktop is not for everyday use. While installing 
server is probably less useful to me. 
Thanks for the comment, I am going to give it ago.

I' using the exact same setup, i7 920, 6GB of RAM with Kubuntu 10.04. No issues.

Regarding flash, I'm using the 64bit beta that is no longer available, but it works fine.

---

### Post by quadproc on 2010-09-15
> **syncmasterpt said:**
> I' using the exact same setup, i7 920, 6GB of RAM with Kubuntu 10.04. No issues.
I am doing something very similar except with Ubuntu and a 950 processor.  There are a couple of minor issues that I have found: 10.04 doesn't automount floppies and the mplayer program errors out when attempting to play a DVD, but I have not seen any major problems.> 
Regarding flash, I'm using the 64bit beta that is no longer available, but it works fine.I'm running the latest flash that I could get from Adobe and I haven't seen any problems yet.

I believe that the wording on the "Get Ubuntu" page is old; there *were* a lot of issues regarding 64 bit software but almost all of them have been resolved by now.

quadproc

---


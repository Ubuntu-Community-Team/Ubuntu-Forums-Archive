---
title: "System Hangs"
date: 2006-02-17
forum: General Help
---

### Post by mishranurag on 2006-02-17
Hi!
Since yesterday, my system started hanging. When it hangs , it does nothing and I have to force restart. 

Although it hangs at other times, it is is very consistent with amarok. Whenever I open amarok, the amarok window comes up and everything stops. I tried to remove it using terminal, the system hung in between and I had to force restart. 

I thought I might have screwed the system somehow while playing with it, so I installed ubuntu-desktop and kubuntu-desktop again (I earlier had removed them to remove some programs I didn't need), updated them, upgraded them, installed amarok again (although terminal hung earlier, amarok got removed, completely or partially, I don't know). 

If I use amarok, again the system hangs completely. Any help would be greatly appreciated.

The other times when system hung when I was trying to remove some stuff (k stuff) using synaptic. As soon as  I selected some stuff, system hung. Once, when I used alt-tab, the system hung. In the last few days, I just had installed the stupid pronview which never worked.

Anurag
I use UBUNTU 5.10 with latest kernel on a ix86 machine. Since yesterday, when start ubuntu, it says kubuntu.

---

### Post by Robgould on 2006-02-17
Are you using Dapper?  My computer started doing the same thing yesterday, but I am using dapper.

---

### Post by mishranurag on 2006-02-17
Breezy.

---

### Post by Robgould on 2006-02-17
coincidence?

---

### Post by mishranurag on 2006-02-17
more than 10 times??
[quote=Robgould]coincidence?[/quote]

---

### Post by mishranurag on 2006-02-19
Hi!

I realized later that it's not only amarok which hangs my system, but sometimes synaptic too. I am extremely confused because everytime my systems hangs I have to force restart. I have atleast done that 20-30 times since yestearday. Please help.

When I restart the system, it doesn't load the greeter theme and gives an error about not being able to find them.

Anurag

---

### Post by mishranurag on 2006-02-19
This is extremely frustrating. either no one know how to solve my problem or no one answers my post. I don know what's the issue. I heard this forum helps everybody, but not me, I guess.
This forum was the only reason for me to stay with UBUNTU. Now UBUNTU hangs and nobody is there to help me.
HUH

---

### Post by akniss on 2006-02-19
I'm pretty new to the whole linux thing, but I had a similar problem with evolution a couple weeks ago.  everytime I started evo, i would have to kill the process, which sometimes wouldn't work and I would have to force restart.  I tried uninstalling evolution with synaptic and apt-get remove, but after a reinstall things would be the same way.  My theory (and the real hackers can correct me if i'm wrong) is that removing programs with synaptic or apt don't completely remove some config files which are causing the problems.  I don't remember how exactly i got through the problem with evolution.

Have you tried going to the terminal and typing 
```
sudo apt-get remove amarok
```
Maybe you will have better luck with the cli instead of synaptic.

---

### Post by mishranurag on 2006-02-19
Thanks Akniss!

I tried this thing with CLI, but strangely it would hang even then too. I did that in recovery mode, but I need amarok. When I reinstalled it did the same to me. Synaptic would hang sometimes randomly too. SO I guess problem is something serious.

Anurag

[quote=akniss]I'm pretty new to the whole linux thing, but I had a similar problem with evolution a couple weeks ago.  everytime I started evo, i would have to kill the process, which sometimes wouldn't work and I would have to force restart.  I tried uninstalling evolution with synaptic and apt-get remove, but after a reinstall things would be the same way.  My theory (and the real hackers can correct me if i'm wrong) is that removing programs with synaptic or apt don't completely remove some config files which are causing the problems.  I don't remember how exactly i got through the problem with evolution.

Have you tried going to the terminal and typing 
```
sudo apt-get remove amarok
``` Maybe you will have better luck with the cli instead of synaptic.[/quote]

---

### Post by mishranurag on 2006-02-20
Well!
Although nobody replied to me :(, I figured out that the reason of crash was the incorrectly configured video card. I reconfigured it and the system is working fine now.
Anurag

---


---
title: "lxdm-binary is killing my cpu"
date: 2011-11-19
forum: General Help
---

### Post by tanoloco on 2011-11-19
I recently installed lubuntu oneiric .. and I've not done so many things with it, so I can say it's almost like a fresh installation.

However today after a dist-upgrade I had my cpu killed running always at maximum. I rebooted and had same scenario, so I ran top and noticed lxdm-binary is always running at 95%.

I googled and found no mention about that. Am I the only one having this behaviour? What can I do? Killing it shut my desktop down.

Thanks in advance for any suggestion!

---

### Post by marinara on 2011-11-19
I found this:
[http://www.ale.org/pipermail/ale/2011-February/126826.html](http://www.ale.org/pipermail/ale/2011-February/126826.html)

But I don't think it will help you.

I've also had serious problems after installing packages.  Not a solution in sight, either.

---

### Post by Rodney9 on 2011-11-20
I don't have answer sorry but may I suggest you add this link to the 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

so other Lubuntu users will see it and they may be able to help.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by SteveDee on 2011-11-20
> **tanoloco said:**
> ...after a dist-upgrade I had my cpu killed running always at maximum. I rebooted and had same scenario, so I ran top and noticed lxdm-binary is always running at 95%....

This is an interesting problem. I took a look at my laptop running 11.04, lxdm-binary is also listed in the task manager after I log on. But its not drawing any load on the cpu.

On a test machine with 11.10 recently installed (not upgraded) lxdm-binary does not appear in task manager after logon. I've just added a second user and applied the latest updates, and its still OK.

My 11.04 laptop has lots of additional apps installed. So I think your problem may be related to something you installed after installing 11.10.

If you use Synaptic to install new apps you will be able to go to the History menu and backtrack (by removing apps one at a time), and maybe find the cause.

---


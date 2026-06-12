---
title: "recent xorg update turns my laptop into a slug - how to revert update?"
date: 2006-05-07
forum: General Help
---

### Post by the0b0rm on 2006-05-07
Hi,

I have an HP NX6125 laptop that was quite happily running Ubuntu until this evening (intallation /was/ a bit quirky, but I managed eventually).

Yesterday morning I installed the suggested updates to (IIRC) kernel and Xorg just before switching off, and this evening I switched on my laptop to find it extremely slow (starting an xterm takes 5 minutes, typing a letter in ittakes ~ 5 seconds)

I tried booting the old kernel, but that didn't work, so I suspect it's the last Xorg update that's to blame.

I'm quite new to Ubuntu (know my way around *BSD and Solaris though), and found ubuntu significantly different from anything I've used before (from a configuration point of view). As a consequence I'm at a loss of how to solve this.

Is there any way to revert this Xorg update and get back a working system? Preferably without starting the synaptic package manager because that takes >20 minutes to start (I'm still waiting).

Any other suggestions?

with kind regards,

Theo.

---

### Post by Ramses de Norre on 2006-05-07
Have you tried reinstalling your graphics drivers? This is necessary with a lot of drivers whenever you install a kernel upgrade (and there came one along with the xorg updates).

---

### Post by the0b0rm on 2006-05-07
I'll give that a try, though that was one of the quircks that made initial installation rather nasty.

As I mentioned, I reverted to the old kernel, so I guess what you're saying is that isn't enough to get the old (installed) driver working again...

cheers, Theo

---

### Post by the0b0rm on 2006-05-08
[QUOTE=Ramses de Norre]Have you tried reinstalling your graphics drivers? This is necessary with a lot of drivers whenever you install a kernel upgrade (and there came one along with the xorg updates).[/QUOTE]

That didn't work, but I found out a little bit more.

What has happened was that the kernel update /also/ updated grub's menu.lst, dropping the (for my system essential) "noapic" option for both the new and the old kernel. Putting the "noapic" back in solved the sluggishness isue.

Now I'm only stuck with a few minor issues...

thanks,

Theo

---


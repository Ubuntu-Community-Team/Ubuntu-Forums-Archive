---
title: "virtual box inforamtion"
date: 2009-08-20
forum: General Help
---

### Post by abhilashm86 on 2009-08-20
i've installed sun virtualbox to run windows for using Visual studio for project..........
i've 2.5 GB ram, so i assigned 1 GB ram to virtual machine, so if i boot ubuntu(host machine), initially 1 GB will be given to virtualbox or only if i start my virtual machine it'll assign 1 GB, 
if i assign even more GB of ram to virtual machine, does it affect ubuntu host?

---

### Post by kanikilu on 2009-08-20
It will only use the memory once you start the virtual machine. And yes, of course as you give more RAM to the guest, the host will have less available, so depending on what you do, it could have a negative affect.

I suppose the worst that could happen would be that the host would need more memory than is available and go into swap...

---

### Post by abhilashm86 on 2009-08-20
> **kanikilu said:**
> It will only use the memory once you start the virtual machine. And yes, of course as you give more RAM to the guest, the host will have less available, so depending on what you do, it could have a negative affect.

I suppose the worst that could happen would be that the host would need more memory than is available and go into swap...

yes i observed it in system monitor yesterday, my host machine had never used swap, i was amazed to see 30% of swap was being used....
since i wont shift workspaces between 2 OS, i'll give more memory to virtual machine, then if i shutdown virtual host, things are pretty cleaned up:)

---


---
title: "can't update,couldn't fetch...."
date: 2009-10-03
forum: General Help
---

### Post by McWeirdo on 2009-10-03
Hi
I was trying to update yesterday through the update manager, and I couldn't retrieve some packages it said : couldn't fetch file, Hash Sum Mismatch.
So I changed my server from the main server to best server(the speed in the main server was very low), and it still doesn't work.
I've searched on the internet how to fix this issue, and there was a command :
udo apt-get update -o Acquire::http::No-Cache=Truecause apparently it's the ISP fault...
but it didnt work for me :<

I really need help solving this issue.

Thank You,

MCW:popcorn:

---

### Post by dcstar on 2009-10-03
> **McWeirdo said:**
> Hi
I was trying to update yesterday through the update manager, and I couldn't retrieve some packages it said : couldn't fetch file, Hash Sum Mismatch.
........
I really need help solving this issue.
........

Everybody should be aware that right now the Ubuntu servers are distributing the new 9.10 beta images to **all the mirror servers around the planet**, and this will (as it does with every new release) cause problems with people accessing the servers for updates etc.

These problems will be magnified in a few weeks when 9.10 is officially released, so the answer is either to be patient as things usually fix themselves in a day or two, or (and this is the best option) select a repository close to your location.

Using the default repository for your country will usually guarantee the worst possible performance choice for updating your system.

---

### Post by McWeirdo on 2009-10-03
> **dcstar said:**
> Everybody should be aware that right now the Ubuntu servers are distributing the new 9.10 beta images to **all the mirror servers around the planet**, and this will (as it does with every new release) cause problems with people accessing the servers for updates etc.

These problems will be magnified in a few weeks when 9.10 is officially released, so the answer is either to be patient as things usually fix themselves in a day or two, or (and this is the best option) select a repository close to your location.

Using the default repository for your country will usually guarantee the worst possible performance choice for updating your system.

 Awesome,I'll wait. I thought there is something wrong with my ubuntu :P  Thank You.

---


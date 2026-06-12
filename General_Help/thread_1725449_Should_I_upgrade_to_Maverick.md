---
title: "Should I upgrade to Maverick?"
date: 2011-04-09
forum: General Help
---

### Post by conradin on 2011-04-09
Hi all,
I'm running 4 computers with the 64 bit version of lucid, i7-960 cpus, x58 sabertooth mobos and 12GB ram. I upgraded to maverick and got a error on boot with a sata controller, but most everything seems to work fine. These computers are going in a lab which the admin will most likely never, ever update them, so this might be the last time I update them for a while. Should I upgrade to maverick or leave them running lucid? (64bit)

What reasons would I want to consider further for upgrading?

---

### Post by bhaverkamp on 2011-04-09
Leave it with Lucid. Its the LTS release.

---

### Post by techunit on 2011-04-09
Stick with Lucid It will be supported up until April 2013. I don't foresee as many problems with Lucid anyway. I do recommend that you make sure to lock permissions if they are going to be in a lab environment.

Good Luck.

---

### Post by 3Miro on 2011-04-09
+1 for Lucid. Then you will upgrade them in a year or two to the next LTS. Minimum effort, maximum stability.

---

### Post by d3v1150m471c on 2011-04-09
i think lucid will still be suported until 2013, march that year to be specific. I rarely upgrade my distro but I do take new packages from new repositories. 
```

sudo cp /etc/apt/sources.list .sources.list.bak
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get install <list of new packages>
sudo sed -i 's/maverick/lucid/g' /etc/apt/sources.list
sudo apt-get update

```

besides, when i did finally breakdown upgrade from 9.10 to 10.04 it broke my x-server and I had to manually repair it. Ubuntu's upgrades seem to rarely be a smooth process but that's been my experience.

---


---
title: "everything is loading/ moving slow"
date: 2009-07-27
forum: General Help
---

### Post by ZuMash on 2009-07-27
i just bought a new laptop. 2.1 ghz, 3gb ram. it has vista on it and that worked fine, so i installed ubuntu 9.04 using a dual boot. its almost unusable since everything lags. browser, explorer, mouse movement across the desktop. what is wrong here?

---

### Post by pqwoerituytrueiwoq on 2009-07-27
same for me run a driver update (i just have less ram and i wiped vista off)
system->administration->hardware drivers

---

### Post by ZuMash on 2009-07-27
> **pqwoerituytrueiwoq said:**
> same for me run a driver update (i just have less ram and i wiped vista off)
system->administration->hardware drivers

the only driver that pops up is the madwifi driver, which my wifi already works fine. any other solutions community?

---

### Post by philcamlin on 2009-07-27
is it the wholle system thats lags is your pc under heavy loads is your pc pinned?

try sudo apt-get update 
sudo apt-get upgrade

see if you get anything to update and see if it gets faster :)

---

### Post by Vaphell on 2009-07-27
everything lagging is most probably caused by missing gfx drivers, what is your chipset?

---

### Post by ZuMash on 2009-07-27
> **Vaphell said:**
> everything lagging is most probably caused by missing gfx drivers, what is your chipset?

chipset is AMD Sempron SI-42 Processor 

laptop info [here]("http://www.walmart.com/catalog/product.do?product_id=11050018")

---

### Post by Vaphell on 2009-07-27
[http://ubuntuforums.org/showthread.php?t=1222304](http://ubuntuforums.org/showthread.php?t=1222304)

the same problem - missing drivers for nvidia gf8200m
solution - [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---


---
title: "fan problems"
date: 2010-05-27
forum: General Help
---

### Post by MacHaddock on 2010-05-27
My fan won't stop running.

My fan is running way more now that I upgraded to 10.04. I'm on a Asus x51r. Does anyone recognize this problem?

---

### Post by mindpowerz on 2010-05-27
Could be Ubuntu's way of ensuring that we have an optimal CPU working temperature...

---

### Post by draclear on 2010-05-27
> **MacHaddock said:**
> My fan won't stop running.

My fan is running way more now that I upgraded to 10.04. I'm on a Asus x51r. Does anyone recognize this problem?

There was a similar problem with the Acer Aspire One, which is solved by the following:

So that the acerhdf module runs at boot type

sudo gedit /etc/modprobe.d/acerhdf.conf  and insert the following

options acerhdf kernelmode=1

May work as is.  May work if you swap acer for asus.  Good luck.

---

### Post by MacHaddock on 2010-05-27
That just opens/creates an empty file.

Thanks though

---

### Post by MacHaddock on 2010-05-28
> **mindpowerz said:**
> Could be Ubuntu's way of ensuring that we have an optimal CPU working temperature...

You mean it didn't have that in 9.10 or what ???

---


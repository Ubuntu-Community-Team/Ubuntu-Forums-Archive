---
title: "Heat issues"
date: 2011-10-08
forum: General Help
---

### Post by nslegacy163 on 2011-10-08
Some background:
I bought a used PC for my girlfriend that had Win7 on it. I'm a Linux/Ubuntu guy so my plan had always been to dual boot it so I can do my work on it as well. Anyways, before I dual booted it she had mentioned the computer BSOD'd. Indeed, it did. About a hundred times. After Windows boots I'd get a BSOD after 5-10 mins. I would receive a few different error dumps. One basic Hardware Failure one and another about driver failures. I looked into those and fixed them. But still received BSODs. So I decided to do what 85% of the world SHOULD do and just load Ubuntu. :D 
 After I got 10.10 64 bit loaded (her machine is 64 bit) I'm cruising around setting it up and BAM! machine shuts down. I restart it and get the "this machine was shut down due to high temps blah blah." Now, the guy I bought it off put a new CPU fan in it that needs help to start itself...that's a non-issue. I thought that was the problem so I put a different fan it but it happened again. I reinstalled the other fan and fired it up...BAM! shutdown for temp again. I was REALLY confused. Then I stuck my hand in the box to see where the heat was coming from. Not the CPU, not the power box...then I touched this heat sink on the mobo and it burned the hell out of my hand! So I'm assuming that's my problem. So, what's my fix? I have no idea that the heat sink is for. I snapped a picture of the mobo and the sink that's hot like sauce. 
  I'm assuming that the heat isn't normal since the PC worked fine before. I'm hoping you guys can give me some insight how to get it back to normal rather than "buy a new heat sink" or cooling solution solution. 
Thanks!

---

### Post by ashwinrao on 2011-10-08
It would be better if you provide hardware specifications to troubleshoot the issue. Just run ```
sudo lshw
```

---

### Post by nslegacy163 on 2011-10-08
> **ashwinrao said:**
> It would be better if you provide hardware specifications to troubleshoot the issue. Just run ```
sudo lshw
```

Attached. It was a race against time and hope it's what you need.

---

### Post by quadproc on 2011-10-08
Would you please furnish the make and model of your mother board, and a description of how it is populated (amount and kind of RAM in particular).

On the system that I am using I routinely observe that the highest temperature thing reported is one of the mother board sensors - I have an ASUS P6T SE with 6 GB of installed RAM.  The mother board runs significantly hotter than the CPU except when I encounter buggy software that spins one or more of my CPUs at 100% utilization.

quadproc

---

### Post by nslegacy163 on 2011-10-08
> **quadproc said:**
> Would you please furnish the make and model of your mother board, and a description of how it is populated (amount and kind of RAM in particular).

On the system that I am using I routinely observe that the highest temperature thing reported is one of the mother board sensors - I have an ASUS P6T SE with 6 GB of installed RAM.  The mother board runs significantly hotter than the CPU except when I encounter buggy software that spins one or more of my CPUs at 100% utilization.

quadproc

It is a Pegatron M2N78-LA with 8GB of RAM. So that hot sink is the MOBO's sink then?

---

### Post by dave01945 on 2011-10-08
If it's getting that hot that quickly it is safe to say the motherboard is broken there isn't anything you can do about it, that heat sink is for the chipset which is used to control the motherboard and it can't be replaced

---

### Post by nslegacy163 on 2011-10-08
> **dave01945 said:**
> If it's getting that hot that quickly it is safe to say the motherboard is broken there isn't anything you can do about it, that heat sink is for the chipset which is used to control the motherboard and it can't be replaced

Can't the MOBO be replaced? Just find the same type and model and swap?

---

### Post by Basher101 on 2011-10-08
> **nslegacy163 said:**
> Can't the MOBO be replaced? Just find the same type and model and swap?

sure it can. but you will need new thermal paste for the CPU because you have to remove the Cooler from it if you swap MOBOs

---

### Post by nslegacy163 on 2011-10-08
> **Basher101 said:**
> sure it can. but you will need new thermal paste for the CPU because you have to remove the Cooler from it if you swap MOBOs

 Hilariously, I have some from my other builds and CPU swaps so no worries. Best thing to do then is to google the same MOBO then so I know it will all sync up nicely and swap it in?

---

### Post by Basher101 on 2011-10-08
Yes thats all there is to it. But when you remove the cooler the thermal paste (or heat paste? not sure how its in english) will crumble a bit. This way it wont be able to function properly as a heat conductor and you will have to scrape it off the cooler and CPU carefully and put new paste on it. Thats what i mean by > sure it can. but you will need new thermal paste for the CPU

---


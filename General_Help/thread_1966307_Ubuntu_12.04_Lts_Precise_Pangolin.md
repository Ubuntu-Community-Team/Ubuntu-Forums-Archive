---
title: "Ubuntu 12.04 Lts Precise Pangolin"
date: 2012-04-26
forum: General Help
---

### Post by Its_Rishi on 2012-04-26
Yesterday i downloded a newer release of ubuntu 12.04 lts which is precise pangolin but it could not booting and shows an kernal error with my cpu
now what should i do?
do i have to download another link of 12.04 lts or what?

---

### Post by techsupport on 2012-04-27
> **Its_Rishi said:**
> Yesterday i downloded a newer release of ubuntu 12.04 lts which is precise pangolin but it could not booting and shows an kernal error with my cpu
now what should i do?
do i have to download another link of 12.04 lts or what?

What does the kernel error look like?

---

### Post by inspiredbylasers on 2012-04-27
Give us more details on how you downloaded it. Upgrade, clean install, dual boot, etc?

---

### Post by dcstar on 2012-04-27
> **Its_Rishi said:**
> Yesterday i downloded a newer release of ubuntu 12.04 lts which is precise pangolin but it could not booting and shows an kernal error with my cpu
now what should i do?
do i have to download another link of 12.04 lts or what?

If your CPU does not support PAE then I believe you have to download the other Ubuntu flavours that still do:

[http://askubuntu.com/questions/122841/why-is-12-04-using-a-pae-dependent-kernel-by-default](http://askubuntu.com/questions/122841/why-is-12-04-using-a-pae-dependent-kernel-by-default)

---

### Post by Its_Rishi on 2012-04-29
> **techsupport said:**
> What does the kernel error look like?

> **inspiredbylasers said:**
> Give us more details on how you downloaded it. Upgrade, clean install, dual boot, etc?

> **dcstar said:**
> If your CPU does not support PAE then I believe you have to download the other Ubuntu flavours that still do:

[http://askubuntu.com/questions/122841/why-is-12-04-using-a-pae-dependent-kernel-by-default](http://askubuntu.com/questions/122841/why-is-12-04-using-a-pae-dependent-kernel-by-default)
I Downloaded this from the ubuntu official site and it's 32 bit after that i burned into a R/W disc and booted in my pc then the following error appears and i already have windows 7 installed in it

---

### Post by IanW on 2012-04-29
Your kernel needs PAE, so dcstar's suggestion is the correct answer for you.

---

### Post by Its_Rishi on 2012-04-29
> **IanW said:**
> Your kernel needs PAE, so dcstar's suggestion is the correct answer for you.
What is PAE...?
and can i get that for my pc?
and i only interested in "ubuntu" rather than xubuntu,kubuntu,lubuntu etc...
Please help me on this pure ubuntu to run in my pc

---

### Post by arpanaut on 2012-04-29
Here's a link that will help: [http://ubuntuforums.org/showpost.php?p=11882333&postcount=518](http://ubuntuforums.org/showpost.php?p=11882333&postcount=518)

kansasnoob (forum member) has been working on this for a while and I think he is close to getting a conversion from Lubuntu destop to Ubuntu desktop with the non-pae kernel.

Read that post and the links therein and you will be getting on the right track. 
Looks like it will take some effort but is doable...  kansasnoob has already done the heavy lifting!

---

### Post by Its_Rishi on 2012-04-29
> **arpanaut said:**
> Here's a link that will help: [http://ubuntuforums.org/showpost.php?p=11882333&postcount=518](http://ubuntuforums.org/showpost.php?p=11882333&postcount=518)

kansasnoob (forum member) has been working on this for a while and I think he is close to getting a conversion from Lubuntu destop to Ubuntu desktop with the non-pae kernel.

Read that post and the links therein and you will be getting on the right track. 
Looks like it will take some effort but is doable...  kansasnoob has already done the heavy lifting!
uffff thank you guys good bye ubuntu...

---


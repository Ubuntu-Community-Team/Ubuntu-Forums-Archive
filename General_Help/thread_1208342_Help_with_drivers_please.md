---
title: "Help with drivers please"
date: 2009-07-09
forum: General Help
---

### Post by JoeSef-IL on 2009-07-09
Hello dear friends,
Today I have installed the ubuntu 9.04 on my PC in side-by-side mod with Windows Xp Home.
I just searched for the drivers to "NVIDIA nForce 550" for linux and i didnt find it.
 
Please help me by giveing me the download link of the driver "NVIDIA nForce 550 chipset":frown:

---

### Post by JoeSef-IL on 2009-07-09
Please help me i really need this!!

---

### Post by mthalis on 2009-07-09
Search "nvidia" in snaptic package manager and install what you want
or search envyng-core it will do it automatically.

---

### Post by JoeSef-IL on 2009-07-09
> **mthalis said:**
> Search "nvidia" in snaptic package manager and install what you want
or search envyng-core it will do it automatically.
 
can you give me the sites?links? something?
 
and i really be grateful to you!:guitar:

---

### Post by mthalis on 2009-07-09
System - Administrator -> Snaptic Package Manager and search.

---

### Post by JoeSef-IL on 2009-07-09
But this is the problem i am now on Win Xp cause only here i have my network driver
 
 
in ubuntu i have no network cause i need this driver to be at the net!

---

### Post by mthalis on 2009-07-09
What do you want to know exacly?

---

### Post by JoeSef-IL on 2009-07-09
where to get the driver for NVIDIA nForce 550 chipset system! for linux because i found it only for windows

---

### Post by mthalis on 2009-07-09
Did you do what i say? or open Firefox and choose "Ubuntu package search" and search "nvidia"

---

### Post by danwood76 on 2009-07-09
I think what you need to understand is that Ubuntu, and the linux kernel in general, comes with drivers for most hardware.
Its not like windows where you have to install lots of drivers after you install, you should just install and go.

To fix your network issues can you please post the output of the following command from a terminal (Applications -> Accesories -> Terminal)
```

lspci -vv

```

---

### Post by akakingess on 2009-07-09
I think there is some confusion, because I think that JoeSef-IL is actually looking for the network card driver.__[URL="http://ubuntuforums.org/member.php?u=871202"]
[/URL]

---

### Post by danwood76 on 2009-07-09
(thats what I assumed so the lspci would be useful)

---

### Post by akakingess on 2009-07-09
> **danwood76 said:**
> (thats what I assumed so the lspci would be useful)
I know you are on top of things Danwood76, I was referring to the original poster/replier. I follow your posts because of your good info a lot of the time.

---


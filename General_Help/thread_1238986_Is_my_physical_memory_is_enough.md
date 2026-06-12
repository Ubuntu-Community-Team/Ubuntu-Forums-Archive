---
title: "Is my physical memory is enough ???"
date: 2009-08-13
forum: General Help
---

### Post by brijith on 2009-08-13
Hai all,
       
         Recently I had to reinstall my system after I bought a new motherboard. I have a 1GB DDR2 with it.When I installed ubuntu 9.04 and enabled desktop effects I found that its slow. What you guys think is my 1GB ram is not enough to enable desktop effects. Do I need to add some more memory?


**[COLOR="DarkOrange"]Thanks[/COLOR]**

---

### Post by Yvan300 on 2009-08-13
I think your graphics card would be more of a concern than your ram. What card do you have?

---

### Post by brijith on 2009-08-13
I am not using any graphics card, I mean I have only the on board graphics


:)

---

### Post by Yvan300 on 2009-08-13
That dosen;t say anything, all computers use a graphics card to render images, and it would not matter even if you had 6 gb of ram, if your graphics card only has 12 mb of memory, then you would not be capable of enabling desktop effects.

---

### Post by lisati on 2009-08-13
> **brijith said:**
> I am not using any graphics card, I mean I have only the on board graphics


:)
Sometimes it's easier for us to refer in a general sense to "graphics card" even if it's on-board graphics.

Are you able to check the amount of RAM associated with it during system boot?

---

### Post by jocko on 2009-08-13
> **brijith said:**
> I am not using any graphics card, I mean I have only the on board graphics


:)
It doesn' matter if you have a separate graphics card in a agp or pcie port or an onboard graphics chipset, it's still the graphics card (or integrated chipset) that is the important part for rendering the desktop effects. Which onboard graphics card do you have? Does it have dedicated video memory or does it claim part of the RAM? If so, how much of the RAM does it use?

---

### Post by mcduck on 2009-08-13
Your graphics chip is the likely problem. Try to find out which one you have, and make sure you have best possible drivers installed for it.

RAM has nothing to do with this, and even graphics memory is unlikely reason, if there's not enough graphics memory Compiz will simply fail, not act slowly.

Besides, It's very rare for a graphics card to have too little memory compared to GPU power, memory is cheap, GPU power is expensive, so even the cheapest solutions are stuffed with way more memory than what they'll ever need because the amount of GRAM is nice and simple (although meaningless) number that can be used for marketing while GPU performance is complicated stuff. :/

---

### Post by brijith on 2009-08-13
See this is my motherborad [[COLOR="RoyalBlue"]click here to see[/COLOR]]("http://in.asus.com/products.aspx?l1=3&l2=11&l3=563&l4=0&model=2507&modelmenu=1")

---

### Post by mcduck on 2009-08-13
Ok, so you have Intel GMA 3100.

While not very powerful, it should be able to handle desktop effects decenntly. But there are some known performance issues with Intel graphics chips on Ubuntu 9.04.

Following one of these quides might help to solve the problem: 
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")
[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by MeanEYE on 2009-08-13
> **brijith said:**
> Hai all,
       
         Recently I had to reinstall my system after I bought a new motherboard. I have a 1GB DDR2 with it.When I installed ubuntu 9.04 and enabled desktop effects I found that its slow. What you guys think is my 1GB ram is not enough to enable desktop effects. Do I need to add some more memory?


**[COLOR="DarkOrange"]Thanks[/COLOR]**

Can you say something more about slow. Like is it slow in a way where you click to start a program and it takes ages to start or it's slow in sense where it behaves like games with low FPS rate?

---

### Post by brijith on 2009-08-13
> **MeanEYE said:**
> Can you say something more about slow. What I mean by slowness is some time when I take effects like flips it wont come in a smooth manner. its seems like some frames missing (in your words 'like games with low FPS rate'). I feel this when there is any music player like songbird or some application which uses some memory running behind ...

---

### Post by MeanEYE on 2009-08-13
> **brijith said:**
> What I mean by slowness is some time when I take effects like flips it wont come in a smooth manner. its seems like some frames missing (in your words 'like games with low FPS rate'). I feel this when there is any music player like songbird or some application which uses some memory running behind ...

I've had a similar experience like yours. Also I noticed when I switch to console (CTRL+ALT+F1) and then return to X (ALT+F7) everything becomes normal again.

Can you please try that and then give me the results ;)

---


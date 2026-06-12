---
title: "Needing some general Ubuntu help."
date: 2010-01-07
forum: General Help
---

### Post by Dropshock on 2010-01-07
Let me first start by saying Ubuntu is the second OS I have every installed on this machine, So I'm just about as new to Linux as can be.
Alright, so I need some help with some general stuff, Wine, Games, ect.
First off I cant seem to get any drivers installed for my GFX card, I've got an ATI Radeon X1300 and when I go to System > Admin > Hardware drivers it seems to find nothing.
I'm pretty sure thats whats causing my next problem; Lag with games.
I installed ony of my favorite games, [Blockland]("http://blockland.us/") and ran it with Wine, First thing right off the bat is its lagging like hell. But, an even worse problem is happening. It doesnt even seem to start up now...
Alright, now let's go to java.
One of my other favorite games, [Minecraft]("http://minecraft.net/"), A game made with java, doesnt seem to work. I can play it for about 10 - 20 seconds until the game just turns white.
There's also Dwarf Fortress, and it seems that I cant even get the linux version running. I looked at the requirements and got some of them, but not all and when I try to run it nothing even happens.
Lastly, Steam.
So far steam is working fine, except when I try and install a game off of it, Steam just immediately closes...
So, If you need my specs or anything just ask. I'd relaly like to fix some of these things so I use Ubuntu over windows, because I just love the feel more than windows.
PS: Sorry if some of my questions are really obvious to fix but I've got no idea, I've even searched around on these forums looking for some answers but I cant seem to find any.

---

### Post by NoaHall on 2010-01-07
1) ATI has stopped supporting your graphics card.
2)Do you use 64 bit or 32 bit?

---

### Post by Dropshock on 2010-01-07
1) Damn. Then what can I do? I dont think I want to buy a new graphics card to use ubuntu.
2)32, I think. Is there a way to check just to be sure?

---

### Post by NoaHall on 2010-01-07
1) Hold on. The ATI open-source driver is getting better :) Fedora 12, if I recall correctly, has a better open-source driver right now.
2)If you go to Applcations -> Accessories -> Terminal and then type ```
uname -a
```

As for Steam, it's probably best to download in Windows, then just copy it over/run with WINE from Program Files on your Windows partition.

---

### Post by Dropshock on 2010-01-07
1) So, where can I get this? or is it not out yet?
2) it returned this; > Linux dropshock-desktop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux


---

### Post by NoaHall on 2010-01-07
> **Dropshock said:**
> 1) So, where can I get this? or is it not out yet?
2) it returned this;

Fedora 12 you can download here - [http://fedoraproject.org/](http://fedoraproject.org/)
However, for the time being, I recommend you stick with Ubuntu.

That means its 32 bit - my advice is to try and reinstall Java from the website.

---

### Post by Dropshock on 2010-01-07
Oh! Its an OS.
Okay then. Well, not to be so picky but when will the open source drivers be out? I game a lot and now I'm usually using Ubuntu for my computer.

Also, Reinstalling java didnt work. Minecraft just turns immediately white. Also, Any help with Dwarf Fortress?

---

### Post by NoaHall on 2010-01-08
> **Dropshock said:**
> Oh! Its an OS.
Okay then. Well, not to be so picky but when will the open source drivers be out? I game a lot and now I'm usually using Ubuntu for my computer.

Also, Reinstalling java didnt work. Minecraft just turns immediately white. Also, Any help with Dwarf Fortress?

Which browser are you using? It works okay with Opera for me.

---

### Post by Dropshock on 2010-01-08
I'm using firefox. I'll give Opera a try.
edit:
It just makes Opera crash when trying to load it :/

---

### Post by NoaHall on 2010-01-08
> **Dropshock said:**
> I'm using firefox. I'll give Opera a try.
edit:
It just makes Opera crash when trying to load it :/

Hm. How are you installing Java?

---

### Post by Dropshock on 2010-01-08
First I installed it by the Software center, then from the java website.

---


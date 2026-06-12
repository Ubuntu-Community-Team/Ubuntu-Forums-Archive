---
title: "CrossOver for games and iTunes"
date: 2009-10-17
forum: General Help
---

### Post by Snuzzer on 2009-10-17
Hey.

I'm considering installing Ubuntu on my stationary PC instead of using Windows XP. But I would like to be able to play some games such as World of Warcraft and because of my iPhone I also need to have iTunes installed - preferably the latest version, iTunes 9.

Do you think I can switch from Windows XP to Ubuntu + CrossOver without losing performance and still be able to have iTunes?

If so, should I buy both CrossOver Games and CrossOver Linux?

Thanks in advance.
Simon B. Støvring
Denmark

---

### Post by khelben1979 on 2009-10-17
I think [VirtualBox]("http://en.wikipedia.org/wiki/Virtualbox") is a better choice if you have the sufficient hardware to use it.

---

### Post by jrusso2 on 2009-10-17
Never used Crossover games but I have used Crossover office.  And the version of itunes it runs is old and worthless.  Newer ones can be run with WINE but its still limited in what it will do so over all its useless.

---

### Post by Snuzzer on 2009-10-17
> **khelben1979 said:**
> I think [VirtualBox]("http://en.wikipedia.org/wiki/Virtualbox") is a better choice if you have the sufficient hardware to use it.
Seems very resource demanding. Having 4GB ram and a Ge-Force 9800 GT video card but only a 3.0 single core processor - yea, I know. I'm already looking for which one to buy.

> **jrusso2 said:**
> Never used Crossover games but I have used Crossover office.  And the version of itunes it runs is old and worthless.  Newer ones can be run with WINE but its still limited in what it will do so over all its useless.
Oh. That crushed my idea, I guess. If there aren't any Linux alternatives for iTunes which has a great iPhone support.
I'm wondering if Songbird can be the alternative.

---

### Post by MacHaddock on 2009-10-17
How about a dual boot with xp and ubunut? or did you not want to have to reboot?

---

### Post by Snuzzer on 2009-10-17
[s]I've just found [Cedega]("http://www.cedega.com"). Do anyone have experience with Cedega?[/s]

EDIT: I don't want to have a monthly fee.

---

### Post by Snuzzer on 2009-10-17
> **MacHaddock said:**
> How about a dual boot with xp and ubunut?

Well, I would prefer using Ubuntu only. The reason for me switching from Windows XP to Ubuntu is mainly to get as far away as possible from Microsofts products. And I would like to play games and still be in the Ubuntu enviroment.

---

### Post by MacHaddock on 2009-10-17
> **Snuzzer said:**
> Well,  mainly to get as far away as possible from Microsofts products

I feel that :D

---

### Post by Snuzzer on 2009-10-17
Oh, now I remember why iTunes is so important for me. I was sure, that I could just use Songbird, but my firmware updates for the iPhone will be a problem.

---

### Post by danwood76 on 2009-10-17
Not just firmware updates.
I think you need to jailbreak the iphone to use it in linux and even then its a bit hackey on how you use it.

You can thank your lovely apple for that ;)

Qemu (or KVM if you processor supports it) is pretty good for emulating windows, I wouldnt use virtualbox as its slower in my experiance.

---

### Post by Snuzzer on 2009-10-17
> **danwood76 said:**
> Not just firmware updates.
I think you need to jailbreak the iphone to use it in linux and even then its a bit hackey on how you use it.

You can thank your lovely apple for that ;)

Qemu (or KVM if you processor supports it) is pretty good for emulating windows, I wouldnt use virtualbox as its slower in my experiance.

Thanks, but my goal was not to be using Windows in any way. It's sad. And I'm confused why Apple doesn't release a version of iTunes for Linux.

---

### Post by danwood76 on 2009-10-17
Well your options are simple.

WoW will run fine in Wine so no problem there.

Iphone support is not good due to apples encrypted firmware btu I have found this document in the community wiki which might be of interest:
[https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x](https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x)

---

### Post by vinutux on 2009-10-17
3 options

1. wine/cediga/crossover --- don't expect gr8 performances here..

2. Virtualbox/VMware --- Recommended option... get 90% performance...

3. Dual boot with windows --- worst/ugly option

---

### Post by danwood76 on 2009-10-17
> **vinutux said:**
> 
2. Virtualbox/VMware --- Recommended option... get 90% performance...

I doubt you get 90% performance with an emulator, infact I know you don't even with kvm.

Wine is a lot faster than virtualisation.

---

### Post by Snuzzer on 2009-10-17
> **danwood76 said:**
> I doubt you get 90% performance with an emulator, infact I know you don't even with kvm.

Wine is a lot faster than virtualisation.

But isn't CrossOver faster than Wine?

---

### Post by danwood76 on 2009-10-17
> **Snuzzer said:**
> But isn't CrossOver faster than Wine?

In short no.

Crossover is based on WINE and all the changes that crossover make get put back into wine.
The only thing that is different is that slightly more apps are supported, if your apps are supported by wine then you may aswell use that.
Theres no point in paying for something that is free and open source.

---

### Post by Snuzzer on 2009-10-17
> **danwood76 said:**
> In short no.

Crossover is based on WINE and all the changes that crossover make get put back into wine.
The only thing that is different is that slightly more apps are supported, if your apps are supported by wine then you may aswell use that.
Theres no point in paying for something that is free and open source.

That's true. I had read about the CrossOver and Wine "relationship" (I belive it's some of the same programmers) I just assumed, that CrossOver was better and more well supported.

---


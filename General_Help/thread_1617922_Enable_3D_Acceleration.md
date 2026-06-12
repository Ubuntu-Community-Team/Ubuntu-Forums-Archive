---
title: "Enable 3D Acceleration?"
date: 2010-11-10
forum: General Help
---

### Post by amplitude166 on 2010-11-10
My relevant system specs are: 
Graphics  - Ati Mobility 5870 Radeon
                                        CPU        - Intel Core i3
                                        Ubuntu    - 10.10 64 bit

My problem is that I am not able to enable 3D Acceleration.

I was looking into Ubuntu for a while and so far it's far better then any other OS. However I need 3D acceleration apparently, this is needed because unfortunately I need that enabled to play a game called Guild Wars. This is a laptop. I only dual boot with Windows 7 because of this. I have spent around 5 days searching and asking friends to find a few solutions that did NOT work obviously. The graphics card DOES support 3D acceleration AND OpenGL. I am not new to all things computer wise, just Ubuntu is new to me as i previously am used to Windows environment. This is the first forum I have joined as it has a real chance of solving this problem and any more that I may have but hope not to with any Ubuntu release. I have tried wine but that was worse then a waste of time. I have Virtualbox installed and are virtualising a Windows XP Pro SP3 OS. Any added info you may need I shall add.

Thank you in advance.

---

### Post by amplitude166 on 2010-11-10
Anyone? :/

---

### Post by zvacet on 2010-11-10
Did you looked>under system>admin>aditional hardware drivers?Maybe from there you can install driver for your card.

---

### Post by amplitude166 on 2010-11-10
its not the driver i need to no how to activate 3d acceleration

---

### Post by jocko on 2010-11-10
> **amplitude166 said:**
> its not the driver i need to no how to activate 3d acceleration
If you install the driver, you will get 3d acceleration (but I'm pretty sure the open source driver should have 3d acceleration too, just not as good).

---

### Post by amplitude166 on 2010-11-10
ATI/AMD proprietary FGLRX graphics driver
Tested by the Ubuntu develpers
License: Proprietary
3D-accelerated proprietary graphics driver for ATI cards.

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards.



thats what additional drivers states its activated and currently in use

---

### Post by jocko on 2010-11-10
> **amplitude166 said:**
> ATI/AMD proprietary FGLRX graphics driver
Tested by the Ubuntu develpers
License: Proprietary
3D-accelerated proprietary graphics driver for ATI cards.

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards.



thats what additional drivers states its activated and currently in use
Then you have 3d acceleration.

---

### Post by amplitude166 on 2010-11-10
yet i cant run games in "PlayOnLinux" because it says 3d isnt enabled and i cant enable it or OpennGL on Virtualbox :/ anymore ideas?

p.s thanks for helping

---

### Post by thomaswei on 2010-11-10
Does "PlayOnLinux" or the game itself state it had no 3D?
If its a problem of PlayOnLinux you should try [http://winehq.org for instructions ]("http://winehq.org/")how to get your game running.

Virtualbox has probably no 3D because it has to to emulate a graphics card through software and therefore can't handle 3D ( the way your graphics card does ).

---

### Post by jocko on 2010-11-10
> **amplitude166 said:**
> I have Virtualbox installed and are virtualising a Windows XP Pro SP3 OS.
Hmmm... Missed this part when I read the post the first time...

Do you mean you need 3d acceleration in virtualbox?
That is a completely different question...
Virtualbox's 3d acceleration is probably not very good, but may work for some games (but you first of all need to have 3d acceleration in the host os).
With the guest os powered off, go to the settings for the virtual machine and look around for a setting that enables 3d acceleration (I don't have virtualbox installed at the moment, so I can't give you any more specific info).
You also need to install the guest additions in the guest. Start up the guest os, then in the guest window's menu, go to Machine-->Install guest additions (the installer will start automatically in the guest).

---

### Post by jocko on 2010-11-10
> **amplitude166 said:**
> yet i cant run games in "PlayOnLinux" because it says 3d isnt enabled and i cant enable it or OpennGL on Virtualbox :/ anymore ideas?

p.s thanks for helping
Just to make sure that you really don't have 3d acceleration and see the possible cause for it, could you post your /var/log/Xorg.0.log?
It's quite a long text file so please paste it between a [noparse]```
 and a 
```...[/noparse]

---

### Post by mastablasta on 2010-11-10
another option would be that the wrong version of drivers is installed. how did you install them?

---

### Post by amplitude166 on 2010-11-10
well i installed the drivers from ati them selves so its legit and latest, im trying to get 3d acceleration to work on ubuntu then virtualbox isnt thtere a terminal comand to check?

---

### Post by amplitude166 on 2010-11-10
hmmmmmmmmmm no more help?

---

### Post by amplitude166 on 2010-11-10
i may have fixed it, i followed a websites terminal prompts and then i looked at additional drivers it said nothing so i reinstalled ati drivers and then play on linux didnt warn about no 3d so i thought hmmmm loaded a game voila works.well its updating the game now which is farther then i had got before i shall post bk when it is done. thank you for all your help you did help alot

---

### Post by thomaswei on 2010-11-10
Well, as statet in my previous post, it would be helpful to know if it was the program "PlayOnLinux" ( which is btw a kind of frontend for WINE ) or the game you are trying to run itself complains about 3D.

If it was only the game you should check winehq and look for the requirements to run this specific game.

---

### Post by amplitude166 on 2010-11-10
yes it does indeed work :3

---


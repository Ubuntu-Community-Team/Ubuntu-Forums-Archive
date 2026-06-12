---
title: "Having some problems with Ubuntu and firefox"
date: 2009-07-22
forum: General Help
---

### Post by Zornox on 2009-07-22
I'm having some problems with Ubuntu and Firefox on Ubuntu

okay the 1st problem is that when i go to appearance preferences then the visual effects and i want them to be Extra, It will go to a loading bar trying to find drivers , then a little windows pops up and says Desktop Effects couldn't be enabled? how can i fix this? and what is going on? 

The second thin is my firefox won't install the Adobe Flash player or anything i need to get on chatrooms or watch youtube videos, when i go to adobe's website and download it for Ubuntu i open the flash player up to install it but i get a little error message beside the staus it says :Error: Wrong architecture 'i386' and i have no idea what the heck that means. so if you could help me on how to Figuar out what is going on thank you

---

### Post by nwadams on 2009-07-22
1. what video card do you have? 

2. open a terminal window and execute the following code
```
 sudo apt-get install flashplugin-nonfree 
```

the reason you are having trouble with the flash is that you are using a 64 bit version of ubuntu and the plugins from the flash website are 32 bit plugins.

---

### Post by Zornox on 2009-07-22
right now i'm running ubuntu on a Gateway Laptop with a dual boot with Vista, i think the video card has something to do with the Mobile Media Accelerator or something like that

---

### Post by wojox on 2009-07-22
Go into System > Administration > Hardware Drivers and see what it says.

---

### Post by nwadams on 2009-07-22
ok. the second part of my first post should make flash work. 

can you also post the output of the following command 
```
 lspci | grep VGA 
```

---

### Post by Zornox on 2009-07-22
> **wojox said:**
> Go into System > Administration > Hardware Drivers and see what it says.

okay i did that and it says 

No Proprietary drivers are in use in the system

---

### Post by nwadams on 2009-07-22
ok, now post the output of 
```
 lspci | grep VGA 
```

---

### Post by Zornox on 2009-07-22
> **nwadams said:**
> ok. the second part of my first post should make flash work. 

can you also post the output of the following command 
```
 lspci | grep VGA 
```

okay i did code and it gives me this: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

i did the first code you gave me and i still couldn't install Adobe Flash Players 

This is the error i get: zornox@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
zornox@ubuntu:~$

---

### Post by nwadams on 2009-07-22
the first code installs adobe flash player, you don't have to download it from the website after. 

ok, so you have the same graphics card as me. Compiz has blacklisted that card because of a bug. u are running jaunty right? (9.04)

ok. can you go to system->administration->update manager
check for updates, and install any new updates. That should un-blacklist compiz for your video card.

---

### Post by Zornox on 2009-07-22
> **nwadams said:**
> the first code installs adobe flash player, you don't have to download it from the website after. 

ok, so you have the same graphics card as me. Compiz has blacklisted that card because of a bug. u are running jaunty right? (9.04)

ok. can you go to system->administration->update manager
check for updates, and install any new updates. That should un-blacklist compiz for your video card.

well i did the code and it didn't install anything because i get that error message 

and yes i am running 9.04

---

### Post by nwadams on 2009-07-22
ok, go system->administration->software sources. and on the ubuntu software tab make sure that main, universe, restricted, and multiverse boxes are checked and then close the window. It will ask you to reload sources, hit reload. 

then you can install the flash plugin. Then do updates in the update manager and compiz should work.

---

### Post by wojox on 2009-07-22
Open the terminal"

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Zornox on 2009-07-22
> **nwadams said:**
> ok, go system->administration->software sources. and on the ubuntu software tab make sure that main, universe, restricted, and multiverse boxes are checked and then close the window. It will ask you to reload sources, hit reload. 

then you can install the flash plugin. Then do updates in the update manager and compiz should work.

well yes i check to see if all of them were checked and they are, I'm doing the updates right now and i think that was the problem the whole entire time because its taking up to 30 mins to install the updates and there are a lot of them , so after the updates install i'm going to see what i can do about my adobe flash player

---

### Post by nwadams on 2009-07-22
good, good. yes lots of updates. Desktop effects shoudl work properly after the updates.

and you can install the ubuntu-restricted-extras or try the flashplugin-nonfree again to get flash working.

---

### Post by Zornox on 2009-07-22
> **nwadams said:**
> good, good. yes lots of updates. Desktop effects shoudl work properly after the updates.

and you can install the ubuntu-restricted-extras or try the flashplugin-nonfree again to get flash working.
Okay thank you so much, I'm new to Linux Entirely so if i have any more problems or question i'll pm you, Thank you!

---

### Post by nwadams on 2009-07-22
> **Zornox said:**
> Okay thank you so much, I'm new to Linux Entirely so if i have any more problems or question i'll pm you, Thank you!

better yet. post questions in the absolute beginners forum. 
but good luck, and ask if you have problems. 

I do have one question for you though. Does suspend work on your laptop? and if it does tell me if it still works THE SAME after you enable compiz. I'm asking because i'm getting some strange behavior that i cannot explain.

---

### Post by Zornox on 2009-07-22
> **nwadams said:**
> better yet. post questions in the absolute beginners forum. 
but good luck, and ask if you have problems. 

I do have one question for you though. Does suspend work on your laptop? and if it does tell me if it still works THE SAME after you enable compiz. I'm asking because i'm getting some strange behavior that i cannot explain.

To be honest i don't know what Suspend is? or how to enable compiz or what compiz is

---

### Post by nwadams on 2009-07-22
suspend is sleep mode (you probably use it in windows)

compiz is desktop effects, sorry.

---

### Post by Zornox on 2009-07-22
> **nwadams said:**
> suspend is sleep mode (you probably use it in windows)

compiz is desktop effects, sorry.

Okay i'll tell you how it goes once i get everything updated

---


---
title: "Ubuntu 11.10 on P4 1GB RAM slow"
date: 2012-01-08
forum: General Help
---

### Post by tyler.mooo on 2012-01-08
I have read many articles but cant seem to find anything that works. Many people have said to others that the system requirements I am running should be fine. 

What I got-
Dell Dimension 2400
Intel Pentium 4 @  2.19Ghz
1 GB RAM
40GB HDD 
250GB HDD I use for storage.
 Intel(R) 82845G/GL/GE/PE/GV Graphics Controller Onboard
Currently running Windows XP Pro SP3

XP runs super fast and snappy for me with no problems, but I wanted to try out linux, more for the security. I tried Ubuntu and it was just so slow. I dual booted it with XP and it was just so slow I couldnt use it. Takes 20 seconds to open andything including menus.

It's still slow in 2d mode, and on a LiveCD which makes me think its hardware related.  When I go to additional drivers, NOTHING comes up, not sure if thats normal? In SmartDrive everything appears good.

Kind of lost what to do now, dont want to give up so any help would be appreciated!

---

### Post by topsites on 2012-01-08
Your PC's video card may be integrated in the motherboard, but it has a video card of some manufacture / hardware architecture because if your computer had no video card it is very unlikely you would have been able to post the above.

First we need to find out your PC's Video Card manufacture and specifications.
Go into WinXp's Device Manager to find out what it is.
It could well be you're missing the drivers, especially if it's an Nvidia derivative.

For now...

---

### Post by tyler.mooo on 2012-01-08
> **topsites said:**
> You're going to need a little bit better knowledge of what exactly you have, there is no such thing as a computer with no video card.
Yours may be integrated in the motherboard, but it has a video card of some manufacture / hardware architecture.

Go into WinXp's Device Manager to find out what it is.
It could well be you're missing the drivers, especially if it's an Nvidia derivative.
Linux won't always tell you what you need, just like Windows we sometimes have to tell it.

Ah, sorry about that. I have Intel(R) 82845G/GL/GE/PE/GV Graphics Controller.

---

### Post by Paqman on 2012-01-08
You won't have an additional drivers available, Intel bundles their drivers into the kernel.

If switching to Unity-2D still doesn't do it for you you'll probably have to switch to a lighter DE. Try installing the packages xubuntu-desktop or lubuntu-desktop and switching to them. They should be a bit snappier.

---

### Post by debd on 2012-01-08
gah!
11.10 got to be slow on that HW
get 10.10 and it'll run smooth as butter 
just make sure you get the necessary updates after you install 10.10 and u'll be fine. support for 10.10'll be upto 2013 and guess after that u'll get bigger ram eh? ;)

---

### Post by dak0 on 2012-01-08
**Which *buntu to pick?**



 **Ubuntu** uses a user interface (or desktop environment) called  Gnome. Gnome is focused on simplicity and usability. Ubuntu includes a  bunch of Gnome-native applications such as Banshee (music player),  Evolution (email client and calendar), and Gedit (text editor). You can  find the full list of software packages in *ubuntu-desktop* [here]("http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=ubuntu-desktop"). 
 **Kubuntu** uses the K Desktop Environment (also known as KDE). KDE  is focused on including a lot of point-and-click configuration options  immediately available to end users. Kubuntu includes a bunch of  KDE-native applications such as Amarok (music player), K3B (CD burning),  and rekonq (web browser). You can find the full list of software  packages in *kubuntu-desktop* [here]("http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=kubuntu-desktop"). 
 **Xubuntu** uses the Xfce desktop environment, which is a lighter one  than Gnome or KDE. In terms of its design principles, it has a bit of a  balance—presenting in some ways more point-and-click configuration  options than Gnome but also retaining some of the simplicity of Gnome.  Its main appeal is its speed, though, and it's ideal for systems with  256 MB to 512 MB of RAM. Both Ubuntu and Kubuntu *can* run on 256  MB of RAM, but they're more ideal for 512 MB of RAM or more. Xfce  includes Thunar (file manager), Thunderbird (email client), and Mousepad  (text editor). You can find a full list of software packages in *xubuntu-desktop* [here]("http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=xubuntu-desktop"). 
 **Edubuntu** uses the Gnome desktop environment but has a different  set of default applications from Ubuntu.  Its focus is on educational  tools.  It includes Kolourpaint (an easy to use paint program),  Atomix  (a puzzle game for building molecules out of isolated atoms), and Xaos  (a real-time interactive fractal zoomer). You can find a full list of  software packages in *edubuntu-desktop* [here]("http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=edubuntu-desktop"). 
 **Lubuntu** uses LXDE, which is an extremely light desktop  environment (even lighter than Xubuntu's Xfce) and is ideal for very  low-memory systems (128 MB of RAM). You can find a full list of software  packages in *lubuntu-desktop* [here]("http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=lubuntu-desktop"). 





[COLOR=Red]Sorce:[/COLOR] [http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

---

### Post by I_can_see_the_light on 2012-01-08
I've installed Ubuntu 11.10 on an old AMD Athlon XP 2.1GHz with 1GB RAM and a Radeon 9600 video card. Except for the video card it's comparable to your setup so you should at least be able to run Unity 2D smoothly. 

Press **ctrl+alt+t** to open up a terminal and enter the following commands:
```
glxinfo | grep -i direct
```and
```
glxinfo | grep -i opengl
```
Copy/paste the output of the above commands in a post.

---

### Post by Supermouse on 2012-01-10
I don't know, Ubuntu 11.10 is really slow latelly...

I tried installing it on my machine (Athlon XP 2800, 1 GB RAM, Graphics Card Radeon 9600XT), and both Unity 3D and 2D where really slow.

Now I installed Fedora with Gnome Shell and I'm an happy camper. I much prefer .deb over .rpm, and I really like Ubuntu, but there where no way I would use it because of it's slugishness. Also, as a bonus, Gnome Shell is ten thousand times better than Unity, my workflow improved at least 100% compared with Unity on 11.04, and even the missus liked it better.


IF Ubuntu gets better at 12.04 and gets Gnome Shell, I may be coming back...

---

### Post by QIII on 2012-01-10
Ubuntu already has Gnome shell...

---

### Post by Supermouse on 2012-01-10
yep, I was reading about this when I stumbled upon this topic. Still we need to install it, and then all the Unity crap remains in the system, and I'm not sure if we can remove it without breaking the system.

Also, I'm afraid of installing 11.10 over my Fedora install 'cause I fear that even with Gnome Shell the system will remain slow (you know, I have read in many places that 11.10 is like the "Vistabuntu").

---

### Post by QIII on 2012-01-10
I believe it installed with Ubuntu.  

Any "Unity crap" will sit off in a corner of a disk when you are using Gnome shell and not bother you unless you whistle and hold out a treat for it.  It doesn't just up and start running in your RAM on its own  just to irritate you.

Vistabuntu?  Really.  That's what everyone said about 10.04, and all of the cool kids tell everyone to reinstall that now.

You'd better get used to Unity and the like because tablets are the future of GP computing and Unity is a taste of that world.

---

### Post by Supermouse on 2012-01-10
YEah, I know the Unity stuff will sit quietly, but the problem is that it bothers me just by being there. I must be obsessive-compulsive (I prefer Gnome over KDE because it's easier to use an QT-Free desktop than use an gtk-free desktop).

Still, I'm confortable with Fedora, maybe on a later date I'll try Ubuntu again, or maybe I'll wait 'till 12.04.

As I said, I don't dislike Ubuntu, just 11.10 didn't work well for me...

---

### Post by QIII on 2012-01-10
There are many things in any distro that you will not likely use.  You don't notice them precisely because you don't use them.

What you think is easier to use may not be what the next guy says is easier to use.

Linux is a "pick your poison" world.

---

### Post by BertN45 on 2012-01-10
What is slow for you. I know for an ATC controller anything that takes more then 0.1 sec is too slow. What is the time you have to wait for e.g. an Nautilus window, is it a couple of seconds?

---

### Post by Paqman on 2012-01-10
> **Supermouse said:**
> YEah, I know the Unity stuff will sit quietly, but the problem is that it bothers me just by being there. 

So uninstall it. It won't break your system. After all, Kubuntu, Xubuntu, Lubuntu and Mythbuntu don't have Unity.

---

### Post by Supermouse on 2012-01-11
Yep, that was exactly my fear, that uninstalling it would break the system. I'll try it next weekend.


As for "what is slow for me", I don't know how to put it precisely, but with Unity the whole system don't feel as smooth as with Gnome Shell. Applications take longer to load, menus have a small delay before opening, window movement don't go smooth, these kind of stuff.


And, about the "tablet interface", I don't want to start a flame war, but, first of all, I don't think Unity is a good tablet interface. Sure, it has big buttons to choose applications, but the dock is always hidden, and, as there's no way to "hover" the finger, showing the dock will be ankward. If the dock stay there, it will take up screen space, which is at a premium on a tablet.
GS, on the other side, use the "Activities" button on the upper left corner to show you the dock, an app list and all of your currently open windows in an Exposé-like mode. Heck, this is exactly how my Android smartphone works, minus the exposé, and it works pretty well for a small screen.

Also, by the number of people I heard saying that Unity ran really slow on their machines (myself included), while GS ran pretty well, I really don't see the point in Unity. Sure, it's an open source world, it's cool to have diversity and I'm all for it, but I can't stop thinking that if Ubuntu continued to help Gnome instead of running an parallel project, the contributed effort would make a far better DE than both interfaces we have now.

---

### Post by QIII on 2012-01-11
From what "number" of people have you heard?  People on this forum?  People don't come here to complain when things are working well.  They come here when they have problems.  What percentage of users does that represent?  You don't know.  What you see here is an invalid sample tainted by "referral bias".

What things "feel" like is subjective and largely a matter of taste.  

You have a preference and you are certainly entitled to it.  It is human nature to assume that what we like or find appealing is what others will.  But that is not the case.  Fedora with Gnome is no better or worse than Fedora with KDE (which is how I like it) or openSUSE with KDE (which is how I like it) or Kubuntu (which is how I like it).  Some don't like KDE because they say it is harder to configure.  It's not.  It is just different.  Humans tend to view "different" as somehow wrong or difficult.

OBJECTIVELY, however, KDE is far too heavy for a low spec machine.  So I used E17 and Bodhi to resurrect an ancient laptop recently.  Gnome would not have cut it.

Likewise, this first coming round of the tablet revolution is as underpowered as Honda's CVCC when it first showed up in the US.  Very light, touch enabled DEs will be in order.  That will change.  The future probably holds DEs you and I can't imagine.

Point is this:  you like pea soup and I like peanut butter.  There is little point in preaching how much better our preferences are in a world where both are allowed.

---

### Post by ernied on 2012-01-11
So, what does one have to do to roll back to the most recent version of Ubuntu 10?

---

### Post by lykwydchykyn on 2012-01-11
> **ernied said:**
> So, what does one have to do to roll back to the most recent version of Ubuntu 10?

You gotta reinstall.  It's the only way.

It's worth mentioning that the video hardware you're working with is well known to have problems with Linux.  I have a lot of Dells around here with the 845 chipset and it's very problematic.  Any version of Ubuntu that depends on 3D video acceleration is going to be painful on it.

My advice is to make sure your BIOS is fully updated (this has mitigated some onboard video bugs on Dells for me in the past).  If that doesn't help, see if the motherboard has an AGP slot, and if so try to locate an old Nvidia GeForce card for it.

Personally, I wouldn't go with an older version; I'd just install a different desktop like LXDE to save resources.

---

### Post by BertN45 on 2012-01-21
> **Supermouse said:**
> As for "what is slow for me", I don't know how to put it precisely, but with Unity the whole system don't feel as smooth as with Gnome Shell. Applications take longer to load, menus have a small delay before opening, window movement don't go smooth, these kind of stuff.


So UNITY is not slow, it is not as fast as GNOME 2. Well that is the price for progress in this modern world. 

Three years ago I compared Windows 7 on my Dell laptop with Windows for Workgroups 3.11 on a pre-Pentium 486DX of 66 mHz, which I bought in 1993. Guess what; the 486 with WfW 3.11 loaded faster and felt faster than the Windows 7 system. But of course Windows 7 has a lot of additional functionality and developing applications is easier due to a higher level of abstraction.

We are now witnessing another big step in that direction of more functionality and a higher level of abstraction. Ubuntu with the Unity GUI and Windows with the Metro GUI, both are needed in the future to support the integration of phone, TV, tablets, PC and many other devices. Everything will become more and more touch screen based.

Windows takes years to develop the Metro GUI, Ubuntu has to do it in steps of 1/2 year without breaking the system. What you now witness is a hybrid system. They have to support all GNOME 2 applications in the UNITY desktop. Probably too many layers have been put on top of each other in Ubuntu 11.xx. In the coming release(s), they have to remove the legacy layers and optimize their architecture.

The UNITY GUI will get faster again, but never as fast as GNOME 2 that has been completely optimized for the classical PC. It is the price of progress and added functionality, but fortunately in the Ubuntu world you can switch for old PCs to Lubuntu, Xubuntu or stick to Ubuntu 10.xx.

Personally I do not get disturbed by Unity, since I have been using 16-bit minis like the PDP11, where I had response-times of 2-3 seconds. I even worked with an ASR33 at 10 characters per second :D
In house we still use a P-III 500mHz with Lubuntu 11.10 and a P-II 400mHz with Ubuntu 10.10 and the children of the family in law like to visit and use them. The P-II, I would call slow, the P-III is OK and feels faster then the original Vista on my Dell laptop. But they both run a Desktop optimized for the classical or even old PC.

---

### Post by I_can_see_the_light on 2012-01-22
> **Supermouse said:**
> As for "what is slow for me", I don't know how to put it precisely, but with Unity the whole system don't feel as smooth as with Gnome Shell. Applications take longer to load, menus have a small delay before opening, window movement don't go smooth, these kind of stuff.

The "slowness" of Unity has supposedly been fixed for 12.04, or if you enable the 'proposed' repository.

Ref: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/861061](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/861061)

---


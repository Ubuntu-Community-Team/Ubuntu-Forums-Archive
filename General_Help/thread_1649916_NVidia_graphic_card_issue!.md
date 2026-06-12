---
title: "NVidia graphic card issue!"
date: 2010-12-20
forum: General Help
---

### Post by nico932 on 2010-12-20
Hello!

I'm new to Ubuntu and it has been an awesome experience. However, learning how to use a new O.S. has proven a bit of a challenge. So far I managed to solve every single issue with some google searches, but right now that approach hasn't been able to provide an answer to the problem at hand.

Thing is, I suspect there are some issues with my graphic card drivers or configuration. Symptoms are:
- Slow playing of some streaming content (flash movies like loosing frames, or sometimes just freezing).
- Small glitches after some time playing of some HQ DVD movies.
- 3D emulation issues: Egoboo runs reaaaaally slow, and after hitting character creation, it just crashes. Similar problem with Never Winter NIghts: after hitting character creation, it crashes and console says "segmentation fault".

So, does anyone have any ideas about what could be the issue? Is it likely that the three problems are related or might the flash plugin be playing a role? 

My laptop is an HP dv6000 series, using an integrated NVIDIA motherboard. Graphic card model is supposed to be 7150m. Currently I'm running Maverik Meerkat (10.10) and using NVidia "Current" drivers.

Thanks in advance!

---

### Post by hoooootz82 on 2010-12-20
When you go to System>Administration>Additional Drivers, is the "current" one the top one with the bigger version number next to it, or is the "current" one the one at the bottom with the smaller version number? I always go with the newer version since it has better support for newer cards. However it is not tested as much so thats why canonical doesn't fully support it. Hope this helps, sorry if it doesn't.

---

### Post by DarkAmbient on 2010-12-20
If you still feel its slow after trying the previous posts directions, try turning off or atleast lower compiz effects. Might help. :-)

---

### Post by nico932 on 2010-12-21
Thanks for your replies!

First, it's not that my laptop runs slow. It actually works like a breeze. The only issues are the 3 I mentioned.

I've already tried your suggestions, as well as installing the Nvidia official drivers. I also tried lowering the 3D performance, without results.

Now, I have no clue where the problem might be. My computer isn't new, but it has been able to run way more resource demanding software than some flash streamed movies and the games mentioned.

Any other suggestion-ideas would be quite welcomed.

---

### Post by theasprint on 2010-12-21
Hi,

As my post says, I can help.

From my point of view, since Canonical has already "confessed" that they don't support Nvidia drivers, I would recommend you to do this way.

1. Turn off/Do not use the Nvidia drivers that Ubuntu provided you.

2. Then, go to Nvidia.com and download the latest driver for your Nvidia Card. Remember to download the Linux version.

3. Then turn off your gdm (graphics manager)
```
sudo service gdm stop
```

4. Install your driver while there's no Graphics running.
```
sudo bash <your Nvidia Driver's directory>
```

5. After installing, turn on your gdm
```
sudo service gdm start
```

*This way is good because you get drivers directly from the driver source

**Note that everytime you update your kernel version, you would need to re-install the Nvidia driver again.

Here is a thread where another also succeeded in his graphics:
[http://ubuntuforums.org/showthread.php?t=1648734]("http://ubuntuforums.org/showthread.php?t=1648734")

Good Luck :D

---

### Post by nico932 on 2010-12-23
That didn't work either. If anything, display did worsen!

For some reason the only way to get the nvidia driver working is after purging the existing drivers (sudo apt-get --purge remove nvidia). Now after that I can't even get the Cannonical drivers to work, even after installing the synaptic packages.

Only way to solve it is performing a clean install, which is kind of a bother. I think I'm giving up on this one...

Thanks anyway.

Cheers!

---

### Post by DarkAmbient on 2010-12-26
Perhaps a'lil to late. But I found this page. If you still having problems, perhaps it could help.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---


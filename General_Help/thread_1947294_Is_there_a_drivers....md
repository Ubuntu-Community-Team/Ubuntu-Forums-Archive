---
title: "Is there a drivers..."
date: 2012-03-26
forum: General Help
---

### Post by Rainersxd on 2012-03-26
Hellow agen ! This time I'm wondering if there are Video card: Sandy Bridge drivers somewhere for Ubuntu or any Linux system. I'm can't find them ! I'm looking already 2-3 weeks and no results ! I have tested all Linux systems (because I hoped then in other systems are drivers) and haven't find any results !
 Pleas help ! Or u can't help me and I will by able to white 3 moths to get new video card ? I don't won't ! I hope you are good people and will help me, but seriously ! Help !!!
 I need video card (Sandy Bridge) drivers for Ubuntu.

---

### Post by jerome1232 on 2012-03-26
Most drivers are simply included with the kernel and should be working automatically, are you having video issues or do you just think that you need to install a driver like this was Windows?

What's the output of this command?

```
sudo lshw -C video
```

---

### Post by Mark Phelps on 2012-03-26
If you're seeing a desktop, not stuck using a Command Line text interface, then you already HAVE video drivers installed.

If you're looking at System Information and seeing "unknown" for video drivers, realize that information is unreliable.

Unless you're having some kind of video issue on your desktop, there's no reason to go hunting around for other drivers.

---

### Post by Rainersxd on 2012-03-26
I have problems ! My video card aren't working ! It's like... It can't run any game ! The video card are inactive !

---

### Post by Rainersxd on 2012-03-26
Hmmm...

 *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:49 memory:fe000000-fe3fffff memory:e0000000-efffffff ioport:f000(size=64)

I got this thingy when I writhed that command.

---

### Post by jerome1232 on 2012-03-26
> **Rainersxd said:**
> Hmmm...

 *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: [COLOR="DeepSkyBlue"]driver=i915[/COLOR] latency=0
       resources: irq:49 memory:fe000000-fe3fffff memory:e0000000-efffffff ioport:f000(size=64)


That looks like the correct driver is already loaded, to my knowledge that driver should be fine, what games are you having trouble playing, just 3d games? To my knowledge these intel cards are not the best performing video cards around. Hopefully someone who knows a bit more about about intel graphics chipsets can chime in if I am wrong.

If the video card was inactive, you wouldn't be seeing anything at all.

---

### Post by Rainersxd on 2012-03-26
I gees I need close this topic. I played mincraft and there was a lines over my screen and textures were empty. Ok sory for disturbing.

---

### Post by jerome1232 on 2012-03-26
Perhaps this thread can help with your issue [http://ubuntuforums.org/showthread.php?t=1726735](http://ubuntuforums.org/showthread.php?t=1726735)

---

### Post by jockyburns on 2012-03-26
Could be that your video card is kaput. Mine packed up a few months back, so I'm just using the onboard graphics for now. You could try plugging your monitor into the onboard graphics connector. You might have to enter bios and set it to only use the onboard graphics though.

---

### Post by Rainersxd on 2012-03-27
1st It's impossible to title this topic as [closed] so I just will leave it in this time I gees.
 2nd I'm played different time of Minecraft Called Tekkit what is different (a lot).
 3th My computer is new and BIOS says that all is ok with graphics.
 4th There was some command what I timed and in system info there was showed status, but I was enable to do anything. Like there aren't no drivers !
 5th So in the End, what I'm soppost to do ?

---

### Post by jerome1232 on 2012-03-27
We have already established your video drivers are fine, have you tried installing oracles java? You are probably using openjdk right now, which can have issues with minecraft.

I haven't personally tested this how too but a quick glance looked about right.
[http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux](http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux)

Good luck.

---

### Post by Rainersxd on 2012-03-28
Thanks for all ! You all are angels !
My problems is ended ! Now I can rest in peas...

---


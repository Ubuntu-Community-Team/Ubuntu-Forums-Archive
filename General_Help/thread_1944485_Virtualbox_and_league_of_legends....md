---
title: "Virtualbox and league of legends..."
date: 2012-03-21
forum: General Help
---

### Post by Panxo on 2012-03-21
Hi guys...

I've finally could load lol into virtualbox. My host operative system is ubuntu 11.10 and guest is windows xp pro. I'm running it under oracle virtualbox 4.1.8

I've recently had to quit a match because of some graphic problems. I hate leaving game, but this time I really had to do that. 

First of all, the map is not completely shown as it was in the other computer I was using. Secondly, it has a lot of lag. Thirdly, the menu for buying items, cast spells and hp and manna is not completely shown, by that I mean it only shows the numbers. When I reach a new level, I don't see the plus upside the spell to upgrade it, and I have to guess where it is in order to do that. Fourthly, champions movements are shown really slow if not completely shown. I could be in the enemies tower and in a few seconds I'm in my tower, but it doesn't show how I reach there. 

For running lol, I've got to install the guest additions, enabled the 3d acceleration, installed directx 9.c and microsoft net framework. However, my computer shouldn't be doing this, I'm sure it's not a bad one if it can run lol under a virtual machine. Perhaps, I'm missing something elese.

Do you have any suggestion for this? I was really exited that I finally could play lol in my pc, but this is well... Frustrating...Should I try running it with a better operative system or?

---

### Post by QIII on 2012-03-21
You must remember that Virtualbox provides the guest OS with a hardware abstraction layer and does not allow the guest OS direct access to the physical hardware in most cases.  Although VBox has made great strides in attempting to provide direct access to hardware, they are still working very hard at making that fully functional.

In this regard, your host OS is not going to make much difference no matter what it is.

I generally tell people that although I have every confidence that VBox will eventually get to that point, the current state of affairs is that graphics-heavy applications like games are often not suitable for use in a VBox virtual machine.  It's hit and miss.  You take your chances and in this case it appears you are on the short end of the stick.

They will get there, I am sure.  But it is a difficult task and they can't make it happen over night.

Edit: In terms of what you can do right now, try giving the virtual machine more memory and more cores.

---

### Post by Panxo on 2012-03-21
Hi, QIII.

Thanks for your answer, but... I wasn't talking about changing the host system, but the guest... Sorry if I mislead you at some point of my post. I knew that some features are given to the guest by the host, but I thought that maybe it isn't a host feature failure.  And, I gave virtualbox the maximum I could of video memory (180mb I think) with no good results. Game is still not working as it should be.

As far as for the cores, I have no idea about what that is. May you explain that to me?

---

### Post by QIII on 2012-03-21
My point was that the guest is limited by the hardware virtualization layer between the physical host and and the virtual machine so there is only so much you can do in the guest to increase performance.

In the Oracle VM VirtualBox Manager, select (but don't start) your virtual machine.

Click the settings icon.  

On the System Tab, go to the Motherboard tab.  You can increase the memory committed to the virtual machine there.  If you have 8GB, for instance, you might give 4GB to the virtual machine. 

Then go to the Processor Tab and you can increase the number of CPU cores committed to the virtual machine.  If you have a 4 core processor, you might give 2 to the virtual machine.

On the Display tab, on the Video tab, make sure you have 128MB selected and 3d Acceleration selected.

Unfortunately, you can't get to  your graphics card directly, although VirtualBox will now try to use it if it can.  There is no setting for this.

For the time being, that is probably the most you can do to increase the performance of your virtual machine to try to get your game to work.

---

### Post by jerome1232 on 2012-03-21
I think you are misunderstanding, this isn't a failure on the host, it's a failure of virtualization software not being able to perform like real hardware does.

I believe in virtual box you can tick a check box that passes hardware 3d rendering to the guest, try that, also make sure to install guest additions, in safe mode you can even install experimental direct 3d support, try that.

Before you go doing all of that, clone your clean guest in case you bork it.

Allocate as much ram as you can to the guest without impairing the hosts ability to function (leave like 1gb for Ubuntu, that should keep unity happy) if you want to get really drastic, maybe even try a very, very light weight environment like openbox, to minimize demands on the host.


All that being said, gaming will probably be shaky in virtual box. (makes me want to try and fire up some Diablo II in my xp guest)

---

### Post by BertN45 on 2012-03-22
+1 for QIII

---


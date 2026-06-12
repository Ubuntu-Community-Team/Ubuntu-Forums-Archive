---
title: "COMPIZ: sphere or cylinder not working in v10.04"
date: 2010-05-01
forum: General Help
---

### Post by doublewitt on 2010-05-01
I'm happy with my new upgrade to 10.04!
I've discovered though, that in compiz settings, though activated,  the sphere and the cylinder no longer work. What can I do to fix this? Something changed in the upgrade process and they no longer work - only the cube works...

---

### Post by cloyd on 2010-05-01
You are not alone. I tried a live usb on my Gateway LT3103u Netbook. I set the USB to be persistent, and installed compiz.There was no option in the compiz configuration menu for cube deformation.  Had a few other issues, too. It ran my CPU about 10 degrees hotter, and screen scrambled upon going to Google. But somehow, the whole thing looked much more polished that my 9.04 or 9.10. I'm waiting for a solution to the compiz and a few others before I actually upgrade.

---

### Post by sparker256 on 2010-05-01
> **cloyd said:**
> You are not alone. I tried a live usb on my Gateway LT3103u Netbook. I set the USB to be persistent, and installed compiz.There was no option in the compiz configuration menu for cube deformation.  Had a few other issues, too. It ran my CPU about 10 degrees hotter, and screen scrambled upon going to Google. But somehow, the whole thing looked much more polished that my 9.04 or 9.10. I'm waiting for a solution to the compiz and a few others before I actually upgrade.

Have you installed compiz-fusion-plugins-extra? That may fix your problem.

Bill

---

### Post by doublewitt on 2010-05-01
> **sparker256 said:**
> Have you installed compiz-fusion-plugins-extra? That may fix your problem.

Bill

I can't recall how I did that! Please explain...
thx

---

### Post by GSF1200S on 2010-05-01
> **doublewitt said:**
> I can't recall how I did that! Please explain...
thx

```
sudo apt-get install compiz-fusion-plugins-extra
```

---

### Post by doublewitt on 2010-05-01
Thanks,
this is what happens in the terminal:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-fusion-plugins-extra: Depends: **compiz-core-abiversion-20090619**
E: Broken packages"

What's next?

---

### Post by GSF1200S on 2010-05-01
> **doublewitt said:**
> Thanks,
this is what happens in the terminal:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-fusion-plugins-extra: Depends: **compiz-core-abiversion-20090619**
E: Broken packages"

What's next?

Do you have any third party PPA's enabled in System>Administration>Software Sources? You can try:
```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
```
But that may not fix your problem if you have 3rd party repos enabled that do not provide repos for Lucid. Try that and then try:
```
sudo apt-get install compiz-fusion-plugins-extra
```
again and let us know what happens.

---

### Post by doublewitt on 2010-05-01
Most of my PPA's were "disabled" on upgrade to lucid. Why? - I don't know...

**sudo apt-get update** >> no packages were found

**sudo dpkg --configure -a**  >> seems like it did nothing

**sudo apt-get install -f**  >> lists packages that were automatically installed and no onger required... suggests to remove them...

**sudo apt-get install compiz-fusion-plugins-extra**  >> same problem = missing dependancy as mentioned above...
**[COLOR="DarkRed"]Depends: compiz-core-abiversion-20090619[/COLOR]**

---

### Post by GSF1200S on 2010-05-01
> **doublewitt said:**
> Most of my PPA's were "disabled" on upgrade to lucid. Why? - I don't know...

**sudo apt-get update** >> no packages were found

**sudo dpkg --configure -a**  >> seems like it did nothing

**sudo apt-get install -f**  >> lists packages that were automatically installed and no onger required... suggests to remove them...

**sudo apt-get install compiz-fusion-plugins-extra**  >> same problem = missing dependancy as mentioned above...
**[COLOR="DarkRed"]Depends: compiz-core-abiversion-20090619[/COLOR]**

Ubuntu does this to prevent dependency errors, although obviously depending on what you have installed, it can still give issues. I would suggest disabling all your PPA's (as they are designed for 9.10) and later on adding ones for Lucid (such as Mozilla PPA which I use). 
Open System>Administration>Synaptic Package Manager, search for:
> compiz
and remove all packages related to compiz (make sure you pay attention to the packages APT wants to remove- dont remove it if it wants to remove 500 packages). Close Synaptic
Open a terminal and type (Again, make sure all PPA's are disabled):
```
sudo apt-get update
```
Then do:
```
sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compizconfig-backend-gconf
```
Any additional dependencies it should pull when it downloads these packages. You should then be able to enable compiz, and should have the extra plugins.

---

### Post by doublewitt on 2010-05-01
Thanks for your response...
OK, did everything you said and in the terminal, after inputting the following:
*[COLOR="Blue"]sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core compiz-fusion-plugins-main compiz-fushion-plugins-extra compizconfig-backend-gconf[/COLOR]*

the result was:
[I][COLOR="blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-fushion-plugins-extra[/COLOR][/I]

the terminal stops here and installs nothing...

---

### Post by GSF1200S on 2010-05-01
> **doublewitt said:**
> Thanks for your response...
OK, did everything you said and in the terminal, after inputting the following:
*[COLOR="Blue"]sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core compiz-fusion-plugins-main compiz-fushion-plugins-extra compizconfig-backend-gconf[/COLOR]*

the result was:
[I][COLOR="blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-fushion-plugins-extra[/COLOR][/I]

the terminal stops here and installs nothing...

OMG.. wow do I feel stupid. Thats:
```
compiz-fusion-plugins-extra
```
NOT
```
compiz-fushion-plugins-extra
```
:oops:

---

### Post by doublewitt on 2010-05-01
don't worry - it's my mistake...! **lol**

---

### Post by doublewitt on 2010-05-01
OK, after lots of scribble, the final lines read:

[SIZE="2"][SIZE="1"]Setting up compiz-core (1:0.8.4-0ubuntu15) ...
Setting up libdecoration0 (1:0.8.4-0ubuntu15) ...

Setting up compiz-plugins (1:0.8.4-0ubuntu15) ...
Setting up libcompizconfig0 (0.8.4-0ubuntu2) ...

Setting up compizconfig-backend-gconf (0.8.4-0ubuntu2) ...
Setting up compiz-gnome (1:0.8.4-0ubuntu15) ...

Setting up compiz-fusion-plugins-main (0.8.4-0ubuntu3) ...

Setting up compiz (1:0.8.4-0ubuntu15) ...
Setting up compiz-fusion-plugins-extra (0.8.4-0ubuntu2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place[/SIZE][/SIZE]

what does the last line mean?
what do I do now?

Do I proceed to install ccsm?

---

### Post by doublewitt on 2010-05-01
OK - so I installed ccsm and all the plugins are now available - **thanks** that was really appreciated - but the sphere and cylinder still do not work... Is there a setting in ccsm that I am overlooking? - something that hinders the sphere or cylinder from rendering... *or maybe there is something else... what could it be...?*

---

### Post by doublewitt on 2010-05-01
OK - I know this might sound weird... but I discovered what the problem was [on my system]...

In ***[COLOR="DarkGreen"]Ubuntu Tweak[/COLOR]***, there is a setting that conflicts with compiz. When I select to "Hide icons on the desktop" - no sphere or cylinder can appear. 

*Hope this can be of help to others...*

---

### Post by kazulius on 2010-05-01
Hi there!
I tried to do every step, but I still don't get sphere, only cylinder... :(
I don't have Ubuntu Tweak installed.

---

### Post by doublewitt on 2010-05-01
There's probably another software that conflicts with your compiz settings. Maybe you can fiddle around with other softwares on your system. Look into applications with settings related to desktop rendering...

---

### Post by DeMus on 2010-05-03
I'm having trouble getting the Window Previews visible. I did what was told here, uninstall everything related to Compiz, disable PPS's and re install. Now sometimes I do get the previews. First when Synaptic was running to install CCSM, then they were gone again. When I start Ubuntu Tweak (just start it is enough) the previews re-appear. Switching of Ubuntu Tweak stops showing them. It is very weird.
Who can shine his light on this?

---

### Post by sb5551 on 2010-05-04
I am having the same problem with only being able to get the cylinder not the sphere. I will try removing Ubuntu Tweak, when I get back to my home computer.

---

### Post by Rubicon421 on 2010-05-04
Similar problem here. I have Ubuntu 10.04 32 bit installed on a P4 with a Radeon 9200 GPU. Initially the extras were missing from Compiz. I got that part figured out and now have all the features I was missing. 

The weird thing is that when I go to System>Administration>Hardware Drivers it says that there are no proprietary drivers in use (none listed as active or in the available section below). In 9.10 on this same system it found the driver. Compiz is working but acts a little funny now. It seems like my desktop will randomly un-compost itself. One minute the desktop cube will work and then a few minutes later it goes back to having desktop effects set to none. Usually I have to restart to get it back to normal.

I also have Ubuntu Tweak installed. I installed several Compiz packs through the Software Center but have not done anything extra in Synaptic or the terminal. It's a clean install of 10.04.

---

### Post by bpowell2005 on 2010-05-04
I have a related problem. Acer Aspire laptop with Intel M4 graphics chipset. Compiz did all I asked of it in Jaunty...upgraded to 10.04 (via a pit-stop in Karmic) and now I can't enable any desktop effects. In fact, when my computer first booted, it said, "Stuck in low res mode" but it still booted to my full size desktop. I also don't get any hardware drivers when I go to that menu (although, I don't remember if I did before).

Anybody get this solved yet?

It's very frustrating to "upgrade" to poorer performance.

---

### Post by martini1179 on 2010-05-06
I didn't have any extra plugins or Cylander/ Cube / 3D Windows in Compiz upon upgrading to Lucid. 

Here's what worked for me: 

Upgraded Compiz to 0.8.6 via Compiz PPA [[https://launchpad.net/~compiz/+archive/ppa]](https://launchpad.net/~compiz/+archive/ppa]) (this step is probably not necessary, this is just what I did)
Open Synaptic
Install missing package compiz-fusion-compiz-extra
Reboot (this is necessary, otherwise CCSM will not save changes)

---

### Post by sb5551 on 2010-05-06
My sphere now works. I didnt do anything, but two days ago there was an update for nvidia (not sure of any more specific detail), but when I restarted my computer (I know I don't have to but I still have a little Windows tendencies) everything worked great. 
 
I did have to go through synaptics to get the compiz extras package, I don't know why it wouldn't work through the terminal.

---


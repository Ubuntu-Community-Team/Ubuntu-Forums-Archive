---
title: "Lean Ubuntu installation for a thin-client box"
date: 2009-07-22
forum: General Help
---

### Post by hellmet on 2009-07-22
I'm trying to install Ubuntu on a thin-client box with only 512MB Flash ROM. 
All the functionality I need is the ability to run ICEwm or E17, connect to the network and run firefox. Nothing else.

Using the Alternate CD and the minimal install mode, I was able to achieve 670MB. But I'm stuck here. I would really appreciate any help that would help me remove unnecessary files and libraries.

Let me know if more details are needed...

---

### Post by t4thfavor on 2009-07-22
If its ROM its read only, and cannot be reflashed. I would bet that its just regular flash, and therefore you will be able to write to it. I think the server install is only 370MB, from which you can install icewm, or whatever WM is small enough to fit on it.


IS the flash a CF card, or is it soldered to the board? If its upgradeable, I recommend you do that.

---

### Post by Cheesemill on 2009-07-22
You're going to be hard pushed to get an installation that small.
Even a Ubuntu JeOS install takes up around 420 MB and that's command line only with none of the standard packages installed.

I'm guessing a Ubuntu CLI install will weigh in at just over 500 MB and that's before you add X and a window manager.

---

### Post by snowpine on 2009-07-22
Check out a "light weight" distro such as SliTaz.

---

### Post by Mighty_Joe on 2009-07-22
What kind of hardware are you using?  Can you boot from a USB drive?

---

### Post by hellmet on 2009-07-22
Well, I don't have the option of using another distro. I have been asked to use Ubuntu only. So, I will have to try and create a lean and mean distro. Will be trying JeOS tomorrow at work.

---

### Post by snowpine on 2009-07-22
IMHO, an unreasonable request has been made of you... Hopefully you can refer your boss to this thread and get permission to install a smaller distro.

---

### Post by Mighty_Joe on 2009-07-22
The problem with JeOS is that it is designed to run within a VM, and only contains the drivers necessary to play nice with them.  It just won't run on "real" hardware.
You could try starting with Ubuntu Server and building up ["Ubuntu Minimal"]("http://ubuntuforums.org/showthread.php?t=1155961"), but as others have noted, that's still a big footprint.
I have a Ubuntu Server box that's just a file and web server (Tomcat).  I just checked and it looks like it weighs in about 600MB without /var which occupies another 811MB.

---

### Post by snowpine on 2009-07-22
Another option is to set up the system on a different computer/virtual machine, then use an app such as Remastersys to create your own Live .iso image. Then, you can use Unetbootin (or similar) to run the .iso from the flash memory. This would only be in "live" mode, not a full, persistent install, but maybe that is all you need in this situation. An .iso is compressed, so a minimal install such as your should come in less than 500mb easily,

---

### Post by KeyserSoze93 on 2009-07-22
What about starting with [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and adding software manually during the install?

---

### Post by hellmet on 2009-07-23
What if I had to create something similar to JeOs but for just standard piece of hardware, like JeOS is only for VM. The only hardware that needs to be supported is the HP thin-client device and its been deployed uniformly across the organisation. 

Would somebody know how one would start on to create something like this? 

I really appreciate the help I'm getting from you guys.. :)

---

### Post by Mighty_Joe on 2009-07-23
I'm no expert at this but I have looked at running Linux on thin clients.  Don't thin clients usually load their OS via [PXE]("http://en.wikipedia.org/wiki/Preboot_Execution_Environment"), so the installed size of the OS isn't a concern, just the in-memory footprint?

---

### Post by hellmet on 2009-07-23
Probably, but our scenario is different. Our users don't need to connect via PXE. They shall have the OS installed *on *the thin client and all that they will be doing is accessing web apps using firefox. Saves the server from being overloaded(I guess).

---

### Post by Mighty_Joe on 2009-07-24
I looked into doing the same thing (install OS locally).  I'd love to have a thin-client box for the kids to play with, so if they broke it I'd only be out $50 or so.  From what I could find, some thin clients can boot from USB.  Is that an option?
What kind of hardware are you using?
I got frustrated in my project because searching for "linux thin client" brings up a lot of configurations using PXE, not for hacking the box to boot locally.

---

### Post by hellmet on 2009-07-24
Buying 500 + USB sticks is not an option. I'm using a HP 5530 thin client.. 
It is quite frustrating to find the minimal cli install > 550MB.
The JEOS would have been perfect had it been for a regular system instead of a VM since I was able to fit the entire system in under 420MB on a VM.

---

### Post by Mighty_Joe on 2009-07-25
The way i see it, your options are:
-set up a PXE server (basically a DHCP and file server).  It will be a lot easier figuring out that then flashing 500 thin clients.
-choose a different Linux distribution that is targeted at thin clients instead of Ubuntu, which is targeted at desktop hardware.

---

### Post by hellmet on 2009-07-27
Well, I think I have managed to do a 500MB install. To cut down further, I would like to know :

- Minimal firefox install - without installing any Gnome deps or extra, unneeded libs or packages
  apt-get install --no-install-recommends firefox still installs a bunch of packages
- Minimal xserver/xorg install. Just enough to fireup X (for IceWM or enlightenment)
- Minimal xfonts-base or alternative to it.

I guess that'll be all I'd need. Appreciate your help!

---


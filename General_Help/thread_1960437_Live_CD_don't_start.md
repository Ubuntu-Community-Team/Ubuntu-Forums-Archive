---
title: "Live CD don't start"
date: 2012-04-17
forum: General Help
---

### Post by jon08 on 2012-04-17
Hello everyone! I'm new with Lubuntu, but I know Ubuntu and other versions like Xubuntu or Kubuntu, also Kealla, Slax...

I want to try Lubuntu on an old computer (AMD Athlon XP 2000 1,6Ghz, 1Go RAM, 10Go + 20Go HDD) so I burned the .iso. When I boot on the CD, that work, I choose my language, but when I choose "Try Lubuntu" or "Install Lubuntu" I have a black screen with a little white line which blink in the left superior corner of my monitor and after, my monitor go to stand by with "no signal"  :-s

I precise that the .iso is the desktop version.


Thanks for you help! ;)

---

### Post by 2F4U on 2012-04-17
What is your graphics card? You could try booting with nomodeset (press F6 and select it from the menu) and see if that helps.

---

### Post by jon08 on 2012-04-17
My graphics card is an Nvidia TNT M64 32Mo. I'm trying your solution and I have the desktop! That work, but I have a question. If I install it on my HDD, what can I expect at next start? (Not live, but with HDD).

Thanks!

---

### Post by Mark Phelps on 2012-04-17
It's generally a bad idea to FORCE the install of any Linux distro on an untried PC.  Choose the Try Ubuntu option first.  That will allow you to see how well it detected your hardware and installed the proper drivers.  That way, if you have problems, you have time to research them and find fixes before you do the real install.

---

### Post by jon08 on 2012-04-17
I tried it! I just tried install option in order to see if the problem was present also here.

So, all work well, just videos not really smooth, but my graphics card is poor :P


What filesystem is recommended on my configuration?

---

### Post by jon08 on 2012-04-17
I installed it with EXT4 filesystem but at reboot, black screen... :(

---

### Post by marinara on 2012-04-17
you probably need a nomodeset fix.  What is your motherboard chipset and graphics card?

---

### Post by Bucky Ball on 2012-04-17
When you install you need to select F6, nomodset option also. Install it with that switch ...

When you boot and get to the grub menu (kernel options) choose the one you want to boot and hit 'e'. Find the line that ends with 'quiet splash' and add 'nomodset' to the end of that. Continue with boot (instructions are at the bottom). If that works, we can look at making that change permanent.

---

### Post by anejo on 2012-04-18
Given that this is an old machine... update the BIOS!
The 'quiet splash' and 'nomodset' should work after that... if even required.

---

### Post by mastablasta on 2012-04-18
> **Bucky Ball said:**
> When you install you need to select F6, nomodset option also. Install it with that switch ...
 
When you boot and get to the grub menu (kernel options) choose the one you want to boot and hit 'e'. Find the line that ends with 'quiet splash' and add 'nomodset' to the end of that. Continue with boot (instructions are at the bottom). If that works, we can look at making that change permanent.
 
they already said that with nomodeset parameter the desktop loads. so nomodeset should be made permanent.
for example:
[http://ubuntuforums.org/showthread.php?t=1761252](http://ubuntuforums.org/showthread.php?t=1761252)

---

### Post by Bucky Ball on 2012-04-18
> **mastablasta said:**
> they already said that with nomodeset parameter the desktop loads. so nomodeset should be made permanent.
for example:
[http://ubuntuforums.org/showthread.php?t=1761252](http://ubuntuforums.org/showthread.php?t=1761252)

Sorry. Way I understood it OP was trying Ubuntu from the CD with nomodset option but not that option when selecting to install. ;)

---


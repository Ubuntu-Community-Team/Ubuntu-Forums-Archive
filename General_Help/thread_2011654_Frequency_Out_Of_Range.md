---
title: "Frequency Out Of Range????"
date: 2012-06-27
forum: General Help
---

### Post by DarkBowser on 2012-06-27
I have Ubuntu 12.04 on a custom built machine.

1.800 GHz Quad Core CPU
The motherboard was taken from an HP machine, it's got 4 HD's
HDD1: Western Digital 300GB (desktop SATA II)
HDD2: Seagate 500GB (desktop SATA II)
HDD3: Western Digital Scorpio Blue 160GB (laptop SATA II)
HDD4: Hitachi 160GB (laptop SATA II) (boot disk.)
It's got 4GB RAM
it's got a stock power supply unit from the HP I mentioned earlier.
It's got 2 front USB, 4 rear.
I'ts got a card reader. No CD/DVD drive, I get my movies from the net.

The lights regarding power and disk usage are custom.

When I boot it up, the  BIOS screen comes on, then there's a blinking underscore in the top left for about a second then the monitor says, "frequency out of range".
Then 5.33 seconds later, the screen flashes and the Ubuntu login screen comes on, and everything is jolly good. How do I fix my "Frequency out of range"? It didn't happen with my old custom desktop, but only with this mobo. Help is most appreciated.:confused:

---

### Post by jmfal on 2012-06-27
Take a look at  this:

[http://askubuntu.com/questions/153040/frequency-out-of-range-please-change-display-mode](http://askubuntu.com/questions/153040/frequency-out-of-range-please-change-display-mode)

And this, Ithink you need to find out what your resolution is before you make any changes:

[http://superuser.com/questions/383806/horizontal-frequency-out-of-range](http://superuser.com/questions/383806/horizontal-frequency-out-of-range)

---

### Post by paulie-m on 2012-06-27
I had this problem exactly when i upgraded from ubuntu 11.04 to 11.10. i have left message on this forum and searched google but have had no sucess solving this problem. i have tried everything that people have suggested. if you solve this problem, please, please let me know. thanks, paul.

---

### Post by efflandt on 2012-06-27
One thing you did not say is what video card or chip you have.

---

### Post by drs305 on 2012-06-27
Try this:
Open /etc/default/grub. 
```
gksu gedit /etc/default/grub
```
Remove the [COLOR="Red"]#[/COLOR] symbol (uncomment) this line:

```
[COLOR="Red"]#[/COLOR]GRUB_GFXMODE=640x480
```
Save the file and run 
```
sudo update-grub
```
If that solves the issue we can take further steps.

---

### Post by DarkBowser on 2012-06-27
I executed the command in the terminal, and entered my password, and /ect/default/grub is empty.

---

### Post by DarkBowser on 2012-06-27
My graphics card is a Geforce 6150 SE. I tried everything you said. My native resolution is 1280x720.#GRUB_GFXMODE=640x480

---

### Post by drs305 on 2012-06-27
> **DarkBowser said:**
> My graphics card is a Geforce 6150 SE. I tried everything you said. My native resolution is 1280x720.#GRUB_GFXMODE=640x480


In your previous post the file may have been empty if you typed it as you did in your post.  */ect/default/grub* rather than */etc/default/grub*

I'm not sure if you accomplished it correctly in your second post or not. The reason for uncommenting is to force a resolution of 640x480. Even though you may get a specific resolution once booted, that same resolution may not be available to BIOS and GRUB (although 640x480 should be). 

You can check the available resolutions from the grub prompt. Press 'c' at the Grub menu and run:
```
vbeinfo
```

Another option in /etc/default/grub would be to not use graphics in the boot menu at all by **uncommenting** the following and then updating grub:
> [COLOR="Red"]#[/COLOR]GRUB_TERMINAL=console

---

### Post by oehq on 2013-01-28
I had this same problem..
turned out the the dell 531 PC 's video on the motherboard did not support the higher graphics required on the Unity desktop.

Switched to a low cost newer style video card $20 at Tiger direct and all works great now.:)

Hope this helps someone else

---


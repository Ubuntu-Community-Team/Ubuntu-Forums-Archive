---
title: "graphics problem with ATI utility"
date: 2009-10-01
forum: General Help
---

### Post by sagioto on 2009-10-01
hi,

I'm using both ubuntu 9/04 and win7 on this system,
i have a radeon hd 4850 card,
i downloaded the ati catalyst utilty and installed it on ubuntu,
suddenly when i boot up into ubuntu the screen becomes a mess of pixels, and i can't opertae the system,

i tried booting safe mode and the auto fix graphics but it didn't help.

what can i do?

---

### Post by pawhtiobo on 2009-10-01
Hi :)

First i think you should remove the ATI driver and utility, since the problem started after that:

[http://ubuntuforums.org/showthread.php?t=517225](http://ubuntuforums.org/showthread.php?t=517225)

See ya...

---

### Post by sagioto on 2009-10-01
the problem is i can't use ubuntu because i can't see anything,

how can i do it?

---

### Post by pawhtiobo on 2009-10-01
Hi :)

Start Ubuntu in recovery mode and select drop to root shell prompt:

[IMG]http://1.bp.blogspot.com/_LKra8AUL9bY/SRleYPWhWfI/AAAAAAAAALY/MetRjP9OxqU/s400/20081111149.jpg[/IMG]

There you can execute all the commands :)

See ya...

---

### Post by sagioto on 2009-10-01
hey,

i tried that but it says that xorg-driver-fglrx doesn't exist,

i also changed the language settings before i restarted,

the ubuntu loading screen actually apears to be in higher-res than it used to be but than when it finisihes the screen becomes a mees of pixels some gray some colorfull, dosn't look like anything...

i really don't know what to do?

should i reinstall the OS?

can i have access to these files from windows?

---

### Post by tom.swartz07 on 2009-10-01
[http://ubuntuforums.org/showthread.php?t=1156640](http://ubuntuforums.org/showthread.php?t=1156640)

I think we both have had the same problem.
If you can, follow along on the thread here ^

When you first turn on your computer, GRUB should appear, correct? 
If not, hit ESC when you first see the BIOS screen disappear. Boot into recovery mode and use

```
 locate ati 
```

then remove it

I think that the thread here should give a fairly good walkthrough

For future reference, ATI is notorious for not supporting video cards in linux. You also might be in the same boat as me- where ATI doesnt provide driver updates for the card either.

Best of luck! Post back with results

---

### Post by tom.swartz07 on 2009-10-01
You could also reinstall X using 

```
sudo dpkg-reconfigure xserver-xorg
```
and then restart your computer.

Do this only if it is still not working after uninstalling Catalyst Control Center and related packages.

---


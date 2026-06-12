---
title: "Help with start up"
date: 2010-01-30
forum: General Help
---

### Post by Mike2972 on 2010-01-30
Hello all. I am pretty new to Ubuntu and Linux in general so please forgive my ignorance if this seems like a silly question . 
I'm having a problem with Ubuntu 9.10. When I start my computer, Ubuntu will not start. But if I put my cd in it will. Is there a way to fix this?

Thanks in advance for any help.

---

### Post by audiomick on 2010-01-30
There probably is a way to fix it. You might give us some more info though...

Which version of Ubuntu do you have?
How is it installed? : alone on the computer, dual boot with windows or a wubi install
What sort of computer is it? Brand, cpu, ram size, desktop or laptop etc.

What happens when you try and boot? Any error messages? How does it behave?

---

### Post by Mike2972 on 2010-01-30
> **audiomick said:**
> There probably is a way to fix it. You might give us some more info though...

Which version of Ubuntu do you have?
How is it installed? : alone on the computer, dual boot with windows or a wubi install
What sort of computer is it? Brand, cpu, ram size, desktop or laptop etc.

What happens when you try and boot? Any error messages? How does it behave?

I'm using Ubuntu 9.10 Karmic Koala. Its alone on my computer. I get no error messages. The logo comes up like it's starting the the screen goes blank. 
my computer is a Dell 1.4ghz processor, 60 gig harddrive, 60 gig slave, 512k sdram

---

### Post by audiomick on 2010-01-30
Ok. More questions, sorry.
It could be a problem with the video driver, or with the boot sequence, I think.

so:
What is the video card?

Do you get to log in, or does it go blank before the log in?

---

### Post by Mike2972 on 2010-01-30
> **audiomick said:**
> Ok. More questions, sorry.
It could be a problem with the video driver, or with the boot sequence, I think.

so:
What is the video card?

Do you get to log in, or does it go blank before the log in?


I'm not sure what my video card is and no, I don't even get to the log in screen. If I boot with the disc It will do the same thing, but after about 15-20 seconds the log in screen comes up. Once i log in it runs fine.

---

### Post by audiomick on 2010-01-30
OK, it is time for the famous "boot info script" I think.

There is a possibility that your drive has a problem, or it is just not spinning up fast enough. I have had that problem. The solution, for me, was to open the case and check that all the cables were really plugged in right and lying "relaxed". One of mine was such that the connector was under a slight pressure the whole time. SATA connectors aren't that flash, really. As well as that, I went into BIOS and disabled all the "fast start" options I could find. Now the boot is a bit slower, but it is reliable. For what it is worth, I have Samsung drives. Cheap, but I wont buy them again.

The other possibility is that the boot loader is messed up, and that is where the boot info script comes in. It is a script written by forum member meierfra that seeks and prints out pretty much everything relevant to the boot process.

Go here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
follow the insructions, and post the result here.
If it turns out I can't help you, I am sure someone else will be able to.

---


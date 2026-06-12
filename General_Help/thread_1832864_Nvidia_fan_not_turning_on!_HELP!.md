---
title: "Nvidia fan not turning on! HELP!"
date: 2011-08-25
forum: General Help
---

### Post by necronzero on 2011-08-25
I have a nVidia 7900GS graphics card on my laptop, when I was on Windows, my cards fan worked properly without issue. When Im on Linux, (any distro) I install the appropiate drivers for the card and everything runs smooth.. When I reboot, my fan stops working, my card starts running hot, and my computer starts running slowly. Is there a way to change the settings for my fan to turn on and to make it turn on before the temperature reaches 75-80 degrees celcius?

---

### Post by sanderd17 on 2011-08-25
Can you try using the acpi_osi= option from my signature?

---

### Post by necronzero on 2011-08-25
> **sanderd17 said:**
> Can you try using the acpi_osi= option from my signature?

So I need to follow the "How to permanently set kernel boot options on an installed OS (not wubi)" part?

---

### Post by sanderd17 on 2011-08-25
> **necronzero said:**
> So I need to follow the "How to permanently set kernel boot options on an installed OS (not wubi)" part?

Better try the temporal part first. If it fails, you just need to reboot. If it works, you can make it permanent.

---

### Post by necronzero on 2011-08-25
> **sanderd17 said:**
> Better try the temporal part first. If it fails, you just need to reboot. If it works, you can make it permanent.

Ok, I'll be back in 20 minutes to let you know if it worked. Thanks in advance.

---

### Post by necronzero on 2011-08-25
Did not work! I noticed the fan only stops working when I have the nVidia drivers installed. What do I do?! My card is at 100degrees celcius atm.

---

### Post by sanderd17 on 2011-08-25
> **necronzero said:**
> Did not work! I noticed the fan only stops working when I have the nVidia drivers installed. What do I do?! My card is at 100degrees celcius atm.

You won't burn your card, the system will shut down when it's too hot. 

When I google your card, I see a lot of old entries of fan problems (2008 and 2009), but no recent ones. Are you sure you have the most current driver?

---

### Post by necronzero on 2011-08-25
> **sanderd17 said:**
> You won't burn your card, the system will shut down when it's too hot. 

When I google your card, I see a lot of old entries of fan problems (2008 and 2009), but no recent ones. Are you sure you have the most current driver?

Version 173, I uninstalled them though.

Edit, just downloaded latest nvidia drivers from their website, its a .run file, how do I install this?
Edit 2: found a way to install them, but I can't because it tells me X server is still running. :( What to do?

---

### Post by sanderd17 on 2011-08-25
try making it executable and run it from the terminal. If the file is calles nvidea.run and is in your home folder, do this:

```

chmod u+x nvidea.run
./nvidea.run

```

---

### Post by necronzero on 2011-08-25
> **sanderd17 said:**
> try making it executable and run it from the terminal. If the file is calles nvidea.run and is in your home folder, do this:

```

chmod u+x nvidea.run
./nvidea.run

```

ERROR: You appear to be running an X server; please exit X before installing.  For further          
         details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the  
         Linux driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by sanderd17 on 2011-08-25
If I'm right, xorg is restarted when you kill it, so going to a tty won't help.

Can you boot into a recovery mode and use the same terminal commands?

---

### Post by necronzero on 2011-08-25
> **sanderd17 said:**
> If I'm right, xorg is restarted when you kill it, so going to a tty won't help.

Can you boot into a recovery mode and use the same terminal commands?

Ok, I installed LATEST nvidia drivers and fan is OFF again -_-"

---

### Post by sanderd17 on 2011-08-25
Great, what now?

I found this here: [http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

Amongst its features, it has "adjust fan speed". But again, from 2009, I don't seem able to find anything newer with fan control.

---

### Post by necronzero on 2011-08-25
> **sanderd17 said:**
> Great, what now?

I found this here: [http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

Amongst its features, it has "adjust fan speed". But again, from 2009, I don't seem able to find anything newer with fan control.

Well, I made a new partition with windows. Fans work A-ok here, I had already tried nvclock, and it tells me that I can't adjust the fanspeed of my card, using the nvclock --fanspeed 40-60 etc...

When I had Ubuntu, my fan didn't turn on when I turned it on, but when my card reached 80°C i rebooted and the fan started to work properly. I changed to Kubuntu, tried the same method, and it won't work. It just wont. I've tried everything. 

God knows what's wrong.

---


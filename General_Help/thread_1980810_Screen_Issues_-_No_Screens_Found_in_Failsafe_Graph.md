---
title: "Screen Issues - No Screens Found in Failsafe Graphic Mode"
date: 2012-05-15
forum: General Help
---

### Post by phosphide on 2012-05-15
Hi all,

Ran into an issue lately when I had an external monitor hooked up to my laptop. I am dual booting 12.04 and 10.04 at the moment. I was using 12.04 and configured the external monitor using the NVidia X Server Settings configuration manager. I set the external to be the main X Screen and did a Twin View. I did not save it as a configuration file.

When I went to restart my computer, I pretty much lost almost all functionality. I could boot into 12.04 without problem until I got passed the login screen. At that point, the speed was incredibly slowed down, the icons on the menu were distorted, a weird screen showed up on the left detailing resolution fails and it was moving around (I can't explain this at all).

So I restarted and tried to run the recovery boot and get into the failsafe graphics mode to reset the X server. However, when I run the failsafe, I get this kind of message:

```
Fatal Server Error: no screens found. 
ddxSigGiveUp: Closing log
```

There was quite a bit of other information as well, but that was the main point and essentially it would kick me back out to the recovery boot options. Any idea of why this is? 

I'm using my 10.04 to post this as it's now almost impossible to use my 12.04 at all.

Here is my graphics card.

```
*-display               
       description: VGA compatible controller
       product: Quadro FX 570M
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:e5000000-e5ffffff memory:d0000000-dfffffff(prefetchable) memory:e6000000-e7ffffff ioport:4000(size=128)
```

Anything would be appreciated.

---

### Post by phosphide on 2012-05-15
I was able to slowly boot in and get a screenshot of the error message that would pop up and move around.

---

### Post by phosphide on 2012-05-16
Well, despite the overwhelming number of responses, I was able to find a solution.

```
sudo rm /etc/X11/xorg.conf
```

Hopefully this will help someone in the future. Probably would be best to back up the file too, just in case.

---

### Post by ivancarrerah@yahoo.co.uk on 2012-11-15
Big [FONT="Arial"][SIZE="4"][COLOR="Blue"]Thank U, U've rescued me![/COLOR][/SIZE][/FONT]:guitar:

---

### Post by pylover on 2012-12-31
Thanks very much , my problem also resolved.

---

### Post by Kernellinux on 2013-05-25
It's really too bad no one was able to help you. Thank you!! Thank you!!! Thank you!! For posting your solution even after you solved your own problem becuase a year later and you just saved me too!!!! I don't know who you are, I don't know where you live, but you are a good person!!


> **phosphide said:**
> Well, despite the overwhelming number of responses, I was able to find a solution.

```
sudo rm /etc/X11/xorg.conf
```

Hopefully this will help someone in the future. Probably would be best to back up the file too, just in case.

---


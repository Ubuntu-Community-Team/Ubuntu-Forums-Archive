---
title: "puter question"
date: 2009-12-02
forum: General Help
---

### Post by judge jankum on 2009-12-02
My son has an old Compaq Presario, it had an AMD K-6-2/380AFR He snatched it out and put an AMD K6 500 in it with 256 ram.... Could this cause havoc? and make it like super slow? We have an old Gateway running Ubuntu 9.04 with the same ram. We managed to get DSL on it but so slow it's not usable...  Any sugestions?

---

### Post by StuartN on 2009-12-02
> **judge jankum said:**
> so slow it's not usable...  Any sugestions?

The Ubuntu requirements suggest that Xubuntu would be more appropriate for your hardware:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by killa.fr0gg on 2009-12-02
StuartN is right. I think you'll find your machine to be much snappier once you replace GNOME with Xfce.

---

### Post by judge jankum on 2009-12-02
For some reason this thing is so slow it almost wont run anything.. I'm just wondering if changing the processor screwed it up.

---

### Post by judge jankum on 2009-12-02
I'm not a computer geek, but don't you have to update the chipset/ motherboard etc?

---

### Post by pbrane on 2009-12-02
If the compaq system board has socket 7 for the CPU then you should be fine. The socket usually says it on there somewhere. You might check the BIOS and make sure it sees the right CPU/chipset. The only thing would be if the system board clock won't run at 500MHz.

But running GNOME on that system will be _SLOW_. I agree with the others install xfce and see if that is better. If so then you can remove gnome.

---

### Post by User3k on 2009-12-02
Are you sure that motherboard can handle the new processor? Just because it is the same model doesn't necessarily mean it will work. Your best bet is to do a search online for that motherboard or the Compaq model and see if you can find the specifications somewhere. That should tell you what cpu's, etc, you can upgrade to.

---

### Post by StuartN on 2009-12-02
> **judge jankum said:**
> I'm not a computer geek, but don't you have to update the chipset/ motherboard etc?

No, it is a 500 MHz replacement for the 380 MHz original - but you could always put the slow one back in. There are possibly some FSB jumpers on the motherboard to get the full speed out of the 500 MHz processor.

Obviously if you say it is slow, then did it work faster before? This is a very slow processor with very small memory.

---

### Post by judge jankum on 2009-12-02
It was much faster before the "upgrade" lol!!!! It ran ok with Win2000  We found the 380 and put it back in...I think I'll try the Xubuntu, Vector linux keeps Installing up to the point of a black screen ...

---

### Post by Some Penguin on 2009-12-02
> **judge jankum said:**
> My son has an old Compaq Presario, it had an AMD K-6-2/380AFR He snatched it out and put an AMD K6 500 in it with 256 ram.... Could this cause havoc? and make it like super slow? We have an old Gateway running Ubuntu 9.04 with the same ram. We managed to get DSL on it but so slow it's not usable...  Any sugestions?

Comparing by megahertz isn't very useful when the processor design has changed.

---

### Post by some-what-Gnu-2-networks on 2009-12-02
Try U-lite: ubuntu for low powered machines.

---

### Post by judge jankum on 2009-12-02
Installing Xubuntu 8.04 right now, Got my "fangers" crossed...

---


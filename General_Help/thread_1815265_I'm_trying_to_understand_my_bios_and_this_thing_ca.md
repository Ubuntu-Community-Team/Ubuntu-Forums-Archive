---
title: "I'm trying to understand my bios and this thing called acpi"
date: 2011-07-31
forum: General Help
---

### Post by ClientAlive on 2011-07-31
Hi,

I have an old desktop machine I've been working on and learning a lot as I go. One of the things is it says it has a type of bios with a feature called "Enhanced ACPI." I've been gooling about it and I'm sure I'll have a lot of questions come up but I was wondering if I could just put down the things that first popped into my head. I was hoping someone can point me in the right direction. Maybe I can just list my questions and see if anyone can help?

The computer in reference is an HP Pavilion a1253 Media Center machine but is no longer entirely original. The mobo and CPU are though. More specifically though the CPU is an AMD 64 Athlon 3400+ (the specs would not indicate that detail).

This is a link to the manufacturer's specs for that machine in case it may help (again though not everything is still original):

[http://h10025.www1.hp.com/ewfrf/wc/documentSubCategory?tmp_rule=48080&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604](http://h10025.www1.hp.com/ewfrf/wc/documentSubCategory?tmp_rule=48080&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604)

And here's a link to the specs for the mobo:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604)

And here's a quote from that section that details the bios on that machine/ mobo:

> 
4Mb LPC EEPROM
HP BIOS with enhanced ACPI, DMI, Green, and PnP Features Plus


Here are the questions that have come to mind right off:

1> Is ACPI so widespread that any computer you buy these days is going to have it? Is all bios ACPI these days?
2> If the answer to the above is no, then can a person get a very current/ recent bios that is not ACPI? Could I (for that, specific, machine)?
3> If there is bios (I mean current/ modern bios) that is not ACPI is there some advantage to having that rather than the ACPI one? Supposedly Linux Torvalds though so when ACPI was coming out.
4> What's the difference between "Enhanced ACPI" and just ACPI? And could this "Enhanced ACPI" play a part in why I couldn't get Linux installed on that machine a time in the past? (About 4 mos ago or so).

There's also other things about my bios that I'm going to look into - like "DMI" and "Green". Whatever those are. I've been building this thing back up and now I've run into an opportunity, a reason really, to learn about these things. This would also be the best time to update or change the bios, if I were going to do so.

I'm assuming that bios (or should I say/ address cmos? I know they are not the same) - that it's compatibility or incompatibility is based on what chipset is on the board. Am I on the right track about that?

I'm gonna google the hell out of everything I can find on it tonight but I'm sure there will be a lot of things I just don't understand. If anyone can share a little on this I would certainly appreciate it.

Thanks.
-------------------

Edit:

Oh, and I forgot one other thing that I reaaaallly should ask. I've been wondering for a long time now (way before this) if there is such a thing as, like, aftermarket bios or cmos. You know, like the way you get aftermarket parts for a car when you customize it. Are there companies out there that write bios or cmos where that's all they do and they aren't the big companies like Microsoft and HP, who do much more than just bios and cmos? Maybe I have the wrong idea about "HP bios" in the first place though. I guess just because they call it "HP bios" doesn't mean HP had anything to do with writing it. Idk.

---

### Post by CatKiller on 2011-07-31
> **ClientAlive said:**
> Oh, and I forgot one other thing that I reaaaallly should ask. I've been wondering for a long time now (way before this) if there is such a thing as, like, aftermarket bios or cmos. You know, like the way you get aftermarket parts for a car when you customize it. Are there companies out there that write bios or cmos where that's all they do and they aren't the big companies like Microsoft and HP, who do much more than just bios and cmos? Maybe I have the wrong idea about "HP bios" in the first place though. I guess just because they call it "HP bios" doesn't mean HP had anything to do with writing it. Idk.

There are companies that primarily write BIOS software. Microsoft and HP don't write BIOS software. The ones you're likely to come across are Award, Phoenix and American Megatrends. Award and Phoenix are now the same company. The customisations that OEMs do to slap their own branding over everything can sometime also serve to make it so that you can't flash a generic BIOS for the motherboard chipset over the top of the existing BIOS.

Modern computers use EFI instead of BIOS, but people tend to still refer to that as the BIOS.

---

### Post by whitethorn on 2011-07-31
ACPI
[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

DMI
[http://en.wikipedia.org/wiki/Direct_Media_Interface](http://en.wikipedia.org/wiki/Direct_Media_Interface)

GREEN
[http://en.wikipedia.org/wiki/Green_computing](http://en.wikipedia.org/wiki/Green_computing)

I would suggest checking out the HPs webpage and see if they offer a BIOS update for you motherboard. Before updating I would back up my data first though.

---

### Post by CatKiller on 2011-07-31
To answer the meat of your question, all motherboards that you're likely to come across will support ACPI.

As is often the case with such things, from a sales perspective, "the way Microsoft does things" is more important than "what the specification says to do," so there was a bad patch where the behaviour of ACPI was buggy or incomplete. In the rush to market they were only tested against the Windows release of the time, which led to problems when using Linux or a different version of Windows.

For the most part these problems have been ironed out, either with more modern motherboards that didn't need to be rushed so they could be allowed to work properly, or with fixes in the Linux kernel.

There are kernel boot options to change the way the kernel interacts with the BIOS for those older, problematic, BIOSes; largely by ignoring some or all of the functions they expose and using legacy behaviour instead. You can also generally turn off ACPI in the BIOS settings, although some OEMs disable configurable options like that as part of their "value-added" customisations.

If there's a more recent BIOS available for that particular motherboard (bearing in mind that the OEM might have added value to it by taking away the option of flashing) then you should only update it if it gives you something that you actually want - support for newer processors, say, or larger hard drives, or if it explicitly fixes a problem you're having. Otherwise, the risk of a bad flash that breaks the motherboard (which is small but non-zero) has no reward to balance it against.

---

### Post by ClientAlive on 2011-07-31
> **CatKiller said:**
> To answer the meat of your question, all motherboards that you're likely to come across will support ACPI.

As is often the case with such things, from a sales perspective, "the way Microsoft does things" is more important than "what the specification says to do," so there was a bad patch where the behaviour of ACPI was buggy or incomplete. In the rush to market they were only tested against the Windows release of the time, which led to problems when using Linux or a different version of Windows.

For the most part these problems have been ironed out, either with more modern motherboards that didn't need to be rushed so they could be allowed to work properly, or with fixes in the Linux kernel.

There are kernel boot options to change the way the kernel interacts with the BIOS for those older, problematic, BIOSes; largely by ignoring some or all of the functions they expose and using legacy behaviour instead. You can also generally turn off ACPI in the BIOS settings, although some OEMs disable configurable options like that as part of their "value-added" customisations.

If there's a more recent BIOS available for that particular motherboard (bearing in mind that the OEM might have added value to it by taking away the option of flashing) then you should only update it if it gives you something that you actually want - support for newer processors, say, or larger hard drives, or if it explicitly fixes a problem you're having. Otherwise, the risk of a bad flash that breaks the motherboard (which is small but non-zero) has no reward to balance it against.

Ok, thanks. I have done some searching on HPs site but have come up empty on any bios update. I've also just done general google search for and come up empty handed too or directed back to HPs site. At this point, I'm not sure there even is an update available (or what it might offer anyway).

One of the things I want to do with that machine involves compiling a kernel but I recall having all kinds of problems trying to install Linux on it before. I imagine that if there's some problem, and I just jumped straight to compiling the kernel, I wouldn't find out until after hours and hours of effort. I'd like to make sure I get it sorted out before trying something that involves a lot of work like that.

I think what I'll end up dong is try to get a regular install on the thing; and, if it works, move on from there. I still have one other hardware issue to deal with first though.


> **whitethorn said:**
> ACPI
[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

DMI
[http://en.wikipedia.org/wiki/Direct_Media_Interface](http://en.wikipedia.org/wiki/Direct_Media_Interface)

GREEN
[http://en.wikipedia.org/wiki/Green_computing](http://en.wikipedia.org/wiki/Green_computing)

I would suggest checking out the HPs webpage and see if they offer a BIOS update for you motherboard. Before updating I would back up my data first though.

Thanks for the links. I love wikipedia. I'll check out those last to also.

---


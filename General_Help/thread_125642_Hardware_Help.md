---
title: "Hardware Help"
date: 2006-02-04
forum: General Help
---

### Post by frost_ad on 2006-02-04
A couple of weeks ago I started having some issues. My computer would freeze up occasionally, totally freeze up. It started doing it more frequently. At first I thought it was something in Ubuntu but I was having problems with my windows partition too.

Sometimes I couldn't even get into ubuntu, it would freeze up during the boot. But if I ran the memtest for a while I could get in. Eventually it would freeze up again though.

I kind of left it alone for a while (busy with school and work during the week) and was just using my ubuntu laptop. Every once in a while though I would notice that I could hear my desktops machines fans running, though nothing was on the monitor and the light around the power button wasn't on. If I held in the power button it would stop like I was doing a hard shutdown.

Today I decided to try and boot it up and get any critical data I had off of it. But now when I power it up several things happen (or don't happen)

1.The light around the power button doesn't come on,
2.The hard drive and cd drive lights do come on
3.Nothing displays on the monitor
4.If I boot with a knoppix live cd I can hear the cd drive spinning and loading and it sounds like everything is normal. However still nothing on the screen, and no light on the power button.

I'd really appreciate any help I can get on this. I'll list below the computer stats and some things I have tried

Emachines with an AMD Athlon XP 2600+ processor
ATI Radeon 9200 graphics card in an AGP slot
80GB hard drive 5400 rpm
512 MB RAM
250 Watt power supply

I've tried plugging the monitor into the ati card and in the motherboard vga. I've taken the ATI card out and tried the monitor in the motherboard vga too. I know the monitor is good I've run it off my laptop just to make sure.

Any ideas? I'm not real knowledgable in hardware so any help I can get will be really appreciated.

---

### Post by awahl on 2006-02-04
Sounds like it might be a psu (power supply) problem. Not sure which vendor eMachines uses, but it's probably a "bargain" nrand for sure. 

If you cannot get into the bios at boot may also be a cmos battery issue...

Try resetting the cmos (check your manual) - there's probably a jumper you need to change. You may also try removing the cmos battery for 5 min or so. 

Watch out for static...

Either way it doesn't sound like an OS issue to me, but who knows...

---

### Post by frost_ad on 2006-02-04
I'm thinking power supply as well. I guess the light not lighting up on the power button is what makes me think that. Why would everything power up though and nothing show up on the monitor? I think I'll check with a buddy that may have an extra power supply and see if that fixes it.

I still welcome any suggestions for fixing/diagnosing what the problem is.

---

### Post by handy on 2006-02-04
Check ALL conections, & test, remove all cards including graphics card if you have on board, & disconect drive cables form mainboard, test. If you still don't get a display, beg, borrow or steal a power supply unit (PSU) & swap to test.  If still no go, swap ram & test, swap cpu & test, swap motherboard!

If you have a success & you don't know which component was faulty, just add one & test, then another & test...

---

### Post by frost_ad on 2006-02-05
Ya, you're right. Easier said then done. Unfortunately I don't have all the extra parts to swap so liberally. However, later this afternoon I will have a psu to try and possible ram (I'm not sure if it is compatible). Hopefully one of those will work.

Thanks for all the help! (and continued help if anyone has any more suggestions!)

---

### Post by handy on 2006-02-05
CPU's fail very rarely, RAM is a little more common, & Motherboards a lot more common again. 

Unless they have been damaged by a power spike, (when literally anything can happen) either through the electricity mains supply or through the phone line; when through the phone line usually the PSU is ok, unless it was a really good spike from lightning that managed to come through both the power & phone lines!  Which does happen.  Or come through just the phone with such force that it can take out anything!

PSU's do fail more often than most parts of a computer, except fans of course, they are the all time winner:( .  

So, if you can swap PSU, that is pretty easy & cheap, if you must buy.  But try a test with all drives & cards disconected from the motherboard that is the easiest way to identify if it is one of the peripheral components, which can have surprisingly strange effects when they go bad!

As far a PSU's go there are 2 basic types for desktop (as in not notebook) machines.  The older AT which has a switch connected directly to the PSU via cable carrying mains voltage, that switch controls the PSU re: on/off.

The other current (no pun intended) model is the ATX which is controlled by the motherboard, so as to allow things like modem's & network cards to turn them on, amongst other more exotic features.  ATX does not have any wires going to a switch at the front of the machine, the switch wires directly to the motherboard on light gauge wire, because it carries a very small voltage.

**[EDIT:]**  I just looked at your original post again, you give your machines spec's, sorry I overlooked that I was comming from a search!   Your machine will definitely be an ATX power supply unit (PSU)!

If your machine used the AT type, you really should have no trouble getting a second hand one for next to nothing, as they are redundant.

If ATX, you will get a new one in the US, for $10 US, or less, in Aust' for about $20 Aus, or less. 

It's not hard, just be patient, carefull & use lots of light! :) 

All the best.

---


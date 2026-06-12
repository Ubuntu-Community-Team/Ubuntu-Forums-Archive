---
title: "Oh no!?!? Screen went black, loud beeping."
date: 2009-09-29
forum: General Help
---

### Post by paulmmj on 2009-09-29
Dear Ubuntu,

My Dell, which I upraded to Ubuntu from Windows about 3 weeks ago, recently just STOPPED WORKING. Symptoms include: not displaying anything on screen, the system speaker loudly beeping. It was brought on by nothing. It just, went black and started beeping and now it won't turn on. I recently reinstalled using the same disk I installed with because I wanted to have a clean slate, for I had downloaded various skins for Ubuntu and decided just that it'd be easier to reinstall than try to purge the computer of the skins I had so stupidly downloaded for a kick. But anyway, this is bad, right? I really hope it can be solved...

Thanks!
Paul.

---

### Post by jerrrys on 2009-09-29
boot up your live cd to make sure that ubuntu is the problem and not your computer...

---

### Post by paulmmj on 2009-09-29
Problem with that is, my screen isn't displaying anything. Like, I don't know, everything just stopped working. I wasn't doing any demanding tasks like video converting, I just logged on to my Facebook account, and then wham! Out of no where, black screen and beeping. The screen works, it turns on, it's plugged in, it just isn't displaying anything from my desktop.

---

### Post by ApEkV2 on 2009-09-29
What bios does your computer run, and what type of beeping is it (two short, two long) describe it.

---

### Post by paulmmj on 2009-09-29
Okay, okay, breaking news. It's displaying things again, and there's no longer any beeping. It said some sort of warning like "previous attempts to boot have failed, contact Dell customer support." I'm booting my Ubuntu CD and I will try and hit "fix" or something along those lines...

---

### Post by paulmmj on 2009-09-29
> **ApEkV2 said:**
> What bios does your computer run, and what type of beeping is it (two short, two long) describe it.

Thanks, and I believe it was just one "longish" beep at regular intervals. I don't know about what BIOS... It's blue?

---

### Post by ApEkV2 on 2009-09-29
If it was having trouble displaying anything on startup (and beeping), it's not ubuntu.
If nothing shows up on the screen on startup, it's the hardware.

What bios does the computer run? Every bios has different meanings for 
those beeps
Examples include Award, AST, AMI

---

### Post by betolima on 2009-09-29
You're describing two scenarios: first one machine is beeping, second one only the screen is black ... and you said you reinstalled the ubuntu, then somewhere in the way you were able to see your display working again .. is that right ?

---

### Post by paulmmj on 2009-09-29
Okay. I reinstalled Ubuntu, computer worked fine for about 10 mins, then screen went black and began beeping. At first that's all it'd do. The recently, it displayed the boot screen and booted from CD, but it subsequently went black and began beeping.

---

### Post by jerrrys on 2009-09-29
my gut is telling me you loss a fan

---

### Post by ApEkV2 on 2009-09-29
>  my gut is telling me you loss a fan 

I've had a fan go before, it doesn't even last ten minutes, but a possibility nonetheless.
What model dell do you have?

---

### Post by paulmmj on 2009-09-29
I'm afraid ten minutes was an overestimate, and that would make this the second time the fan has gone, so I would be much inclined to agree. Dell Dimension 4700. Very, very old for a computer. I use a Macbook with OS X for school and recording (GarageBand), but I used my old machine with Ubuntu to watch video streams on Hulu, and the fan would get very loud, so I believe. Before I take it to my friend to confirm the fan hypothesis, is there any self diagnostic tests I could run to confirm it for myself?

---

### Post by tom66 on 2009-09-29
I'd consider getting it repaired, because it sounds like a hardware fault.

---

### Post by ApEkV2 on 2009-09-29
>  Before I take it to my friend to confirm the fan hypothesis, is there any self diagnostic tests I could run to confirm it for myself?

there are, 
1. open your computer case
2. carefully take the fan off of the cpu heatsink (leave it plugged in)
3. while monitoring the temp of the cpu heatsink with your hand, turn on the computer
4. if the fan is dead, the heatsink will get hot to the touch and the fan will not turn on
5. turn off your computer once you've confirmed the fan is alive or not

(be sure to ground yourself first (static))

---

### Post by tom66 on 2009-09-29
Actually second thoughts. Take off the case and tell us how dusty it is in there. If it's dusty, get a can of compressed air and blow the dust out. Do NOT use a vacuum cleaner (as someone I can recall did), as you could easily damage the components by ESD.

---

### Post by ApEkV2 on 2009-09-29
> **tom66 said:**
> Actually second thoughts. Take off the case and tell us how dusty it is in there.

Ha lol I didn't think about how clogged with dust it could be.
It's always good to clean the inside of a computer now and then.

---

### Post by paulmmj on 2009-09-29
Thank you for all your help, and I've confirmed it is the fan. One big hint was that it doesn't turn on. Funnily enough, I was amazed at how smooth my old computer ran after reinstalling Ubuntu. I thought to myself, "it didn't even run this fast the first time I installed it." Additionally, the CPU was quite hot.

---

### Post by jerrrys on 2009-09-29
don't know how your dell is setup, but there can be more than one fan.  system/case fan; power supply fan; video card fan...

---


---
title: "Pc does not start anymore after updates"
date: 2012-01-25
forum: General Help
---

### Post by InspiredIndividual on 2012-01-25
This morning I updated some required packages using Synaptic. Upon completion, the system told me a restart was required. I chose to restart later and finish some work first. Just now I tried to do the required restart, but unfortunately my pc does not want to start anymore.

The startup process is not even getting started. The pc makes some normal noises until it starts beeping a few times, and then, nothing. The screen remains black; there seems to be no input whatsoever. 

I had a similar problem the previous time I had to do a required restart. At that time I managed to get my system up and running again by turning off the power completely. This time I tried the same, to no avail. I tried booting from a Live-CD, but that didn't work either. I am running the most recent LTS Ubuntu version (10.04).

Any ideas about what else I can try, or how to determine the possible cause of the problem? To me it seems peculiar that the problem occurs after a software update, while at the same time the failure to boot from a LiveCD suggests a hardware problem, right?!

---

### Post by Zimmer on 2012-01-25
Try investigating your 'Beep code' . Sounds like a hardware issue, not software.

If you get an unhelpful 'Motherboard failure' it is often due to overheating (not always, though,
[http://www.pantherproducts.co.uk/Articles/Motherboard/BIOSbeep.shtml](http://www.pantherproducts.co.uk/Articles/Motherboard/BIOSbeep.shtml)
[http://www.computerhope.com/beep.htm](http://www.computerhope.com/beep.htm)

[http://www.fixya.com/f/landing/tagspage/Bios_Beep_Codes](http://www.fixya.com/f/landing/tagspage/Bios_Beep_Codes)

---

### Post by InspiredIndividual on 2012-01-25
Thanks for the quick reply! The beep codes seem to differ depending on the manufacturer. How can I find out what kind of BIOS I have? I did a quick search on the forum, but the suggested ways to answer the question depend on the command line.

---

### Post by Zimmer on 2012-01-25
Usually you can go to the BIOS setup screen on boot and the info should be there (somewhere ). However, if the computer is not passing POST (Power On Self Test) you will need to refer to the manufacturer's specification (on their website or , if you are lucky, in the documentation) for your machine.

Good Luck

---

### Post by InspiredIndividual on 2012-01-25
Well, the computer was customly assembled, so I am not really sure how to find out. I suppose I could ask the guy who assembled it for me - he probably ought to know.

Anyway, the beep code is "1 long - 3 short". If I understand correctly, this could mean:

1. EGA/VGA (display error) in the IBM BIOS
2. Memory failure in AMI BIOS

Let me summarize to see if I understand correctly what I should do now. 

- If it's a display error: would it mean a problem with the video card or with the display adapter? In the first case, I would have to replace the video card. Could I rule out an adapter error by trying to plug the monitor into another computer?

- It it's a memory problem, is it be possible to check my 4 memory sticks by disconnecting all of them from the motherboard, and then rotating them in one after another to see if one of them is defective?

---

### Post by Zimmer on 2012-01-25
Likliest is Video Memory/card failure.

Try removing and re-inserting the Video card. If that does not solve the problem then maybe try a known working  Video Card....

---

### Post by grahammechanical on 2012-01-25
Is the motherboard an IBM motherboard. If so, then it will quite likely have an IBM BIOS chip. Non-IBM motherboards do not usually have IBM BIOS Chips.

You can open the case and look at the motherboard. You need to do that anyway. The BIOS chip might have the maker's name stuck on it.

Regards.

---

### Post by InspiredIndividual on 2012-01-26
I haven't located the problem yet, but I am posting a short update anyway since I figure that this information is useful for others with the same problem.

I found out I have an ASUS P5K motherboard, which has an AMI BIOS. 

According to the official documentation the beep code "1 long beep - 3 short beeps" indicates a memory problem. Hence, I went on to test my RAM. I removed all external hardware, opened the case and cleaned the inside with a soft brush and a vacuum cleaner. Afterwards I rotated my memory sticks in one after another and tried to boot my pc (with just keyboard and monitor connected). Surprisingly, both memory sticks worked fine. I double-checked my conclusion by performing a memtest (that was among the boot options). No errors whatsoever. Completely mystified, I removed all RAM from the motherboard and tried to boot, which resulted in the BIOS beep code "1 long beep - 2 short beeps". My conclusion is that the beep codes in the official documentation are probably wrong. A quick Google search led me to [this thread]("http://www.tomshardware.co.uk/forum/193422-13-asus-p5wd2-premium-long-short-beeps-blank-screen"), in which the discussion led to a similar conclusion.

I will continue to try and pinpoint the cause of my problems, but I thought I'd share the information I found so far in case other people with the same AMI BIOS run into a similar problem.

---

### Post by InspiredIndividual on 2012-01-29
I verified the meaning of my original BIOS beep code "1 long - 3 short" by trying to boot without a video card. This resulted in this exact sequence of beeps. Accordingly, it seems reasonable to conclude that the BIOS beep codes in the official specifications are mixed up. The correct beep codes seem to be:

ASUS P5K motherboard
AMI BIOS
"1 long beep - 2 short beeps" indicates memory failure;
"1 long beep - 3 short beeps" indicates video card failure.

and not the other way around as stated in most documentation on the web, including the official specifications for the AMI BIOS.

---

### Post by mcduck on 2012-01-29
> **InspiredIndividual said:**
> I verified the meaning of my original BIOS beep code "1 long - 3 short" by trying to boot without a video card. This resulted in this exact sequence of beeps. Accordingly, it seems reasonable to conclude that the BIOS beep codes in the official specifications are mixed up. The correct beep codes seem to be:

ASUS P5K motherboard
AMI BIOS
"1 long beep - 2 short beeps" indicates memory failure;
"1 long beep - 3 short beeps" indicates video card failure.

and not the other way around as stated in most documentation on the web, including the official specifications for the AMI BIOS.
There are many versions of each BIOS, and also the error codes can be changed to fit the hardware manufacturer's preferences. So unless you find information about the error codes for *your exact hardware*, you shouldn't take them as absolute facts.

(what I'm trying to say that you should search for error codes of Asus P5K, not AMI BIOS, if you want to make sure the information is correct.)

---

### Post by InspiredIndividual on 2012-01-29
> **mcduck said:**
> 
(what I'm trying to say that you should search for error codes of Asus P5K, not AMI BIOS, if you want to make sure the information is correct.)

Yes, I understand - more precisely, I understand that now. I didn't when I first encountered the error. The additional information I provided is more for the sake of others with a similar problem (diagnostics: AMI BIOS beep) who search the forum for more information, as I did myself before starting this thread.

Anyway, thanks for your clarification. I have a working video card right now, so I will connect all external hardware and mark the thread as solved if I manage to boot without errors.

EDIT: everything seems to be in working order again. Thanks to all of you for your help.

---


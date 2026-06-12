---
title: "Ubuntu Fried My Computer"
date: 2009-07-03
forum: General Help
---

### Post by BraydenW on 2009-07-03
My alternate computer has been happily running Windows XP for over 4 years without much going wrong.  I recently decided that because I have a newer computer, to install Ubuntu 9.04 on this old one and try it out.  I first used it as a live CD, which worked fine, and then installed it.  After install, I restarted the computer as prompted to. Ubuntu booted and ran for about 15 seconds then crashed completely.  Now my computer is bricked.  It will not power up.  No post, no fans, no nothing.  When I hit the power button nothing happens.  I find it hard to believe this is a coincidence as it has ran without problems for many years and suddenly dies 15 seconds into running Ubuntu.  Can anyone help me get my computer running again?

Here's the hardware specs...
Motherboard: ECS P4M800PRO-M478
Processor: Intel Pentium 4 @ 3.0GHz
RAM: 512mb
Video Card: ATI Radeon 9200SE
Hard Drive: Maxtor 120GB

Thanks to anyone who is trying to help and I eagerly wait for your replies.

---

### Post by wojox on 2009-07-03
This is a hardware problem. Unplug the computer from the back and hold the power button in the front in for 15 seconds.

Then plug back in and try to turn on.

---

### Post by BraydenW on 2009-07-03
Yes, I understand it is a hardware problem and I will try your suggestion there.  The thing I'm wondering is why did Ubuntu fry it?  I can't imagine it overheated my components while idling on desktop.  Is it incompatible with my motherboard chipset?  I can't see that either because I've Googled other people who seem to have it running seamlessly with the same motherboard.  I'm just confused.  I'll try your suggestion and get back to you.  I'm afraid I might be either trashing this computer or replacing some components though.

---

### Post by QIII on 2009-07-03
Post hoc ergo propter hoc is not a good method of diagnosis.

The fact that one thing occurs after another does not imply causality.  Ubuntu would not have "fried" your computer.

If it won't POST, you have a hardware issue.

---

### Post by synapsys on 2009-07-03
> **BraydenW said:**
>  I can't imagine it overheated my components while idling on desktop. 

You are right. There is nothing Ubuntu or any other operating system (for that matter) can possibly do to 'fry' your computer within fifteen seconds. It's most likely an unfortunate coincidence. 

From the symptoms you're telling me you have, this is what I think of:

Power Supply >> Motherboard >> CPU

I would first blow the insides out with some compressed air. Then put your nose close to the exhaust of the power supply, if it has gone bad you can usually smell some burnt wire nasty. If it smells alright, make sure all the power connections to the motherboard are properly seated. While you're in there you can also check the ram situation and make sure it's properly seated. Also visually inspect the motherboard and look for any blown capacitors and/or dark spots. 

Just as a long shot, you can remove and replace the CMOS battery, and see if that doesn't help anything. (looks like a watch battery)

You can get a power supply tester for relatively cheap nowadays, but pretty much the only way to troubleshoot motherboard/cpu issues is by replacing them. I'm just not sure that's really worth it on a p4.

---

### Post by sXeChris on 2009-07-03
I really doubt Ubuntu 'fried' your computer. I doubt any operating system is capable of that. Maybe it was a coincidence and the actual thing respoinsible was a hardware issue.

---

### Post by JOHNNYG713 on 2009-07-03
I have one of those motherboards and the same thing happened ! it is most likely your power supply ! check all the connections then.....replace the power supply! they don't give any warning before they fail .kinda like a light bulb! be sure to replace it with the exact same one,as these boards are VERY finicky ! our beloved ubuntu however had nothing to do with your rig's failure. good luck!:guitar:
johnnyg

---

### Post by BraydenW on 2009-07-04
Alright guys, it's back up and running and Ubuntu is running fine.  I guess it was a coincidence, a pretty big one.  My guess is that the power supply shorted because of an improper ground or something.  I checked the cable afterward and it's seen better days. I'll get a new one and it'll be running stable as ever.  Thanks for the help guys.

For the record, software can fry a computer.  Usually by methods of overheating.  Hence the word fry.  It was skeptical in this case because the computer was idling at the time.  Just a coincidence that the 2 events, install Ubuntu and interrupting power coincided so perfectly.

---

### Post by philcamlin on 2009-07-04
good to see that you fixed it :D

---

### Post by cariboo on 2009-07-04
If you have overheating components, that means that they are being cooled properly, either due to fans clogged with dust, or fans not working at all. Most motherboards have failsafes that shut it down if things get to hot.

I have a friend that thought his laptop was fried, because it would only run for 10 minutes and then shut down. It turns out the heat sink was so clogged with dust that it came out in solid chunks. All it needed was a good cleaning and he was back in business again.

---

### Post by tommcd on 2009-07-04
> **BraydenW said:**
> Alright guys, it's back up and running and Ubuntu is running fine.
Just out of curiosity, what exactly did you do to get it running again?

---


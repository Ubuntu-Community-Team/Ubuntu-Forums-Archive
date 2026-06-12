---
title: "Ubuntu Trouble"
date: 2010-07-13
forum: General Help
---

### Post by Volfan94 on 2010-07-13
Hey guys, earlier today I had been thinking about putting Ubuntu 10.04 on my older Desktop because I thought it would breathe some new life into it as Linux based software uses WAY less system resources than Windows Vista. Well, I downloaded Ubuntu and put it onto my USB Drive. I then hooked up my old computer, set the BIOS to boot from the USB Drive. It booted right up and I began messing around with Ubuntu, making sure I wanted to install it. I went up to the Ubuntu Panel on the top of the screen and clicked on the Power icon. I then clicked on suspend because I was going to be gone for a little bit doing something. I come back to try and wake it up...NOTHING. So I reboot my computer, still nothing...there's nothing even displaying on the screen. Can anyone please help?

---

### Post by Twitch6000 on 2010-07-13
> **Volfan94 said:**
> Hey guys, earlier today I had been thinking about putting Ubuntu 10.04 on my older Desktop because I thought it would breathe some new life into it as Linux based software uses WAY less system resources than Windows Vista. Well, I downloaded Ubuntu and put it onto my USB Drive. I then hooked up my old computer, set the BIOS to boot from the USB Drive. It booted right up and I began messing around with Ubuntu, making sure I wanted to install it. I went up to the Ubuntu Panel on the top of the screen and clicked on the Power icon. I then clicked on suspend because I was going to be gone for a little bit doing something. I come back to try and wake it up...NOTHING. So I reboot my computer, still nothing...there's nothing even displaying on the screen. Can anyone please help?

This is due to horrid suspend support on linux. It is getting better,but still one of those iffy things. However some distros seem to have better suspend support then others. You might wanna try one of them to see if it does any better.

---

### Post by dtrot55 on 2010-07-13
Yeah I agree...If your going to be gone...just shut the computer down if you don't want it to be on the whole time...I think Ubuntu loads up fast enough that it shouldn't cause any problems for ya...I also just have my laptop set up to do a blank screen after so long...suspend just caused me to have to reboot...so anythng that was set to suspend I changed to something else.

To address your issue...

Have you tried completely turning the computer off...and then powering back on?  That's what I had to do to my laptop when I would get stuck with a black screen during suspension?

---

### Post by Volfan94 on 2010-07-13
> **dtrot55 said:**
> Yeah I agree...If your going to be gone...just shut the computer down if you don't want it to be on the whole time...I think Ubuntu loads up fast enough that it shouldn't cause any problems for ya...I also just have my laptop set up to do a blank screen after so long...suspend just caused me to have to reboot...so anythng that was set to suspend I changed to something else.

To address your issue...

Have you tried completely turning the computer off...and then powering back on?  That's what I had to do to my laptop when I would get stuck with a black screen during suspension?

Yeah, I've tried that and still nothing but a black screen.

---

### Post by QIII on 2010-07-13
Suspend can be problematic for both Linux and Windows, particularly with older machines, when USB devices are attached.  Other causes can be frequency scaling, running daemons, APIC, older ATI graphics cards (from before AMD bought them).

Will the machine start without the USB device attached?

---

### Post by Volfan94 on 2010-07-13
> **QIII said:**
> Suspend can be problematic for both Linux and Windows, particularly with older machines, when USB devices are attached.  Other causes can be frequency scaling, running daemons, APIC, older ATI graphics cards (from before AMD bought them).

Will the machine start without the USB device attached?

No it won't start with the USB Drive removed. All I'm still getting is the black screen. This PC does have an ATI Radeon Xpress 1100 GPU.

---

### Post by QIII on 2010-07-13
I presume you have an OS on the hard drive?  Windows?

---

### Post by Volfan94 on 2010-07-13
> **QIII said:**
> I presume you have an OS on the hard drive?  Windows?

Yes, I have Windows Vista Home Basic 32 bit.

---

### Post by QIII on 2010-07-13
If you reset your BIOS to boot first from the optical drive, can you start a live session?

---

### Post by Volfan94 on 2010-07-13
> **QIII said:**
> If you reset your BIOS to boot first from the optical drive, can you start a live session?

I can't even get into the BIOS.

---

### Post by QIII on 2010-07-13
Do you hear any beeps during the POST?

---

### Post by Volfan94 on 2010-07-13
> **QIII said:**
> Do you hear any beeps during the POST?

No, the only things I hear when I attempt to boot my pc is the optical drive churning for just a second. I guess that's just part of the boot order since it has always done that.

---

### Post by QIII on 2010-07-14
Did you normally hear the beeps during the POST until now?

(Sorry about so many questions.  One step at a time.  I like to actually diagnose instead of reeling of a list of things it could possibly be.)

---

### Post by Volfan94 on 2010-07-14
> **QIII said:**
> Did you normally hear the beeps during the POST until now?

(Sorry about so many questions.  One step at a time.  I like to actually diagnose instead of reeling of a list of things it could possibly be.)

I've never heard any type of beeps whatsoever.

---

### Post by QIII on 2010-07-14
Difficult to use that diagnostically, then.  Is your system speaker hooked up?

(Oh, before I move on...  The optical drive spins up when power is applied.  That does not necessarily mean that it was queried by the POST.)

OK.  I don't want to fall into the trap of Post Hoc Ergo Propter Hoc here.  Roughly translated, that means "After this, therefore because of this."

Your problem is most likely hardware related.  This does not mean that your hardware was damaged by your experiment with Ubuntu.  Nor, unfortunately, can that be ruled out.

My first suspicion goes to memory, which is why I was hoping we could gather some information from the beeps during POST.  Most mobos indicate memory issues with a rapid or periodic and continuous beeping during the POST.

Let's do the basics first.  Can you remove the cover of the machine, then carefully remove and reseat your memory modules and all of your cards?  While you're in there, blow out the dust bunnies, grab a flashlight, and really check out your mobo for blown or swollen capacitors, scratched traces and the like.

Do you have more than one memory module?  Can you remove one and try to restart?  Remove the other and try to restart?  Swap all of your memory with known good modules?

Not trying to insult.  Just trying to start from the start.  Over the past 35 years, I have to admit I have been frustrated more than once by a computer that would not even turn on only to find that the dang power cable had been jarred loose!

---

### Post by Volfan94 on 2010-07-14
> **QIII said:**
> Difficult to use that diagnostically, then.  Is your system speaker hooked up?

(Oh, before I move on...  The optical drive spins up when power is applied.  That does not necessarily mean that it was queried by the POST.)

OK.  I don't want to fall into the trap of Post Hoc Ergo Propter Hoc here.  Roughly translated, that means "After this, therefore because of this."

Your problem is most likely hardware related.  This does not mean that your hardware was damaged by your experiment with Ubuntu.  Nor, unfortunately, can that be ruled out.

My first suspicion goes to memory, which is why I was hoping we could gather some information from the beeps during POST.  Most mobos indicate memory issues with a rapid or periodic and continuous beeping during the POST.

Let's do the basics first.  Can you remove the cover of the machine, then carefully remove and reseat your memory modules and all of your cards?  While you're in there, blow out the dust bunnies, grab a flashlight, and really check out your mobo for blown or swollen capacitors, scratched traces and the like.

Do you have more than one memory module?  Can you remove one and try to restart?  Remove the other and try to restart?  Swap all of your memory with known good modules?

Not trying to insult.  Just trying to start from the start.  Over the past 35 years, I have to admit I have been frustrated more than once by a computer that would not even turn on only to find that the dang power cable had been jarred loose!

Ok. Give me a few and I'll report back.

---

### Post by Volfan94 on 2010-07-14
Re-seating the memory did the trick! Thank you so much for your help! I guess if I end up putting Ubuntu on my PC that I will remember not to put it into suspend mode until they have addressed the issues. Lol

---

### Post by QIII on 2010-07-14
At least not with an older ATI card.  Suspend works fine for me with a supported AMD/ATI card.

I won't be so impolite as to tell you not to listen to know-it-alls who just say "Install something other than Ubuntu!"

Oh, wait.  I just did, didn't I?

---

### Post by Volfan94 on 2010-07-14
> **QIII said:**
> At least not with an older ATI card.  Suspend works fine for me with a supported AMD/ATI card.

I won't be so impolite as to tell you not to listen to know-it-alls who just say "Install something other than Ubuntu!"

Oh, wait.  I just did, didn't I?

I just got in installed about 15 minutes ago and I am VERY impressed! Ubuntu is the future in my opinion. I just don't see why Open-Source software isn't taking off. It's made for the people, by the people.

---

### Post by QIII on 2010-07-14
There is a steep learning curve if what one expects is Windows...

Don't just go with Ubuntu because it's your "first love".  I really highly recommend trying out several distros to see what you like and dislike about each.

My point was simply that there are those ... ahem ... who seem to have nothing better to do than to make post after post with no better goal than to distro-bash and give you a knee-jerk "Ubuntu sux" answer.  It may not be the distribution for you.  It's not all that is out there.

If you have enough resources, consider installing the PEUL version of VirtualBox and creating a series of virtual machines to run several.  Try Fedora for an RPM-based distro (Ubuntu is Debian based), Debian, Slackware-based, etc.

You might also want to try a direct Unix descendant like Solaris 10, OpenSolaris (which may, unfortunately, be on its death bed) or one of the BSDs.  If you go that route, some of them will take some tech-knowhow.

There are a lot of choices out there, and choice is what makes this thing great.

---


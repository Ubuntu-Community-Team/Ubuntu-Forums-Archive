---
title: "Black screen of death"
date: 2011-08-12
forum: General Help
---

### Post by RageMachine on 2011-08-12
[CENTER]:(   Black Screen Of Death   :(

[LEFT]1st i would like to say hello, and that i have come over from the dark side lol. YaY Linux.
I'm still kinda new to Linux / Ubuntu, i have been using Ubuntu 10.04 for about 3-4 months, and still learning the in's and out's.

OK enough chatting, my problem is this back screen of death. ( now going to be called B.S.O.D ) i have been running Ubuntu 10.04 for about 3 - 4 months with no problem tell about a week ago, i installed plymouth theme manager. ( splash screen themes)
Everything worked good for a bit then i started getting random B.S.O.D on boot ups and restarts, and i would boot up from an previous kernel, the restart the laptop again and everything would work fine, till my next random B.S.O.D.

Now that doesn't work i get B.S.O.D on:

Ubuntu, with Linux 2.6.32-33-Generic
Ubuntu, with Linux 2.6.32-33-Generic (recovery mode)
Ubuntu, with Linux 2.6.32-21-Generic
Ubuntu, with Linux 2.6.32-21-Generic (recovery mode)

I have tryed a few things to try and fix this.

in GRUB "press e " and tryed a bunch of cmd's but everything i try'ed ends up the same.
Some times i can see the load text but it goes buy so fast i cannot read it.

is their something i can do like windows pop in the cd and click repair lol.
i hope i gave enough info, and i did search the forms but everything i tryed didn't work.
thanks in advanced for the help:D
 
laptop: dell latitude 131L



                                                  > Thanks you decoherence for trying to help me, and responding so fast. 
So i fingered it out.

Ok so what i did was start my laptop pressed F12 to boot from cd, loaded up Ubuntu 10.04 LTS live cd
and ran a disk scan from terminal.
it said i had some kinda free space errors and bitmap size errors and  another one cannot remember what it was now. Now everything is good as  gold.... till my next adventurer lol.

     Code:
     fsck /dev/sda5 

 [/LEFT]
[/CENTER]

---

### Post by decoherence on 2011-08-12
Just to clarify a couple of things:

Does this only happen during boot or at random while you are using the computer?

Does it eventually finish booting and give you graphics?

thanks,

---

### Post by RageMachine on 2011-08-12
> 
decoherence:
Just to clarify a couple of things:

Does this only happen during boot or at random while you are using the computer?

Does it eventually finish booting and give you graphics?

thanks,only at boot, I can no longer get any kinda of graphics with the exception of GRUB loader screen

---

### Post by decoherence on 2011-08-13
> **RageMachine said:**
> only at boot, I can no longer get any kinda of graphics with the exception of GRUB loader screen

Perhaps plymouth is locking up when trying to load a particular theme?

Sorry, not an expert on plymouth but if you aren't using the default theme, perhaps a problem with whatever theme you're using is causing it?

---

### Post by RageMachine on 2011-08-14
Thanks you decoherence for trying to help me, and responding so fast. 
So i fingered it out.

Ok so what i did was start my laptop pressed F12 to boot from cd, loaded up Ubuntu 10.04 LTS live cd
and ran a disk scan from terminal.
it said i had some kinda free space errors and bitmap size errors and another one cannot remember what it was now. Now everything is good as gold.... till my next adventurer lol.

```
fsck /dev/sda5 
```

---

### Post by decoherence on 2011-08-15
Glad to hear you figured it out!

I guess fsck was running when you tried to boot up and either taking a really long time (with nothing on the screen, it looks a lot like a crash but would come up after potentially a really long time) or it actually hung (and would never come back up.) 

One thing that I didn't think of when I was responding to you but that I normally do in situations similar to yours is check the drive activity light (unless you're running on a mac then you don't have one. maybe you can hear it?) If I'm getting a blank screen but the hard disk is doing heavy activity, it's usually a good indication that fsck or some database rebuild is running and I may just wait it out.

Anyway, like i said glad you got it sorted!

cheers,

---


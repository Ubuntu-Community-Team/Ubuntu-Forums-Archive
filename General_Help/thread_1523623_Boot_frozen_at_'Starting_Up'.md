---
title: "Boot frozen at 'Starting Up'"
date: 2010-07-03
forum: General Help
---

### Post by firemaplegirl on 2010-07-03
I lost power to my ubuntu box earlier today, so it didn't shut down properly.  I'm now trying to start it but it keeps getting stuck at 'Starting Up' for over an hour.  I've tried pressing escape to boot a different version or into recovery mode.  The only difference I get is when loading a recovery mode it just puts up a flashing underscore instead of 'starting up . . .' - it still hangs there.  This is a small box without a optical drive which is why I haven't tried  a live CD.

Any suggestions on what else to try?  I'm not really familiar with linux or boot issues, so I'd appreciate clear through instructions on how to implement the suggestion.

---

### Post by Seanlol on 2010-07-03
> **firemaplegirl said:**
> I lost power to my ubuntu box earlier today, so it didn't shut down properly.  I'm now trying to start it but it keeps getting stuck at 'Starting Up' for over an hour.  I've tried pressing escape to boot a different version or into recovery mode.  The only difference I get is when loading a recovery mode it just puts up a flashing underscore instead of 'starting up . . .' - it still hangs there.  This is a small box without a optical drive which is why I haven't tried  a live CD.

Any suggestions on what else to try?  I'm not really familiar with linux or boot issues, so I'd appreciate clear through instructions on how to implement the suggestion.

Please run the boot script in my signature and post the results here. Be sure to code the results, please.

EDIT: No Optical drive, install it to a USB stick.

---

### Post by firemaplegirl on 2010-07-04
I need to be able to be in the OS to run the script either by booting from the hard drive or live disc, correct?

I installed the ubuntu-10.04-desktop-i386 iso to a usb using [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/).  I verified it worked on my (windows xp) netbook.  When I try and use it to start my ubuntu machine it hangs at "verifying dmi pool data".  The build currently installed on that box is Karmic, but I didn't think that would affect the live disc operation.  I'm downloading the 09.10 iso to try next though.

---

### Post by dino99 on 2010-07-04
can you boot on recovery mode ?

---

### Post by firemaplegirl on 2010-07-04
Nope. If I select any of the recovery modes a flashing underscore appears and it hangs on that.

---

### Post by robsoles on 2010-07-04
> **firemaplegirl said:**
> I need to be able to be in the OS to run the script either by booting from the hard drive or live disc, correct?

...

No. Seanlol's boot script actually needs to boot itself (I haven't checked by trying it, just going by his post here and looking at the stuff from the link in his signature) so as to dump info on why your system isn't booting in a normal way.

You can use another PC to make a bootable USB for this machine which can then boot it for a look-see. You can use Seanlol's stuff to make it a lot easier for him to help you or you can use a LiveCD written out to a USB stick to boot from.

Do you have another PC you can use to make the bootable USB? If so, I am guessing you'll need a 'walk-through' to get a bootable USB happening for you so just post back with this answer perhaps: 'what operating is that other PC running?'

---

### Post by firemaplegirl on 2010-07-04
> **robsoles said:**
> No. Seanlol's boot script actually needs to boot itself (I haven't checked by trying it, just going by his post here and looking at the stuff from the link in his signature) so as to dump info on why your system isn't booting in a normal way. Can you explain how?  Looking at the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1291280"), it appears that you have to be booted in the system to run it.  Perhaps I am misunderstanding it. 

> **robsoles said:**
> You can use another PC to make a bootable USB for this machine which can then boot it for a look-see. You can use Seanlol's stuff to make it a lot easier for him to help you or you can use a LiveCD written out to a USB stick to boot from. I made a bootable usb using the instructions on the ubuntu download page.  When I tried to boot with that using the most recent edition of ubuntu, it hung on 'Verifying DMI pool info" as mentioned below.

> **robsoles said:**
> Do you have another PC you can use to make the bootable USB? If so, I am guessing you'll need a 'walk-through' to get a bootable USB happening for you so just post back with this answer perhaps: 'what operating is that other PC running?' Yes, I have machines running both Windows Vista and Windows XP.  The XP netbook is significantly easier for me to access while troubleshooting the linux box than the vista machine.  (The linux box usually runs headless, so I have to manually switch the KVM between the two.  And yes, these components were used with the linux machine previously without issue, so I don't believe that they are the problem.)

---

### Post by robsoles on 2010-07-04
Stuck at work as I post but freer in 5 or so hours - will look harder at this about then...


here is edit: That looks like different boot info stuff to me than Seanlol's - why would he mention boot media (not optical but usb) if he didn't mean for his stuff to be booted?

---

### Post by firemaplegirl on 2010-07-05
I got to that thread by clicking on the link Seanlol posted and then clicking on the 'How To' link in the left column of the page.  Either way, it appears as if I need to be able to open the terminal, meaning I have to have booted the computer in some manner, and thus far I haven't been able to accomplish that.

---

### Post by robsoles on 2010-07-05
> **firemaplegirl said:**
> I got to that thread by clicking on the link Seanlol posted and then clicking on the 'How To' link in the left column of the page. ...

Sorry, not the first I've skimmed through something and gone off half cocked, I wish I thought it might be last but alas....

Ok, you say that when you try to boot from your USB stick it hangs at 'Verifying DMI pool info' which I am more used to being a BIOS step rather than a booting from hdd step.

Would you try to find the simily of 'Load failsafe defaults' in your BIOS and choose it, save it and then try to Boot off the USB stick - if it boots then perhaps just shut straight back down and try booting into a recovery mode off your harddrive again.

If you will load defaults in your BIOS then please post back what result that gets you but if you won't you'd better post that statement and we can try something else - just easier if you can stand to try failsafe defaults and if it won't boot up off that USB stick (and usb stick boots another machine no probs) then it seems like a hardware issue to me at this point!

---

### Post by firemaplegirl on 2010-07-18
Sorry for the delayed response, but I had to suddenly leave town due to a death in the family.  It looks like it is indeed a hardware issue.  I tried turning it on again, and there was a faint but distinct electric burn smell.  Upon cracking open the case I discovered several bulging capacitors.  I plan to contact the manufacturer to see if I can get the mobo replaced, but since it's out of warranty, I'll probably try a soldering iron and some new caps and see if that does the trick.  Thanks for all the help!

---

### Post by robsoles on 2010-07-18
Welcome regarding help, sorry to hear about bulging caps - glad to hear you are likely to be able to help yourself over that one ;)

---


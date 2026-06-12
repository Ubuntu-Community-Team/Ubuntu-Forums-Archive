---
title: "BIOS update after fitting new CPU, necessary???"
date: 2010-08-08
forum: General Help
---

### Post by migel_wimtore on 2010-08-08
Hello.

I have inherited a Dell Inspiron 1300 with a 1.6 Ghz Celeron M and would like to fit a Pentium M 765 2.1 Ghz.

My questions are, will i need to update the BIOS after fitting it, or can i just plug and play?

If an update is not necessary, as such, will i see any kind of gains from doing so?

and if an update is necessary will i have to do it from a boot CD?

Also, as a side note, i plan to eventually boost the RAM and install a bigger HD, will a BIOS update be required after fitting either?

Thanks.

---

### Post by GregBrannon on 2010-08-08
Inspirons are all laptops, right?  Is a CPU change possible?  Most of those laptop motherboards have the CPU soldered to the board.  Perhaps you know that, and it's not a problem for you, but I'd be surprised if it can be done at home.

Assuming you have the technology to get it done, I would check the internet to see if your Inspiron model was available with the CPU you'd like to use, and if there was or is now a BIOS version available for that configuration.  That should answer your first question.

As for upgrading the memory and HDD, the existing BIOS should be able to handle updates to both to the architectural limits of the laptop.  Depending on the age of the laptop, there's a possibility you could add something that the BIOS didn't know was possible when the laptop was put together, so updates should exist for the new possibilities.

Good luck!

---

### Post by Ginsu543 on 2010-08-08
As long as your current BIOS supports the new processor you want to install, it should work just fine. If it doesn't, obviously you will have to update the BIOS.

As far as whether you'll see any gains from updating even if not necessary, that will depend on what kinds of improvements the motherboard company put into the new BIOS. You should check out their website and compare the differences between the two versions. If the improvements they've made have no bearing on your system, then again there is no need for you to update.

To update the BIOS, you should follow the directions given by your motherboard manufacturer (should be on their website). Most motherboards update the BIOS using either a USB thumbdrive or a floppy drive. You just run the updater program which will copy the new BIOS image onto your motherboard's CMOS and will checksum it for you.

The BIOS can affect at what speed/timings/voltage you can run your ram. Check with the motherboard manufacturer to see which ram is compatible.

The HD should be least affected by BIOS version. The BIOS should be able to support most if not all HD models out there. Again, check with your motherboard manufacturer for compatibility.

---

### Post by migel_wimtore on 2010-08-08
Okay, thanks for the replies guys.

To answer your questions GregBrannon this little Inspiron 1300 (a model name and number) is such a tidy little laptop, it looks like splat, but it really is a nice little beast and cheap too, the CPU, RAM and HD are all very easily accessed, removed and changed, a far cry from the iBook G4 i'v just retired.

So, to suck your brain a bit more Ginsu543, would a workable method of finding out whether my BIOS supports the new CPU  be to just fit it (i know that the Pentium M 765 is supported by the Inspiron 1300 more generally, as for by the BIOS...), boot the beast and see what she says, if nothing, then go about updating the BIOS, or am i going to brick her?

Also, you say that to find out about any possible BIOS improvements i should check with my motherboad company, however it is Dell who provide a host of BIOS versions for download, so...?

Plus, how do i find out the brand of my motherboard? A program like Hardinfo perhaps? Would all Inspiron 1300s use the same brand? Okay maybe im just being lazy, i could probably find that out for myself, but...

As far as the RAM and HD go im planning to buy items expressly marketed at my model so probably no problems there right?

Thanks so much for the advise.

PS: iv never used so many ellipses before but... (:p) ...they just seemed to work.

Cheers.

---

### Post by Ginsu543 on 2010-08-08
I checked the Dell support website for the 1300 and the BIOS version available is the A10. What is the version you have currently?

When I initially responded to your post, I had in mind upgrading a desktop computer and not a Dell laptop (my fault, it just didn't register in my brain that you said you had a Dell Inspiron). So let me fine-tune some of my thoughts:

To upgrade your cpu, you have to make sure that it is pin-compatible with the socket you have. It looks like you already know the Pentium M 765 is pin-compatible, but if there is any doubt, you might want to give Dell support a call and ask one of their techs. Normally (i.e. for desktop motherboards), you have to make sure the motherboard provides the right voltage for the new cpu, and this is done through a setting in the BIOS (or you can let it use default settings which can read what the necessary voltage is from the cpu and set it automatically). With Dell BIOSes, however, you can't change that feature at all. So your best bet is to put the new chip in, fire her up, and see if she will POST. If you already have an OS installed, passing POST will immediately result in your OS booting. If, as you say, "nothing happens," then yes, you'll have to update the BIOS at a minimum.

Having said all this, I think it will be worth your while to just update the BIOS to A10 anyway. There is no point in figuring out what brand your mobo is because Dell usually gets them custom-made by the motherboard manufacturer with a few changes added in.

[An aside here, but a friend of mine once blew his Dell motherboard because he swapped out the Dell power supply with a third-party one. Unbeknownst to him, the Dell motherboard had an ATX power supply socket with some of the wire leads swapped. So when he plugged in the standard ATX PSU, it blew out his motherboard. This is one of the ways Dell forces you to buy their stuff.]

That is why you should always use Dell's BIOSes. As for RAM and HD, if you get ones expressly marketed for your model, you should be okay.

---

### Post by migel_wimtore on 2010-08-08
Yeh, sorry, could have been more specific about it being a laptop.

Well, i currently have A06 installed, so i guess il set about updating that. Though, is there any pressing reason i should do that before putting in the new chip? 

Impatient, you see.

Im pretty positive that the chip itself is compatible and should slot right in, as for the voltage, the Celeron is (according to Wikipedia) 1.004–1.292 V, while the Pentium is 0.988–1.356 V. If i read you correctly your saying that often you can adjust the voltage provided by the motherboard to the CPU in the BIOS but with Dell you cant, so all i can do is cross my fingers and hope that it makes the required adjustments by itself?

If so, will do.

As far as updating the BIOS goes, iv never done it before and am some  what intimidated. But, i suppose i might as well do it right? Live and learn. So, get  A10 from Dell burn it to disk and boot from it. Or, perhaps, follow instructions much like these ones:

[http://www.ubuntu-unleashed.com/2007/09/howto-easily-upgrade-dell-bios-in.html](http://www.ubuntu-unleashed.com/2007/09/howto-easily-upgrade-dell-bios-in.html)

?

Funny you should mention the power supply thing, this laptop was my  girlfreinds for ages and she eventually shelved it as it was drenched  in virus and had, what we though was a faulty power supply, boaght a  new one off ebay, same prob, got a chap to have a look inside,  apparently the power supply connector had come away from the mother  board (or something) so he soldered it, but it didnt hold and you had  to do all sorts of acrobatics to get it to register, and then force the  laptop to sit in that position (wire all tucked under and a wedge forcing  it up from behind), lest it stopped registering again. Then, i just saw this  third party one in my mates box of cables, thinking "thatl fit" and lo, it  did, and i havnt had a problem since.

As for as corporate lock-in goes iv been plinking away on an apple for the last seven years, granted it had been dual booting various GNUs for the last two (on a 30Gb HD!). So,  it might seem ironic to you but with this Dell, in terms of computers,  iv never felt freer:

"What i can take the CPU out and upgarde it! Be this terra beneath mine feat?

Nice one for all the help mate.

[IMG]http://forum.snesclassics.com/images/smilies/cheers.gif[/IMG]

---

### Post by Ginsu543 on 2010-08-09
Give it a go and let me know how it goes here

---

### Post by migel_wimtore on 2010-08-09
Will do, its on its way from your side of the pond, so il let you know in a few days.

---

### Post by migel_wimtore on 2010-09-25
Well, the processor took 2 months to arrive and, as a result, my findings are very unscientific. As i was bored whilst waiting, i just updated the BIOS ayways, for something to do, before fitting the new CPU.

So, i cant say whether the BIOS update was necessary or not, but the new chip was accepted by my laptop and my BIOS is up-to-date.

Alls well that ends well.

Thanks to Ginsu543 for all the help and advise.

Cheers.

---


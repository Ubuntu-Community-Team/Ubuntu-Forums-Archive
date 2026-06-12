---
title: "Fresh Install not working correctly"
date: 2010-03-19
forum: General Help
---

### Post by Justinv916 on 2010-03-19
I just built my PC and loaded ubuntu on it.
When the ubuntu desktop comes up everything looks ok. but when I click on any of the drop down menus, or anything else for that matter, the computer freezes immediately.
Ive tried copying the iso boot file to a new cd and reloading ubuntu but the problem remains. Ive also tried removing one of the two ram sticks,but again, the problem remains.
PC specs (in case it helps)
intel dh55hc board
intel i3 cpu 3ghz
2 Corsair 2gb RAM sticks
750 western digital HD
Sony lightscribe DVD drive

Thank you.
-Justin-

---

### Post by Rasa1111 on 2010-03-19
can you try to disable the "visual effects" in System> Preferences>Appearance> (visual effects, None)
See if that helps.   (will it stay "unfroze" long enough to do that?)

 if not, at least the thread got a bump. lol
sorry could not be more help. 
 good luck man.

---

### Post by Justinv916 on 2010-03-19
Thanks for the speedy reply.
I couldnt do that if i wanted, as soon as i click system ubuntu freezes.

---

### Post by Rasa1111 on 2010-03-19
no prob, 
ohh man,  sorry to hear that bro....

most I can do (besides my simple little "help" im able to provide once in a great while, lol) is just reply to  bump the threads that need help, 
and i usually learn in the process, so.....     Let us figure this out shall we? lol

  Ubuntu Pros~  is there not a way to be able to try and turn off compiz without actually being in the desktop?
(if thats even the issue, but it sounds like it may be)) 
 Im pretty sure there is a way, I just dont know of it off the top of my head. But I am pretty sure settings can be toyed with w/out being in the desktop. 

  enlightenment, anyone ?

---

### Post by wojox on 2010-03-19
When it freezes can you still move the mouse? Maybe an X problem. What Graphics card/chip do you have?

---

### Post by wilee-nilee on 2010-03-19
> **Rasa1111 said:**
> no prob, 
ohh man,  sorry to hear that bro....

most I can do (besides my simple little "help" im able to provide once in a great while, lol) is just reply to  bump the threads that need help, 
and i usually learn in the process, so.....     Let us figure this out shall we? lol

  Ubuntu Pros~  is there not a way to be able to try and turn off compiz without actually being in the desktop?
(if thats even the issue, but it sounds like it may be)) 
 Im pretty sure there is a way, I just dont know of it off the top of my head. But I am pretty sure settings can be toyed with w/out being in the desktop. 

  enlightenment, anyone ?

You can remove it from the command line at the boot by hitting c which gives you a command line.

I doubt that compiz is the problem though, OP how does Ubuntu run on the live CD?

---

### Post by Justinv916 on 2010-03-19
I have a GeForce 210 vid card. but i havent installed it yet. i figured i would get things going first then install it. Currently im just using the mobo as the video card.
When it freezes the mouse is frozen as well.
I havent tried running it from the cd.
Do you mean the cd that i used to load ubuntu?

---

### Post by wilee-nilee on 2010-03-19
> **Justinv916 said:**
> I have a GeForce 210 vid card. but i havent installed it yet. i figured i would get things going first then install it. Currently im just using the mobo as the video card.
When it freezes the mouse is frozen as well.
I havent tried running it from the cd.
Do you mean the cd that i used to load ubuntu?

Yes it is the best way to see if the ISO is working correctly and that everything is running as it should before installing. I would try the live cd now and see if you get the same anomalies.

I would also consider another download. I would check the disc for errors with the live cd on either this is a option on boot of the live CD, you can also check the md5 sums.

It may be a hardware problem so these are just options.

Does mobo mean motherboard, and do you have a graphics card running at all?

---

### Post by xifer on 2010-03-19
switch to console and check /var/log/Xorg.o.log file for any errs

you could also try to run top in the console and see what's chewing the cpu.

might be Xorg in which case restart X - do not reboot your machine!  just restart x and see if it recurs on subsequent logins.

---

### Post by Vlatzki on 2010-03-19
Is everything okay with your power supply ? I had the same issues with defective power supply, so... Check it  :)

---


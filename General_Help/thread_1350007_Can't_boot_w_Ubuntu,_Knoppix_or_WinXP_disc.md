---
title: "Can't boot w/ Ubuntu, Knoppix or WinXP disc"
date: 2009-12-08
forum: General Help
---

### Post by phatyphil on 2009-12-08
Hi Everyone,
New guy here, and I've got issues.  I recently upgraded my processor to an AMD Opteron 175 dual core and all was well.  I ordered a new fan for my processor and that's when all hell broke loose.  It seemed like a simple task, but after replacing the fan somehow my computer would not boot.  (I should say while I was in there, I also moved my hard drives around to more optimal locations).  I normally run Windows XP and it tried to boot in safe mode, but kept getting stuck after loading all the drivers.  So I downloaded Ubuntu to see if that would help me figure out what is going on.  I put the disc in and it starts to work, and I choose the 'run ubuntu without changing anything' option and then some code pops up on the screen with the last line being 3.116381 [<c0104007>] kernel_thread_helper+0x7/0x10  So that was last night and I was stumped.  Today I acquired a Windows XP disc (as mine had gone missing) and I downloaded Knoppix 6.2, neither which will work.  WinXP says an error has occured very early in the Windows setup and Knoppix just stops with a picture of the 'sad penguin' (those are my wife's words).  So I thought it may be related to my cd drive so I just loaded Ubuntu onto USB and it started to load and low and behold that same code/error message that happened with the CD boot pops up.  So now I am just confused/frustrated and all that.  I'm starting to think it may be a hardware issue and getting scared I damaged my processor or something like that.  Oh, I should also mention I tried unplugging all my HDs except for one and that didn't work.  I also tried to put in fresh/extra HD I have and that didn't work.  I have 4GB ram.  I don't know what other info may be useful.  I am very computer competant but this is really starting do get annoying.  Any input whatsoever is gratefully appreciated.  Thank you in advance!
-Phil in Oregon

---

### Post by u.b.u.n.t.u on 2009-12-08
> **phatyphil said:**
> I damaged my processor or something like that.

Hi and welcome to the Ubuntu community.

I would think that if the CPU is damaged, it would not work.

How many fans fit the current CPU?

In moving the HDDs, did you adjust the BIOS and HDD pins (if applicable) accordingly with reference to master, slave etc?

---

### Post by phatyphil on 2009-12-08
Thanks for the quick response.  Yes, I did adjust the BIOS and pins.  I was also thinking/hoping that since it does turn on, it was not the CPU (just starting to get frustrated and think the worst).  Technically, if all I had was a CD drive with no HD, should I be able to boot from disc, or no?  Just curious.

---

### Post by phatyphil on 2009-12-08
Oh, and only 1 fan fits the current CPU.  I got a Freezer 7 Pro Rev 2.

---

### Post by fluffman86 on 2009-12-08
Yeah you definitely have a hardware issue somewhere.  Follow these steps in order:

1. unplug all of your hard disk drives, and re-seat your ram and processor and fans to make sure everything is getting a good connection.
edit: and I *do* mean to UNplug your hard drives.  You don't need them to boot from CD or USB.

2. boot from the ubuntu cd or usb again, this time selecting the MemTest86 or Memory Test option.

3. If you get errors (a red screen) then you have a bad piece of ram somewhere.  If you are going to get errors, they will probably be before or during test #4.  Run the test all the way through, though, to be sure.  It will automatically run again if you leave it running.

4. Again, if you found errors, you won't know which stick of ram it was.  Remove all but 1, and re-run the test all the way through.  Do the same for *each* stick *individually*.  

5. Once you are running with *only* good RAM, you can choose "Try Ubuntu" again.  If you still get errors, then it's probably your processor or your motherboard.  Return it or buy a new one.

---

### Post by u.b.u.n.t.u on 2009-12-08
> **phatyphil said:**
> Technically, if all I had was a CD drive with no HD, should I be able to boot from disc, or no?  Just curious.


Correct. The BIOS will have a boot order. I have set mine that the CD-DVD drive is checked first, second the master HDD.

---

### Post by u.b.u.n.t.u on 2009-12-08
> **fluffman86 said:**
> Yeah you definitely have a hardware issue somewhere.  Follow these steps in order:

1. unplug all of your hard disk drives, and re-seat your ram and processor and fans to make sure everything is getting a good connection.
edit: and I *do* mean to UNplug your hard drives.  You don't need them to boot from CD or USB.

2. boot from the ubuntu cd or usb again, this time selecting the MemTest86 or Memory Test option.

3. If you get errors (a red screen) then you have a bad piece of ram somewhere.  If you are going to get errors, they will probably be before or during test #4.  Run the test all the way through, though, to be sure.  It will automatically run again if you leave it running.

4. Again, if you found errors, you won't know which stick of ram it was.  Remove all but 1, and re-run the test all the way through.  Do the same for *each* stick *individually*.  

5. Once you are running with *only* good RAM, you can choose "Try Ubuntu" again.  If you still get errors, then it's probably your processor or your motherboard.  Return it or buy a new one.

A very thorough walk through, but I would add one more point:

6. Have a cup of coffee on a table as it will take some time to do all this!

Let us know how it goes.

---

### Post by phatyphil on 2009-12-08
Wow, thanks for the tip fluffman.  It's running right now and nothing but errors.  This is testing RAM, correct?  How does that get damaged?  I have an extra stick I can try that wasn't in the computer, so maybe there is hope.  Thanks again for your help.

---

### Post by fluffman86 on 2009-12-08
Yes, that's testing RAM.  It can get shocked with static electricity and go bad, or you could have fried the slots on your motherboard.

Test each stick individually.  If they all test bad, then test them individually in each slot on your motherboard.  Then test a known good stick of RAM in each slot.  If THAT tests bad, then you have a bad motherboard, or at least know which slots are bad.

---

### Post by u.b.u.n.t.u on 2009-12-08
Stay with your original hardware. Just do the tests as advised by fluffman86. No need to change hardware if there is no problem.

UPDATE

With the RAM, before you handle it, touch the metal case. That will discharge static electricity. RAM should not be covered with dust and neither should the RAM slots - air in a can is useful. Make sure the installed RAM is well seated, with all the clips in their correct lock position.

---

### Post by phatyphil on 2009-12-08
Okay, we're getting somewhere.  I started the RAM test and found a stick that seemed okay.  Now I'm booting Ubuntu with just that stick and it seems to be working, we're well beyond the previous sticking point.  I can't thank you guys enough for the troubleshooting help.  I guess now I'll finish testing each stick/slot and see what we're left with.  I really appreciate it.

---

### Post by u.b.u.n.t.u on 2009-12-08
> **phatyphil said:**
> Okay, we're getting somewhere.  I started the RAM test and found a stick that seemed okay.  Now I'm booting Ubuntu with just that stick and it seems to be working, we're well beyond the previous sticking point.  I can't thank you guys enough for the troubleshooting help.  I guess now I'll finish testing each stick/slot and see what we're left with.  I really appreciate it.

Good news phatyphil, and credit to fluffman86, good call!

---

### Post by fluffman86 on 2009-12-08
;) you're welcome.

You may be able to boot back into windows now as well...but why? :P

---

### Post by phatyphil on 2009-12-11
I just wanted to thank everyone for the help again and thought I'd give a status update.  Turns out only 2 of the 4 ram slots are bad, so I was able to get things back up and running with no $ (which was great), and now have 2GB ram instead of 4.  Oh well.  Also I'm installing Ubuntu on an older machine and ready to get familiar with it and hopefully someday make the full leap from Windows.  Thanks everyone!

---

### Post by u.b.u.n.t.u on 2009-12-11
> **phatyphil said:**
> I just wanted to thank everyone for the help again and thought I'd give a status update.  Turns out only 2 of the 4 ram slots are bad, so I was able to get things back up and running with no $ (which was great), and now have 2GB ram instead of 4.  Oh well.  Also I'm installing Ubuntu on an older machine and ready to get familiar with it and hopefully someday make the full leap from Windows.  Thanks everyone!

RAM slots are the physical mainboard slots into which RAM (a RAM stick) are inserted.

Are the RAM sticks normal or better quality from a recognised manufacturer? Do the RAM sticks have dust, dirt, grim on them? Are they physically damaged or scratched or scuffed in any visible manner?

It may well be worth investing in  a can of compressed air for computer use. A careful burst into the RAM slots and the RAM itself, may well help to clean such. Use no other method of cleaning!

---


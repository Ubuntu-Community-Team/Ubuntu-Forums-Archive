---
title: "Skype Echo123 test call fails."
date: 2009-07-25
forum: General Help
---

### Post by DJonsson2008 on 2009-07-25
If I go to Options>Sound Devices Make a Test call, it starts to make a test call and then quickly comes up with "Call Fails"

At this point this is not a sound problem, as microphone, headphones seem to be working fine.

I can call 1800 stardard numbers and they seem to be ringing and answering, I've yet to bug any of my Skype friends by calling them.

The otherthing I notice is that the icons on my list of Skype friends do not turn green, they all remain greyed out, even when I know some of them are online from my windows machine.  Skype works on windows on the same lan, so this leads me to thing something needs be tweaked with Skype or Ubuntu/linux setup to make the test call work.

---

### Post by DJonsson2008 on 2009-07-25
I've now managed to test this situation with a Contact.

* The contact shows me as being offline, I see them as offline.
* They can send chat message to me, I can't send chat message to them.
* My call to a skype contact as well as skype test call both
return 'call failed'

* I can though call regular phones.

Is this related to my Skype linux incoming port?

Any clues appreciated

---

### Post by DJonsson2008 on 2009-07-25
I found elsewhere in the forums this idea...

"rm -rf ~/.Skype" then restart

I actually did this via nautilus using ctrl+h to
see the hidden .Skype directory. I renamed it to
error on the side of caution .SkypeWot and restarted
Skype.

---

### Post by DJonsson2008 on 2009-07-25
Oops forgot to say this resovled the test call 'call fail' problem

via nautilus using ctrl+h to
see the hidden /home/username/.Skype directory. I renamed it to
error on the side of caution .SkypeWot and restarted Skype.

anyhow test call and skype contacts are now on.

---

### Post by Midahed on 2009-10-02
THANKS!!  That fixed my problem.  No mention of it on the Skype 'support' site... :-(

Mike

---

### Post by javafiend on 2009-10-02
Awesome!  I was having the same problem and this fixed it.  Thanks!\\:D/

---

### Post by garba on 2009-10-06
i was having the same problem with the skype test call service, removing the skype data dir did it, thanks

---

### Post by mªrty on 2009-10-06
:lolflag: I think I saw 'skype' and 'support' in the same sentence

---

### Post by t4sseltine on 2010-11-04
Thanks! I had exactly the same issue - all fixed now. :)

---

### Post by tommacca on 2011-01-10
Same issue here too. This fixed it.

Thanks!

---

### Post by mattstat on 2011-02-24
I not only had this problem, but I could not even log on to Skype.  It started up and and said "Signing In..." endlessly, but never logged in.

Clearing the ~/.Skype directory solved all the problems.

I have the 64-bit version on Maverick.

---

### Post by SuperFabius on 2011-04-10
Having the same problem with the skype test call service in Ubuntu 10.10 32bit...

Removing the .skype dir solved it.

Thanks a lot  :P

---

### Post by tomsfeenie on 2012-06-24
Thank you, worked for me!

---

### Post by sffvba[e0rt on 2012-06-24
*Old thread **closed**.*


404

---


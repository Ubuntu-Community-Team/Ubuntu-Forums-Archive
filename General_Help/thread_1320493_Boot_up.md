---
title: "Boot up"
date: 2009-11-09
forum: General Help
---

### Post by tomharto on 2009-11-09
Is they anyway i can program ubuntu to start up at X oclock and go to sleep at X o clock on a weekday? Or is they not a option for that?

Thanks

---

### Post by tomharto on 2009-11-09
Is they a option to do this anywhere?

---

### Post by tomharto on 2009-11-10
anyone found a way to program ubuntu to do this function?

---

### Post by MelDJ on 2009-11-10
i dont think it is possible, because turning on the computer involves the hardware

---

### Post by tomharto on 2009-11-10
OK ty, i know the mac has this function but i was unsure to if ubuntu had

---

### Post by scouser73 on 2009-11-10
I think it can be done via the BIOS settings but you'd need to consult your own settings for that.

---

### Post by tomharto on 2009-11-10
Ok ill look in the BIOS, would put machine to sleep at x oclock be in the bios or is there a utility for that?

---

### Post by Devi1903 on 2009-11-10
If you wanted to put it to sleep and wake it up then that would be easy. To actually shut it down would mean you would need BIOS. I have been looking for a way to get machines to power on ethernet and how this works if anyone knows?

---

### Post by tomharto on 2009-11-10
Sleep and wake is fine, could you give me a quick guide on how to do it?

Thanks

---

### Post by Devi1903 on 2009-11-10
Well it seems to me the easiest way to do this would be a cron job to run the sleep command. Then rather than having to run sleep and wake up command you can just tell it how long to sleep for.

Have a look at the following for how to setup a cron job.

[HTML]https://help.ubuntu.com/community/CronHowto[/HTML]

Then the command you want to use will be something like "sleep h 12" if you run the cron at 7pm and want it to wake up at 7am.

---

### Post by kio_http on 2009-11-10
Starting up has to be configured in bios.

---

### Post by tomharto on 2009-11-10
Ty, once im done backing up ill test it, would wake be just wake h 12 or something?

---

### Post by Devi1903 on 2009-11-10
I have not played around with it myself as i have had no real need. I will have a play tomorrow and let you know what i find.

But from what i can see, if the system is told to sleep for 12 hours, then at the end of 12 hours it would just stop sleeping, so wake itself up. Therefore i see no need for a wake command at all.

But i will let you know once i have played around a bit myself.

---


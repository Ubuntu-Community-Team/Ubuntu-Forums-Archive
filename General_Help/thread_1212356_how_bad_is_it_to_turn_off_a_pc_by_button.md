---
title: "how bad is it to turn off a pc by button?"
date: 2009-07-13
forum: General Help
---

### Post by GirlofTime on 2009-07-13
Hello,  I'm going to be using a custom pc as a NAS but I don't want to leave it on all the time.  I can turn the pc off by holding in the power button for about 4 secounds.  Does this hurt the pc in anyway compared to shutting down the proper way through th os.  Thanks a bunch.

---

### Post by lisati on 2009-07-13
Sometimes holding the power button down for a few seconds is called a "forced shutdown". It's risky because, amongst other things, it bypasses any checks that the OS does to make sure all data is properly written to disk.

---

### Post by GirlofTime on 2009-07-13
> **lisati said:**
> Sometimes holding the power button down for a few seconds is called a "forced shutdown". It's risky because, amongst other things, it bypasses any checks that the OS does to make sure all data is properly written to disk.

That does sound risky.  Maybe I can learn how to ssh into it from my phone (G1) and do a shutdown command.  That sounds like the next best option.

---

### Post by paradigm2 on 2009-07-13
> **GirlofTime said:**
> That does sound risky.  Maybe I can learn how to ssh into it from my phone (G1) and do a shutdown command.  That sounds like the next best option.

Yes. Do not force a shutdown using the power button if you can help it.  sshing in is much safer. 

"shutdown -h now" (halt / shutdown)

"shutdown -r now" (reboot)

---

### Post by Shpongle on 2009-07-13
iv fried a mb before doing that i was messing round on an old pc, and was making hardware adjustments and rather than shutdown i just switched it off for speed , i was doing it a few times to test different components, 9 times out of 10 youll be alright but i still wouldnt leave it to chance,

---

### Post by badrunner on 2009-07-13
> **GirlofTime said:**
> Hello,  I'm going to be using a custom pc as a NAS but I don't want to leave it on all the time.  I can turn the pc off by holding in the power button for about 4 secounds.  Does this hurt the pc in anyway compared to shutting down the proper way through th os.  Thanks a bunch.

Most modern machines with acpi will actually get a signal when you just press the shutdown button (and not do the force shutdown hold), and gracefully shut them selves down. Obviously it depends on the particular hardware, but you can at least try this.

Im not sure which part of ubuntu is responsible for this, i imagine that its actually something in the desktop and power management code, so if you are just running a nas server im sure there is some config/a package you can install to make it work the same as the desktop.

---

### Post by bodhi.zazen on 2009-07-13
It also depends on the underlying file system.

I have had problems with data loss powering down like that with both ext4 and xfs .

set shutdown as a cron job ;)

---

### Post by GirlofTime on 2009-07-13
> **paradigm2 said:**
> Yes. Do not force a shutdown using the power button if you can help it.  sshing in is much safer. 

"shutdown -h now" (halt / shutdown)

"shutdown -r now" (reboot)

Thanks for all the replies.  And thank you for these commands.  Off to learn how to ssh into my pc from outside my network now.  I don't have wirless set up yet.  I'm paranoid what can I say.  =)

---

### Post by renkinjutsu on 2009-07-13
if you're paranoid about setting up your wifi.. you're gonna have even MORE trouble exposing your server to the big bad internetz D;

just make sure all of your ports are closed save the one you want to use.

---


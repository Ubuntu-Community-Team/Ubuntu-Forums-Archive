---
title: "Problems when attempting to boot"
date: 2010-03-22
forum: General Help
---

### Post by lpn8778 on 2010-03-22
Hi,

I recently installed Ubuntu 9.10 on my computer.  I previously had it installed alongside Vista, but I rarely used Windows and wanted to free up the space.  

The problem is that now my computer doesn't boot most of the time.  I have to restart it around five to ten times to get it to boot.  The rest of the time it just stops at a blank screen right after the BIOS screen.  

I tried to boot my 9.04 live CD and the Vista recovery disk, both of which I have successfully used before, but neither will work at all.  Does anyone have any idea what is going wrong?

---

### Post by Hikayu on 2010-03-22
Tell us **WHEN** this started. **WHAT** you did prior to this happening. And **WHY** this is happening (by providing a command line output.)

---

### Post by prodigy_ on 2010-03-22
> **lpn8778 said:**
> I tried to boot my 9.04 live CD and the Vista recovery disk, both of which I have successfully used before, but neither will work at all.  Does anyone have any idea what is going wrong?
A hardware issue, quite likely.

---

### Post by Hikayu on 2010-03-22
> **prodigy_ said:**
> A hardware issue, quite likely.

Not just likely, but *Extremely likely*.

I don't get exactly *WHAT* you're trying to do. Are you trying to reinstall your system? Or remove Windows? Or what???

---

### Post by lpn8778 on 2010-03-22
I am very new to all of this so I'm not sure how to provide a command line output.  Is there a guide for doing this anywhere?  Is there any way to confirm if it is a hardware issue?

---

### Post by Hikayu on 2010-03-22
> **lpn8778 said:**
> I am very new to all of this so I'm not sure how to provide a command line output.  Is there a guide for doing this anywhere?  Is there any way to confirm if it is a hardware issue?

Oh, a new person. Welcome to UbuntuForums.

Normally, providing a command line output involves copying and pasting. But I juts realized that you *can't* because you can't boot into Ubuntu. I believe that the best thing you could do is to fully document what you saw/did. It's the golden rule to posting questions. Sometimes people with potential to solve your problem won't even try without proper information.

---

### Post by lpn8778 on 2010-03-22
Sorry, I probably should have been more clear.  I am posting from work so I am trying to type whenever I can.  

I had no problems when I was dual booting Vista and 9.04.  Then I did a fresh install of just 9.04.  It upgraded to 9.10, I shut the computer down and the next day the problem happened.  I tried reinstalling 9.04 to see if that would fix it, but my computer would not boot from a CD at all.  

I apologize if this is too vague for anyone to really help me, but I appreciate the replies anyway.

---

### Post by Hikayu on 2010-03-22
> **lpn8778 said:**
> Sorry, I probably should have been more clear.  I am posting from work so I am trying to type whenever I can.  

I had no problems when I was dual booting Vista and 9.04.  Then I did a fresh install of just 9.04.  It upgraded to 9.10, I shut the computer down and the next day the problem happened.  I tried reinstalling 9.04 to see if that would fix it, but my computer would not boot from a CD at all.  

I apologize if this is too vague for anyone to really help me, but I appreciate the replies anyway.

No problem. But, I'm sorry to say, it's *still* vague. Did you *completely* reinstall the system (removing everything and installing 9.04) or did you install the fresh 9.04 on a new partition? Or did you remove the old 9.04 and replace it with the fresh one? Or is it something else?

I also have a theory : Your GRUB boot got corrupted.

---

### Post by lpn8778 on 2010-03-22
> **Hikayu said:**
> No problem. But, I'm sorry to say, it's *still* vague. Did you *completely* reinstall the system (removing everything and installing 9.04) or did you install the fresh 9.04 on a new partition? Or did you remove the old 9.04 and replace it with the fresh one? Or is it something else?

I also have a theory : Your GRUB boot got corrupted.

Yes, I completely formatted my hard drive and installed 9.04.

---

### Post by Hikayu on 2010-03-22
> **lpn8778 said:**
> Yes, I completely formatted my hard drive and installed 9.04.


You shouldn't have installed 9.04 if you wanted to upgrade to 10.04. Upgrading is the *worst* things you can do. It installs tonnes of packages you wont use (once I had 2 gigs used up) And commonly (like 35%) results in problems. Since you have no problems whatsoever with formatting your computer *again*, I suggest you install *9.10* instead of *9.04*. Heck, even go up to *10.04* if you want*.

And you said your DVD drive doesn't work. You could try with a LiveUSB instead of a LiveCD. Same thing. Just install the thing. It should be quick and painless.

---

### Post by Hikayu on 2010-03-22
Also, as for GRUB, there are many posts explaining how to revive it.

Cheers
Hikayu

Hope it works.

---

### Post by lpn8778 on 2010-03-22
> **Hikayu said:**
> You shouldn't have done that. Upgrading is the *worst* things you can do. It installs tonnes of packages you wont use (once I had 2 gigs used up) And commonly (like 35%) results in problems. Since you have no problems whatsoever with formatting your computer *again*, I suggest you install *9.10* instead of *9.04*. Heck, even go up to *10.04* if you want*.

And you said your DVD drive doesn't work. You could try with a LiveUSB instead of a LiveCD. Same thing. Just install the thing. It should be quick and painless.

I'll try that as soon as I get home.  Thank you for putting up with my ignorance.

---

### Post by Hikayu on 2010-03-22
> **lpn8778 said:**
> I'll try that as soon as I get home.  Thank you for putting up with my ignorance.


No problem. I learned it the hard way too. I'm currently fixing my mistakes, that's why I'm on the forums. Nothing to do. ;)

---


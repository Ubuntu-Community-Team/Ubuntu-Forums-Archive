---
title: "&quot;Quiet splash,&quot; need to be removed from grub by default"
date: 2009-10-10
forum: General Help
---

### Post by petrus4 on 2009-10-10
One of the most consistent help topics I've noticed in here, revolves around Ubuntu users ending up in front of a non-functional, apparently unrecoverable black screen.

Pretty much every time, the suggestion is to go back in, in recovery mode, and edit /boot/grub/menu.lst to remove "quiet splash," from grub's boot options, so that people can get the normal debug and error messages which the system produces, so that they can actually find out what went wrong, and how to fix it.

I want to propose that these options, "quiet splash," be removed from grub by default in the next version of Ubuntu.  Having the initial text appear will not harm users when everything is working fine, and when things cease to work, it will provide them with valuable information, which they can then bring here, in order to get more specific (and thus effective) help for solving their problems.

---

### Post by SkyNet2029 on 2009-10-10
the same can be had by posting the output of
```
$dmesg tail | more
```

---

### Post by aheckler on 2009-10-10
A more appropriate place for this suggestion might be [Ubuntu Brainstorm]("http://brainstorm.ubuntu.com/").

---

### Post by petrus4 on 2009-10-10
> **SkyNet2029 said:**
> the same can be had by posting the output of
```
$dmesg tail | more
```

Not if the system crashes partway through the boot sequence, it can't.

---

### Post by CatKiller on 2009-10-10
What you want your machine to do when you're troubleshooting is not the same as what you want your machine to do normally.

While some people like having arcane text scrolling up the screen, it would hardly help us shake the "Linux is only for geeks" image, would it?

+1 on putting the idea on Brainstorm, since that's what Brainstorm is for, but -1 on the idea itself.

---

### Post by wojox on 2009-10-10
It's already enabled.

Reboot your computer
Hit “Esc” when prompted in order to enter the GRUB menu.
Select the proper kernel and hit the letter “e” to edit.
Arrow down to the Kernel line, and hit the letter “e” again.
You should see the last few words in the line. Remove the words “quiet splash” and hit enter.
Hit the letter “b” to boot the kernel without the Ubuntu splash screen.

That will temporarily disable it.

---

### Post by CatKiller on 2009-10-10
> **wojox said:**
>  That will temporarily disable it.

That's my point. Whatever reason you want to see boot-up text for, it's a temporary reason. It's not something that you want every time for every single user of Ubuntu worldwide.

---

### Post by Frak on 2009-10-11
I agree with both points. Ubuntu needs to drop the fancy glitter to find out the errors, while Ubuntu still lacks support some a section of hardware that exists. Though, due to the attempt to try and overcome the "Geek" image, glitter is put on, leaving some users out in the cold with a black screen, waiting for something to happen.

That's why it's not 100% ready yet for mass distribution, and it won't be for the next 30 years.

---

### Post by barthel on 2009-10-11
What would be nicer would be a "verbose" entry in the grub menu. Then instead of forcing a user to edit the command, they could simply move the cursor and hit [ENTER].

---


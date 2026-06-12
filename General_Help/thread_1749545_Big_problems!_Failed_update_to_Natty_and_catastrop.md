---
title: "Big problems! Failed update to Natty and catastrophe!"
date: 2011-05-04
forum: General Help
---

### Post by rotors on 2011-05-04
So I was updating to Natty (from the latest stable release with all updates) when my computer lost power (laptop battery ran too low) and shutdown! I was so close to plugging it in.

Now this is the problem I have when I boot up:

init: udevtrigger main process (483) terminated with status 1
init: udevtrigger post-stop process (487) terminated with status 1
init: udevmonitor main process (482) killed by TERM signal
The disk drive for / is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery

When I press "S" a bunch of stuff comes up, then the computer goes to a blank screen with a blinking cursor at the top right and doesn't do anything 

If I wait, nothing happens.

What should I do? Is there some manual recovery command I can do to fix all this?

Thanks!

---

### Post by dniMretsaM on 2011-05-04
What happens when you hit M?

---

### Post by rotors on 2011-05-04
When I press M i get this:

[I]Root filesystem check failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system
root@*computername*: ~#[/I]

---

### Post by rotors on 2011-05-04
i'm trying to run fsck but I don't know which drive to target. and I'm not sure about the command prompt and where to run it. I do have a live cd 10.10, and I can get a live cd of 11.04 but I dunno which to use and how to use them to fix this.

---

### Post by rotors on 2011-05-04
any help?

---

### Post by Hedgehog1 on 2011-05-05
If you can get an 11.04 LiveCD, that will be helpful later.

Right now, if you can boot off your 10.10 LiveCD/LiveUSB, you can copy any documents you may not have backed up to and external hard drive or USB stick.

Then, please do the following so we can see what the status is of your install:

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

p.s. Do you have a separate '/home' partition?

---


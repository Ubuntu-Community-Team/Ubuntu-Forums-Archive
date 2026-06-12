---
title: "Random Shutdown/Power Off"
date: 2010-01-24
forum: General Help
---

### Post by dch24328 on 2010-01-24
I've been using Ubuntu on and off since 8.04, but only last week decided to make a real switch across to it. After installing 9.10 64bit though, my laptop while running Ubuntu just turns itself off at completely random times - it doesn't seem to go through any shut down procedure or anything, it's more like the power's just suddenly cut. It sometimes happens 5 minutes after being turned on, or sometimes 4 or 5 hours, it really is random.

I really have no idea where to even begin trying to stop this. I think it must be a software thing because this has never happened with windows or earlier versions of Ubuntu, but other than that I don't know what to do to stop this.

I'm dual booting Windows 7 32bit and Ubuntu 9.10 64bit, and this is on a Toshiba L350-D 11-D laptop, which has a 64bit AMD processor. I'd really like to switch completely but this fairly major problem is holding me back, so any help would be really appreciated. Thanks.

---

### Post by happyhamster on 2010-01-24
> **dch24328 said:**
> I've been using Ubuntu on and off since 8.04, but only last week decided to make a real switch across to it. After installing 9.10 64bit though, my laptop while running Ubuntu just turns itself off at completely random times - it doesn't seem to go through any shut down procedure or anything, it's more like the power's just suddenly cut. It sometimes happens 5 minutes after being turned on, or sometimes 4 or 5 hours, it really is random.

I really have no idea where to even begin trying to stop this. I think it must be a software thing because this has never happened with windows or earlier versions of Ubuntu, but other than that I don't know what to do to stop this.

I'm dual booting Windows 7 32bit and Ubuntu 9.10 64bit, and this is on a Toshiba L350-D 11-D laptop, which has a 64bit AMD processor. I'd really like to switch completely but this fairly major problem is holding me back, so any help would be really appreciated. Thanks.
Looks like something is overheating: the shutdown is there to protect the hardware. Perhaps the powermanagement stuff (ACPI) isn't handling the fans correctly.
Another possibility is that some temperatures are reported incorrectly, and the shutdown is unnecessary. Reading temperatures is also handled by powermanagement.

It seems there are quite a few bug reports concerning this on launchpad, for example (this isn't the exact same thing you seem to experience though):
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578)

Anyway, there is no hard and fast way to deal with this. Some people choose to go through a lot of trial and error for example: randomly enabling/disabling parts of ACPI (this isn't without risk).

A few things you could do: 

- Verify if the temperatures are normal or not when running ubuntu (compare when running win7). 
- Check if you get the shutdowns when running a live-session from a live-cd. Just boot from a live-cd (don't install anything, especially no drivers), and try to use it like you would normally (it will be slow though :)).
- Rule out memory errors (linux uses RAM very agressively, so you might notice errors when running ubuntu, while win7 appears unaffected). To run a memtest: boot from a live-cd and run memtest (let it pass the full set of tests a few times).
- Take a look in your log for acpi-related errors, or any errors for that matter. It may look like gibberish, but any errors or warnings will be signalled as such. It's easiest to dump the log in a text file (because it's pretty huge). In a terminal*, run:

dmesg > dmesg.log

- to create a file called "dmesg.log". Open it in any text-editor to view. You could also attach it here if you like.

- Also: which video-driver are you using?

*edit: you can open a terminal, by choosing Applications-->Accessories-->Terminal

---

### Post by dch24328 on 2010-01-26
There were no errors in the dmesg log, and I couldn't run a memory test as when I tried to the fan didn't come on at all so it shut itself down (the furthest it got was about 4% I think). It runs at a normal temperature (about 50 degrees) under Windows, so from the looks of things I think you're right about there being no easy fix for this. For now I've dropped back to Ubuntu 8.10 which doesn't seem to have this problem whatsoever - I would have used 9.04 because I don't remember having this problem with it, but it had some other stability issues on this laptop.

I mainly just wanted to say thanks for your help - at least I know what the problem is now, and maybe I'll try 10.04 when it comes out to see if that's any better.

---

### Post by warfacegod on 2010-01-26
Toshibas tend to have fan problems in Ubuntu. Go to: System> Admin.> Synaptic> search for Toshiba and select toshutils and fnfxd and apply. One of the two has helped numerous Toshiba users with fan troubles. Fortunately, I'm not one that needed it.

---


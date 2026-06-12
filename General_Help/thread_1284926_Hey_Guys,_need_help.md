---
title: "Hey Guys, need help"
date: 2009-10-07
forum: General Help
---

### Post by bigpond on 2009-10-07
Hey guys, I've had Ubuntu for about 4 days now (switched form vista) and im loving it. I've read some posts about 32bit ubuntus not using 4gb ram and seeing only ~3.5gb.

I've got a 32bit

My Specs:
Dell Studio 1555
Processor 0: Intel (R) Core(TM) 2 Duo CPU T6500 @2.1 GHz
Processor 1: Intel (R) Core(TM) 2 Duo CPU T6500 @2.1 GHz
(how do i check my graphics card?)
4 gig RAM

Instead of ubuntu seeing ~3.5 gb RAM like its suppossed to (?) it only sees 2.9gb, do i have something going on thats interfearing with my RAM.
Am i able to upgrade to 64bit?
Will 64bit solve my problem?
How do i upgrade to 64bit?

Sorry for all the nooby questions, feel free to link to other posts if this has already been answered.

Also how do i get rid off the loud beep when i turn off my comp (scared the hell out of me last night :))

---

### Post by TheGreenFox on 2009-10-07
Yes you need to upgrade to 64-bit ubuntu. For the system beep go to System<Preferences<Sound and find the setting "System beep" and turn it off:P

Good Luck,

---

### Post by wojox on 2009-10-07
Post back the results of:

```
uname -m
```

And to shutdown the speaker:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

And at the bottom of the page put:

```
blacklist pcspkr
```

Save and close. It will take a restart to take effect.

---

### Post by bigpond on 2009-10-07
> **wojox said:**
> Post back the results of:

```
uname -m
```And to shutdown the speaker:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```And at the bottom of the page put:

```
blacklist pcspkr
```Save and close. It will take a restart to take effect.

uname -m gave me i686

---

### Post by bigpond on 2009-10-07
Hey thanks for the quick feedback!:)

---

### Post by wojox on 2009-10-07
Okay well you definitely have a 32 bit so you can't upgrade to 64 bit. You can however read here about installing PAE enabled kernel [https://answers.launchpad.net/ubuntu/+faq/669](https://answers.launchpad.net/ubuntu/+faq/669)
And here
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by bigpond on 2009-10-07
> **wojox said:**
> Okay well you definitely have a 32 bit so you can't upgrade to 64 bit. You can however read here about installing PAE enabled kernel [https://answers.launchpad.net/ubuntu/+faq/669](https://answers.launchpad.net/ubuntu/+faq/669)
And here
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

So the PAE decreases performance. Does extra RAM increase performance? Or would extra RAM just let my copy stuff faster?

---

### Post by wojox on 2009-10-07
Yes it does decrease performance from what I've read. Never actually used PAE. I'd leave it all alone. I have 512 MB of DDR RAM and I've yet to ever have a problem.

---

### Post by bigpond on 2009-10-07
What would happen if i tried to install 64bit. Would it wreck my comp, or just not work?

---

### Post by wojox on 2009-10-07
I don't think it would work. It probably wouldn't even install. Never tried it.

---

### Post by fela on 2009-10-07
> **bigpond said:**
> What would happen if i tried to install 64bit. Would it wreck my comp, or just not work?

To install 64 bit you'll have to reinstall the whole operating system due to all the programs being compiled differently (for 64 bit architecture vs. 32 bit). It's a matter of opinion whether the extra 1.1GB (in your case) of RAM and the small performance boost (or sometimes large depending on what you do with your computer) is actually worth it. I'm not sure what kinds of programs benefit most from 64 bit.

But if you decide that you want to replace your current 32 bit with 64 bit, the easiest way is to backup all your important files to a separate drive and reinstall, this time with the 64 bit disk.

---

### Post by 3rdalbum on 2009-10-07
> **wojox said:**
> I don't think it would work. It probably wouldn't even install. Never tried it.

The Core 2 Duo is a 64-bit processor, so it would work.

A 32-bit operating system can use 32-bits for memory addresses, which gives 4 gigabytes of addressable space. It's like if your post office only let you put three digits for the house number - then the maximum number of houses you could put on a street would be 999 (well, you could put more, but they wouldn't be able to get mail).

64-bit is like allowing six digits for a house number; you can have many, many more houses on the street.

Now, the reason why a 32-bit operating system will report less RAM than 4 gigabytes is because some parts of your computer have memory onboard, that needs to be addressed. The biggest amount of non-main memory is usually on the graphics card. So if you've got two 1gb graphics cards in your computer, then they will take up two gigabytes of your address space, and the maximum amount of usable system memory on 32-bit is 2 gigabytes.

So basically, the reason why you have 2.9 gigabytes of usable system memory is because the components of your computer have their own little bits of memory that must be addressed. If you went for a 64-bit operating system, this memory would be taken out of the total of 64TB of address space; basically you'd get the full 4GB of RAM addressed and usable.

It's possible to install the PAE kernel which gives you 36 bits in memory addresses, but when you next want to do a fresh Ubuntu install you might as well make it 64-bit. There aren't really any reasons I can think of NOT to go 64-bit, but on the same token there aren't any powerful reasons to make the switch immediately.

---


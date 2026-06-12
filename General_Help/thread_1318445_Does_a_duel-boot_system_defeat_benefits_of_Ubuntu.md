---
title: "Does a duel-boot system defeat benefits of Ubuntu?"
date: 2009-11-07
forum: General Help
---

### Post by wavery on 2009-11-07
Two great benefits of Ubuntu for me is not having to constantly update and scan with AV and malware software, and how much faster my old laptop runs compared to Windows.  Are these benefits lost using a duel-boot system?

Background:  I dove in all the way the other day on an extra computer and wiped out Windows and installed Ubuntu for the first time.  I felt okay about the move because there's only one program I use Windows for on the computer and I was told it would work with Linux using Wine, DirectX, and net Framework.   So far I love what the OS does compared to Windows, but haven't been able to get the one program running after several hours of messing around with it.  So at this point I'm face with the decision of continuing to tinker (I'm not in a hurry) or biting the bullet and configure a duel-boot system (I hate the thought of maintaining Windows for one program).

So back to the main question.  Let's say I don't spend too much time and energy protecting the Windows partition.  Does this endanger the Linux partition where I would keep anything important?  Secondly, would a duel-boot configuration signficantly affect the way Ubuntu runs (i.e., the nice speed increase I see with Ubuntu)?  Thank you.

---

### Post by ranch hand on 2009-11-07
Install Win JerryLewis Pro in Virtual Box within Ubuntu.

---

### Post by MickS on 2009-11-07
If you do everything else in Ubuntu and only use windows for the one important program, then, provided that program doesn't access the net you wont need antivirus in windows either so dual booting would be a near ideal solution I would think.


Mick

---

### Post by coffeecat on 2009-11-07
> **wavery said:**
> Let's say I don't spend too much time and energy protecting the Windows partition.  Does this endanger the Linux partition where I would keep anything important?

No.

> **wavery said:**
> Secondly, would a duel-boot configuration signficantly affect the way Ubuntu runs (i.e., the nice speed increase I see with Ubuntu)?

No.

But let me give a +1 to ranch hand's suggestion. Install Virtual Box. Get the version [here]("http://www.virtualbox.org/"), not the one in the repos. So long as you've got enough RAM, simply run Windows in a Virtual machine for that one program you can't do without. Greatest advantage: you can disable networking for the Windows virtual machine. That way it can't catch a cold. :p

That's what I do. It saves the anguish of trying to get things to work in Wine.

---

### Post by wavery on 2009-11-07
> **MickS said:**
> If you do everything else in Ubuntu and only use windows for the one important program, then, provided that program doesn't access the net you wont need antivirus in windows either so dual booting would be a near ideal solution I would think.


Mick

The program would access one server that I think is well protected.  I know there's always some risk in that, but there really wouldn't be anything important on that partition.

---

### Post by wavery on 2009-11-07
> **coffeecat said:**
> 
But let me give a +1 to ranch hand's suggestion. Install Virtual Box. Get the version [here]("http://www.virtualbox.org/"), not the one in the repos. So long as you've got enough RAM, simply run Windows in a Virtual machine for that one program you can't do without. Greatest advantage: you can disable networking for the Windows virtual machine. That way it can't catch a cold. :p

That's what I do. It saves the anguish of trying to get things to work in Wine.

I'm liking this suggestion.  Is the learning curve reasonable compared to the tinkering I've been doing with Wine, etc?  And is 1GB enough RAM?  Thanks again.

---

### Post by coffeecat on 2009-11-07
> **wavery said:**
> Is the learning curve reasonable compared to the tinkering I've been doing with Wine, etc?

Difficult to say, but VirtualBox is much better now than when I first tried it about 18 months to 2 years ago. Download the manual to get an idea of what it's all about, but it all makes much more sense when you do it. Download the .deb appropriate for your Ubuntu version and simply double-click on it to install it - couldn't be easier. And read about guest additions and how to install them in the guest. Until you do, guest window control and mouse control in the guest is a pain.

> **wavery said:**
> And is 1GB enough RAM?  Thanks again.

Hmmm - you're pushing it a bit. Vista and W7, absolutely not. XP can run (limp?) in as little as 256GB RAM, so long as you don't have any AV software running. So let's say you allocate 384GB for Windows, you've still got dumpity-dum left for Ubuntu, which can run quite well in only 512GB. As long as that's XP you're thinking of and you're not going to do video rendering in Windows, you should be OK - just.

The advantage of VirtualBox is that you can vary the amount of RAM allocated to the virtual machine, so you can fine tune your settings to get the best of Ubuntu and Windows.

---


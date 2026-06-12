---
title: "v box question"
date: 2010-02-17
forum: General Help
---

### Post by degarb on 2010-02-17
I was poking around in the snaptic package manager and noticed two version of virtual box!!!  

1.I don't know which version is better. 2.  I was also wondering how you install it an what will happen next?

3.Would it be possible to install a version of windows 98 on a usb stick?  This would be very useful, since only about half my windows programs I tried work in wine (though I have been focused on Ubuntu, more than testing my essential windows sw without replacements, like dragon and ahk).

---

### Post by gsmanners on 2010-02-17
The OSE version has slightly fewer features. See: [http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by howefield on 2010-02-18
> **degarb said:**
> I was poking around in the snaptic package manager and noticed two version of virtual box!!!  

1.I don't know which version is better.

What versions do you see, give us the package names ?

The version in the repository is the OSE version, "Open Source Edition". The PUEL (Personal Use & Evaluation License) version available from the virtualbox website includes some closed sources code giving you extra features, main one being ability to ise USB devices in your guest, but there are other notables.

> 2.  I was also wondering how you install it an what will happen next?

You decide which version you want, (if you are still talking about Synaptic) then check the box and mark for installation, click apply, then apply again and you have Virtualbox installed, start from the Applications > System Tools menu.

You then need a disk or iso of the operating system you want to install as a guest. The installation of your guest tends to be identical to a "normal" install in that you follow the same process, although it tends to be much quicker.

Once you have created your guest, you likely want to install guest additions, which will give you an improved set of drivers, particuarly graphics and allow you to go full screen, seamless ect.   

> 3.Would it be possible to install a version of windows 98 on a usb stick?  This would be very useful, since only about half my windows programs I tried work in wine (though I have been focused on Ubuntu, more than testing my essential windows sw without replacements, like dragon and ahk).

Probably. You can create the virtual hard disk any place you like. It is probably better to have your virtual machines on a separate disk to your host operating system, from a performance point of view, although usb sticks wouldn't be so fast.

There are several short videos at virtualbox.org that are worth watching taking you over the steps, from installing virtualbox, creating a guest system, then exploring some of the features.

---

### Post by degarb on 2010-02-18
> **howefield said:**
> 
Probably. You can create the virtual hard disk any place you like. It is probably better to have your virtual machines on a separate disk to your host operating system, from a performance point of view, although usb sticks wouldn't be so fast.

I asked this on the virtual disk forum, but I think they misunderstood my question; and said this wasn't possible but the vdi could be on stick.  I think they thought I asked if the virtual box program would go on the stick.  I asked if the virtual machine would go on the stick.   I assume that the 20 meg or so vbox program will run on my machine--a 20 meg loss on my HD that has less a gig left.   But I want nothing of the windows guest machine on my hard drive. 

This right?

Also, I don't know virtual box's minimal needed specs for the machine.  Does my swap need to be enlarged to run it? ( I hope not.)  (win 98 with kernelex will be my guest.  Win 98 runs on slower machines than Ubuntu.  I have a old pentuim 3 (600 or 1 mhz, not sure) with 500 meg ram and 6 gig hd.  But runs about same, with Ubuntu, as other laptop with xp on a 1.6 ghz/160 hd/1 gig ram, just some essential programs do not have replacements and I guess (tell me if I am wrong) half the kid educational software doesn't run under wine.)

---

### Post by degarb on 2010-02-18
I of course want to keep the laptop, a laptop, for the living room for the wife and kids.   So, probably an external hard drive, which need external power, is not an option.  

I saw a double speed 8 gig flash card at wally world.  Maybe some small external reader than that card would be more tolerable than a jump drive.   Currently, I just have a gig jump drive affixed with clear 3m tap to cord to cooling mat.   This work in the real world for practical ergonomics of a machine that goes from coffee table to lap and back. 

Any other suggestion would be great.   Maybe someday there will be wireless usb external drives.  And hopefully, a guest OS could be run from it!

---

### Post by howefield on 2010-02-18
> **degarb said:**
> I assume that the 20 meg or so vbox program will run on my machine--a 20 meg loss on my HD that has less a gig left.   But I want nothing of the windows guest machine on my hard drive. 
This right?

That is correct. The main program would be installed/run from within your Ubuntu system and the vdi (your virtual hard disk) would reside on your flash stick.

> Also, I don't know virtual box's minimal needed specs for the machine.  Does my swap need to be enlarged to run it? ( I hope not.)  (win 98 with kernelex will be my guest.  Win 98 runs on slower machines than Ubuntu.  I have a old pentuim 3 (600 or 1 mhz, not sure) with 500 meg ram and 6 gig hd.  But runs about same, with Ubuntu, as other laptop with xp on a 1.6 ghz/160 hd/1 gig ram, just some essential programs do not have replacements and I guess (tell me if I am wrong) half the kid educational software doesn't run under wine.)

The minimum specs are that you need enough hardware to run both your host and guest systems simultaneously. Particularly RAM, and to a lesser extent graphics memory and processor. But as always, bigger and better is bigger and better ;)

You do not need to change swap or anything about your host system.

I'd expect the requirements for Windows 98 to be fairly mimimal, and you'd be fine, even on your limited hardware, (talking about your pentium 3 machine here, your other laptop would be more than fine).

---

### Post by degarb on 2010-02-18
Thanks, thanks, thanks!  Exactly the clear answer I was looking for.

While the question for media recommendations remains unanswered with suggestions.  One other question, when you set up the vdi, is this a fix file size or does it change?  Do I need to format the drive ext4?


----------------------

I assume even on a slow machine, if you weren't doing anything special on linux/closed unused program, when you switched to win98, there would be no real issues.  The issues would crop up in trying to run many programs and do cpu cycles in both operating systems.

As crappy as 98 was, it is very light weight, I could boot on my 166 mhz machine with 96 meg of ram, in 40 seconds.     With kernelex it ran oo and ff fine, but not chrome.   Though, those programs are not needed on a linux machine, I assume they help more xp compatibility with even unknown programs.

---

### Post by howefield on 2010-02-18
> **degarb said:**
> While the question for media recommendations remains unanswered with suggestions.

Not exactly sure what you are referring to here, if it is the remark about "external hard drive, which need external power" you have a variety of options including externally powered disks. 

> One other question, when you set up the vdi, is this a fix file size or does it change?  Do I need to format the drive ext4?

It is your choice as to whether you fix the size of the virtual hard disk beforehand, or allow it to dynamically grow. The advantage of the former is speed, with the disadvantage of not being resizable. 

Virtualbox will take care of the file system, during the setup stage, you will tell Virtualbox what the operating system is and it will sort it (file system) out for you.

> I assume even on a slow machine, if you weren't doing anything special on linux/closed unused program, when you switched to win98, there would be no real issues.  The issues would crop up in trying to run many programs and do cpu cycles in both operating systems.

Well, yes. That's kind of the way it works :)

---

### Post by degarb on 2010-02-18
> **howefield said:**
> Not exactly sure what you are referring to here, 

A outlet powered external drive for a laptop is not a viable option.  A laptop that sits on a desk, yes.  But not a laptop, used as a laptop.

Thus to keep the laptoppiness of the unit, other options would need to be explored.

I guess, the argument could be made that if only external powered drive needed when playing or doing some special task, then just get a long usb cord and attach as needed.

---

### Post by howefield on 2010-02-18
> **degarb said:**
> A outlet powered external drive for a laptop is not a viable option.  A laptop that sits on a desk, yes.  But not a laptop, used as a laptop.

Not all external drives require to be outlet powered. I use a nice little 250 gig Maxtor basics.

---


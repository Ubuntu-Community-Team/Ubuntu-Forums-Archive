---
title: "Booting windows without dual boot?"
date: 2011-06-23
forum: General Help
---

### Post by kaizo2560 on 2011-06-23
Hi I am currently installing kubuntu on my laptop on a new hard drive.

The problem is that I need to use windows as well every now and then for gaming. So I have an internal hard drive dedicated to windows out of my laptop and one inside for kubuntu. Changing hard drives out every time I game is a bit of a bother and wondered if anybody has booted into windows without fiddling about with the hard drives.

Can windows be booted from outside the laptop? (e.g. by using a sata to USB converter frame)?

Thanks in advance

---

### Post by sanderd17 on 2011-06-23
You need to use it for gaming LOL

Apart from that, I believe it is possible, I think updating GRUB would be enough since you can boot from an USB stick as well (full boot or live boot).

---

### Post by BFG on 2011-06-23
Could you not just set up dual boot on the internal hard drive?

---

### Post by kaizo2560 on 2011-06-23
> **BFG said:**
> Could you not just set up dual boot on the internal hard drive?

Potentially yes. But I have two problems with that 1) the disk space is too small... (games are taking up the space!) 2) I have had some bad experiences with dual booting and its not my preferred choice.

If anybody has any howto links to the grub updates sanderd17 is referring to please let me know. Thank you sanderd17 for letting me know :)

Again thanks in advanced.

---

### Post by sanderd17 on 2011-06-23
Just plug in your drive (wait until it's detected and so) and run
```

sudo update-grub

```

See in the terminal if grub discovers Windows and when you boot, you should be able to pick windows.

If your drive is not connected, the windows entry will still be shown, but choosing windows will just result in an error.

This is what I expect, I hope it will be this way, but it will certainly not mess up your GRUB.

---

### Post by BFG on 2011-06-23
You know what - I'm using a phone and totally failed to read your thread title properly. Oops!

I've had problems years ago, but dual boot works really well now.  Install windows first and then let ubuntu install do the rest.

When you say you're changing hdd every time, presumably they're easy to access on this laptop.  Is hdd upgrade a possible?

If not, a update-grub might work.

---

### Post by flemur13013 on 2011-06-23
> **kaizo2560 said:**
> 
 So I have an internal hard drive dedicated to windows out of my laptop and one inside for kubuntu. ...
Can windows be booted from outside the laptop? (e.g. by using a sata to USB converter frame)?


You should be able to boot using a USB HD adapter *if* your BIOS will let you do it: check your BIOS boot options; if so, this sounds like an easier, safer method than dual booting with grub.  I don't think you'd need to do anything except hook up the adapter. DON'T "update grub"!  Except  maybe for buying (borrow one to try) the adapter, trying the USB adapter method should be a no-risk, no-changes option, and the adapter's a handy thing to have anyway.
BUT! running Windows from the USB drive might be slower than having that disk installed in the computer...try it!

---

### Post by kaizo2560 on 2011-06-23
Thanks to the both of you will do the grub update and will let you know how it goes. (Still installing right now)

Potentially yes to getting an update but my own personal version of austerity measures has kicked in :P

Sorry _flemur13013_ just got the post will check my bios

---

### Post by kaizo2560 on 2011-06-27
Hmm I got a HDD enclosure and I tried booting 

It reaches the stage of seeing the windows logo half way but it does not let me get past that stage taking me to a OS recovery option...

Any ideas to solving this problem?

---

### Post by sanderd17 on 2011-06-27
So it worked for 3 days?

Can you switch the HDDs? So that Windows is the only one present?

---

### Post by kaizo2560 on 2011-06-27
Sorry for the confusion I have just got the enclosure today and will try switching the HDD as sandered17 suggested tonight

ideally i would like to avoid this as that would mean me carrying around an extra harddrive to work.

Thanks again in advance.

Edit:

Good news everyone once I reversed the arrangement i.e. windows inside the laptop and kubuntu in the external and it works flawlessly. Didn't even need to do anything.

I thought it may affect the speed but I didn't notice much difference. I will definitely advise this setting if anyone wants to keep a gaming set up but use Kubuntu/Ubuntu for everyday use.

---


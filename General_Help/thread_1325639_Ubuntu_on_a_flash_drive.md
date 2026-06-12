---
title: "Ubuntu on a flash drive"
date: 2009-11-13
forum: General Help
---

### Post by Auraomega on 2009-11-13
I'm trying to make a multi distro flash drive with persistence working, however I'm having a couple of small and rather annoying issues, if anyone can help me iron out the creases so to speak, I'd appreciate it.

My first issue is when running the flash drive, I can't access the flash drive, it refuses to mount at all infact, [this]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") says to format the drive and place the files in the seperate partition, but that seems a lot of hassle if it's possible to sort out some other way.

My second is getting persistance to work without conflict, having not yet managed to get Ubuntu running as desired I've not attempted any other distros, however I'd like to know if I could use the same casper file for different distros, it seems unlikely but I'll ask anyway. If that isn't possible then how would I direct Ubuntu to a different file other than casper-rw, is this configurable in the menu.lst file or not?

---

### Post by wilee-nilee on 2009-11-13
> **Auraomega said:**
> I'm trying to make a multi distro flash drive with persistence working, however I'm having a couple of small and rather annoying issues, if anyone can help me iron out the creases so to speak, I'd appreciate it.

My first issue is when running the flash drive, I can't access the flash drive, it refuses to mount at all infact, [this]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") says to format the drive and place the files in the seperate partition, but that seems a lot of hassle if it's possible to sort out some other way.

My second is getting persistance to work without conflict, having not yet managed to get Ubuntu running as desired I've not attempted any other distros, however I'd like to know if I could use the same casper file for different distros, it seems unlikely but I'll ask anyway. If that isn't possible then how would I direct Ubuntu to a different file other than casper-rw, is this configurable in the menu.lst file or not?

Does the usb show up in gparted if it does delete the 1 partition then format it to fat 32, then close gparted then unplug it then plug it in and open usb creator and see if it shows there. Then attach the iso look to the bottom of the gui there is a slider for the persistent portion slide all the way to the right hit the go button and you should have a live usb with persistent. You probably will do best with a 4 gig  if you want to add a alot of stuff, a 2gig usb will work though. I don't know about the Casper question. This is for a single distro, I am not sure about multiple set ups.

---

### Post by Auraomega on 2009-11-13
Did you just qoute my message to make it appear as if you read it? :p

I'm setting it up by hand. To contain more than 1 distro, the USB Creator fails, hence why I didn't choose the obvious route. It's formatted to fat32 but just won't mount when its running. Backtrack allows me to mount my flash drive so I can access all my files on there as normal without issue.

---

### Post by wilee-nilee on 2009-11-13
You just narrowed the response field by lashing out to a response with a smart *** response. Using your frustration as a projection onto getting help is not good. We can cannot read your mind, you said in the first post that first the usb doesn't show up, wouldn't this be the main issue and shouldn't you have included what you have done to get to a mounted point and formatting in your 1st post or at least qualified that in  the last post since then this is how for you have gotten. Good luck getting any help.

---

### Post by Auraomega on 2009-11-13
Maybe you missed my humour, obviously the ':p' wasn't obvious enough.

I never said it didn't show up, more to the point that it doesn't mount, the drive itself is formatted correctly otherwise I wouldn't be able to boot from it in the first place or even copy the files and install GRUB.

---

### Post by wilee-nilee on 2009-11-14
The only thing more that I will say is that the 1st post is confusing. Using using a smiley doesn't remove your intentions, come on man your back-peddaling. 

I notice now that nobody has responded, I think your goals can be reached but I don't have the skills to tell you how to go about it. So If it was me I would call this thread solved, and start a new thread with a better description of where your at so far and what other distros you want to load on the thumb. 

The 1st post may make sense to you but to me it doesn't, and I am a fairly experienced user. When you say you can't mount the usb it sounds like it can't be read by your computer so you don't have access. This forum and the threads are easiest to use when you are very specific and don't ask for more then is expected in a single thread. You have to draw the people to help you then ask the extra questions.

At the least this response will bump you onto the main lineup so merry Christmas.

---


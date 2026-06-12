---
title: "mounting a VirtualBox drive"
date: 2010-02-22
forum: General Help
---

### Post by coldraven on 2010-02-22
I have a bona fide XP PID number, it came installed on this laptop.
It was a "downgrade" from Vista Business edition to XP Pro.
In fact I have three, one on a sticker on the base (for Vista), one that XP reported and another that Aida found in the registry presumably. 

I wiped the hard drive and installed Karmic.
However after  installing Windows as guest in VirtualBox it will not activate, it rejects all my activation keys.

Can I somehow mount the virtual disk image and tinker with it? At the moment Windows will not go past the login screen. I'd like to try putting the original wpa.dbl file back into the /system32 directory and see if that fixes it.

I've looked at VBox help but cannot find anything that would do it.
All info gratefully received!

p.s. XP was working fine but I let it go beyond the 30 day activation period, I suppose I'll have to re-install it from scratch :(

---

### Post by jpl888 on 2010-02-22
Well if you boot the virtual machine from a live CD you will be able to get access to the Windows XP partition.

---

### Post by coldraven on 2010-02-22
> **jpl888 said:**
> Well if you boot the virtual machine from a live CD you will be able to get access to the Windows XP partition.

I don't want to boot the virtual machine, if I do I only get one option namely to enter an activation key. I want to be able to edit the files on it.
Unless I have misunderstood your meaning.

---

### Post by jpl888 on 2010-02-22
If you boot the virtual machine off a live CD you will be in the live CD environment, not Windows, and therefore you will have access to the drive (to copy over that file you were talking about) but won't be harassed by WGA.

---

### Post by snowpine on 2010-02-22
It's more of a Windows problem than an Ubuntu problem, really. ;)

You will need a valid XP activation key, and nobody on these forums is allowed to help you circumvent this requirement.

jpl888 is correct that you can use an Ubuntu Live CD to recover any files on your Windows drive (real or virtual).

---

### Post by coldraven on 2010-02-22
> **jpl888 said:**
> If you boot the virtual machine off a live CD you will be in the live CD environment, not Windows, and therefore you will have access to the drive (to copy over that file you were talking about) but won't be harassed by WGA.

Windows is not on a partition, it is a 1.8GB .vdi file.
After I had installed it I also did an export machine from VirtualBox and have it as a 723MB .vmdk file.
AFAIK it can only be accessed by VBox but as I said I don't want to run it, only mount it.
Maybe we are talking on cross purposes but thanks anyway :)

---

### Post by jpl888 on 2010-02-22
> **coldraven said:**
> Windows is not on a partition, it is a 1.8GB .vdi file.
After I had installed it I also did an export machine from VirtualBox and have it as a 723MB .vmdk file.
AFAIK it can only be accessed by VBox but as I said I don't want to run it, only mount it.
Maybe we are talking on cross purposes but thanks anyway :)

Yes I am telling you the easiest way to be able to mount and access the VDI file. It still involves booting the virtual machine but you would be starting from a live CD. When in the live CD environment you could then mount a virtual box share or sftp a file into the VDI.

I think you are having some conceptual problems here, what I am suggesting to you will allow you to edit/copy files into the VDI without starting windows on it.

---

### Post by coldraven on 2010-02-22
Ah yes, my conceptual powers have gone all fuzzy! :D
My excuse is that it's late in the day....
Mind you I have been off and discovered this
[http://forums.virtualbox.org/viewtopic.php?t=52](http://forums.virtualbox.org/viewtopic.php?t=52) 
and have been having a learning experience with dd !
I'm not trying to pirate Windows as I have a legal key, its just that it is not being accepted.
Like I said this is a new laptop from Compaq that was downgraded from Vista to XP pro. I mean it arrived with XP installed on it.
Well it was new a year ago when I bought it!
Thanks for replying, I'm off to bed now, I'll post back tomorrow and let you know if I have success.

I only want XP so that I can run Sketchup, I don't want Wine and I would prefer to have Windows isolated from the internet.
Thanks again guys, happy hacking!

I haven't had the time to mess around with windows, I will probably re-install XP in VBox but make the virtual disk a fixed size.
Then at least I can try the solution that I found above.
Thanks again for your replies.

---


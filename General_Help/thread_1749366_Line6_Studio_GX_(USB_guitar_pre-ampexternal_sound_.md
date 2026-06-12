---
title: "Line6 Studio GX (USB guitar pre-amp/external sound card) causes kernal panic in 11.04"
date: 2011-05-04
forum: General Help
---

### Post by diablo75 on 2011-05-04
Please go easy on me when I say I don't know how to file a bug report properly.  Every time I've ever tried I get yelled at for doing it wrong or filing it under the wrong project or whatever.  Again, I don't know how to file a bug report properly.

I can confirm that this Line6 adapter that I have causes Ubuntu 11.04 to go into a kernel panic during boot when it is plugged in.  It happened right after I upgraded to 11.04 until I unplugged it, and still happens when it is plugged in during boot.  If it's unplugged the system doesn't crash.  I booted into 10.10 multiple times with this adapter connected and it never went into a panic.

So what do I do next to get this bug report filed.  To whom am I suppose to direct this kind of report?  What information are they going to demand I have ready for them?  How do I gather this information?

---

### Post by sekhar.rahul on 2011-07-17
I've had the same problem with a Line 6 UX2, and I have the same query.

---

### Post by apolon on 2011-09-30
I know this thread is somewhat dated but I was curious if anyone ever found a solution for this bug?? I searched the Internet quickly without any luck...and I'm not shutting my system down enough to where it is a hassle or I would dive in and try to find the problem. If anyone has any info I'd appreciate it. Thanks.

---

### Post by diablo75 on 2011-10-01
I just installed Ubuntu 11.04 from scratch about a week ago and just connected my GX expecting it to lockup the system after I had logged on.  It didn't.  I haven't yet tried to see if the same problem occurs during boot after POST/before logon, but I can at least say that after plugging it in while logged on, the light on the top of the GX became green indicating a successful connection and it also immediately became listed in the audio preferences panel via the volume control meters (see attached screenshot).

So... if nothing else, backup your stuff and install a fresh copy of the latest version of Ubuntu.

---

### Post by MarkSparks on 2011-10-15
I have the same problem, only slightly different. I just put 11.10 on my laptop, but this happened in 11.04 as well. Any 10.x version and this is not an issue...

I have to unplug my UX2 until I get to the GUI, then I can plug it back in. If I try select Ubuntu from the grub menu, it goes to a dark purple-ish screen and stays there forever. 

A work around, until the UX2 gets some love, if your is like mine, is unplug until GUI. 

Hope that helps.

---

### Post by diablo75 on 2011-10-15
> **MarkSparks said:**
> I have the same problem, only slightly different. I just put 11.10 on my laptop, but this happened in 11.04 as well. Any 10.x version and this is not an issue...

I have to unplug my UX2 until I get to the GUI, then I can plug it back in. If I try select Ubuntu from the grub menu, it goes to a dark purple-ish screen and stays there forever. 

A work around, until the UX2 gets some love, if your is like mine, is unplug until GUI. 

Hope that helps.

Same here.  I didn't really mention that in my previous post (hadn't tested) but I can't boot with the GX attached.  Have to plug it in after login.

---

### Post by aza484 on 2011-10-22
Hi guys, apologies for slightly threadjacking but you all seem to be happily using your UX2 and I was wondering how I can get it to work for recording? I'm using 11.10 ubuntu studio, trying to record into Ardour, and I can get it outputting via my UX2 but not recording - its like its not 'activated' or something, like in Win before you start gearbox or podfarm.

Any tips please? its frustrating me a lot!
Thanks!:)

---

### Post by warloc on 2011-12-19
I have same problem.
Ubuntu 11.10
It startup successful if UX2 unplugged and fail with kenel panic if it's plugged in.
If I plug device after startup it begins to work, but i hear some (on max loud level) noise in left channel. And indicator on front of device show clipping in left channel.
UX2 is not damaged, it successfully work with Win7 at my work.

---


---
title: "Ubuntu 10.10 won't start. Strange, cryptic letters."
date: 2011-04-02
forum: General Help
---

### Post by CoolBreeze47 on 2011-04-02
Hi people.

I've been using Ubuntu 10.10 for some time and have never had any issues with it. In fact, I love it!. This morning I started my laptop up but halfway through the boot process it stopped loading, played a little two-syllable tune and then gave me an error message telling me that it could not start due to not having write access to .ICEauthority.

After clicking through a few more error messages, I noticed a very strange serious of cryptic letters and symbols in the very upper-left corner of the black screen I had arrived at. Here's what I saw...

OKefrbcy
TholmdDE
wist: N' l
ngap' /Cu

What does this mean?. Has anyone else ever seen this?. Have I been hacked or something?.

Thanks for any help you can offer as I am really concerned about this!.

- CB

---

### Post by securitymeddler on 2011-04-02
Hey dude, 

I am not Linux expert or anything but if you didn't make any system changes then it sounds like some sort of file corruption. System crash or failing HDD maybe. 

I would start by booting off your ubuntu CD and running fsck on the disk and see if that fixes anything. You might also want to backup/delete the folder it claims it doesn't have write access to. 

No lack of how-to's on FSCK
[http://www.google.com/search?q=FSCK&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=FSCK&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Might not hurt to do a hard drive diagnositc if you can. I always feel Drive Fitness test does a good job.

---


---
title: "High CPU usage"
date: 2009-07-17
forum: General Help
---

### Post by Flippy209 on 2009-07-17
Recently I have been having an issue where my CPU is constantly running at 55% to 75% usage. This happens only after an account has logged in. For example, starting from a fresh boot I can SSH into the box and run top and see 0.1 CPU usage. Once I log in I am instantly up to at least 50% usage. I open a terminal and run top and I see init and xorg jumping around the top, which is typical (at least from what I've seen) except when counting the CPU usage for each process I'm not even coming close the the ~55% usage being stated in top. I also run AWN with CPU monitor, and that reports the same thing. I've turned compiz off and there is no difference. I've reinstalled NVIDIA drivers and there is no difference. I don't think it is a system (hardware) issue due to the fact that top lists low usage when nobody is logged in.

I've never ran into a problem like this and am not sure how to troubleshoot it. I asked in #ubuntu and didn't really get much help (not a problem as I understand that channel to be for new ubuntu users) so this is my last resort. Google searching has not done much good. 

If anybody would be willing to help a poor sap out like me please post what configs or other things you would suggest I look at.

Thanks!

---

### Post by t4thfavor on 2009-07-17
Run top, and find out what is hogging from a terminal after you log a user in.

Then post back.

---

### Post by Flippy209 on 2009-07-17
I'm attaching two screen shots. The first was taken right when I got home. As you can see I still have steam running and a few other things. The second is after a fresh reboot.

Sorry about the screen shots I tried top > top.txt but that did not work... I'm a noob.

---

### Post by t4thfavor on 2009-07-17
The individual amounts look like mine, its just your totals that look out of the ordinary, do you by chance have a dual processor PC?

---

### Post by Flippy209 on 2009-07-17
I do and I used to run 64 bit but went back to 32 because some of the apps I like to use weren't supported in 64. Would you recommend I use 64 bit instead?

---

### Post by t4thfavor on 2009-07-17
I use all 64bit on all my capable machines. I was just thinking that it could have something to do with the appearance of high CPU usage (the dualie) I only have hyperthreading on this machine, so I can't really give it a proper test.

If its not affecting your battery, heat, or performance, I would probably think its OK to ignore.

---

### Post by Flippy209 on 2009-07-17
Well, ever since this started happening TF2 has been really laggy. I think I will give 64bit another shot. Heck, I could even fire up the live CD and see how that uses the CPU.

---

### Post by Flippy209 on 2009-07-18
I installed 64 bit and so far so good.

---


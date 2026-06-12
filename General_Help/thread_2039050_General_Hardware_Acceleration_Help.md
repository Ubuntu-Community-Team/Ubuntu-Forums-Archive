---
title: "General Hardware Acceleration Help"
date: 2012-08-08
forum: General Help
---

### Post by ToxicMastodon on 2012-08-08
I wasn't quite sure where to put this inquiry/help request so I am putting it under General Help. Right now I am doing a back up of my main drive on a secondary drive running Ubuntu. I am compressing 200 gigs of data on the second drive, while also compressing 100 gigs on the primary drive. This is eating up my dual core CPU, at 100% load. It is also taking for ever to get anywhere (probably a better idea to go one at a time, but I plan to have this run in the background while I sleep). I am wondering how I would be able to offload the computations for the compressing to my graphics card so it would be faster and still allow me to do other things, ya know hardware acceleration. Any help would be nice.

---

### Post by xycris on 2012-08-08
hi ToxicMastodon,

i think what you are asking will still be impossible at this point of time.

gpus are meant for graphic rendering and really helps a lot on people who are so keen into multimedia quality. since gpus are really ment to render graphics, they have no hard drive writing capability. if ever they do, then you will face another problem: data writing bottleneck.

processors nowadays are really fast, so fast that other parts of the computer can't keep up. the speed limiting factor now are: RAM, motherborad's FSB, HD write/read speed, and Internet speed.

i can't really explain it to you technically but i hope this thread will help you understand:

[http://gpgpu.org/forums/viewtopic.php?t=5390&sid=474e9db05f55a14c4115b2f0c48ee331](http://gpgpu.org/forums/viewtopic.php?t=5390&sid=474e9db05f55a14c4115b2f0c48ee331)

cheers,
xycris

---

### Post by mastablasta on 2012-08-08
hmm wouldn't it be easier to make it use onlly one CPU core instead?
 
GPU's can probably do that but i don't know if they can offer hardware acceleration at the same time.

---

### Post by dcstar on 2012-08-08
> **ToxicMastodon said:**
> I wasn't quite sure where to put this inquiry/help request so I am putting it under General Help. Right now I am doing a back up of my main drive on a secondary drive running Ubuntu. I am compressing 200 gigs of data on the second drive, while also compressing 100 gigs on the primary drive. This is eating up my dual core CPU, at 100% load. It is also taking for ever to get anywhere (probably a better idea to go one at a time, but I plan to have this run in the background while I sleep). I am wondering how I would be able to offload the computations for the compressing to my graphics card so it would be faster and still allow me to do other things, ya know hardware acceleration. Any help would be nice.

[LIST=1]
[*]No, you can't "offload" things to the GPU unless the particular program has that code in it.
[*]2. Open a terminal:
```
 man nice
```
[/LIST]

---


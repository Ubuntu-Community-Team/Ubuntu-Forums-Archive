---
title: "Is my Ubuntu installation configured for speed ?"
date: 2006-04-17
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-17
Here are my system specs.

> 2.2 Ghz AMD Anthlon Processor
512 of Ram
ATi Radeon Xpress 200M Graphics Card

Here is what I have done:

1. I am using InitNG
2. Disabled uneeded services from starting
3. Tweaked my filesystem for a performance boost
4. Using reisersfs
5. Using the new 2.6.16.7 kernel from kernel.org + all uneeded modules are disabled + it is completly custom compilied + I compilied it for my AMD processor.
6. DMA is enabled
7. Prelink
8. I check my filesystem for errors on boot.
9. Using Swiftfox instead of Firefox
10. Using the latest ATI linux drivers.

Anything else I can do to make my system faster ?

---

### Post by dickohead on 2006-04-17
Yes it is, and maybe try a K7 kernel?

---

### Post by spartan777 on 2006-04-18
yeah, do the k7 kernel. i wouldn't use swiftfox though. there are some bugs in it, it's a headache for all the website admins of the sites you visit, and isn't much better than firefox already is. good job though.

---

### Post by Stirling on 2006-04-18
[QUOTE=spartan777]i wouldn't use swiftfox though. there are some bugs in it[/QUOTE]Such as?

[QUOTE=spartan777]it's a headache for all the website admins of the sites you visit[/QUOTE]How so?  It identifies itself as Firefox.

---

### Post by darrenrxm on 2006-04-18
Buy more ram. It is not always a software solution.

---

### Post by xXx 0wn3d xXx on 2006-04-18
I am already using a k7 kernel. I built the kernel to match my AMD processor.

---

### Post by spartan777 on 2006-04-24
[QUOTE=Stirling]Such as?

How so?  It identifies itself as Firefox.[/QUOTE]


well, of course, swiftfox is just a modded firefox. what swiftfox does is it takes all the links on a page, and starts loading them before you even click on it. this uses up loads of bandwidth, and just isn't really that great. if you have broadband, swiftfox isn't necesarry. 

i guess swiftfox doesn't really have that many bugs that firefox doesn't, but it does have problems with extensions, like not starting if it has any.

---

### Post by Stirling on 2006-04-26
[QUOTE=spartan777]well, of course, swiftfox is just a modded firefox. what swiftfox does is it takes all the links on a page, and starts loading them before you even click on it. this uses up loads of bandwidth, and just isn't really that great. if you have broadband, swiftfox isn't necesarry. [/QUOTE]
Ahh yes, you must be referring to the network.prefetch-next option.  I think that is enabled in default Firefox builds too though.

[QUOTE=spartan777]i guess swiftfox doesn't really have that many bugs that firefox doesn't, but it does have problems with extensions, like not starting if it has any.[/QUOTE]
Which extensions?  You try the 1.5.0.x builds, the trunk builds or the 1.8 branch builds?  I know extensions are probably broken for all trunk and 1.8 branch builds, but again that is the same in the equivalent Firefox builds.  :-k

---


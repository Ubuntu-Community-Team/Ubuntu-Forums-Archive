---
title: "Quest for Speed - Calling all users..."
date: 2006-04-13
forum: General Help
---

### Post by Haegin on 2006-04-13
Hi,
I am trying to compile a list of anything that can be done to speed up ubuntu in any way that will interest more than about 10% of the ubuntu user-group. 

So far I have:
[LIST]
[*]InitNG for bootup
[*]Swiftfox and Fasterfox for a faster web browser
[*]Prelinking for faster app loading times
[*]Openbox for a faster window manager
[/LIST]

If you have any other things that can speed up ubuntu (even if its only a tiny amount) then please tell me. I am aware that dapper promises to be faster than breezy, I plan on trying it shortly.

Does anybody know which is the faster file system, ext3fs is the default but does reiser fs, xfs, jfs or any of the others offer a reasonable speed boost while  still remaining stable enough for general day to day use?

HumanPrototype

---

### Post by xXx 0wn3d xXx on 2006-04-13
[QUOTE=Human Prototype]Hi,
I am trying to compile a list of anything that can be done to speed up ubuntu in any way that will interest more than about 10% of the ubuntu user-group. 

So far I have:
[LIST]
[*]InitNG for bootup
[*]Swiftfox and Fasterfox for a faster web browser
[*]Prelinking for faster app loading times
[*]Openbox for a faster window manager
[/LIST]

If you have any other things that can speed up ubuntu (even if its only a tiny amount) then please tell me. I am aware that dapper promises to be faster than breezy, I plan on trying it shortly.

Does anybody know which is the faster file system, ext3fs is the default but does reiser fs, xfs, jfs or any of the others offer a reasonable speed boost while  still remaining stable enough for general day to day use?

HumanPrototype[/QUOTE]

1. Tweak your ext3 filesystem for a performance boost
2. Compile the latest kernel from kenel.org
3. Make sure DMA is enabled.
4. In terminal type:

> sudo apt-get clean

This will get rid of all uneeded temporary packages that are used at the install of all programs.

---

### Post by SomeoneWhoIsntMe on 2006-04-13
Make sure you have a kernel with all your processor's extentions. For example, since I have a Venus core Opteron 144, I would compile a kernel with x86-64, MMX+, 3DNow!+, SSE, SSE2, and SSE3.

---


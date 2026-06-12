---
title: "Kernel, Plymouth Question"
date: 2009-12-30
forum: General Help
---

### Post by moore.bryan on 2009-12-30
I'm running Ubuntu Netbook Remix 9.10 on an Asus EeePC 1005HA and am looking into playing around with kernel 2.6.33 and Plymouth, but have a couple questions.

[LIST=1]
[*]I thought, perhaps incorrectly, the UNR came with an "adjusted" kernel specifically mod-ed for netbooks, but it looks to have the stock 2.6.31-generic; can anyone help me out?
[*]Is there anything specific I should do to the 2.6.33 kernel to make it more "responsive" to my Asus?
[*]I've read several guides on how to get Plymouth running on Jaunty with the Plymouth-devel PPA, but can't seem to find any specific guidance for the same on Karmic; a simple omission or is it just as good a guide and I can supplement "Karmic" for where it writes "Jaunty?"
[/LIST]
Thanks, in-advance, for any guidance!

EDIT:
So, I jumped off the cliff, installed the 2.6.33 kernel, turned on mode-setting because--apparently--all kernels since 2.6.29 have had KMS built-in by defaults, and installed Plymouth. Downside: no beautiful splash, only text. Any bright ideas now?

---

### Post by PaulReaver on 2009-12-30
I don't know about the security of the packages on this site but check 

[http://array.org/ubuntu/](http://array.org/ubuntu/)

---

### Post by moore.bryan on 2009-12-30
Yeah, PaulReaver, I looked at those when I was considering Eeebuntu or EasyPeasy, but the Array kernels/releases are a step behind Karmic.

As of now, it looks like I have to just play around with the install how I have it.

---

### Post by moore.bryan on 2009-12-31
Things are a little more complicated now. I've installed Plymouth and the 2.6.33 kernel, turned-on mode-setting, and still nothing. [this]("http://fedoraforum.org/forum/showthread.php?t=206612") Fedora page shows some grub.conf changes being necessary, but as Fedora still uses the "old" grub, there's no such equivalent grub2 settings I can find.

Any help?

---


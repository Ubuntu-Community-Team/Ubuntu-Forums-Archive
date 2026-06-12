---
title: "Ubuntu sometimes doesn't boot, sometimes does."
date: 2010-08-05
forum: General Help
---

### Post by marshall.robert on 2010-08-05
Hi,

I have a couple of machines, both Dell Vostro 430, and sometimes they hang on boot (after GRUB) and sometimes they boot nicely.

When they do boot, there is something about plymouth being killed (sigterm or something). I understand that plymouth is the boot screen, and it being killed on a successful boot makes me think that the problem, when it doesn't boot, is  plymouth.

Ideally I would like to keep plymouth because the Idea is to theme it to the company logo and colours.

Any light on the situation, and help on fixing would be greatly appreciated.

Many thanks, Rob.

---

### Post by varunendra on 2010-08-05
Plymouth seems to have a history of bugs with Lucid. Some have their fixes released while some still pending. Yours seems to be an older one whose bug-fix might have been released:
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/550219](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/550219)
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538292](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538292)

Update your packages and see if it gets fixed. Otherwise report yours and disable it for now.

---


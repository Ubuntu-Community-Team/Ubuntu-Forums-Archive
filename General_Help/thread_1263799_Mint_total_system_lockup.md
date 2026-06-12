---
title: "Mint total system lockup"
date: 2009-09-11
forum: General Help
---

### Post by beak02 on 2009-09-11
The title says it all!

I'm running mint and have found several times over the past few days that the system has completely locked up - It wouldn't even let me do a ctrl alt backspace.  I haven't noticed any recuring factors, it just seems to be a windows wannabe - "I want to spontaneously lock up to!"

Any ideas?  Anyone know the problem and have fixed it in the past?

Thanks in advance!

Luke

---

### Post by P4man on 2009-09-11
You could try booting the kernel with
noapic
nolapc
noacpi

as kernel options. Try them one at the time. noacpi will have a lot of sideeffects, like limited power management options, but worth a shot if all else fails. See here for help how to set kernel options:

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

---


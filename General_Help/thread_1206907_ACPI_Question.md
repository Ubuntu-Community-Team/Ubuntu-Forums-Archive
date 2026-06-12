---
title: "ACPI Question??"
date: 2009-07-07
forum: General Help
---

### Post by cottfcfan on 2009-07-07
I`m running Jaunty on a Dell Inspiron 531.
When  I turn ACPI off in Grub Menu, my computer boots faster, is more responsive, and plays streaming videos (ie BBC Iplayer) without the jerkiness I normally get.
 On the downside I lose the ability to "suspend" which is useful.
 My Questions are. Is it safe to turn ACPI off? What does it do? and is there anyway to get suspend back without it?

---

### Post by CatKiller on 2009-07-07
As with many things some BIOS implementations are a bit rubbish. The state for your particular BIOS might get better as more testing data is received by whoever writes that part of the kernel, or it might not.

> **cottfcfan said:**
> What does it do? and is there anyway to get suspend back without it?

[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

...maybe. APM (which is the earlier standard for power management) does have at least one Suspend state. I have no idea what the state of APM support is.

---

### Post by cottfcfan on 2009-07-08
I`ve read on the forums of a lot of people having jerky video playback and live streaming.
Their blaming the adobe flash player. but turning off ACPI has resolved all those problems for me, and my computer is just all round more responsive. 
 The problem is ive lost all my power functions. Anyone know of a way round this?
I tried APM. But apparently my kernel dosent support this.

---

### Post by cottfcfan on 2009-07-08
Ive looked further into this and this is weird.
After enabling ACPI again and Rebooting everythings fine, but on subsequent boots, video and streaming quality get worse.
This holds true everytime ACPI is disabled and then enabled again.
Has anyone else experienced this problem?

---


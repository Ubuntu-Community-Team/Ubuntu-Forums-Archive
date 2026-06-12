---
title: "Skype and another audio app."
date: 2006-02-12
forum: General Help
---

### Post by mempf on 2006-02-12
How do I get skype to work while getting audio from XMMS, Gaim or anythign really.

I got most other things working well with each other.

Thanks

---

### Post by paulmilliken on 2006-02-12
This link [https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29](https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29) suggests that some users have had problems trying to share audio between skype and other applications using ESD.

Paul

---

### Post by joft on 2006-02-13
Hi,

I think your problem is (like the SkypeHOWTO also says; which paulmilliken suggested), that Skype is an OSS-only application and doesn't know about how to output to ALSA. ALSA has an OSS emulation and Skype is using this - but by doing so, it blocks the whole sound device - no sound mixing happens - Skype will be the only app able to output sound.
**NOTE: All this only occurs, if you have got a sound card/chip which is not able of doing sound mixing of several sources in hardware.**

I already described the general situation here:
[http://www.ubuntuforums.org/showpost.php?p=710369&postcount=2](http://www.ubuntuforums.org/showpost.php?p=710369&postcount=2)

And the text in the above link points to **my HOWTO**: an alternative solution how to get **software mixing for all OSS-apps**. I came up with this solution after trying different other things without success.
[http://www.ubuntuforums.org/showpost.php?p=695990&postcount=6](http://www.ubuntuforums.org/showpost.php?p=695990&postcount=6)

---


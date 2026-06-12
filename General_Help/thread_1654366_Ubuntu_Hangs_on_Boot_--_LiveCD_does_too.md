---
title: "Ubuntu Hangs on Boot -- LiveCD does too"
date: 2010-12-28
forum: General Help
---

### Post by michboy on 2010-12-28
Hi all,

I've been working with Linux for about 12 years and have always found solutions to my problems on forums such as this one (and this one in particular), but this time I just had to register and post because this problem has me pulling my hair out.

I have 10.04 64-bit Server edition (I believe... a colleague installed it and doesn't remember for sure what he installed).  This machine has worked well for a few months now.  Yesterday, I restarted the machine through the OS (not a hard reset), and now the OS will not boot.  It hangs with a blinking cursor.  When I set noquiet, I don't see any errors in the bootup text.  The last thing that prints out is 

NET: Registered protocol family 1

Whatever it's trying next is not happening.

Here are some things I've tried:

- setting a combination of "noapic noacpi xforcevesa nomodeset" at the Grub loader
- flashing the latest BIOS
- resetting the BIOS settings
- Booting in recovery mode
- Booting a previous kernel version
- Loading from a LiveCD.  The same thing happens.  This makes me feel that it's a hardware issue, maybe a screwed up NIC? 

Unfortunately, I can't run the famous Boot Info Script because I can't even load the LiveCD.  

Thanks for any input you may have.


[U][B]Update

[/B][/U]After a ton of fiddling with the BIOS, the default setting that was keeping it from loading had to do with the Legacy USB support.  It needed to be at FULLSPEED instead of HISPEED.  Don't ask me why.  Yes, this was the only modification needed to get it running for me.

---

### Post by vipergts706 on 2011-02-10
Thanks so much for the update. I had to turn legacy USB support off for mine to work but I would have never thought to do that without this post.

---


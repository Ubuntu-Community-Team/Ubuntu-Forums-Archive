---
title: "HP mini, battery drain, and the netbook remix"
date: 2009-08-25
forum: General Help
---

### Post by JPBodner on 2009-08-25
Hi all

I recently got a HP mini 110.  Nice little machine.  One problem that I've had (and other as well according to the HP forums) is that the HP MIE Linux doesn't seem to shut off everything when you power the system down, so the battery drains at about 7%/12 hours.  It's definitely not a hardware thing (I replaced the battery), and yes, I mean complete shutdown, not hibernate.  If you unplug the battery from the machine, the problem doesn't occur. 

So one theory is that its an old Ubuntu issue that has been corrected in the latest release (Jaunty).  HP's MIE is based on an earlier Ubuntu release and they apparently didn't implement a patch (How could they miss it?!?!).  So, I'm hoping the the netbook remix would have this problem licked.  Can anyone confirm that by installing the remix, the battery drain issue is solved?  

Thanks!  ):P

---

### Post by P4man on 2009-08-25
I can't confirm, I got no idea :)
But i do find it interesting. The only thing that I can think off that would explain it, is that the ethernet card or usb hub is not powered down (to allow wake up from lan, or wake up from usb). Perhaps even the wifi. Or bluetooth? 

You can change those shutdown scripts manually, but Id have to google for that. I once changed mine so my ethernet and usb would not power down (you guessed it, to allow wake on lan :) ).

So if you dont feel like upgrading and losing your HP MIE interface, perhaps we can see if we can figure this out instead?

---

### Post by JPBodner on 2009-08-25
I'd be happy to try that. I'll probably upgrade to UNR someday soon, but it would invalidate my warranty apparently, so I'm ok sticking with MIE for now.  After all, it is Ubuntu!  

Thanks

---

### Post by P4man on 2009-08-26
it can't void your warranty. At worst HP may not give you any support since you're using a different OS. Warranty won't be affected though.

Anyway, Ill see what I can find on the shutdown scripts, want to learn that anyway. Unless someone can tell right away where I should start looking?

---

### Post by Keen101 on 2009-08-27
haha, it wouldn't invalidate your warranty. :D

Just make sure you leave the recovery (hidden fat32) partition alone. When you install UNR just install ext4 over the old ext3 partition, and reuse the swap partition. then add this to your new GRUB:

title System Restore
root (hd0,2)
chainloader +1
boot

I recently install UNR, and then screwed it up by trying to do a forced upgrade to Karmic 9.10. It totally screwed the UNR stuff up since there were LOTS of bugs in karmic. I had to use the recovery partition (which worked very well :D) to restore MIE.

I now have MIE, and am waiting until Karmic 9.10 UNR comes out of alpha/beta. The karmic version of MIE works with sound and ethernet out of the box (unlike jaunty).

---

### Post by P4man on 2009-08-27
There is a long discussion about (what seems to be) your issue here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784)


It does seem to be an issue with the kernel, which may or may not have been fixed by now, but i thought Id highlight this post:

> I'm thinking/confirming its now only hardware related....

With "Wake-on LAN" and "USB Sleep and Charge" both [Disabled] drain over the weekend was a mere 2%.

Sorry folks still having problems, but it looks (to me at least) that Jaunty + BIOS settings = acceptable battery drain while shut down.

@karl
You may find that simply changing the BIOS, but staying on Hardy helps on your NB100.....


I dont know if your bios has such settings, and even less if it would help with hardy, but its worth checking.

---

### Post by JPBodner on 2009-08-28
Keen, 

Did you happen to have the battery drain behavior before you installed UNR?  Did the upgrade fix it?

---

### Post by Keen101 on 2009-09-03
> **JPBodner said:**
> Keen, 

Did you happen to have the battery drain behavior before you installed UNR?  Did the upgrade fix it?

well, i never thought about it before. i never thought about it with unr either. However i tried seeing if my battery had drained after hibernating it a night now with my mie (restored). The battery seems to not drain on my machine. it was still 100% after 12 hours being off.

not sure why yours is draining.

---

### Post by PhilMize on 2009-09-08
> **Keen101 said:**
> haha, it wouldn't invalidate your warranty. :D

Just make sure you leave the recovery (hidden fat32) partition alone. When you install UNR just install ext4 over the old ext3 partition, and reuse the swap partition. then add this to your new GRUB:


Um... So what happens if you wiped the recovery partition? Could the be the reason I can't reinstall the MIE OS? I downloaded the os installed from hp and everything it installed just fine but when it boots it freezes at about 20% and will sit there forever.

I don't mean to go off topic... :D

---


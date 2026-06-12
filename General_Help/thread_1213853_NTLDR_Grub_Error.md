---
title: "NTLDR Grub Error"
date: 2009-07-15
forum: General Help
---

### Post by android73 on 2009-07-15
Hi,

I am running a dual boot machine on two separate hard drives, one Ubuntu 9.04 and the other Windows XP home. Everything has been working fine. Well, unfortunately I seem to have trashed my GRUB loader after cold booting my machine with a flash drive plugged in as well as an SD memory card plugged into my monitor. Ouch. Now I get an error saying NTLDR not found, press Ctrl, Alt Del to reboot. Well I went into Ubuntu since XP won't load anymore. I then read a few forum posts and changed my grub at the end to something like this:

title	 Microsoft Windows XP Professional
root	 (hd1,0)
 map	 (hd1) (hd0)
 map	 (hd0) (hd1)
savedefault
 makeactive
chainloader	+1

Now I can't even get into Ubuntu or XP.  Fortunately I was able to simply unplug my ubuntu drive and get back into windows as normal. So how do I go about fixing this?
Any help would be greatly appreciated. I love using Ubuntu!

Regards,
Andrew

---


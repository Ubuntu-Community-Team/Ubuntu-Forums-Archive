---
title: "wake up from hibernate takes too long"
date: 2010-01-16
forum: General Help
---

### Post by michalre on 2010-01-16
Hi guys,

I am having a problem with a slow wake up from the hibernate in karmic with gnome.

My desktop has 2GB of ram and 4GB of swap. I am doing standard hibernate from the menu.

Hibernation takes 44s, which I can live with for now. But wake up measured from grub boot menu to unlock dialog takes 2m 47s. I think it's reasonable to expect it to take less than a minute.

I would be very thankful for any help. Let me know if you need more info.

Regards,
Michal

---

### Post by tgalati4 on 2010-01-17
How long does it take to cold boot?  

Wake from suspend on linux takes me ~10 seconds.  On a 5-year-old powerbook running Tiger 10.4, wake takes 3 seconds.

Wake from hibernate takes almost as long as cold boot. So . . .

Either the linux boot is as fast as it can be (since a memory snapshot from disk takes as long as loading from scratch).

or

Reserve use of Hibernate for special situations.  For example you have 4 workspaces with 4 applicaitons running in each (a total of 16 apps running).  When you hibernate, you can keep all of those apps open right where you left them.  It would certainly take longer to boot and reopen all of those apps.

For most folks, if you can get suspend to work properly, use that.  Hibernate works better in Windows because you can normally come out of hibernation in a minute vs 4-minute boot for most older, crapware-laden, Windows machines.

---


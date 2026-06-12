---
title: "Asus k40ab + hd4570"
date: 2009-10-19
forum: General Help
---

### Post by tyk on 2009-10-19
Hi all, I got me an ASUS K40AB with an ATI Radeon HD4570 and for many days was unable to get the video card working on (any version of) 'buntu. Now after much googling I have found that this comp comes with two GPUs, an onboard HD3200 series and the HD4570. This is the Power Xpress technology. This basically means that on a Vista like OS it switches between the GPUs in realtime. Like for most of the time it runs the onboard GPU and for demanding tasks (games/3d work etc.) it switches to the 4570. All this is happening to save power. Now this is great if you run Vista but realtime GPU switching in Xorg is not even begun. Read [_this_]("http://www.phoronix.com/scan.php?page=news_item&px=Njc2Nw") and [_this_]("http://ajaxxx.livejournal.com/60080.html"). These guys explain it well.

So the solution is to keep it running only on the 4570. This is done by  installing XP which can switch the GPU to the 4570 permanently. Before you do that please read [_this_]("http://support.asus.com/faq/faq.aspx?no=F59CF0E0-E14E-6244-FBF1-9FF9C5727ABC&SLanguage=en-us") and [_this_]("http://support.asus.com/faq/faq.aspx?no=FE94C8A8-38EE-8A15-BFE1-4712A666978D&SLanguage=en-us").

I installed XP and then Xubuntu 9.04 amd 64. Updated to kernel 2.6.28-15 and ran the ati catalyst 9.9 driver. This has finally worked. Performance is acceptable. glxgears=1000fps~. All confirmation from lspci which does not show the HD3200 series any more. Tried foobillard (personal favorite) and performance was a little choppy but acceptable. The best part was that after installing XP I didn't have to actually boot into it.

Issues with this laptop:
1. camera is upside down. (not solved yet)
2. Atheros wireless requires jaunty-backports
3. VGA out to external monitor works on ubuntu but not xubuntu. Correction: it works on Xubuntu as well after installation of fglrx module.

---

### Post by P4man on 2009-10-19
Your links are from 2008, and its no longer entirely true there is no support at all. on some notebooks at least you can do a cold switch (does require rebooting)

[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

If you got a hybrid SLI or PowerXpress notebook, id suggest you check out the last post there and follow the link, and submit your DSDT information if it hasnt been posted yet, That will allow devs to reverse engineer the bios and perhaps one day give us a good solution. until then, Id say keep spamming nvidia/intel/amd support asking when they will support this on linux.

---

### Post by tyk on 2009-10-19
Yes the links are old I admit. Thanks for pointing that out. They're more for the explanation..
Still, 'hot-switching' seems a little far away only. Reboot+switch is simply not tenable for real world usage. My DSDT.dsl is already on there.
Cheers.

---


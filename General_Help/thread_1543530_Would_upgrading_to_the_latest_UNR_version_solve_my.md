---
title: "Would upgrading to the latest UNR version solve my wireless problem?"
date: 2010-08-01
forum: General Help
---

### Post by ShinigamiKiba on 2010-08-01
I have a Lenovo Ideapad s10, wireless is enabled in the bios and all, but after doing some research and talking to people I learned that the reason it never so much as tries to detect wireless let alone connect to it is because I disabled it using the hardware switch in Windows and the only way to re-enable it is to install Windows, the needed drives, enable the switch there and then install Linux again.

I'm currently using UNR 9.10 with my netbook and it works perfectly except for the wireless not working at all.
Would updating to 10.04 fix this so I don't have to install Windows just to enable the switch? I tried a live session of 10.04 netbook edition(I assume it's the same thing) and I couldn't install the wireless drivers on that so I couldn't test it.

---

### Post by kerry_s on 2010-08-01
nope.

---

### Post by ShinigamiKiba on 2010-08-01
Thanks.
I have another question though, if I do go through the whole process of installing windows and setting everything up to enable wireless, then when I reformat back to Linux if I disable my wireless in Linux using the switch either on purpose or by accident, would I have to do the whole windows thing again?

---

### Post by ShinigamiKiba on 2010-08-01
bump

---

### Post by snowpine on 2010-08-01
Can you enable networking from BIOS?

---

### Post by ShinigamiKiba on 2010-08-01
I can, but it does nothing, I even tried disabling it, restarting and then enabling it and nothing.
As I said, I talked to people about this, it's an issue with some of the Lenovo IdeaPad s10 systems apparently and the only way to enable wireless is through windows.

---

### Post by kerry_s on 2010-08-01
over here-> [http://www.linlap.com/wiki/lenovo+ideapad+s10](http://www.linlap.com/wiki/lenovo+ideapad+s10)
it says you need to run->
[B]sudo apt-get install bcmwl-kernel-source
[/B]
or use synaptic package manager

for the wireless to work.

---

### Post by ShinigamiKiba on 2010-08-01
I did that a while back, it's also up to date and everything.
As I said, THE only way to get wireless to work if disabled from Windows at some point is to install windows again and enable it from there.
I know because people who had the same computers and people who service computers have told me so irl and online.

but thanks anyways.

---

### Post by NFblaze on 2010-08-01
As far, as I am aware if you have a software switch that is enabled and the last setting for it was enabled before removing Windows. You should be fine.

It's really stupid idea to have a software switch that completely controls your wireless in another operating syste...but alas that's how it is.

---

### Post by ShinigamiKiba on 2010-08-02
^ yeah, so there's no version of Linux that can enable this switch? It's kind of lame they didn't fix this in 10.04 :(
guess I'll have no other choice but to reinstall windows, reformat and do all that boring stuff, then go back to ubuntu because I honestly hate using windows if I don't have to. (I'm not a very computer savvy guy, I just like ubuntu better on my non gaming systems)

---

### Post by NFblaze on 2010-08-02
> **ShinigamiKiba said:**
> ^ yeah, so there's no version of Linux that can enable this switch? It's kind of lame they didn't fix this in 10.04 :(
guess I'll have no other choice but to reinstall windows, reformat and do all that boring stuff, then go back to ubuntu because I honestly hate using windows if I don't have to. (I'm not a very computer savvy guy, I just like ubuntu better on my non gaming systems)

Yes, you have to install Windows again.

I dont think they can fix it. It's up to the dumbass manufacturers to stop doing it.

---

### Post by ShinigamiKiba on 2010-08-03
Sorry for bumping this, but is there any linux distro which might be able to let me enable the switch with so I do go through the whole boring process of installing windows just for this?

---

### Post by gyffes on 2010-09-09
I don't know why you guys are telling him this. I moved my S10-3 from Win7 starter (which actually worked quite well on this device.. just overly loaded with crapware) to Linux Mint (8) and it was great with the exception of a really whacked trackpad that I could not get under control.

Wifi worked fine. Just want that clear.

THEN, trying to fix the trackpad issue, I proceeded to try every iteration of Ubuntu 10.04. Nada. All told me my wifi was disabled despite BIOS and physical switch saying otherwise. Proprietary Hardware screen shows... none installed.

In a desperate attempt to fix this, I even installed a v9.10 version of ubuntu andddddd no go. I'm about to try Mint 9 (seeing as Mint 8 worked)... because I truly don't want to buy an external CD just to install 7.

I'll keep you posted, but I wish you guys had solutions for him (and me) before just sayin' "Nope". Where's that vaunted Ubuntu Community Support??

---


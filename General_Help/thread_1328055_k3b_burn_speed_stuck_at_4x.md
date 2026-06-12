---
title: "k3b burn speed stuck at 4x"
date: 2009-11-16
forum: General Help
---

### Post by stonebit on 2009-11-16
In jaunty 9.04 i was burning everything at any speed. After upgrading to 9.10 karmic, k3b "Medium or Burner does not support writing at 20x [or 16x or 12x]. Swithing burn speed to 4x."

I have checked DMA (it's on) and i've tried increasing the buffer to 128Mb (from auto). 

Any ideas?
I'm thinking it's an issue with k3b, but can it be resolved?

---

### Post by bernardfrancois on 2009-11-16
Some dvds or cds have a maximum burn speed which is indicated on the packaging. Especially rewritable media have slower maximum burn speeds.

If it's not a 4x max cd or dvd you were trying to write, your dvd/cd writer may not be recognised properly.

---

### Post by stonebit on 2009-11-16
I'm using 16x DVD-R media and 48x CD-R media. The DVD writes at 4x and the CD writes at 16x. Also, K3b lists my device perfectly.

I also tried upgrading the firmware, but that didn't change anything.

After toying with the settings and testing some stuff i found that checking "Force unsafe operations." under K3b Settings > Advanced, K3b is now burning at max speed. Funny enough, it still gives the message, but the second part says that it is switching burn speed to 22x (for DVDs)! What!? At least i can select 16x and it will burn at that now. 

Given the other bugs i've found (busy icon on K3b window most of the time, lack of file system updating in the file selection window) in K3b and the fact that it's version 1.68 alpha version in karmic, i'm sure now that my issue is a bug. 

At the least, i got my firmware updated, which pumps my burner up to 22x support.

---

### Post by arnab_das on 2009-11-16
> **stonebit said:**
> I'm using 16x DVD-R media and 48x CD-R media. The DVD writes at 4x and the CD writes at 16x. Also, K3b lists my device perfectly.

I also tried upgrading the firmware, but that didn't change anything.

After toying with the settings and testing some stuff i found that checking "Force unsafe operations." under K3b Settings > Advanced, K3b is now burning at max speed. Funny enough, it still gives the message, but the second part says that it is switching burn speed to 22x (for DVDs)! What!? At least i can select 16x and it will burn at that now. 

Given the other bugs i've found (busy icon on K3b window most of the time, lack of file system updating in the file selection window) in K3b and the fact that it's version 1.68 alpha version in karmic, i'm sure now that my issue is a bug. 

At the least, i got my firmware updated, which pumps my burner up to 22x support.

you see even i face this prob sometimes. its the prob of the dvd and not of k3b. just insert another dvd and check if you get the 16x option.

---

### Post by stonebit on 2009-11-16
Naw. Definately K3b. I downloaded Nero (trial just to test) and it works correctly in that and it works on my Windblows notebook.

---

### Post by bernardfrancois on 2009-11-16
You could try nero for linux:
[http://www.nero.com/enu/linux4.html](http://www.nero.com/enu/linux4.html)

---

### Post by enzio on 2009-11-28
I have encountered this same problem (but stuck at 6x). Interestingly, it seems to occur in brasero as well. So, it looks like it is not just a k3b problem.
By the way, doing "force unsafe operations" also fixes the problem for me.

---

### Post by seeker5528 on 2009-11-28
I have not looked to see what the defaults are in K3B, but I just burned a DVD today for the first time with Karmic, upgraded from Jaunty, and since it was the first time I told it to use the defaults for burning. I had the opposite experience, it told me that 15x or whatever it was defaulted to was not supported so the speed was being bumped up to 16x.

There is a PPA to make newer KDE stuff available during a release period:

[http://amarok.kde.org/wiki/Download:Kubuntu](http://amarok.kde.org/wiki/Download:Kubuntu)

But I'm not seeing K3B in there.

Later, Seeker

---

### Post by OmegaPhil on 2010-04-25
I have been sorting out burning under Linux this weekend, and have settled with k3b.

I've also experienced the bullshit degradation of burn speed as described in this thread (6x forced in my case) - my drive burns at 16x, and I use 16x rated high quality DVD+R discs (Verbatim-branded Taiyo Yuden dye).

Since wodim was clearly the source of this misinformation, I changed the program responsible for burning to growisofs (Auto appears to pick wodim). I have so far burnt at speeds >10x, so it has clearly worked.

I didn't want to force unsafe operations incase it actually did cause a serious failure...

---

### Post by enzio on 2010-04-25
OmegaPhil,

Thanks for post on this. The "force unsafe operations" method didn't seem to be causing any problems for me, but based on your post, I switched to using growisofs. This seems like the better solution and it is working fine.

-Enzio

---

### Post by OmegaPhil on 2010-04-26
No problem enzio.

I don't really know why wodim is picked over growisofs by default, so there may be some hidden issues yet to be discovered.

---

### Post by pt123 on 2010-05-03
I have the same problem K3B was working fine on Intrepid, but eversince I moved to Karmic, it is stuck at 4x. 
I can't find any mention of wodim, but there is growisofs. Where can you find what is being used for burning. 
Is this caused by KDE4? in Intrepid K3b was using KDE3.

Edit: After turning on allow "Advance Configuration", I was able to select growisofs, and now it burns at more 4x.

---

### Post by ghostborg on 2010-05-07
Changed mine from Auto to growiso and it worked for me. Thanks
Using Lucid- did not have the problem in Karmic.

---

### Post by sarge1077 on 2010-11-22
going to have to try that doesn't matter which burner i use nero brasero or keb its all burning at 8X for me with a 16X dvd and a sony 22X burner using ubuntu 10.4

---


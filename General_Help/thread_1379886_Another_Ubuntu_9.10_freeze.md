---
title: "Another Ubuntu 9.10 freeze"
date: 2010-01-13
forum: General Help
---

### Post by kennny2004 on 2010-01-13
Hey everyone, sorry for making another thread about random freezes, i've read the other dozens that i found and nothing seemed to work. So far i installed ubuntu 9.10 on my acer laptop. And it started freezes every 5 minutes or so and nothing moves no mouse pointer or anything, none of the shortcuts seem to work but ill try again next time. 

At first i browsed the forums and found i should get backport and after this is seems to have stoped freezing for a day and then while doing my computer science homework it froze and gedit didnt save anything and here i am. The only way i can get it to work is to turn it off and back on.

I've got atheros wireless card ( not sure how to spell it ) ath5k module
         Intel 945gm graphics card

And those are my biggest suspects on why this is happening.

I don't expect anyone to know the answer right away, so my question is if i can somehow replicate this freeze running some scripts, or stress test something. Because right now its random and i would like to narrow it down a little.

Thanks ;), I am going to spam ctrl+s now,

That remind me i get mini freeze when i press ctril-c to copy text or something, my mouse freezes for about 1-2 seconds after that.

---

### Post by slooksterpsv on 2010-01-13
Run a memory check on the system, run fsck -fy, try to open Youtube, I'm trying to think of things that would cause my system to freeze and how I resolved them.

When I had my 80GB drive, it was starting to fail and every so often Linux would freeze, no movement, nothing, finally one day, I started the computer and it warned me about the SMART status. All in all, it was the HDD going out.

Another time when I've had this happen is with an outdated version of Flash. I'd play some videos or what not and then after a while it would freeze, the whole system, doing nothing but in Pidgin. If I didn't open a flash video, I was fine, otherwise, I was causing system instability. Thats my 2 cents.

---

### Post by kennny2004 on 2010-01-13
Thanks i will try the check right now

fsck -fy gave me:
/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: ***** REBOOT LINUX *****
/dev/sda1: 182598/5857280 files (1.5% non-contiguous), 1868414/23416737 blocks

And youtube works fine with no freeze/crash and videos play fine

Meh managed to fix the problem with the fsck -fy then resintalling ubuntu i guess, no freeze yet

---

### Post by micio on 2010-01-22
any news?
It still freezes?
So you did just fsck -fy and reinstall ubuntu?
I also have some hdd issue, but now i can't change disk...

Thanks

Micio

---


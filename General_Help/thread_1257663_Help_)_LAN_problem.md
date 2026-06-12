---
title: "Help :) LAN problem"
date: 2009-09-04
forum: General Help
---

### Post by FireStorm102389 on 2009-09-04
ok, i was running windows and ubuntu linux as a dual boot on a 200G hard drive...well, i swapped hard drives to use the [DBAN]("http://www.dban.org/") program for a diff hard drive of mine, nothing went wrong was perfectly fine, then i plugged in my original 200G hard drive, everything ran smoothly till i noticed i forgot to plug my ethernet cord back in...needless to say i plugged it into my onboard lan port instead of my lan card and i got a blue screen of death on windows...linux still operated for a short period of time till it took a crap on me, yay linux :D anyway...i wanna know if any1 has any ideas on how to fix this, cuz i used the dban on my 200G later and now im running just linux ubuntu, but if the computer starts without any error18 or what not is a 50/50 chance, not to mention every time anything loads it says that its trying to boot or whatever from my ethernet port which makes no sense, that is y my windows doesn't work, linux seems to try and boot from the port then move on...how do i deactivate the onboard LAN port so it stops trying to boot from my home network?

---

### Post by HiImTye on 2009-09-04
it'll be in your CMOS, check your motherboard manual :)

---

### Post by FireStorm102389 on 2009-09-04
ok, ty, ill check into that :) ill let ya know what i come up with, just in case, im going to use my other hard drive...

---

### Post by Bucky Ball on 2009-09-04
Hit the appropriate key to get into your BIOS at boot (possibly F1 or Delete) and reset the boot order in there. It sounds like you are trying to 'Boot from LAN'. Set it to boot from the appropriate hard drive instead.

---

### Post by FireStorm102389 on 2009-10-26
yea, i think i got the problem solved :) linux was the solution, i just figured ill go all ubuntu instaid of a dualboot...ubuntu loads right up, and it prolly was my cmos, my stepdad reset those for me and it still kinda tries once in a while, idk what it is, but i built a new comp and its all good now, running ubuntu 64bit right now. thnx guys

---

### Post by Bucky Ball on 2009-10-27
> **FireStorm102389 said:**
> yea, i think i got the problem solved :) linux was the solution, i just figured ill go all ubuntu instaid of a dualboot...ubuntu loads right up, and it prolly was my cmos, my stepdad reset those for me and it still kinda tries once in a while, idk what it is, but i built a new comp and its all good now, running ubuntu 64bit right now. thnx guys

Build your own ... only way to go if you're into it. Nothing quite like that feeling!!

Good work and good luck. Please mark thread as solved. :)

---

### Post by FireStorm102389 on 2009-10-27
lol, i always build my own, and how do i mark as solved?

---

### Post by lisati on 2009-10-27
> **FireStorm102389 said:**
> lol, i always build my own, and how do i mark as solved?

Near the top of the page should be a link "thread tools". Click on that and you should be given an option to mark the thread as solved.

As for the CMOS settings, the next time you're looking at your BIOS settings (usually accessed by pressing a key at system startup) you might want to check if there's an option to reset them to default.

---


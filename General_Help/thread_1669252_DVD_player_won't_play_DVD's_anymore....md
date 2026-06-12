---
title: "DVD player won't play DVD's anymore..."
date: 2011-01-17
forum: General Help
---

### Post by Mesqueeb on 2011-01-17
I am using 10.10
My DVD player is Plextor PX712SA
It has never worked on 10.10...
Any advice?
Thanks!!!

-Mesqueeb

---

### Post by Smart Viking on 2011-01-17
It is because your DVD have DRM encryption on it. To get through that, run:
```
sudo apt-get install libdvdread4 libdvdcss2
```

---

### Post by mc4man on 2011-01-17
If by not working at all you mean with dvd movie disks try this

Insert an audio cd (must be an audio cd, not a data cd
After the cd is recognized then eject it, then insert your dvd.

---

### Post by Mesqueeb on 2011-01-17
> **Smart Viking said:**
> It is because your DVD have DRM encryption on it. To get through that, run:
```
sudo apt-get install libdvdread4 libdvdcss2
```

This was already installed it would seem....  

but:

> **mc4man said:**
> If by not working at all you mean with dvd movie disks try this

Insert an audio cd (must be an audio cd, not a data cd
After the cd is recognized then eject it, then insert your dvd.

THIS WORKED!!! How come!?!? xD

Hey, and what's up with many of my DVD files showing horizontal lines each time someone moves...? While downloaded movies *usually don't.

-Mesqueeb

---

### Post by mc4man on 2011-01-17
> THIS WORKED!!! How come!?!? xD
there is a **very** obscure issue w/ some plextor drives and I don't know what. (possibly the kernel

This issue was the reason i first came to this forum back in fiesty - [posted a thread]("http://ubuntuforums.org/showthread.php?t=551147"), then stumbled upon the solution myself.
(the fix is the same now as then  - insert audio cd, though some of the symptoms are different

At some point it stopped happening, either an update in fiesty or gutsy and has been fine since.
I recently replaced a benq with a plextor 712 ( new, stashed) and noticed the issue had returned in Maverick.

Cannot for the life of me find the cause, while inserting an audio cd ect. seems quite nonsensical it does work and there's possibly a clue there.
Note - you'll need to do this on every fresh boot once per session, you should be good for the life of the session

---

### Post by SirWeazel on 2011-08-02
This is crazy!! Spent 12 hours trying to figure this issue out, until i posted a new thread. mc4man is correct, and how you figured this out is beyond me. This bug occurs with the Plextor PX-755SA drive also.

---

### Post by mc4man on 2011-08-02
There is something about some plextor drives, here I only saw 4 yrs. ago for a short time with a 708a, then started again in natty with a 712a
I stumbled upon the solution way back then by using a cleaning disk on the drive. It started working fine. 
The next day same thing, made no sense. Then I realized cleaning disks are actually audio cd's. So tried one and well...

I've spent some time trying to get to the bottom of this with little success.
If you wish to file a bug then link here, I never bothered because I thought this was just with the low 700 series plextor's which not many have anymore.

Just remember this only lasts till you reboot

---

### Post by SirWeazel on 2011-08-02
Cool, thanks for the info/help.  I've never filed a bug report before, but i'll figure it out later.  And i'll link to this thread. I've got a cheap drive in a drawer somewhere i'll swap out with. It's been awhile, but i thought my drive (755sa) was fairly good in its day. I could be remembering wrong, but i think i got it when i was still in school and blindly getting everything maximum pc recommended.  Once again, thanks for the help.  It still doesn't make any sense as to why this occurs. Unless it has something to do with region protection.

Edit: also, i need to put the cheap drive in to make it simple for my wife to use. (all our computer run ubuntu).

---

### Post by mc4man on 2011-08-02
Back when the kids where around ect. I used to do a lot of burning ect., always liked plextor drives back then, That;s how I happened to have an extra unused one to put in my desktop last year only to see this happen again.
It would be interesting to see a bug against though I'm fairly sure it won't go anywhere.
The only clue may be to really understand what happens when an audio cd is inserted (drive wise), and that's the strangest part - no other type of media will do the deed.
( I'm using 11.10 presently and this still happens

---

### Post by Spyderkid on 2011-08-02
you need to install the decryption lib, it doesn't come as standard due to legal issues?!

---


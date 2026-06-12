---
title: "ATI Remote Wonder (X10) has multiple button sends"
date: 2006-06-28
forum: General Help
---

### Post by caviidae on 2006-06-28
Hi, I have a ATI Remote Wonder X10 remote control. 

I plugged it in and everything seems to load up appropriately and work. But every time I press a button it "happens" appox. 4 times. Looking at the output of xev I found that every button press would give around 8 events.  So each button was being sent 4 times!

I don't think it is a hardware error with the remote.
- works improperly on my computer (ubuntu). 
- works properly on my laptop (kubuntu).
- works improperly on my wife's computer (ubuntu), same ~4x problem.
- works properly on my computer booted from a live cd (geexbox).

So it would seem that this is a problem with ubuntu dapper. 

But what in ubuntu could be doing this? 
Does anyone have any suggestion as to how to fix this? 
Any comments are appreciated I am banging my head against the keyboard about this. ](*,) 

Thanks for any help

NOTE: my laptop (kubuntu) wasn't properly upgraded to dapper, it was done though /etc/apt/source.list

---

### Post by Leppiz on 2006-06-28
Hi!

I just tried my ATI Remote Wonder, and it seems to do the same. It seems that somebody forgot to set the delay to prevent accidental repetitions or to be precise, removed it.

I'm sure it worked fine in Breezy and pretty sure it worked a few months ago in Dapper.

I would also like to have this fixed, now it started bothering me...

---

### Post by greg963 on 2006-07-05
I have been having the same trouble for a few weeks, any help would be greatly appreciated.  I have rebuit the kernel module but I have not been able to figure out how to change the repeat rate for the keystrokes genetated by the ati remote.

---


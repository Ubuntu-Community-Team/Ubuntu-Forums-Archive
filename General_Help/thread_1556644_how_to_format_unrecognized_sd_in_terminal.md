---
title: "how to format unrecognized sd in terminal?"
date: 2010-08-19
forum: General Help
---

### Post by owners4life5 on 2010-08-19
okay so i have an sd card that when i put into my reader, it doesn.t show up. i tried a different one, and it worked fine. so my initial reaction is "format it".... i would rather use the terminal than g.u.i, for obvious reasons. there.s nothing important on the card so i can format it or screw it up. no big deal.

any help is greatly appreciated.

thanks

---

### Post by utnubuuser on 2010-08-19
man dd

---

### Post by owners4life5 on 2010-08-19
> man dd

explain please

---

### Post by owners4life5 on 2010-08-21
bump

---

### Post by owners4life5 on 2010-08-23
bump

---

### Post by owners4life5 on 2010-08-24
come on, guys, no one can answer this?

---

### Post by owners4life5 on 2010-09-28
trying to revive my old, unsolved threads..

so bump

---

### Post by coffeecat on 2010-09-28
> **owners4life5 said:**
> i would rather use the terminal than g.u.i, for obvious reasons.

What are the obvious reasons? Does the card show up when you do 'sudo fdisk -lu'?

So long as it shows up in fdisk (demonstrating that it's not completely defunct), the easiest way would be to use Disk Utility in the System > Administration menu. But if you really want to use the terminal, you could use fdisk. It's been years since I did that, so you'll have to read the fdisk man pages if you really want to use the terminal.

**edit:** no, that won't do. fdisk will only edit the partition table. You'll still have to create a filesystem in the empty partition(s). Use Disk Utility and save yourself some grief. :)

---

### Post by owners4life5 on 2010-09-28
no see, the problem is, it will not show up for anything..nada. i need to completely "reset it", per se

---

### Post by coffeecat on 2010-09-28
> **owners4life5 said:**
> no see, the problem is, it will not show up for anything..nada. i need to completely "reset it", per se

That probably means that it's dead. It's an ex-SD card. It's nailed to the perch. Sorry. If it doesn't show up with sudo fdisk -lu even as an unformatted device, then it's likely a goner.

SD cards have a short life. Like all flash devices they die much sooner than hard drives.

---

### Post by owners4life5 on 2010-09-29
thank you for all of your help,

i really do appreciate it..

but as i said earlier, i.ll stick it into another xp machine, and it displays and works properly.

---

### Post by spillage2 on 2010-09-29
I've had this before. I have started to format a pen drive or card and then screwed the format process.

This killed the card when used in ubuntu. 

I found reformatting in xp brought it back to life. May be worth installing vbox with xp running..make sure you don't use the one from the repo as that one is not usb compatible.

Sure there should be another way to bring it back to life within ubuntu though.

spill.

---

### Post by coffeecat on 2010-09-29
> **owners4life5 said:**
> but as i said earlier, i.ll stick it into another xp machine, and it displays and works properly.

You said earlier? In this thread? No, I don't see that otherwise I wouldn't have suggested the card is dead.

I agree with spillage2. If you can see the card in XP, try reformatting it in XP.

---

### Post by spillage2 on 2010-09-29
I would also like to add that ubuntu has seen a few drives that windows has show as doa so dont feel as though this os is all to blame.

I have been an avid user of windows for year and in the last few months now have 1 desktop and 4 laptops all running lucid. The only real problems I have had is the user (me)  but eventually worked things out.

---

### Post by owners4life5 on 2010-09-29
> **coffeecat said:**
> You said earlier? In this thread? No, I don't see that otherwise I wouldn't have suggested the card is dead.

I agree with spillage2. If you can see the card in XP, try reformatting it in XP.

> okay so i have an sd card that when i put into my reader, it doesn.t show up. ***_i tried a different one_***, and it worked fine. so my initial reaction is "format it"

i did.

but i.ll try spillage2's suggestion.

---

### Post by coffeecat on 2010-09-29
> **owners4life5 said:**
> [quote="coffeecat"]You said earlier? In this thread? No, I don't see that[quote="owners4life5"]okay so i have an sd card that when i put into my reader, it doesn.t show up. ***_i tried a different one_***, and it worked fine. so my initial reaction is "format it"                      [/quote]

i did.

but i.ll try spillage2's suggestion.[/QUOTE]

@owners4life5, I wouldn't normally bother arguing such a trivial point, but I'll make this comment to help you get the most out of this forum. Your original post  was not clear. The way I read "I tried a different one" is that you tried a different card, not that you tried it in a different OS. There is no mention of XP, or another computer. **You** knew what you meant, but others wouldn't necessarily from what you posted. :) You need to make sure your posts describe your problem accurately. That way people can address your problem in a way that helps you.

But apart from that I hope reformatting it in XP works for you.

Good luck! :)

---

### Post by owners4life5 on 2010-09-29
thanks. sorry for being a pain.

---

### Post by owners4life5 on 2010-09-29
i know this is no excuse...but i.m sorry...it.s just been a long week at school is all.... you seem like a helpful person, and i appreciate you even trying. i.m sorry for not being specific..

---

### Post by coffeecat on 2010-09-29
No problem, owners4life5. It's quite an art posting to a forum and being quite clear what you mean. If I had £10 for every time someone's misunderstood one of my posts I'd be a rich man. :)

Take care now. :wink:

---

### Post by owners4life5 on 2010-10-06
so the card is dead.

oh well.

---

### Post by emonette123 on 2013-03-27
> **owners4life5 said:**
> so the card is dead.

oh well.

Not necessarily.  Use a camera to format your card, it worked for me to recover from a bad image write.

---

### Post by coffeecat on 2013-03-27
Back to sleep, old thread.

---


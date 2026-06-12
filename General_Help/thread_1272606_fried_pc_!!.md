---
title: "fried pc !!"
date: 2009-09-22
forum: General Help
---

### Post by linux_dragon on 2009-09-22
my pc case got a couple of hard hits the other day, and stopped booting windows properly,,it boots up, but when it reaches startup restarts,.,.
so i tried booting ubuntu jaunty from the live cd, but it just stops while loading, and the caps lock and scroll lock start dimming, till it restarts!!
knowing that i used to boot ubuntu all the time...
so what hardware is damaged? if anyone could tell ?!!
and any ideas ??!

---

### Post by scragar on 2009-09-22
By the sounds of it the problem is either a fault on the motherboard or a failing power supply. Given the damage that those parts can do if they're faulty I would be carefull about switching it on until you identify the problem. There are a few ways you can test the powersupply to make sure it's giving constant levels of power, but it might be easier to just take it into any good computer store and have them check it out for you.

---

### Post by linux_dragon on 2009-09-22
i c, so nothing i can fix my self ?!
and if it is a faulty in the motherboard, does that mean a new motherboard ??

---

### Post by doas777 on 2009-09-22
ok, you wanna check your hardware in this order
1)<unplug all uneeeded peripherals>
2)Hard Disks (SMART tools, hddtach, etc)
3)Ram (memtestx86, available on ubuntu liveCD)

if all of these turn up no problems, then the next step if to replace the Mobo. usually your mobo will be damaged before your processor, but if you have to buy a new proc you prolly need to replace teh mobo as well. it is up to you which was would be more cost effective, but in the very few cases I have had to replace a proc for nonfunction, I have ended up wasting money on a replacement mobo first, only to find that the problem did not go away, and that in replacing the proc, I had to buy another mobo for it....

---

### Post by scragar on 2009-09-22
I'm going to say it's about 90% likely to be your power supply, but it's impossible to rule out the mobo based purely on what you've said. As I said, you want to test the power output from the PSU, see if it fluctuates, this is easy for me to say, since I recently bought [one of these](http://www.scan.co.uk/Product.aspx?WebProductId=391645).
If you can't test it yourself though it's probably good to take it into a show and see if they'll test it, any good computer store should have a method of testing faulty hardware and probably won't charge you if you're planning to buy the replacement from them(scan have never changed me for testing hardware before, not even my faulty mobo which I bought on ebay(which is why I don't buy on ebay anymore :p)).

---

### Post by P4man on 2009-09-22
"hard hits" ? you mean like hitting it or dropping it or  something?
If it was turned on while that happened, then the most likely thing to have occured is a harddrive crash. Try disconnecting it and see if ubuntu boots from a cd.

Other things I imagine could have happened: cable come lose (IDE/SATA or anything really). Heatsink knocked off the cpu. Actually, check that first!. A PCI card that has come lose (videocard or other). Memory modules no longer properly seated..

I very much doubt your motherboard would be damaged though, I suspect you could drop a PC case from a second floor (well, on your lawn) and it might still be okay.

---

### Post by FCS tech on 2009-09-22
First reseat your memory. take each one out (0ne at a time) and put it back in. try booting.
check that everything else is seated cables ect.
if you have another power supply swap it out to see if that is your problem.
take if from another computer.
 
post what happens. good luck.

---

### Post by scragar on 2009-09-22
I just want to ask those people mentioning the hard drives what planets they are on, the liveCD has the same problem, it is so impossibly unlikely to be the hard drives causing the problem that it's negligible to mention them other than to recommend they be disconnected so they don't suffer any further damage from dodge power flow.

p4man is right about checking wires and such, I never thought of that since it's always the first thing I check, and if your heatsink came loose I'm sure you would know(Mine did that once, I heard it rattling for days before I opened my case and the heatsink just fell out. Stupid me.)

---

### Post by linux_dragon on 2009-09-22
i just tried the ubuntu memtest, and it showed lots and lots of errors, but now i restarted it again,,,,and its not showing any errors!!

ps: i think it was hit from the top right side, where the dvd drive lies..

---

### Post by doas777 on 2009-09-22
> **scragar said:**
> I just want to ask those people mentioning the hard drives what planets they are on, the liveCD has the same problem, it is so impossibly unlikely to be the hard drives causing the problem that it's negligible to mention them other than to recommend they be disconnected so they don't suffer any further damage from dodge power flow.

an HDD that is physically damaged but still connected can cause serious problems, even if the disk is not in use. the LiveCD does not preclude a hdd issue, unless you have physically disconnected it.

---

### Post by scrooge_74 on 2009-09-22
You should get that powersupply check, cause if could work well today, but tomorrow problems could return, and powersupplies tend to damage things bit by bit. You could get ram damage today, tomorrow something in the motherboard and one day the HD goes.

So better check that powersupply

---

### Post by P4man on 2009-09-22
> **scragar said:**
> I just want to ask those people mentioning the hard drives what planets they are on, the liveCD has the same problem, it is so impossibly unlikely to be the hard drives causing the problem 

Its fairly likely in fact. A live cd does look for your harddisks and will even enable swap on any swap partitions it finds. If the drive is borked physically, there is a good chance the livecd won't boot or hang while trying to read the drive.

---

### Post by scragar on 2009-09-22
> **P4man said:**
> Its fairly likely in fact. A live cd does look for your harddisks and will even enable swap on any swap partitions it finds. If the drive is borked physically, there is a good chance the livecd won't boot or hang while trying to read the drive.

But for lights to slowly dim and the machine to restart? Sounds very much more like a power problem to me.

---

### Post by linux_dragon on 2009-09-22
yeeeahh,, atlast.. ok so ive disconnected the power from the harddisk,,
and now ubuntu live cd successfully booted,, no problems at all.....
so is this just the harddisk ??

---

### Post by doas777 on 2009-09-22
> **scragar said:**
> But for lights to slowly dim and the machine to restart? Sounds very much more like a power problem to me.


and if the problem is one mechanical motor drawing too much power? that sounds like somthing a hdd could do to me, if the PSU is already underpowered. 

i;m not arguing with you; I agree it is likly a PSU or Mobo issue, but there is a certain set of steps you wanna follow when isolating a failed component, and to be honest an impact is going to affect a HDD a lot more often than it will affect a PSU.

now the question is, if it is a bad PSU, then how much of the other equipment has been damaged/destroyed by the power fluctuations? usually if you pop you mobo from a surge, your cpu is toast as well...

---

### Post by P4man on 2009-09-22
> **linux_dragon said:**
> yeeeahh,, atlast.. ok so ive disconnected the power from the harddisk,,
and now ubuntu live cd successfully booted,, no problems at all.....
so is this just the harddisk ??

Hard to say for sure, but, yeah probably.

---

### Post by linux_dragon on 2009-09-22
thanx to all,,
it seems its just the hard disk..

---


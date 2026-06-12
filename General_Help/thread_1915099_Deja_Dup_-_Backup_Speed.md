---
title: "Deja Dup - Backup Speed"
date: 2012-01-25
forum: General Help
---

### Post by svtguy88 on 2012-01-25
I'm trying to use Deja Dup (the default backup software) to backup some of my data.  It seems to work, and the interface is simple and easy to use.

However, the backup speed seems ludicrously slow.  Is there a way to improve this?  htop shows that only one of my processors appears to be working (though they alternate, one will peg to 85-95%, and then the other will) on the backup.  I am backing up a lot of data (~2 TB), but OS X's Time Machine handled everyting nice and quickly (and that was on an old G4 machine).

Originally I thought it would be just the first backup that would take forever, but even the incremental ones go very slowly.

Any tips?  My machine is a dual Xeon (@3.0ghz) with 8 GB RAM.

---

### Post by svtguy88 on 2012-01-26
No one?  Does anyone else at least have the same problem I'm having?  

It's been twelve hours since I posted this.  At that point, my backup was ~25% done.  It's now just under 50%.  I started the process over a day ago...

---

### Post by raziel09 on 2012-01-26
I have used Deja Dup for the last couple of years and never had to wait over 10 mins for the initial backup and the incremental ones take mere minutes. 

One thing that might help figure out your issue is where are you backing upto?

Mines an very old internal 20GB IDE drive and my process is an old AMD ATHLON 64 3200+. So nowhere near as powerful as yours.

If your backing up over the network or possibly to Ubuntu one then i would expect it to be slow but still only take about 30 mins - 1 hour to complete.

Hopefully someone else will be along to help or who may have the same issue as yourself.

---

### Post by dcstar on 2012-01-26
> **pkmgarf said:**
> I'm trying to use **Deja Dup** (the default backup software) to backup some of my data.  It seems to work, and the interface is simple and easy to use.
...........
Any tips?  My machine is a dual Xeon (@3.0ghz) with 8 GB RAM.

Do you have enough free space in /tmp?

I've just installed this package and given it a try, I must admit that I like the **Unison** package (which I have been using for a while) better.

---

### Post by lukeiamyourfather on 2012-01-26
I'm not a fan of Deja Dup. I much prefer using rsync to backup my data because of the reliability and performance. Though it lacks features compared to Deja Dup. To get the most performance from Deja Dup try disabling encryption and backup to local disks that use native interfaces (like SATA or SAS and not USB or Firewire).

---

### Post by unoniasog on 2012-01-26
This may be a substantial deal for the do-it-yourself woodworker who likes to maintain active by doing factors. This method stands out as the MyShedPlans Woodwork Bundle and it truly is filled up with a great deal of options.                              You'll find an enormous selection of plans which might be simple for almost any skilled to work with.                              If you like solid wood doing work, you may have over 12,000 programs and patterns from clock housings to stables. In order to create your own personal shed to retailer goods, there are numerous ideas, which you could put along with your family more than a saturday and sunday. You are going to also have got a list of components you will want. You're going to know almost everything which you need and do not want to your woodworking venture.                              You are likely to have a great deal of thorough guidelines for woodworking projects and home enhancement jobs. You will have an uncomplicated time constructing your initial shed.                              Just what number of folks would like to get a garden shed inside their yard to place their products in? Nevertheless they simply cannot see spending the money that it expenses to get one particular presently created.      [yard sheds](http://www.tas-aircraft.com/index.php/member/29345/)   [diy shed plans](http://www.emilyjohnson.tv/index.php/member/28035/)   [shed prices](http://www.digieffects.com/index.php?/member/242446/)   [free shed blueprints](http://www.exchangechambers.co.uk/index.php/member/4064/)   [garden shed drawings](http://sebrinausonny6.insanejournal.com/523.html)   [shed plans online](http://yesprep.org/member/203928/)   [shed kits plans](http://www.refreshrichmond.org/index.php/member/22579/)   [gambrel roof shed plans](http://www.articleplugin.com/2012/01/effortless-solutions-for-do-it-your-self-residence-improvement/)   [free garden plans](http://frobertbell.com/index.php/member/7674/)   [ebay sheds](http://www.nutritionblognetwork.com/index.php/member/1090/)  [how to build a yard shed](http://learningtoeat.com/2009/03/07/black-tea-whisky-honey-lemon/)[how to build a 8x10](http://forlordphoto.com/tiberias/forum/bbs/viewthread.php?tid=17715&extra=page%3D1)[how to build a shed from scratch](http://tabletdunyasi.com/item/21-asus-eee-pad-slider-transformer-and-memonun-avrupa-fiyati-belli-oldu)[how to build a shed step by step](http://jborda.aprendedrupal.es/trabajofinal/node/12447)[how to build a shed roof over a deck](http://www.twhois.com/forum.php?mod=viewthread&tid=66851&extra=)[how to build a yard shed](http://www.sego.com.tw/modules/newbb/reply.php?forum=1&topic_id=1%252525252525252525252525252525252525252525252525252525252525252525252525252bresult:%252525252525252525252525252525252525252525252525252525252)[how to build a flat roof shed](http://www.muehle-mayer.it/guestbookadd.htm)[how to build a 10x1](http://real-ch.m78.com/bbs/kumaug/light.cgi?res=7185)[how much would it cost to build a shed](http://kioskimmo.free.fr/phorum/read.php3?num=1&thread=13&action=1)[how to build a barn style shed](http://www.eurobikemaine.org/cgi-bin/yabb/YaBB.cgi?board=news;action=display;num=1327520553;start=0)

---

### Post by dcstar on 2012-01-26
> **wap980 said:**
> **I much prefer using rsync** to backup my data because of the reliability and performance. <snip>

Which is what Unison front-ends with a nice GUI.

---

### Post by svtguy88 on 2012-01-27
lol...the initial backup is *still* running.  Looks to be at about 90%.

Some more detials...I'm backing up from one SATA drive to another, both of which are plugged into the motherboard. The system itself resides on a RAID array that runs off of a PCI card (3 SATA drives).  I honestly don't remember if I clicked "use encryption" or not, but even if I had...two days, really?

As for /tmp.  I see no reason it would be low on space.  The "properties" window of nautilus shows something like 50 MB in /tmp right now 

As a side note, I had used rsync before this, but wanted to give the default app with the pretty/simple GUI a try.  I think I may go back to a script and rsync.

---


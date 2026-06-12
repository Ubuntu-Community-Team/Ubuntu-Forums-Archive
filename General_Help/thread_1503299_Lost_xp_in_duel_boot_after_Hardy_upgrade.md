---
title: "Lost xp in duel boot after Hardy upgrade"
date: 2010-06-06
forum: General Help
---

### Post by houseworkshy on 2010-06-06
I've just had a phone call from an 8.04/win xp duel boot user who has lost the boot entry to xp after a  8.04 update.  I guessed at a system upgrade but she checked and is still on Hardy.  They write and only have the xp for printing as there is no Linux support for the cannon printer.  Using the printer is important.  I've said I'll pop round and try to sort it out.  Any ideas how I can do this.  Update grub in recovery mode maybe or if I need the command line what should I try?  I'd like to know before calling as though I'm not quite a novice this isn't a problem I've had to cope with since grub 2 beta ( didn't solve it then either an am still using 9.04 ).  Hacking legacy will be new to me.  As this is a writers machine with all her work on it I'd regard it as a  critical pc, don't want to mess things up for her.  I'd be very grateful for any good advise.

---

### Post by Sylslay on 2010-06-06
Is basic checked?
run in 8.04 in console:
os-prober and then
update-grub2

More advance: (work for 2 linux when one os use grub and second use grub2)
just install second OS , say 10.04 on second partition (must erase 8.04 and do clean install)
when installing os , choice instead MBR , choice begin of partition for Os , say sda2 for 10.04, it will not touch MBR  with windows (or/and old version of grub ) and when you get to new linux than You go to step 1 - basic,and if 1 grub does,t not appear with xp than second grub2 has to.

IMHO, It should work flawless, but not tested with windows.
works for problems with PCLinuxos and Ubuntu 10.04.:popcorn:

---

### Post by wilee-nilee on 2010-06-06
Once there is a boot problem especially when you didn't do the update/upgrade the boot script will show you whats going on.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
If you need help with this fix post it in code tags if needed.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

I would be very careful with this, if you start just trying to reload grub or the xp boot without more information you may have a worse situation. I wonder if they hit the upgrade button by mistake, and it was borked.

---

### Post by wilee-nilee on 2010-06-06
> **Sylslay said:**
> Is basic checked?
run in 8.04 in console:
os-prober and then
update-grub2

More advance: (work for 2 linux when one os use grub and second use grub2)
just install second OS , say 10.04 on second partition (must erase 8.04 and do clean install)
when installing os , choice instead MBR , choice begin of partition for Os , say sda2 for 10.04, it will not touch MBR  with windows (or/and old version of grub ) and when you get to new linux than You go to step 1 - basic,and if 1 grub does,t not appear with xp than second grub2 has to.

IMHO, It should work flawless, but not tested with windows.
works for problems with PCLinuxos and Ubuntu 10.04.:popcorn:

I would say besides being almost not understandable this is a bogus answer without more information about the system overall. Your honest opinion is not a good one.

---

### Post by houseworkshy on 2010-06-06
Sorry it took so long to get back, I had a visitor.  
What I shall do, as apparantly she can't find the ntfs partition in system monitor either ( it is a single drive 32bit so the duel boot is based on partitions ) , is take a copy of puppy round too and hope that can find windows.  If it can I shall then load it to ram and use it to back up her work before touching anything else.  I'll look at the logs, install sysinfo, Ubuntu *seems* to be working, and *if* her internet is ok post the results here.  
It seems strange to me that if this was a simple update not a distribution upgrade that there aren't other posts on the same theme.  All 8.04 users get the same updates so why no fuss here on the forums.  Therefore a messed up accidental dist upgrade does seem likely to me too.  Any advise would be appreciated before I go round tomorrow as I can't be sure of her connection.  If, with your help, I can mend it then all is well.  If not then I pray I can save her work, she's 79 and there are several novels on the machine.  I've nagged about backing up so much previously that I don't anymore as it causes anger though I did do one for her around a year ago but there are tens of thousands of words under the bridge since then.  It is good writing too, she's really hit form in recent years and puts in many hours a day.
If it is not mendable then I suppose I'll put in something like mint as though she can make open office jump through hoops the geeky techy system stuff is way beyond her.  The problem with that is that though, for technophobes, recent releaces of mint have been "Ubuntu mended" it is a configured version of kde and She is used to gnome.   
Feel pretty guilty about this as having had many problems with windows ( I had to mend/clean the dratted thing at regular intervals ) it was at my recomendation that she put in Ubuntu.  Which in the 8.04 days was fine bar the printer but ... enough posts on that theme already.
Well the main thing is saving the work. Then; open office working, being able to print, browse and email.  Funky new features have no value whatsoever to her, in fact changes are offputting.  All that matters is that it has got to be simple, stable and do all the basics.   Mending it would be best, that at least buys time untill 10.04 gets ironed out to smooth gui auto-install on duel boots.  I'll look at the video card too, all I know is that it is not nvidia or ati.  And a ps the only additional repositories are the defaults and mediabuntu.  Can this really have been due to an update?  I'll post back when I know more, meanwhile all advice is appreciated.

---

### Post by wilee-nilee on 2010-06-06
I'm probably not the person to rely on, I know more of what not to do then what to do. This is a issue that none of us including you know whats going on. Hopefully others will have some advice that is applicable.

The boot script is helpful for knowing if the boot has been changed and other stuff, but it is not a easy read. I think for sure just looking at the HD with gparted from the bootable puppy is a good start.

It is easy to take on more responsibility for others setups then really is applicable, if this person is stubborn and just can't get the need for backing stuff up off the computer it is not your fault. Nobody wants to see anything lost but sometimes you have to detach from the emotions of the responsibility and just state here is what needs to be done and I wont do anything if you don't do it.

This sounds cold but is a technique used with interventions with people with addictions.

---

### Post by houseworkshy on 2010-06-06
Point taken but she happens to be my Mum.  It's not bias about the quality of the writing either, agents are interested.  Got to be saved.  One is a book which though not a faithfull auto biograpy is based on her time as a evacuee during ww2 the other about the RAF, my father was in bomber command shot down and then in stalag 4b, a rather good sci-fi and lots of stories from all genres.  There is a lot more than that but, thankfully, it has got to the hard copy stage and the final versions of all the older work are on cd as well.  Mum has had an amazing rush of high productivity recently.  I can't help a certain emotional attachment.  I remember windows ( helped by a power cut mid-defrag ) destroying my fathers last book, none of the undelete software got any back and we tried all we could find.  He managed to re-write a few chapters of it but there wasn't time in the end.  The whole familly write and we've all lost work to operating systems I'd hoped linux might....ah well.  Not as bad as windows yet but getting there it seems.

---

### Post by wilee-nilee on 2010-06-06
> **houseworkshy said:**
> Point taken but she happens to be my Mum.  It's not bias about the quality of the writing either, agents are interested.  Got to be saved.  One is a book which though not a faithfull auto biograpy is based on her time as a evacuee during ww2 the other about the RAF, my father was in bomber command shot down and then in stalag 4b, a rather good sci-fi and lots of stories from all genres.  There is a lot more than that but, thankfully, it has got to the hard copy stage and the final versions of all the older work are on cd as well.  Mum has had an amazing rush of high productivity recently.  I can't help a certain emotional attachment.  I remember windows ( helped by a power cut mid-defrag ) destroying my fathers last book, none of the undelete software got any back and we tried all we could find.  He managed to re-write a few chapters of it but there wasn't time in the end.  The whole familly write and we've all lost work to operating systems I'd hoped linux might....ah well.  Not as bad as windows yet but getting there it seems.

I suspected that it was a family member. I had to do a similar thing with my mom just this week as I described detaching. I certainly hope that you can get this fixed. If it was me I would buy a external HD and just transfer it first before doing any repairs. It may be a simple fix, but it would be a shame to lose any of this as it at the least has a core value to her and you as well. I will when I see anybody that I know is good at this, let them know about your thread.

This is a situation that there is always a chance of losing it no matter what is done now or in the future, so backing it up would be a main priority.

---

### Post by houseworkshy on 2010-06-07
That's a good idea for when I have more funds. Meanwhile I have a couple of flash sticks and a tub of blank cd's. So stage one backup, via puppy, to cd. I'll grab the address book while I'm in there too. That's the important stuff. If that works the panic is over as format and reinstall becomes a viable option again if all else fails. I haven't seen it yet but not finding the ntfs partition in system monitor is worrying if true, even if the boot is mucked up one should at least be able to see the partition. I'll know more tommorow ( later today now ...woops) when I see it first hand. If the connection is sound then I'll be able to post, if not I'll save logs, htop, sysinfo and all the other diagnostic stuff I can thing of to flash and come back home to to post from my machine.

Thanks for your help whatever happens. If I can fix it I'll mark the thread as solved, if not watch this space. Signing off to sleep now.

The next day.  Just about to set out.  Panic level downgraded too, recent work has been done in Ubuntu and so it's fairly safe plus the internet works.  So all I need to take is puppy 5 and a few blanks as I shall be able to access the forums from Mums machine.  All that needs to be done is back up recent work and get the boot record back for the glorified printer driver ( win xp ) Back here in an hour or two.

Change of plan.  Total reformat and reinstall.  Getting a new printer :) so bye bye windows either HP auto smart 4680 or HP f2480.  One or the other as things need to be done and that is what is in the shop.   Which would be better stability and ease of setup and use being the priority, also 8.04 or 10.04  Not duel boot this time, any windows appearances will be limited to wine or virtual box.  It is a 32 bit system.

---


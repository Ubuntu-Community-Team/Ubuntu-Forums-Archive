---
title: "Ubuntu just destroys DVD+RWs"
date: 2010-11-21
forum: General Help
---

### Post by cd-r80 on 2010-11-21
Ubuntu just destroys DVD+RWs. K3b gives always success but then it says hal cannot mount... etc. & disc tools formatting incomplete. And the result is unusable disc.

---

### Post by cd-r80 on 2010-11-21
More information & .png attached:

Nov 21 17:05:04 lightning kernel: [24982.213627] sr 10:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00 00 00
Nov 21 17:05:04 lightning kernel: [24982.217597] sr 10:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov 21 17:05:04 lightning kernel: [24982.217606] sr 10:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Nov 21 17:05:04 lightning kernel: [24982.217616] sr 10:0:0:0: [sr1] Add. Sense: Logical block address out of range
Nov 21 17:05:04 lightning kernel: [24982.217627] sr 10:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00 00 00
Nov 21 17:05:54 lightning kernel: [25031.837760] sr1: CDROM not ready.  Make sure there is a disc in the drive.

---

### Post by cd-r80 on 2010-11-21
Well I found reasons why.

[http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html)

and also discussed in:

[http://jeff.ecchi.ca/blog/2010/05/31/burnt-by-disc-burning/](http://jeff.ecchi.ca/blog/2010/05/31/burnt-by-disc-burning/)

Perhaps the same thing with the freezing problems and no answers or fixes.

"is the reason,not that you`d ever find that out on the ubuntu site or forums,I was searching for months for a solution but only very recently did I get to the heart of the real reason for the failures.

Looks to me like corporate-inspired sabotage.[snip]"

---

### Post by cd-r80 on 2010-11-21
Finally I managed to fix my DVD burning. Ubuntu packages for Burning in Lucid are broken or "broken" (Karmic too, Maverick?).

[http://media.cdn.ubuntu-de.org/forum/attachments/2511837/cdrtools-a80pre_3.0-amd64.tar.bz2](http://media.cdn.ubuntu-de.org/forum/attachments/2511837/cdrtools-a80pre_3.0-amd64.tar.bz2)

It comes with install script. First time for a long time I can Burn dvd+rws.


[http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html)


"Many Linux distributions now come with broken variants of cdrtools"

---

### Post by wilee-nilee on 2010-11-21
Look up the meaning of confirmation bias, and recognize your own.

Complaining about something not working when it seems you just don't understand some ways to get around this **free **software seems counter productive.

---

### Post by cd-r80 on 2010-11-22
Don't understand your answer totally. I asked about this burning problem long ago. No answers. But Then I found answers why it is not answered. All the Drives work now.

This was one possible answer:
"In summer 2006, the attacks from the group of Debian maintainers escalated and in September 2006, these people created something they call a fork from cdrtools. They soon added a lot of bugs and this way turned the "fork" into a questionable experiment. The last work on this "fork" has been done eight months later on May 6th 2007, then the leader of the attacks stopped his efforts on the fork and instead started to advertize for nerolinux".

But I mark this solved anyway. I hope that the packets (link above )help fix DVD-burning.

---

### Post by drewsus on 2010-11-22
Yeah, that was kind of a rude comment wilee-nilee. So he shouldn't ask for help or comment on a problem because its free software? Then what is the point of this forum?

Im glad you got it working cd-r80 and thanks for posting information and solutions as well! 

You might want to mark this thread solved so that others looking for a solution to this problem know where to look.

Furthermore, just to add, I have never had a problem burning dvds/cds in hoary, breezy, dapper, edgy, feisty, gutsy, hardy, intrepid, jaunty, lucid or maverick. And fyi I prefer Gnome Baker.

---

### Post by wilee-nilee on 2010-11-22
> **drewsus said:**
> Yeah, that was kind of a rude comment wilee-nilee. So he shouldn't ask for help or comment on a problem because its free software? Then what is the point of this forum?

Im glad you got it working cd-r80 and thanks for posting information and solutions as well! 

You might want to mark this thread solved so that others looking for a solution to this problem know where to look.

Furthermore, just to add, I have never had a problem burning dvds/cds in hoary, breezy, dapper, edgy, feisty, gutsy, hardy, intrepid, jaunty, lucid or maverick. And fyi I prefer Gnome Baker.

**Feel free to report me**, the links were just confirming a bias as well as the wording look closer.
[http://en.wikipedia.org/wiki/Confirmation_bias](http://en.wikipedia.org/wiki/Confirmation_bias)

I think what is missing is that we all practice this bias amongst many others it is just recognizing this that is helpful.

---


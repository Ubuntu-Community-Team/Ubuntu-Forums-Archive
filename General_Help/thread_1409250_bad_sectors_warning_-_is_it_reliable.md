---
title: "bad sectors warning - is it reliable?"
date: 2010-02-17
forum: General Help
---

### Post by rdh61 on 2010-02-17
Hi, 

Since a few days all of my computers (3) running Ubuntu 9.10 report on startup that my external drive has "lots of bad sectors".
I have checked this disk on Windows XP with chkdsk and with the SeaTools diagnostic tool dowloaded from Seagate. Both report no problems.
Does anyone else suspect these Ubuntu "bad sector" warnings are unreliable?

Thanks.

---

### Post by nothingspecial on 2010-02-17
I think they are unreliable. I have checked my disk that gets reported in this way with 3 separate diagnostic tools and everything else says it is clean.

Put your live cd in and check it with gparted.

---

### Post by audiomick on 2010-02-17
There was a spate of threads on the subject a few weeks ago. I seems that it is possible that such warnings could be unreliable. I don't know if that is still current or not.

If several other file checkers report no problems, then you probably don't need to panic, but backups are always a good idea. :p

I would suggest searching the forum a bit using "bad sectors" and such like as a search criterion. As I said, there was a lot of traffic on the topic a few weeks ago.

---

### Post by nothingspecial on 2010-02-17
[[COLOR="Magenta"]Bug report[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136")

---

### Post by Mark Phelps on 2010-02-17
However, just because it's not "reliable" doesn't mean that it is necessarily false, either. Some folks have reported sudden increase in SMART errors when the bad sector messages started appearing.  So, unfortunately, sometimes, it IS true.

It's best to do as others have suggested -- use utilities that ARE reliable to check your drive.

---

### Post by Sentience on 2010-02-26
I have seen about 2 dozen reports of Karmic Koala killing multiple hard drives on different computers in the same house simultaneously....And its not just a false warning. Peoples hard drives are actually dying.

Yet every time I log into this site I am yet again confronted by nobody knowing anything about it. 

I know you are all volonteers just doing your best to help people for free, which is admirable, but this is very frustrating.

---

### Post by nothingspecial on 2010-02-26
> **Sentience said:**
> 

Yet every time I log into this site I am yet again confronted by nobody knowing anything about it. 


Would you care to enlighten us all then.

---

### Post by Sentience on 2010-02-26
I have no idea whats causing it. One person who seemed to know what he was talking about said that the problem was fixed, but now I lost a third hard drive so I am thinking that it probably wanst fixed.

I bumped several threads where people are having the same problem.



Like others, I was getting the bad sectors but the computers were new and then the hard drives actually did fail. Recently I didnt get the bad sector warning but the hard drive yet again still failed.

3 lost hard drives.....

I am by no means a linux guru but I would think that this would be widely talked about and addressed already.

---

### Post by Sentience on 2010-02-26
[http://www.bitsbythepound.com/karmic-upgrade-and-drive-fail-warning-137.html](http://www.bitsbythepound.com/karmic-upgrade-and-drive-fail-warning-137.html)

---

### Post by switch10 on 2010-02-26
> **Sentience said:**
> I have no idea whats causing it. One person who seemed to know what he was talking about said that the problem was fixed, but now I lost a third hard drive so I am thinking that it probably wanst fixed.

I bumped several threads where people are having the same problem.



Like others, I was getting the bad sectors but the computers were new and then the hard drives actually did fail. Recently I didnt get the bad sector warning but the hard drive yet again still failed.

3 lost hard drives.....

I am by no means a linux guru but I would think that this would be widely talked about and addressed already.

Are you suggesting that Linux is killing your hard drives??  The original poster is having a problem with a false bad sector error.  In your case the bad sector error was correct, because your drive failed.

What brand of hard drives do you buy??  I have seagate and western digital, no problems ever....

---


---
title: "Ubuntu deleted EVERYTHING"
date: 2010-03-11
forum: General Help
---

### Post by cscott5288 on 2010-03-11
OK, so I was surfing the web the other day and I went to open something on my desktop and noticed something odd ... there were no items on my desktop. I then tried to navigate to my desktop through nautalis and low and behold: no files existed. I checked in "Places" for My Music folder, Documents, anything. Nothing was there. Everything had been wiped clean. I even checked the space occupied on my hard drive which turned out to be 5.9 GB in Filesystem Properties with the words "some contents unreadable" in parenthesis. I ran file searches for the names of files I knew existed. Nothing. 

I don't know how this happened. The hard drive that I am using has about 45 bad sectors (it's brand new so I have no idea why it has bad sectors). I still have apps and programs installed like Google Chrome (all of my bookmarks are still there) but all my files are just gone!

I am still able to read and write files to locations like the Desktop ... none of it makes sense. 

Anyone want to try and guess what happened? Luckily I did a backup 10 days ago because I am SO USED to this kind of crap happening. It's pretty much the story of my life ([view this thread]("http://ubuntuforums.org/showthread.php?p=8813478#post8813478")).

---

### Post by scottuss on 2010-03-11
"The hard drive that I am using has about 45 bad sectors"

Um, you need any more clue than that? A duff hard disk. Ubuntu doesn't just make stuff disappear.

---

### Post by nothingspecial on 2010-03-11
Either your hard drive has a problem (unlikely, as it`s brand new)

Or, your computer has a problem (likely, as an old and new hard drive, both, don`t like it).

Ubuntu itself - no.

---

### Post by scottuss on 2010-03-11
> **nothingspecial said:**
> Either your hard drive has a problem (unlikely, as it`s brand new)

Or, your computer has a problem (likely, as an old and new hard drive, both, don`t like it).

Ubuntu itself - no.

He/she specifies that there are bad sectors

---

### Post by nothingspecial on 2010-03-11
> **scottuss said:**
> He/she specifies that there are bad sectors

Did you view the thread?

---

### Post by Ghost|BTFH on 2010-03-11
> **nothingspecial said:**
> Did you view the thread?

Just curious if you actually bothered to read the whole original post, or if you're even familiar with the term DOA hardware?

It's actually VERY possible to get a bad piece of new hardware.  The average tolerable defect rate for most companies is around 10%.  With sales usually hitting into the millions internationally, that gives you a logical estimate of well over 100,000 defective drives floating around.

He/she did state there are bad sectors on the drive already.

That, for any hardware tech, is a very serious warning that you've purchased a bad drive - take it back.

Period.

Your analogy of it more likely being his "computer" having the problem would be like you asking why you smelled smoke, and someone says, "Oh, it's probably your polyester clothing..." while completely ignoring the fact that your hair is currently on fire.

To the OP: Listen to the first reply - it is 90% likely you have purchased a defective hard drive, go replace it and enjoy life again.

Cheers,
Ghost|BTFH

---

### Post by nothingspecial on 2010-03-11
Also,

And I don`t want to assure or worry you

palimpsest has had many bug reports, telling users hey have corrupted disks when they don`t.

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

[http://ubuntuforums.org/showthread.php?t=1305452&page=3](http://ubuntuforums.org/showthread.php?t=1305452&page=3)

---

### Post by ElSlunko on 2010-03-11
Some bad sectors is pretty normal after use, especially on huge drives. However! If you have a NEW drive & it has 45 bad sectors from the get-go, that's kind of a red flag.

---

### Post by scottuss on 2010-03-11
> **Ghost|BTFH said:**
> Just curious if you actually bothered to read the whole original post, or if you're even familiar with the term DOA hardware?

It's actually VERY possible to get a bad piece of new hardware.  The average tolerable defect rate for most companies is around 10%.  With sales usually hitting into the millions internationally, that gives you a logical estimate of well over 100,000 defective drives floating around.

He/she did state there are bad sectors on the drive already.

That, for any hardware tech, is a very serious warning that you've purchased a bad drive - take it back.

Period.

Your analogy of it more likely being his "computer" having the problem would be like you asking why you smelled smoke, and someone says, "Oh, it's probably your polyester clothing..." while completely ignoring the fact that your hair is currently on fire.

To the OP: Listen to the first reply - it is 90% likely you have purchased a defective hard drive, go replace it and enjoy life again.

Cheers,
Ghost|BTFH

Thanks Ghost|BTFH, I'm guessing nothingspecial *didn't* read the original thread.

@cscott5288 My friend has this laptop (same model, I think... and had the same problem with overheating) HP denied there was a known issue (search around, there are loads of forum posts about it on laptop / hardware forums)

As for the drive, it's not impossible that it came from the supplier with bad sectors

---

### Post by scottuss on 2010-03-11
> **nothingspecial said:**
> Also,

And I don`t want to assure or worry you

palimpsest has had many bug reports, telling users hey have corrupted disks when they don`t.

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

[http://ubuntuforums.org/showthread.php?t=1305452&page=3](http://ubuntuforums.org/showthread.php?t=1305452&page=3)

I don't mean to be rude, but did *you* read both posts? The OP has already stated that he **has** a corrupted disk. Or maybe the data magically disappeared....

---

### Post by nothingspecial on 2010-03-11
> **Ghost|BTFH said:**
> Just curious if you actually bothered to read the whole original post, or if you're even familiar with the term DOA hardware?

It's actually VERY possible to get a bad piece of new hardware.  The average tolerable defect rate for most companies is around 10%.  With sales usually hitting into the millions internationally, that gives you a logical estimate of well over 100,000 defective drives floating around.

He/she did state there are bad sectors on the drive already.

That, for any hardware tech, is a very serious warning that you've purchased a bad drive - take it back.

Period.

Your analogy of it more likely being his "computer" having the problem would be like you asking why you smelled smoke, and someone says, "Oh, it's probably your polyester clothing..." while completely ignoring the fact that your hair is currently on fire.

To the OP: Listen to the first reply - it is 90% likely you have purchased a defective hard drive, go replace it and enjoy life again.

Cheers,
Ghost|BTFH

Yes, you could have bought a bad hard drive.

If you think you have, take it back and demand a new one.

Just don`t trust palimpsest at the moment. It seems there are problems with it.

And yes, Ghost ....., I did read the whole post.

---

### Post by Ghost|BTFH on 2010-03-11
> **scottuss said:**
> @cscott5288 My friend has this laptop (same model, I think... and had the same problem with overheating) HP denied there was a known issue (search around, there are loads of forum posts about it on laptop / hardware forums)

As for the drive, it's not impossible that it came from the supplier with bad sectors

Ah yes, HP usually has excellent product, but heating issues can cook a drive in a heartbeat.  If it's under warranty, return it and have them replace it.  Period.  If it's out of warranty, might I suggest prying open the wallet and picking yourself up a sweet SSD drive that would improve the performance of the system and reduce the heat issues (at least the drive wouldn't be part of them ;) )

Hope you can get it resolved quickly and efficiently.  Oh, before you return it, you *might* want to do a quick reinstall of the original software - they *can* get cranky over having something completely different installed.  I've even had one tech claim that LINUX caused a hardware issue...yes, there are people that stupid working in places like that.

At that point however, I explained to him that I was a computer repair tech and information security specialist and that *I* had personally installed the alternate operating system for my client, and that I would be just chuffed to speak with his supervisor...the problem was resolved rather quickly from that point on.

Cheers,
Ghost|BTFH

---

### Post by ElSlunko on 2010-03-11
What backup software do you use?

---

### Post by nothingspecial on 2010-03-11
> **ElSlunko said:**
> What backup software do you use?

I don`t use any software. 

I backup my stuff to an external drive as soon as it`s there.

Then once a week, I back up whatever has changed to a drive that immediately gets unplugged and stored somewhere else.

Using good old cp (with arguments, of course)

see man cp

rsync is great, but I have to be sure :D

---

### Post by Ghost|BTFH on 2010-03-11
> **cscott5288 said:**
> Luckily I did a backup 10 days ago because I am SO USED to this kind of crap happening.

Just a guess, *nothingspecial* but I believe he was asking the OP.

Cheers,
Ghost|BTFH

---

### Post by ElSlunko on 2010-03-11
I was. Just wanted to see if maybe his settings in Ubuntu with some problem could've caused this.

---


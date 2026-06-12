---
title: "Benifits of installing 64-bit version?"
date: 2006-06-22
forum: General Help
---

### Post by MJSOnline on 2006-06-22
Hi all.

I am looking at buying a new motherboard as mine died on me last month.  So I am looking at amd64 but what is the benifits with regards to applications in Ubuntu using an amd64 chip?  Also is printing to cd using my Epson R300 easy in version 6.06?  Thanks. M

---

### Post by lamego on 2006-06-22
If you install the 64 bits ubuntu version and run 64 bits applications you should have a reasonable performance increase compared to the 32bit versions.
On the other hand a lot of applications and drivers are not stable or simply don't have yet 64bits versions.

---

### Post by MJSOnline on 2006-06-22
[QUOTE=lamego]If you install the 64 bits ubuntu version and run 64 bits applications you should have a reasonable performance increase compared to the 32bit versions.
On the other hand a lot of applications and drivers are not stable or simply don't have yet 64bits versions.[/QUOTE] Ok.  How many apps are there avilable in 64bit? M

---

### Post by Ramses de Norre on 2006-06-22
Many, but only a few will really benefit from 64bit technology. In fact 64bit is necessary when running high-end servers or when doing very heavy video editing on machines with more the 4Gig of ram.
On a normal desktop I think the benefits of 64bit are so small that they aren't worth all the trouble, things like flash, w32codecs, sun java etc are a lot of work to install.

---

### Post by MJSOnline on 2006-06-22
[QUOTE=Ramses de Norre]Many, but only a few will really benefit from 64bit technology. In fact 64bit is necessary when running high-end servers or when doing very heavy video editing on machines with more the 4Gig of ram.
On a normal desktop I think the benefits of 64bit are so small that they aren't worth all the trouble, things like flash, w32codecs, sun java etc are a lot of work to install.[/QUOTE]  So for me to spend money on [this]("http://www.ebuyer.com/product/110725/product_info/rb/19993679814") , would be a waste of time?

---

### Post by incubus on 2006-06-22
What's the other option and price, if I may ask?

Most processors/motherboards are now 64-bit capable, through AMD64 or EM64T (Intel's implementation), and they have full support for 32-bit applications at insignificant loss of speed. Because the architecture has been improved, if this is an upgrade you will see a performance boost.

The big thing you have to decide is whether or not to install a 64-bit OS.

incubus

-
Edited to note that one can still run 32-bit programs.

---

### Post by panurge77 on 2006-06-22
64 bits runs lots of things faster, even if they're 32 bits apps. Windows games for example are made in 32 bits and run better on 64 chips. I guess that only matters for heavy loads, though. The question is.. will you need a 64 bits OS?
Heh... i had not read incubus post..

---

### Post by bruce89 on 2006-06-22
I am using it now, and the only things you can't do are Flash, Java applets, WINE, and w32codecs.  Actually that is quite a few things, but I don't need any of them.

---

### Post by patrickfromspain on 2006-06-22
I'm running Ubuntu 6.06 32bit on an Asus mobo and an Athlon64 3200+... and it works really well!! Athlon64 are very good CPUs and have a top price/quality/perfomance relation...

---

### Post by panurge77 on 2006-06-22
I'm also very satisfied with my atholn 64 3200 running on 32 bits :D

---

### Post by incubus on 2006-06-22
bruce,

You know you can get those things working (some natively, others not), right?
[http://www.ubuntuforums.org/showthread.php?t=191205](http://www.ubuntuforums.org/showthread.php?t=191205)
(there's also an Automatix script for amd64, I heard)

Well, but like you, I don't use them and never cared to install.

Right now I'm running Ubuntu AMD64 in a Pentium D and I agree with patrick, Athlons are great, very efficient and stable. I opted for the Pentium D because of the price (for a dual core) and Virtualization Technology, which is also present in the new AMD AM2 socket. 

incubus

---

### Post by loserboy on 2006-06-22
well they've all said everything there is to say, all i have to add is sooner or later you'll need a 64bit,  if you found one and the price is right why not go ahead and grab it, any probs with ubuntu 64bit will be fixed soon  ( i hope cuz i'm in the same boat)

but this is coming from an ubuntu baby (see only 5 cups hehe)

---

### Post by Kilz on 2006-06-22
IMHO anyone running a 32 bit version of Dapper with a 64 bit possessor falls into 1 of a few categories.
1. Someone who is a newbie and doesn't know how to follow a howto
2. Someone who tried running 64 bit Breezy and remembers how hard it was so they assume its hard on Dapper.
3. Someone who just wants automated scripts to set up their system because they cant be bothered to spend 2 hours.
4.Someone who bought the opinions of someone in #2 and didn't check it out for themselves.
5. Someone who has real rare hardware, something special ordered especially for them.

Dapper is a whole new ballgame when it comes to 64 bit. Its not hard or impossible to setup win32codecs, Firefox with flash/java/etc, adobe acrobat,wine,realplayer,mplayer, etc. In fact anyone who can read the sticky in the 64 bit forum can find easy work arounds for most common applications.
Breezy was hard, Dapper is not, it can run 32 bit applications with minimum work, force in the application and copy in the needed lib's. 
Of the reasons above IMHO only #5 has a reason to keep using a 32 bit OS. Like I said, if you custom built your computer and put super super unique hardware in it you may have problems. But if you bought a pre built computer, or built one with components off a store shelf you will find 64 bit drivers in most cases. 
If you are waiting for the 64 bit OS to get better, don't. The more people downloading it and using it will show that its popular. The bigger the user base the better. Because with more users , more development will go into 64 bit. Its going to happen anyway, 64 bit is the future.
You can live in the 32 bit past, me I'm future all the way! :D

---

### Post by MJSOnline on 2006-06-23
[QUOTE=Kilz]IMHO anyone running a 32 bit version of Dapper with a 64 bit possessor falls into 1 of a few categories.
1. Someone who is a newbie and doesn't know how to follow a howto
2. Someone who tried running 64 bit Breezy and remembers how hard it was so they assume its hard on Dapper.
3. Someone who just wants automated scripts to set up their system because they cant be bothered to spend 2 hours.
4.Someone who bought the opinions of someone in #2 and didn't check it out for themselves.
5. Someone who has real rare hardware, something special ordered especially for them.

Dapper is a whole new ballgame when it comes to 64 bit. Its not hard or impossible to setup win32codecs, Firefox with flash/java/etc, adobe acrobat,wine,realplayer,mplayer, etc. In fact anyone who can read the sticky in the 64 bit forum can find easy work arounds for most common applications.
Breezy was hard, Dapper is not, it can run 32 bit applications with minimum work, force in the application and copy in the needed lib's. 
Of the reasons above IMHO only #5 has a reason to keep using a 32 bit OS. Like I said, if you custom built your computer and put super super unique hardware in it you may have problems. But if you bought a pre built computer, or built one with components off a store shelf you will find 64 bit drivers in most cases. 
If you are waiting for the 64 bit OS to get better, don't. The more people downloading it and using it will show that its popular. The bigger the user base the better. Because with more users , more development will go into 64 bit. Its going to happen anyway, 64 bit is the future.
You can live in the 32 bit past, me I'm future all the way! :D[/QUOTE]

Ok. I am sold on the "using 64bit version" so far.  Just worried about certain apps that over the time I come across and would lke to run on it.  i am worried about ripping my DVD's for a start.  Printing onto cd using my Epson R300 printer, now that is a big problem. M

---

### Post by bob_the_d on 2006-06-23
I'm sort of in the same boat as you.  I own an A64 chip that was running up until now, Windows XP 32 bit (Windows x64 edition was just way too unstable and buggy).

But I mean it all boils down to what you're actually using the computer for.  Myself, I'm a computer science student, so while switching to Linux makes more sense, I'm still a student.  None of my programs are going to strain the CPU so hard that I would need 64 bits.  In fact, there are those times where 64 bits gets in the way of programming when most other systems are in 32 bits.  Like I said, it's rare but it doesn't help its case.

However, like the others are saying, if you're doing heavy computations and things like heavy audio and video editing/processing, it might make more sense to go 64 bit.

For most applications, however, I think that the sliver of performance that going 64 bit gets you isn't worth the headaches.  For example, I still can't get Flash to work with Firefox.  Yes, I tried the nswrapper thing but it just doesn't work on my system.  Of course should I ask, everyone will probably just say "read the sticky" or something as unhelpful as that.  But Flash is very important.

Personally, I would say go ahead and buy the 64 bit hardware, but I'd say unless you absolutely need it, go for the 32 bit OS.  As few as those headaches are, and as easy or hard as they may be to fix it, what I'm wondering is why anyone who doesn't need it would bother when the margin of benefit is so small and 32 bit Dapper just works?  I'm actually thinking of reverting back to 32 bit Dapper because Flash and nswrapper are both being a pain in my *** and I just don't think it's worth it.

But hey, you might have better luck.  I mean the software's all free anyway.  While I would suggest sticking with 32 bit, go ahead and give 64 bit Dapper a shot anyway.  Couldn't hurt.  You might have better luck than me, and at the worst you spent a few hours learning what works and what doesn't for future reference.

---

### Post by Kilz on 2006-06-23
[QUOTE=bob_the_d]I'm sort of in the same boat as you.  I own an A64 chip that was running up until now, Windows XP 32 bit (Windows x64 edition was just way too unstable and buggy).

But I mean it all boils down to what you're actually using the computer for.  Myself, I'm a computer science student, so while switching to Linux makes more sense, I'm still a student.  None of my programs are going to strain the CPU so hard that I would need 64 bits.  In fact, there are those times where 64 bits gets in the way of programming when most other systems are in 32 bits.  Like I said, it's rare but it doesn't help its case.

However, like the others are saying, if you're doing heavy computations and things like heavy audio and video editing/processing, it might make more sense to go 64 bit.

For most applications, however, I think that the sliver of performance that going 64 bit gets you isn't worth the headaches.  For example, I still can't get Flash to work with Firefox.  Yes, I tried the nswrapper thing but it just doesn't work on my system.  Of course should I ask, everyone will probably just say "read the sticky" or something as unhelpful as that.  But Flash is very important.

Personally, I would say go ahead and buy the 64 bit hardware, but I'd say unless you absolutely need it, go for the 32 bit OS.  As few as those headaches are, and as easy or hard as they may be to fix it, what I'm wondering is why anyone who doesn't need it would bother when the margin of benefit is so small and 32 bit Dapper just works?  I'm actually thinking of reverting back to 32 bit Dapper because Flash and nswrapper are both being a pain in my *** and I just don't think it's worth it.

But hey, you might have better luck.  I mean the software's all free anyway.  While I would suggest sticking with 32 bit, go ahead and give 64 bit Dapper a shot anyway.  Couldn't hurt.  You might have better luck than me, and at the worst you spent a few hours learning what works and what doesn't for future reference.[/QUOTE]

Nswrapper isn't the only solution for getting flash to work. You could just as easily use just install the 32 bit firefox and plugins. Unfortunately a member of the document team keeps deleting the page with the information on how to set it up. I will be writing my own howto on the subject later today. Until then here is the difference page from the old one, its directions are still followable.
[https://wiki.ubuntu.com/FirefoxAMD64FlashJava?action=diff](https://wiki.ubuntu.com/FirefoxAMD64FlashJava?action=diff)

---

### Post by bob_the_d on 2006-06-23
I tried that, and it seems that Flash works for the most part.

Except that I'm getting sound problems.  There is no sound.  It just animates.

I tried installing the libraries, but it still didn't work.  Actually, I used to use x64 Vidalinux before moving to Ubuntu, and I had the same problem there.  Installed 32 bit FireFox and installed Flash, but that too didn't have any sound.  Couldn't find a solution there, still can't find one here.

Any thoughts?

---

### Post by bruce89 on 2006-06-23
[QUOTE=loserboy]but this is coming from an ubuntu baby (see only 5 cups hehe)[/QUOTE]
I was still on five cups only a matter of a few weeks ago.

---

### Post by bob_the_d on 2006-06-23
Haha.  And now when I run firefox32 from the terminal as well as the shortcut, it loads up the 64 bit version.  This is really throwing me off now.

---

### Post by MJSOnline on 2006-06-23
[QUOTE=bob_the_d]Haha.  And now when I run firefox32 from the terminal as well as the shortcut, it loads up the 64 bit version.  This is really throwing me off now.[/QUOTE]
See it is this like this that worries me about  going to 64bit.  M

---

### Post by bob_the_d on 2006-06-23
Yeah.  Like I said, I'm sure I could fix it, but I'd rather be more productive on something that works than spending time and effort on fixing things that just should work.  I'm switching back to x86 Ubuntu until these other applications get ironed out.

---

### Post by brt on 2006-06-23
I have tried Hoary 64bit with setting up a 32bit-chrooted-firefox to get flash working but after having problems with sound i switched back to 32bit.

I could not see any advantage in 64bit, performance is just the same as with the 32bit OS. i believe the reason is, that AMD has done a good job in designing a CPU which can run 32bit software just as good as 64bit one.

If 64bit would really perfom so much better on a common desktop-pc, where are the benchmarks?

My recommendation:

If you want a OS as-hassle-free-as-possible choose the 32bit version, but if you like playing around and really want to know how much faster the 64bit version is by yourself, give it a try, as you always can switch back to 32bit, (keeping your home-folder you don't even loose all your personal settings :)

---

### Post by panurge77 on 2006-06-23
Just one more thing I forgot to mention. Dapper boots 10 seconds faster in 32 bits on my athlon 64 3200. I never understood why, but there must be a reason.

---

### Post by glacierre on 2006-07-09
Here is one [benchmark (spanish)]("http://www.tod-os.com/index.php?p=1240"). Despite not being in english I think you can understand more or less the table at the end of the page.

> **brt said:**
> 
If 64bit would really perfom so much better on a common desktop-pc, where are the benchmarks?


---


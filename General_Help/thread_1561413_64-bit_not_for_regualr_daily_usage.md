---
title: "64-bit not for regualr daily usage???"
date: 2010-08-26
forum: General Help
---

### Post by AmpersUK on 2010-08-26
I have a 64-bit computer and needed to download 10.04 again and now notice the following:

**64-bit** - Not recommended for daily desktop usage

This worries me so I would like to ask a couple of questions here if I may.

QUESTION ONE
What version, on a 64-bit machine, should I download for use every day and all day?

QUESTION TWO
If the answer to Question One is, "use the 32-bit version", and I have 8GB of memory, I can only use 3.4GB with 32-bit so would the other memory be available to use if I downloaded vbox and used a second operating system?

---

### Post by Fire_Chief on 2010-08-26
> **AmpersUK said:**
> I have a 64-bit computer and needed to download 10.04 again and now notice the following:

**64-bit** - Not recommended for daily desktop usage

This worries me so I would like to ask a couple of questions here if I may.

QUESTION ONE
What version, on a 64-bit machine, should I download for use every day and all day?

QUESTION TWO
If the answer to Question One is, "use the 32-bit version", and I have 8GB of memory, I can only use 3.4GB with 32-bit so would the other memory be available to use if I downloaded vbox and used a second operating system?


Answer ONE: You can use either the 32-bit or 64-bit for nearly everything on a daily basis. The only troubles may come from the usual suspects *cough* flash *cough*. I have 64-bit running at home and everything is great.

Answer TWO: Especially since you have 8GB of RAM, use the 64-bit version. Just as you stated, you would only get access to 3.4GB if you run 32-bit. And no, that extra memory is not usable by apps on the system. It is inaccessible by the OS and therefore everything that runs on top of it (applications, services, etc). 

Cheers!

---

### Post by AmpersUK on 2010-08-26
> **Fire_Chief said:**
> Answer ONE: You can use either the 32-bit or 64-bit for nearly everything on a daily basis. The only troubles may come from the usual suspects *cough* flash *cough*. I have 64-bit running at home and everything is great.

Answer TWO: Especially since you have 8GB of RAM, use the 64-bit version. Just as you stated, you would only get access to 3.4GB if you run 32-bit. And no, that extra memory is not usable by apps on the system. It is inaccessible by the OS and therefore everything that runs on top of it (applications, services, etc). 

Cheers!

Wow! That was fast.

Thanks for that, I have had some probs with my update system, errors because of things in "Software Sources" and as I am too old to learn too many new tricks, and as my home directory is on another partition, I think it will be easier to reload the system.

Used to be an IT Journo with Windows and can never stop playing and well... errr... playing :-)

Ampers

---

### Post by bobcollard on 2010-08-26
Actually it's the Kernel that decides how much memory you can use.  In Linux Mint, a derivative of Ubuntu, the 32 bit Kernel has an additional part that allows the system to see all your RAM.  As for using 64 bit daily Ihave for a year now and have no problems, even with flash.  It depends on which distribution you are using.  The limitations are rare anymore, most all the applications are available in 64 bit.  I'd say go for it.

---

### Post by sorin7486 on 2010-08-26
> **Fire_Chief said:**
> Answer ONE: You can use either the 32-bit or 64-bit for nearly everything on a daily basis. The only troubles may come from the usual suspects *cough* flash *cough*. I have 64-bit running at home and everything is great.

Answer TWO: Especially since you have 8GB of RAM, use the 64-bit version. Just as you stated, you would only get access to 3.4GB if you run 32-bit. And no, that extra memory is not usable by apps on the system. It is inaccessible by the OS and therefore everything that runs on top of it (applications, services, etc). 

Cheers!

Actually I just installed the 32 bit version and it sees my whole 4 gigs. I was fed up with the 64 bit version and all the problems I had with it.But yeah 8 gigs might be a different story.

---

### Post by AmpersUK on 2010-08-26
> **bobcollard said:**
> Actually it's the Kernel that decides how much memory you can use.  In Linux Mint, a derivative of Ubuntu, the 32 bit Kernel has an additional part that allows the system to see all your RAM.  As for using 64 bit daily I have for a year now and have no problems, even with flash.  It depends on which distribution you are using.  The limitations are rare anymore, most all the applications are available in 64 bit.  I'd say go for it.

Yes, I am *"going for it"*.

Over the next couple of days I am producing a document listing all the things I need to do to make sure I can get it done and up to scratch within an hour in the future.

But then I have always been a planner ;-)

And, thanks also to @bobcollard.

---

### Post by dabl on 2010-08-26
With your IT background, you should go for the 64-bit OS, IMO.  I've been using it for 4 years, with very few issues related to the architecture.

I personally think Canonical just got sick and tired of the kinds of crap you can read in the now-closed 64-bit forum. "USB thingy not found on my 64-bit system", "No sound on my 64-bit system", "CD player won't play on my 64-bit system" and on and on, as you can see.  It's 99% unrelated to the arch, but the perception (being the reality for new users) is that the first issue they have must be due to the 64-bit architecture.  So now they've warned them off, just to cut out the BS complaints.

With the exception of Adobe's withdrawal of their buggy 64-bit flash player, and the occasional rare instance of a third-party package that has not been pre-compiled for the 64-bit architecture (you might have to compile it yourself), there's nothing to worry about, and your hardware is designed to run it.

---

### Post by AmpersUK on 2010-08-26
> **dabl said:**
> With your IT background, you should go for the 64-bit OS, IMO.  I've been using it for 4 years, with very few issues related to the architecture.

I personally think Canonical just got sick and tired of the kinds of crap you can read in the now-closed 64-bit forum. "USB thingy not found on my 64-bit system", "No sound on my 64-bit system", "CD player won't play on my 64-bit system" and on and on, as you can see.  It's 99% unrelated to the arch, but the perception (being the reality for new users) is that the first issue they have must be due to the 64-bit architecture.

With the exception of Adobe's withdrawal of their buggy 64-bit flash player, and the occasional rare instance of a third-party package that has not been pre-compiled for the 64-bit architecture (you might have to compile it yourself), there's nothing to worry about, and your hardware is designed to run it.

Agreed, especially with your second paragraph, I had come to that supposition myself.

What did you do for "flash"? I found the alpha flash for v11 on the Adobe website was pretty well-behaved.

The only issues I have had was a double click doesn't select a word, and one or two other small, equally inconsequential issues.

---

### Post by dabl on 2010-08-26
Yep, I use the alpha flash player too.  Previously there were issues with Java 64-bit, but I haven't seen any problem with that in at least a year.

---

### Post by sorin7486 on 2010-08-26
> **dabl said:**
> With your IT background, you should go for the 64-bit OS, IMO.  I've been using it for 4 years, with very few issues related to the architecture.

I personally think Canonical just got sick and tired of the kinds of crap you can read in the now-closed 64-bit forum. "USB thingy not found on my 64-bit system", "No sound on my 64-bit system", "CD player won't play on my 64-bit system" and on and on, as you can see.  It's 99% unrelated to the arch, but the perception (being the reality for new users) is that the first issue they have must be due to the 64-bit architecture.  So now they've warned them off, just to cut out the BS complaints.

With the exception of Adobe's withdrawal of their buggy 64-bit flash player, and the occasional rare instance of a third-party package that has not been pre-compiled for the 64-bit architecture (you might have to compile it yourself), there's nothing to worry about, and your hardware is designed to run it.

Actually I had some rather big problems with my 64bit version on my computer at work. Things like the mouse not reacting to clicks and parts of Gnome crashing. Also some java applications would hang in the background like Eclipse for example: whenever I closed it the thread wouldn't die. I'm not sure if this was because it's the 64bit version but I also use Ubuntu (32bit) at home and I never had such problems.

---

### Post by Vaphell on 2010-08-26
unless you test both architectures on the same pc you can't say that it's 64bit that causes problems. I use 64bit version for at least 2 years and never had any problem with it. Only flash required a bit of manual intervention because 64bit is not prepackaged in repos, but 32bit flash can be used with wrapper. You can use lovinglinux's plugin FLASH-AID for firefox (kudos) that will iron out and automate flash issue for you. BTW, Adobe abandoned flash 64 for linux in a state with known vulnerabilities, so wrapped up 32bit plugin is actually safer.

---

### Post by sorin7486 on 2010-08-26
> **Vaphell said:**
> unless you test both architectures on the same pc you can't say that it's 64bit that causes problems. I use 64bit version for at least 2 years and never had any problem with it. Only flash required a bit of manual intervention because 64bit is not prepackaged in repos, but 32bit flash can be used with wrapper. You can use lovinglinux's plugin FLASH-AID for firefox (kudos) that will iron out and automate flash issue for you. BTW, Adobe abandoned flash 64 for linux in a state with known vulnerabilities, so wrapped up 32bit plugin is actually safer.

Well I just installed the 32bit version today and so far I haven't seen any of the problems I had on the 64bit version. Well apart from the fact that my sound card is apparently not supported on this kernel but for some reason worked on the 64bit one.

---

### Post by Grenage on 2010-08-26
I thought they pulled the x64 player due to a vulnerability.

I've been using Ubuntu x64 on all my machines for a couple of years.  Initially I had the odd quirk, but not these days.

---

### Post by Alver on 2010-08-26
I can only comment on my personal experience (how ever limited that may be). Some months ago I purchased a Toshiba Satellite L505-10M with 6GB ram an W7 64 bits preinstalled. After some familiarisation with W7 I installed U 10.04 64b in a dual boot mode. I did have some minor issues with the wireless internet connection (had to install a second applet, Wcid, to get the thing going) but that was all. I also had to install some additional packages from Avasys to get my Epson Stylus SX 410 all-in-one going. Everything is working well now. My computer usage does not include highly demanding work such as video or movie editing and the like so I cannot comment on these. 
I hope this little bit of info may help future 64 bit users.

p.s. I read somewhere that the 32 bits PAE kernel does address all of the available ram.

Alver

---

### Post by 3Miro on 2010-08-26
I have been using 64-bit exclusively since 8.10. The only issues that I have had:

1. Flash - the best solution that I found is to install 32-bit swiftfox browser and use 32-bit flash with it.

2. Some windows specific codecs may not run. This depends on the situation, usually it is not a problem, since those are very specific. It can be resolved by compiling your own 32-bit mplayer.

3. Some printer drivers give trouble. I resolved that with VirtualBox (I don't do much printing).

In general, 32-bit should see almost all of 8GB of RAM, however, it will run a bit slower than 64-bit.

---

### Post by kerry_s on 2010-08-26
i just installed 64 bit on mine everything runs fine, just treat it like a normal 32 bit install.

for flash, i'm using the 32 bit in the wrapper installed with ubuntu-restricted-extras. i watched some youtube vids, played some games, had no problems, so no need to jump through hoops.

i can tell you it sure feels faster then 32 bit ubuntu, i also notice it does use a bit more ram, but well worth it.

specs:
atom 230
1gb ram
80gb hd

it' a foxconn nettop.

---


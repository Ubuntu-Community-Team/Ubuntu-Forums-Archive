---
title: "input/output error lucid lynx"
date: 2010-04-20
forum: General Help
---

### Post by spin498 on 2010-04-20
I have installed 9.10 on a P4 system running a 20 gig Maxtor HD. What I am running into, is after performing say 5 or 8 processes, not necessarily all at once I run into an issue where no commands will run off of the drop down lists. I get the Input/output error child system or something like that. I have reinstalled 9.10,  3 times with no improvement. I don't believe it's a memory issue as the mouse still works and all the initial drop downs activate as normal. I've also memtested and it's passed. By way of information, this drive had WinXP on it and got infected badly, I nuked it, reformated both low level and high level using Maxtor's PowerMax. I then tested it fast scan and full scan and it passed. The system has 2 gigs memory.

---

### Post by jkxx on 2010-04-20
That's a curious error and it still sounds suspiciously like the drive might have a hardware problem. 

You could try getting something like SMART Linux [http://smartlinux.sourceforge.net/]("http://smartlinux.sourceforge.net/") and booting that up, then running the SMART diags on the drive.

If that fails, try to hook up the drive to another computer and then test/use it to store files or install Ubuntu on it there. If it works without problems on the other system the problem could be the disk controller.

---

### Post by gmargo on 2010-04-20
A 20G drive?  Do you have any swap space?

---

### Post by spin498 on 2010-04-20
> **gmargo said:**
> A 20G drive?  Do you have any swap space?

Yes, 902 mb set by the sytem on the install. And another 902 mb extended partition.

---

### Post by spin498 on 2010-04-20
> **jkxx said:**
> That's a curious error and it still sounds suspiciously like the drive might have a hardware problem. 

You could try getting something like SMART Linux [http://smartlinux.sourceforge.net/](http://smartlinux.sourceforge.net/) and booting that up, then running the SMART diags on the drive.

If that fails, try to hook up the drive to another computer and then test/use it to store files or install Ubuntu on it there. If it works without problems on the other system the problem could be the disk controller.

Would this be more accurate than Ubuntu's native disc utility? It's currently reporting the disc as healthy.

---

### Post by spin498 on 2010-04-20
I think I've traced the issue to an external HD that was connected by USB.

---

### Post by spin498 on 2010-04-20
Nope, I was wrong it's still happening. The actual error message reads "failed to execute child process (whatever app I tried) input/output error".

---

### Post by gmargo on 2010-04-21
So this is only when you try to run something from the menu?  Do you get a pop-up with the error?

My suggestion would be to try to run the same application(s) from the command line and see what the error says there.

But I suspect that your swap space is full. Try opening a terminal and running 'top' in it, to see the memory/swap usage.  2G ram and 0.9 swap can easily fill up if you're running some memory hogs.

---

### Post by spin498 on 2010-04-21
> **gmargo said:**
> So this is only when you try to run something from the menu?  Do you get a pop-up with the error?

My suggestion would be to try to run the same application(s) from the command line and see what the error says there.

But I suspect that your swap space is full. Try opening a terminal and running 'top' in it, to see the memory/swap usage.  2G ram and 0.9 swap can easily fill up if you're running some memory hogs.

I have run top as suggested, what it reports is that my RAM is almost completely depleted by the system running in the background. my swap file is barely being touched. 430000k of 443000k of ram is being used.
Only top and firefox are running.

---

### Post by gmargo on 2010-04-21
> **spin498 said:**
> I have run top as suggested, what it reports is that my RAM is almost completely depleted by the system running in the background. my swap file is barely being touched. 430000k of 443000k of ram is being used.
Only top and firefox are running.

Keep an eye on it as you continue to do work. Particularly when the menus stop working.

I just saw an article on Slashdot saying there is a major memory leak in Lucid's X.org server, so I wonder if you are a victim of this.
[http://it.slashdot.org/article.pl?sid=10/04/21/2021247](http://it.slashdot.org/article.pl?sid=10/04/21/2021247)

[your subject line says "lucid lynx" but your text says "9.10" which is Karmic - so which is it?]

---

### Post by spin498 on 2010-04-21
> **gmargo said:**
> Keep an eye on it as you continue to do work. Particularly when the menus stop working.

I just saw an article on Slashdot saying there is a major memory leak in Lucid's X.org server, so I wonder if you are a victim of this.
[http://it.slashdot.org/article.pl?sid=10/04/21/2021247](http://it.slashdot.org/article.pl?sid=10/04/21/2021247)

[your subject line says "lucid lynx" but your text says "9.10" which is Karmic - so which is it?]

Sorry for the confusion, I run 3 separate Ubuntu systems. My main one for general computing is Karmic. I have Ubuntu Studio for my photography. Both of which run flawlessly. The system I've put Lucid on is a test system of sorts. And right now it's failing the test!!

---

### Post by spin498 on 2010-04-22
Now I'm confused as to what top is reporting. I've run it on my Studio machine with nothing running except Firefox. It's reporting that 2 gig of my 2.5 gig of RAM is being used. Why would that be?

---

### Post by gmargo on 2010-04-22
> **spin498 said:**
> Now I'm confused as to what top is reporting. I've run it on my Studio machine with nothing running except Firefox. It's reporting that 2 gig of my 2.5 gig of RAM is being used. Why would that be?

Change top to sort by %MEM instead of %CPU (just hit the '>' key once to shift the sort column right.)

Are you using compositing software like compiz?  My understanding is that it is fairly piggy.

---

### Post by spin498 on 2010-04-22
> **gmargo said:**
> Change top to sort by %MEM instead of %CPU (just hit the '>' key once to shift the sort column right.)

Are you using compositing software like compiz?  My understanding is that it is fairly piggy.

All I'm running currently is a web browser trying to get audacity downloaded and installed. I purchased one of those Cassette decks that plugs in via USB port. Plan is to convert my millions of old cassettes to MP3.

---

### Post by spin498 on 2010-04-22
> **gmargo said:**
> Change top to sort by %MEM instead of %CPU (just hit the '>' key once to shift the sort column right.)

Are you using compositing software like compiz?  My understanding is that it is fairly piggy.

So I've done that, it shows firefox using 13% of memory and a slew of other processes using up about
46% of my memory, yet I've only launched Terminal and Firefox. It's got things like Eveoution Alarm running and I've never set Evolution up. Metacity? don't even know what it is. It still says I'm only using about 8000k of the swap total.

---

### Post by spin498 on 2010-04-23
I think I'm just going to roll back to 9.10 for now and let Lucid get the bugs worked out.

---

### Post by spin498 on 2010-04-24
I rolled my system back to 9.04 and left it running all night loading updates. This morning it was fine, not locked up, not even sluggish. So I guess Lucid has a major memory leak.

---


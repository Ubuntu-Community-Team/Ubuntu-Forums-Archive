---
title: "Various Dapper woes......"
date: 2006-06-05
forum: General Help
---

### Post by jabeez on 2006-06-05
Well, I've been running Dapper since about Flight 6 or so on my computer, and haven't really had any problems to speak of, everything was easy to get up and running and I've been loving it, so much so that I waited until the final release and installed it on my girlfriends computer, and it's been a much different experience. I think I've got it pretty well set but there are 2 issues that are driving me nuts, and after much searching through these forums and around the web I still can't get resolved...

1) The Canon i550 printer (parallel) will not print, or even respond in any way whatsoever. I installed the PIXi550 drivers I found on the web, and they are seen in the add printer wizard, but alas no printing whatsoever. I'll print the test page and it says job sent to printer, click ok after page prints, and nada. It shows up in print jobs as completed but it never even starts. I've also tried various other drivers with the same results. Printer says ready/accepting jobs and jobs appear to be sent, but nothing happens. I installed KDE 3.5.3 hoping it might be resolved but no luck, which brings me to problem 2......

While upgrading to KDE 3.5.3 I also thought might as well upgrade Amarok to 1.4, and for the most part it's all gravy except for one thing: the musicbrainz tag lookup doesn't work, it spits out two different errors, either that *.mp3 is not supported or that no information was found in the database. This is odd, seeing as how I've got KDE 3.5.3 and Amarok 1.4 installed on my computer with (I think) all the same multimedia codecs and it works like a charm on mine.

Any thoughts?

---

### Post by ticool on 2006-06-05
Wrong Topic sry---

---

### Post by andy_cowman on 2006-06-05
If you are still having problems then this might be of interest. I had the same problem with my canon I9950 and it was very annoying. I could print only an inch or so of something, then I installed the older version of cups and could print nothing even though it could see the printer.

I eventually updates to the lastest Dapper, and downlaoded the newest Turbo Print drivers and the newest cups which isnt in the repos (at least it wasnt last week) and now everything works perfectly

Good luck

andy

---

### Post by stephen_lau on 2006-06-05
I have the i550 - have you tried using the USB connection?
I'm using the BJC-7000 driver that came with ubuntu, and it works very nicely

---

### Post by jabeez on 2006-06-05
Yeah I guess I could try out the USB connection, thanks for the suggestions. I'll be back.......

---

### Post by jabeez on 2006-06-05
Oh yeah Andy, so the CUPS that comes with Dapper isn't the newest? I heard about the Turbo drivers but don't they cost? I'll try the USB first.....

---

### Post by jabeez on 2006-06-05
No luck with the USB connection, same exact thing. No matter what driver I pick, nothing happens when I print a test page. How frustrating, seems like it should be so simple yet..........DOH!!! Maybe that's the devious master plan of Linux, it lulls you in with the first computer and everything works great then you try to spread the joy and look a fool.........

---

### Post by jabeez on 2006-06-05
Another development, when I'm in the printers configuration, when I click on print server configuratioin it asks me for ROOT password?!? Well, I've never set a root password and from what I understand the whole point of sudo is to avoid doing so. Stoopid printer..............

---

### Post by jabeez on 2006-06-16
Well I just installed Kubuntu 6.06 on my computer, a fresh install on my main HD over Windows, and I'm now having the same problems with musicbrainz. It was working fine the whole time I was running previous beta flights, now it's broke? Any help???

---

### Post by Underclocked on 2006-06-16
Ubuntu Dapper is the first Linux distro that has a real chance of becoming mainstream, IMHO.  I predict the new Vista OS is going to turn off a lot of formerly devout Windows users (me at least) and they'll be looking for simple alternatives.  Aside from fighting legitimate bugs, I think the developers should look at a full bore effort to increase driver support in general, printers and scanners in particular.  I would be using Dapper now if only the os had drivers for my Canon printer and scanner -  Pixma 3000 and scanner of the same model number.  

By the way, the Vista beta will not support my scanner either.

Just a comment, for what it's worth, from someone that is a noob (at best) at Linux of any sort.

---


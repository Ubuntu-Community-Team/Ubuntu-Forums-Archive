---
title: "Maybe it's a Firefox problem and not an ACPI problem"
date: 2010-03-02
forum: General Help
---

### Post by Shawn K on 2010-03-02
Hi all,

I've been experiencing the same kinds of random shutdown issues with 9.10 that other people are having.  I'll be working on something, and then all of a sudden... *bam*... my laptop just shuts itself off with no warning.

I first tried modifying my power management settings with several variations, but none of them made any difference.

I tried changing power settings in BIOS, but it appears that my BIOS doesn't have that ability (Phoenix BIOS in an Acer Aspire 5610).

I've looked at the logs, and I'm not seeing anything described as "error" or likewise.  Maybe I'm not reading the right logs...

I did start to notice one thing, though.  I'm 99% certain that I only experience these random shutdowns when a Firefox window is open.  I've noticed anecdotally that it seems like my laptop will stay on indefinitely if I'm running anything *other than Firefox*, but if there's a browser window open - even if minimized and only for a few minutes - something will most likely go haywire.

Is this a known issue for Firefox and 9.10?  I've tried Googling for information, but I'm not finding anything helpful.  How does a guy go about determining if Firefox is actually the problem, and what would I look at to fix it if it were?

---

### Post by tgalati4 on 2010-03-02
Open a terminal and type:

firefox --debug

Keep the terminal window on top at all times (shrink it somewhat so that you can still browse).  Pay attention to any errors that pop up and especially if a bunch of errors happen just before shutdown.  You may not be able to catch the errors, but you want to see if a bunch of errors show up and then shutdown occurs.

If shutdown happens without any error messages, then I would suspect the battery or power circuitry.  How old is the laptop?

---

### Post by Shawn K on 2010-03-02
If I'm reading the sticker correctly on the underside of the unit, I think it's a late 2006 laptop.

This new behavior never happened when I was using 9.04.  It started after I upgraded to 9.10.  I don't know if that's related or just cosmic coincidence.

Running a debug window as I type.  Nothing at this point.

---

### Post by tgalati4 on 2010-03-02
Batteries are only good for 3 years or 300 charge cycles.  If you have an old battery, it's possible that it's causing the shutdown.  Clean the contacts with an eraser.  Make sure it's not loose in it's holder.  All it takes is a slight expansion--such as when firefox and a flash video causes the laptop to heat up, to cause a disconnect and a shutdown.

Try booting the laptop without the battery installed, using only the power cord.  Not all laptops allow this.  If your power supply gets overly warm, it may be worn out as well.

Do a search on your Acer model number and see if others are have sudden shutdown problems.  That should make an interesting night of reading.

---

### Post by Shawn K on 2010-03-03
Pulled out the battery this morning.  Thankfully, the computer will run without it.

I'll try it for a while and see if that cures anything.

---

### Post by Shawn K on 2010-03-06
Well, no dice.  I've had the battery removed for the last couple of days.  Things were looking good for a while, and then I got three shutdowns in a 3-hour span.

So apparently the battery isn't the issue.

Anyone have any other ideas?

---

### Post by lildigiman on 2010-03-06
Laptops tend to "turn off" if they overheat. I've had a laptops screen black out often, and look as if it were "off." Seems to be a heating issue for me.

---

### Post by agnes on 2010-03-06
Can you estimate what the temperature of the laptop was before shutting down? Mine automatically shuts down when 100 degrees Celcius. Has happened to me some time (fan is dirty), also always presumably due to Firefox, I guess because esp. Flash can use a lot of resources.

---

### Post by Shawn K on 2010-03-06
Not sure how to go about measuring the temp.  If anyone can point me to some utilities, that'd be great.

Just split the case about 2 weeks ago and took some compressed air to all the innards.  Oddly enough, it was surprisingly clean inside, so I'm not yet convinced that overheating is the issue.

These problems all started happening after I switched to 9.10.  I never had this problem with earlier versions.

During the last shutdown, all I had running was Firefox with a single tab open.  I happened to be looking at a Craigslist listing through Search Tempest.  No Flash that I'm aware of.

---

### Post by Shawn K on 2010-03-21
Follow-up:

I seem to have narrowed down the problem a little bit.  For whatever reason, my random shutdowns only happen when I have Firefox open.  I've also started to notice that it's nearly always precluded by a spontaneous disconnect of my wireless connection that's left unattended.

To explain - I usually have my laptop connected to an ethernet line, but it still connects wirelessly at the same time to my home network.  After using the computer for a while, the wireless will randomly disconnect.  If I don't manually select "enable wireless" and reconnect it, then I tend to have a random power shutdown within a short timeframe if I still have a Firefox window open.  If I reconnect the wireless, it tends to remain stable (so long as the hard line is connected).

If I unplug the ethernet and go full wireless, the computer will stay on all day *so long as I never open Firefox*.  If I'm running Firefox on wireless alone, I'll still have random shutdowns. 

So it seems like it's either a Firefox problem, or a combination Firefox/wireless problem.

Anyone have any thoughts?  I'm way outta my league here.

What gets me is that I never had this problem until the day I switched to 9.10.  I'm starting to think that I should do a backup, wipe everything clean, and roll back to the last version.

---

### Post by phen0m on 2010-03-21
If you wanted to investigate this further you could try taking a look through the system logs from the time the crash occured.

System->Administration->Log File Viewer
Check the *messages* or maybe *syslog*s

For monitoring my temperatures I use conky.  
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by Shawn K on 2010-03-22
I have to admit that I'm out of my league when it comes to diagnosing and fixing problems at a system level.  I'm not shy about learning, I just don't know what I'm doing at this point.

What kinds of things am I looking for, and what do I do with that info once I find it?  Will the syslogs actually say "error" something-or-other?

---


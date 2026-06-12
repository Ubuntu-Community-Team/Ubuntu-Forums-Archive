---
title: "Laptop possibly over heating"
date: 2010-02-01
forum: General Help
---

### Post by timZZ on 2010-02-01
Hi,

I have noticed that my processor sits at 55oC - 68oC.

According to the meter being in the red, I can only assume that there is something wrong.

Anyone have any advice?

---

### Post by Greenbean209 on 2010-02-01
Pretty vague post. What processor do you have and what are you doing?

---

### Post by jamesisin on 2010-02-01
Sure.  Loads.  I don't know how much of it might apply...

Are you blocking your vents?
Is your laptop on your lap?
Do you have enough RAM?
Are you over-clocking?

Important questions aside, here is some information about my ideas concerning laptops (and though I own my ideas I don't expect anyone else to either use them or care).

1) Don't buy a laptop as a desktop replacement and expect to get desktop performance.  Laptops are really much better at quick usage and portable scenarios.

2) Over-clocking is a great way to produce more heat.  Consider under-clocking instead.

3) Run only what you need to run.  Applications appreciate the refreshness of starting over from time to time.  So does X.

4) Graphical applications produce more heat than command line applications (as a general rule).

5) Get a piece of sheet metal (heavy gauge aluminum works great) and place your laptop on that while it's on your lap.

---

### Post by timZZ on 2010-02-01
Yes, I am sorry about the vagueness.

Processor = Intel Pentium 4-M 1.9 GHz (Think Pad r40)

55oC - Idle
68oC - Loading a web page, scrolling through applications etc.

---

### Post by M1GEO on 2010-02-01
What laptop are you using?  On my MacBook, the fans don't work by default.  I had to do some messing about.  Check your fans are clear.  Blow them through with a can of compressed air/vacuum cleaner - draw air through the cooling vents the wrong way.

---

### Post by houseworkshy on 2010-02-01
And clean or have it cleaned.  Muck inside can really make it hot.  Yearly is a good idea, if around smokers twice that.

---

### Post by Greenbean209 on 2010-02-01
Sounds like a case of "old-man" syndrome. At 1.9ghz there's not much you can do without ending up over-clocking. I suggest you look for lighter programs and maybe a different desktop environment.

---

### Post by timZZ on 2010-02-01
I have used a vacuum and condensed air on the vents.  The fan seems free of debris.

---

### Post by timZZ on 2010-02-01
> **Greenbean209 said:**
> Sounds like a case of "old-man" syndrome. At 1.9ghz there's not much you can do without ending up over-clocking. I suggest you look for lighter programs and maybe a different desktop environment.

That's an interesting thought.

It reaches 68oC running firefox.

This machine comes pre-loaded with Windows XP.

I am running Gnome.

Are you sure your advice is accurate?

---

### Post by switch10 on 2010-02-01
my laptop overheats and shuts off if i don't blow out the dust every few months.  try that.

---

### Post by M1GEO on 2010-02-01
try using htop (or top) and look what is using the CPU most.  You can also use powertop to determine what is interrupting the processor.

these are all installable from the repositories using apt.

Also, check out System > Administration > System Monitor, then on the Processes Tab, sort the list by CPU (by clicking on the heading).

---

### Post by switch10 on 2010-02-01
> **timZZ said:**
> I have used a vacuum and condensed air on the vents.  The fan seems free of debris.

you have to actually unscrew, and take off the panels to clean it well.  Get a can of compressed air.  it will do wonders..

---

### Post by timZZ on 2010-02-01
Maybe the sensors-applet isn't accurate.

Looking up the CPU shows the running temp is. 

Intel Pentium 4, Pentium M (notebooks)
Intel Pentium 4    64 - 78°C

We are talking 10°C safety margin.

I am just trying to figure out what is making this machine constantly crash.

I thought I was onto something.

I might not be accurate in my assumption.

---

### Post by Greenbean209 on 2010-02-01
Well is your computer giving you any problems besides registering as running at a high temp? Is it slowing down or freezing? Is the fan constantly on or working real hard?

---

### Post by switch10 on 2010-02-01
gkrellm is showing 58C for me..  im on a dual core AMD processor

---

### Post by timZZ on 2010-02-01
> **Greenbean209 said:**
> Well is your computer giving you any problems besides registering as running at a high temp? Is it slowing down or freezing? Is the fan constantly on or working real hard?

**Is it slowing down**

Seems challenged for example using the scroll wheel on the mouse to view the thread index. (Jerky Refresh Rates)

**The fan is constantly on.**

If for example I was to reload this page.  The fan will come on.  The fan is off while I type this. However the fan will turn back on when I click submit.

**working real hard?**

Loading the web pages etc. will trigger the CPU to sit at 100% for a good period of time.

The computer is challenged mainly using browsers.  When using Open Office for example and using the scroll wheel.  The computer will drag.

---

### Post by Greenbean209 on 2010-02-01
Just to clear things up. When did you notice your computer was running under this amount of stress? Did you just recently install Linux or had it been running decently before in your current OS?

---

### Post by bobarry on 2010-02-01
I just ordered a 32gb ssd drive for mine and it said it was rated to 70C, which surprised me. That's hot, but OK.

Bo

---

### Post by martysweeney on 2010-02-01
Best thing to do is open it up, clean the fan on the inside. Using air is ok if you do it every now and again but if you havent cleaned it in a while it will clog up and the best cure is to remove the casing and unscrew the fan and give it a good clean use compressed air on the rest of the board, dust and dirt are killers of any computer, try checking youtube for tutorials on how to do this. If your not confident enough then leave it into a repair shop to have it cleaned..

---

### Post by timZZ on 2010-02-02
> **Greenbean209 said:**
> Just to clear things up. When did you notice your computer was running under this amount of stress? Did you just recently install Linux or had it been running decently before in your current OS?

Sorry for the slow reply.

Thanks for taking the time to reply.

**Did you just recently install Linux or had it been running decently before in your current OS**?

The current OS history for this machine is.

- Windows XP (Pre-installed)
- Fedora Core 8 - 9
- Ubuntu 8.04 LTS
- Fedora Core 11
- Ubuntu 9.04

The main change other then linux distribution was I have added a Netgear G wireless usb stick.

I have only noticed this problem on Ubuntu 9.04.  I have had trouble with usb wireless sticks with any version of Ubuntu less then 9.04.  I had a cd laying around so I installed Ubuntu 9.04.

**When did you notice your computer was running under this amount of stress?**

I am using this laptop for work.  (not my normal machine, I am not a fan of laptops, this was an old work laptop from a previous company from 2004 I believe)

I am running the following applications for work.

DB visualizer
gEdit
FileZilla
FireFox
Chrome
Open Office Spread Sheet

If I run Firefox or Chrome (Alone or at the same time as the other applications) my processor will sit at 100%.  Eventually the laptop will freeze and become unresponsive.

At times I have noticed the caps key turn on and off. (This may be a delayed reaction to me trying to figure out the over-all condition of the computer by seeing if the caps-lock key light responds)

I try to rescue the system with alt + SysRq + s (to sync) then alt + SysRq + 0 (to reboot).

This is not responsive.

---

### Post by timZZ on 2010-02-02
> **martysweeney said:**
> Best thing to do is open it up, clean the fan on the inside. Using air is ok if you do it every now and again but if you havent cleaned it in a while it will clog up and the best cure is to remove the casing and unscrew the fan and give it a good clean use compressed air on the rest of the board, dust and dirt are killers of any computer, try checking youtube for tutorials on how to do this. If your not confident enough then leave it into a repair shop to have it cleaned..

I am comfortable doing this.  I just do not have the tools on me at this current time.  You suggestions are not in vein regardless ... I will try this when I can.

---

### Post by M1GEO on 2010-02-02
Have you tried removing plugins from Firefox/Chrome?  I have a lot of problems with Adobe Flash under Linux.  Especially with 64-bit.  Flash munches alot of resources on my box.  Just a thought.

---

### Post by timZZ on 2010-02-02
Flash + Javascript heavy sites seem to take a toll on the laptop.

This has worked under windows.

Is there a problem with linux + browsers + client side languages?

---

### Post by jamesisin on 2010-02-02
These languages (Flash and JS) are very browser intensive.  I see this being a problem in Opera (across all three major platforms).  I tend to browse with them globally turned off and only turn them on for specific sites.  This reduces but does not eliminate the problem.

---

### Post by ankit singh on 2010-02-02
a temperature of 68 c is not quite high for any kind of laptop but if you are getting any stability issues you should check out your manufacturer.You can also use a laptop cooling pad.Another solution to this is you take your laptop to your manufacturer's service centre and see if they can service it and clean the insides for you.There could be a lot of dust clogged in the heat sinks or the fan might be running slower.Also don't go for any overclocking, if done load it to default option as laptop are not designed for any such things.

---

### Post by timZZ on 2010-02-02
> **ankit singh said:**
> a temperature of 68 c is not quite high for any kind of laptop but if you are getting any stability issues you should check out your manufacturer.You can also use a laptop cooling pad.Another solution to this is you take your laptop to your manufacturer's service centre and see if they can service it and clean the insides for you.There could be a lot of dust clogged in the heat sinks or the fan might be running slower.Also don't go for any overclocking, if done load it to default option as laptop are not designed for any such things.

**a temperature of 68 c is not quite high for any kind of laptop**

Yes I noticed when looking online the processor is still within operational range at 68c it isn't a problem until 78c.

**if you are getting any stability issues you should check out your manufacturer**

I would agree BUT the issue is .. I have not had this problem before.

I am not saying that problems don't develop through use.  However this problem mainly occurred when I installed ubuntu.

Less then 2 weeks ago I have had FC11 on this laptop.  I have been converting my fedora core machine for ubuntu.

**Also don't go for any overclocking, if done load it to default option as laptop are not designed for any such things.**

Everything is the same from default install. I have done nothing to over clock.  When I look at the CPU frequency switching.  The most is 1.9 so I am assuming it is operating as intended.

---

### Post by timZZ on 2010-02-03
Just to note upgrading from 9.04 to 9.10 has made a visible different.

---

### Post by ankit singh on 2010-02-14
Sorry for long time i took to reply

Its also good to hear that you are not facing any unstability.

You need not take any tension.
It looks karmic takes more processor power than its 9.04 version.Many posts have been made eg.
[http://ubuntuforums.org/showthread.php?t=1396936](http://ubuntuforums.org/showthread.php?t=1396936)

---


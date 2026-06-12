---
title: "Long random pauses using Firefox on Ubuntu 9.04"
date: 2009-07-18
forum: General Help
---

### Post by damien_d on 2009-07-18
Dear all,

I am having problems that seems to manifest itself mostly when using firefox on Ubuntu 9.04 (Jaunty), on both my desktop (x64, Phenom quad core, 6GB RAM) and laptop (i686, Centrino duo, 2GB RAM).

At random, there are long pauses from Firefox where it refuses to respond to any input for periods of up to 30s or more.  At the end of this, it processes all events at once.

During this time, some other applications will also pause, but not always.  I can sometimes switch between uses.

I have never observed this behaviour before the last two weeks or so, and never on 8.10 on both my laptop and desktop.

During this time, I have also noticed that:
  * My HDD activity light remains on
  * The system monitor shows that processor usage drops from 100% use down to 50%, 25% or 0% (i.e. cores are no longer processing - I run BOINC in the background).
  * The system monitor shows that the hard disk activity significantly increases during this time.

My laptop exhibits the pauses (it does not run BOINC).  I only have CPU in the system monitory showing on that machine, and it can be seen to significantly drop if I am compiling code (although it does "freeze" when completely otherwise idle too).

Needless to say, this is extremely frustrating.  I have completely cleared firefox's cache ("clear private data"), but it still exhibits the same behavior.

Occasionally, I may have spotted it using other applications, but nowhere nearly as consistantly as with Firefox.

I have not observed it with opera, but I have only used it for very short periods.

---

### Post by GiveLove on 2010-03-06
Hello damien_d, :)

Wish I had an answer for you. I've been having a very similar problem in Ubuntu 9.04 ever since I started using this version for quite some time now. And while it has not been a show stopper, it has been consistent enough now that I'm curious as to what it is and why it is happening. 

For me, these brief(5 to 10 seconds) system wide pauses generally happen once, or maybe twice shortly after logging in. I can't verify that Firefox has anything to do with it, as generally that is the primary application used on my computer, and the first program run after logging in. I keep two separate "System Monitor" applets running in the top panel. One showing the CPU activity, and the other the hard drive activity with reads and writes different colors. What I've noticed is that during these pauses, the hard drive is a doing a continuous write. And as soon as it is done writing, the system is freed up again. And there is very little CPU activity going on during that. After it is done, everything runs normally like it should. And I don't ever remember having this problem with prior Ubuntu releases. 

Any ideas, or further diagnostics to try running, or logs to look at?
Thanks. :)

GiveLove

---

### Post by dcstar on 2010-03-06
Find out where the bad block is on your hard drive and stop it being accessed.

---

### Post by GiveLove on 2010-03-07
Ok, so I figured out some more specific information regarding this problem. After booting up and logging in today, I specifically loaded up other applications besides Firefox, and could not get the this pause to occur. But shortly after loading Firefox the pause happened. So it definitely has something to do with Firefox. I watched my hard drive system monitor applet as it occurred, and it started with a mixture of reads and writes, and then went to one long continuous write. 

So I'm pretty sure this is not a bad block on my hard drive. It's something specific to Firefox. Besides which dcstar, giving that sort of advice without any information to backup your theory, and no instructions in how to verify that this would indeed be the case really reeks of posting just to increase your post count. So if you truly want to be helpful, you'll have to put more effort and information into your posts.

GiveLove

---

### Post by Elludium_Q-36 on 2010-03-16
There are plenty of trolls here now and ones who post malicious code.

One wrote: "Blah blah blah...just wipe the damn thing and reinstall and stop whining."
[http://ubuntuforums.org/showpost.php?p=8959406&postcount=23](http://ubuntuforums.org/showpost.php?p=8959406&postcount=23)  
Yeah, let's all throw the baby out with the bath-water when the new bath-water will be just as dirty!

Maybe posting alot get's them that half caraffe, full caraffe but many are still just a couple sandwiches shy of a picnic, if you know what I mean!

9.04 is a release that seems to have been frought with peril.

I have the same issue and Opera seems not immune, Firefox as well and other mozilla gecko browsers.  I would just use Konqueror but it does not seem to connect over KPPP.

I've read a LOT of posts, more on launchpad but have seen no universal solution.  Have you seen those three wheeled bicycles that have ice-cream coolers on-board?  The ice-cream man does fine, 'till an elephant tries to hitch a ride!

I had a serious issue with KPPP in that if there was an unexpected disconnect, modem hangup or if I tripped over the USB cable; I had to reboot the machine.  This was a pain because it took AGES to open web-pages I wanted to see and needed to download from those open pages.
Finally the issue seemes to have been fixed with the latest backport/update release but I never found an answer.

It would be nice to hear if someone was at least working on the issue...

---

### Post by Elludium_Q-36 on 2010-03-16
If you haven't seen it in other threads, here's one useful bit of advice.

Disallow ALL javascript in firefox.  Above the navigation bar is the Menu bar -> Edit -> Preferences -> Content -> uncheck "Enable Javascript".  I have the "No Script" add-on/extention and allow JS on VERY FEW websites but notice a problem when I do.

I have Greasemonkey & GreaseFire so I can run custom scripts of my own choosing and not at the whim of the web-developer.  For example, I currently have all javascript turned off for websites but a local script changes the appearance of pages to be night vision friendly, white text on black background, etc.  Sometimes I go outside at night I would still see the bright white Google page ;-)

I have the develper's toolbar so it's quick to allow JavaScript and NoScript proivdes a white-list.  Again, when I have this issue, it's usually when JavaScript is enabled.  I'm going to TRY to remember to open pages that are so draconian to require JS in other browsers and kill them when done.  That's just my 2¢ and you should give it a try or you can live by the tag-line from the Snickers commercial, "Not going anywhere for a while?"

---

### Post by GiveLove on 2010-03-16
Hello Elludium_Q-36, :)

Thank you so much for your two responses. That's a real shame with trolls and people posting malicious code. I'd read about it in the stickied thread the moderator put up, but had never seen it first hand. Fortunately the problem is not bad enough that I want to tinker with javascript and custom scripts which is not my skill set anyways. It only happens once, sometimes twice after loading Firefox, and then no more until restarting the operating system. So unless someone comes up with a definite answer, I can live with it until I do a fresh install of 9.10 in April. Thanks again

GiveLove

---

### Post by Elludium_Q-36 on 2010-03-16
I never said I am currently a writer of scripts but I am one who turns them off.

I've enabled a couple from greasefire but I took a chance and read the reviews.  They could have been malicious and If I had been the only one having problems with firefox, I might have assumed as much.

Here's the thing;  EVERYTIME YOU VISIT A WEB-PAGE AND ALLOW JAVASCRIPT, you allow whomever controls that website to RUN A SCRIPT OR PROGRAM ON YOUR COMPUTER!!!  Now while that MAY lead to a compromised system, it certainly does uses CPU cycles.  Have you ever seen a message like "script busy"/"script not responding"?  I've seen it more with Firefox on Windows but not so much since I disallowed Javascript.

While I haven't found a solution, I have found that many people have this issue which seems to be tied to X.org and often with Firefox running.  I killed a bunch of processes and removed their packages, which I did not need but I kinda need a working web browser.  A lot of people report this issue with 9.04 and yes, I'm waiting for 10.04 too but let's hope that things are in fact fixed in that release.

Meanwhile you can do no harm by turning off javascript and it does not require you to "tinker".  The worst that can happen is that a page will complain that it needs JavaScript to work properly and if you really need that page, just re-enable and reload the page.

You don't have to rely on my word alone but I'm trying to steer you in the right direction.

---

### Post by dcstar on 2010-03-16
> **GiveLove said:**
> 
..........
So I'm pretty sure this is not a bad block on my hard drive. **It's something specific to Firefox**. Besides which dcstar, giving that sort of advice without any information to backup your theory, and no instructions in how to verify that this would indeed be the case really reeks of posting just to increase your post count. So if you truly want to be helpful, you'll have to put more effort and information into your posts.

GiveLove

You specifically stated that:

*"Occasionally, I may have spotted it using other applications, but nowhere nearly as consistantly as with Firefox"*

so make up your mind before bagging people who offer a possible solution.

If you want a detailed explanation on every little bit of advice that you ask for then good luck, otherwise you are free to disregard anything that might be of use if you feel it isn't packaged in a way that suits your delicate sensibilities.

I may have explained the many reasons why such a thing can cause issues like yours, but funnily enough now I just couldn't be bothered.

---

### Post by GiveLove on 2010-03-18
Hello dcstar, :)

I won't deny you your choice to pass the blame onto me. But it doesn't change anything. Nor does it solve the problem or make the forums here friendly and helpful for people.  

This forum is comprised of people of all skill and experience levels. Not just people that know everything about Ubuntu and Linux. And no matter how many years I've been using Ubuntu, there is always aspects of it that are new to me that require explanation. Much like the majority of users here. 

Your welcome to do as you please. But expect your responses to be seriously questioned when you offer possible solutions with no explanation and detailed instructions to test to see if it applies.

So unless you have anything useful to add to this thread, it's best left ended here. 

GiveLove

---

### Post by Elludium_Q-36 on 2010-03-19
I have before tried to disabuse others of a train of thought derailed but found it only a practice in typing.  In person, such endeavors are a waste of breath.

Both "dcstar" and I offered advice to one, not the original poster of this thread and both had our respective advisements muddled.

It's far easier to post for help, like sheep that makes "Bla-a-a-t" noises than to go in search of lost sheep, entangled in bramble and offer help.  The wolves can be most convincing and offer malicious code with a smile.

Too many people IRL (In Real Life) seek my advice on things I am nearly expert yet scoff.  I don't need that coming out of my computer screen when I've been nice enough to proffer help.

There is fully paid support for this Ubuntu product and you may feel free to tell the support personnel that they know not of what they speak; especially when talking on "your dime".

I would wager that there are some on here who are more knowledgeable than many a tech-support or "helpless desk" person and many companies have the low level "tech" merely read from a script.  Of course covering the basics is important as it is easy to gloss over the simple things that a script may cover like a flow chart.

Most of us have different hardware, with different packages installed so only a psychic, deity or one logged in remotely would be able to see what you see.  That psychic would have to be legitimate AND adept at Unix/Linux/Ubuntu/Kubuntu, etc.  Lots of luck and deity have other concerns.

It's easy to see you have a negative attitude or let a bad day get to you but one should always read what they have written before posting or hitting send.  There are articles written about drunk-texting and the concept transcribes well.

I did not scoff at advice offered and my system is working far better now.  I only thought to "give back" and work out the few remaining bugs.
I'm certainly going to read other people's post histories before trying to be helpful, from now on.  Perhaps I will PM those who seem like they might listen.

Feel free to scoff everyone's advice and keep doing as you have been doing.  Of course there's that quote, attributed to one Albert Einstein:  
"Insanity: doing the same thing over and over again and expecting different results."  While you're at that, migrate back to Windows.

---


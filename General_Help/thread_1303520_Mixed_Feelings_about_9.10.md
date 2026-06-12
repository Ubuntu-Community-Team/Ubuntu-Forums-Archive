---
title: "Mixed Feelings about 9.10"
date: 2009-10-28
forum: General Help
---

### Post by ubuwatson on 2009-10-28
I have been a very happy ubuntu user.  For a while I only considered myself a hobbyist and when 9.04 came out I switched to ubuntu completely.  

As the IT Director of my company, I needed to evaluate Windows 7 as many of our XP systems will begin the progression over to Windows 7 sometime next year.  I begin using Windows 7 on a trial basis, and over time I begin to appreciate it.  I installed Windows 7 RC/RTM on several machines and have been evaluating it's performance over the last few months.  It's a great operating system, but only time will tell if it's worthy of it's initial praise.

I recently begin using 9.10 also, dual booting Karmic on the same Windows machines and all have updated to the release candidate as of late.  I really do think that 9.10 is another fantastic release and I have nothing but praise for the fine work that has been done.  That being said one issue I have noticed over and over again (and it existed in past releases as well) is the speed in which applications launch.  Clicking on just about any application or even just opening nautilus shows a delay.  Sometimes the delay lasts just a second, and sometimes the spinning ball of death goes on for a bit longer than normal.  I know folks on the forum tend to blame hardware or drivers, but I think that scapegoat has run its course considering I am using 9.10 on several different machines and all experience the same delays - as such I feel this issue is software dependent, not hardware dependent.

I understand that Ubuntu in many ways is still in it's infancy and I love the project and I am fully dedicated to supporting it so don't take my words as harsh criticism, but running ubuntu on  very current and fast Intel processors with class leading ram and hard drives should *NOT* show delays launching applications.  This to me in all honestly is not acceptable.  Even the resource hogging and typically inefficient kernel of the windows operating system does not suffer from these issues.

I don't plan on giving up on Ubuntu, like I said I love it, but this is 'tough love' in that I don't feel like I am giving back unless I do point out what I consider some important issues. Issues I am willing to deal with, learn about, and hopefully resolve.

If I am the only one who notices this (even though I have it running on four different machines), than I apologize in advance for my cristism.

---

### Post by coffeecat on 2009-10-28
> **ubuwatson said:**
> That being said one issue I have noticed over and over again (and it existed in past releases as well) is the speed in which applications launch.  Clicking on just about any application or even just opening nautilus shows a delay.  Sometimes the delay lasts just a second, and sometimes the spinning ball of death goes on for a bit longer than normal.  I know folks on the forum tend to blame hardware or drivers, but I think that scapegoat has run its course considering I am using 9.10 on several different machines and all experience the same delays - as such I feel this issue is software dependent, not hardware dependent.

Since you're experiencing this issue on several machines, it must be a real issue. I do not dispute that. What puzzles me is that I am not experiencing this myself on my own machines. And I've been using Ubuntu since 5.10 on a variety of computers. For example, on this Core 2 Duo T6400 (2GHz) laptop running Jaunty*, Nautilus opened near-instantaneously (certainly quicker than Windows Explorer in Vasta on the same machine). Gedit, VLC and Brasero took about a second, and Open Office writer took about 8 seconds to be opened first time (which is pretty good considering it's OpenOffice), but only about 2 seconds on a subsequent opening. I think that's all quite acceptable.

I think we do have to look at hardware or drivers. But you may be right - maybe it is software dependent, but dependent on which hardware/drivers you're using. Can you give us a rundown of the particular hardware of a machine that's giving you this trouble - motherboard chipset, video chipset, that sort of thing?

* **Edit:** just happened to be using Jaunty. Karmic on this laptop is just as responsive, if not more so, than Jaunty.

---

### Post by lancest on 2009-10-28
Just occasional slowness from Firefox but not seeing it lately on Karmic (5 machines). Google Chrome blazes! Open Office does not get loaded into memory like MS Word at bootup so is a little slower of course. I hear OO 3.2 will have speed fixes.
 All the Windows machines i have touched lately have been dog slow so I'm biased. I'm very fussy about my software launching fast and Ubuntu is just fine.

---

### Post by ubuwatson on 2009-10-28
> **coffeecat said:**
> Since you're experiencing this issue on several machines, it must be a real issue. I do not dispute that. What puzzles me is that I am not experiencing this myself on my own machines. And I've been using Ubuntu since 5.10 on a variety of computers. For example, on this Core 2 Duo T6400 (2GHz) laptop running Jaunty*, Nautilus opened near-instantaneously (certainly quicker than Windows Explorer in Vasta on the same machine). Gedit, VLC and Brasero took about a second, and Open Office writer took about 8 seconds to be opened first time (which is pretty good considering it's OpenOffice), but only about 2 seconds on a subsequent opening. I think that's all quite acceptable.

I think we do have to look at hardware or drivers. But you may be right - maybe it is software dependent, but dependent on which hardware/drivers you're using. Can you give us a rundown of the particular hardware of a machine that's giving you this trouble - motherboard chipset, video chipset, that sort of thing?

* **Edit:** just happened to be using Jaunty. Karmic on this laptop is just as responsive, if not more so, than Jaunty.

coffecat, my good friend also says he does not notice any delays either.  I wish I could nail down the source of the issue.

System 1:

IBM Thinkpad T500 Notebook
Intel Core 2 Duo
4 gigs ram.
500 G Western Digital Scorpio Blue
Intel Video Chipset (shared ram)

System 2:

HP Pavillion 6775us Laptop
Intel Core 2 Duo
3 gigs ram.
320 G Western Digital Scorpio (7200 RPM)
Nvidia GeForce 8000 - 256 m dedicated ram.

System 3 (Desktop)

Quad Core Intel
8 Gigs of Ram
Western Digital (dual) 500G drives.
Intel Integrated Video 



All three of the machines above are extremely fast, fast enough that under Windows (XP and 7) there are no delays launching applications, the system just feels quick and snappy.

There is nothing hogging resources and on two of the machines no proprietary drivers are in use.  I have installed both 9.04 x86 and 64b version along with 9.10 RC x86 and 64b.

To me the problem seems to be in how the system launches applications, not sure what overhead is involved (is it GTK, Gnome, etc) and I am not trying to nitpick but many of these applications are small in footprint and written in C and show easily appear as quick as you click the mouse, especially so on my hardware.

I am probably more sensitive than the average user.  I have 100s of windows machines under my watch many of which vary in hardware so I am well versed in what to expect.  The only things that slow down windows machines is the software that people install on them.  All of our windows machines run very well and very fast with the only significant problems being malware and Trojans.

Like I said before, I have noticed this issue for a long time and even under different distros so I believe the linux kernal is somehow inefficient compared to windows in how application are executed (though I do feel it deals with many other things better than the windows kernel).  In some ways I am splitting hairs as the launch times aren't painful, but as someone who has written software such as very heavy, bloated .NET software under windows I am quite surprised out how long these applications take to launch considering the .NET software i author typically opens as fast as one can click the mouse.

---

### Post by MarcusW on 2009-10-28
I also notice that delay compared to windows or mac. Totally worth it though...

---

### Post by solwic on 2009-10-28
> **lancest said:**
> Just occasional slowness from Firefox but not seeing it lately on Karmic (5 machines). Google Chrome blazes! Open Office does not get loaded into memory like MS Word at bootup so is a little slower of course. I hear OO 3.2 will have speed fixes.
 All the Windows machines i have touched lately have been dog slow so I'm biased. I'm very fussy about my software launching fast and Ubuntu is just fine.

Google Chrome is available on Linux now?  How do I get it?

---

### Post by ukripper on 2009-10-28
> **iRun said:**
> Google Chrome is available on Linux now?  How do I get it?

Follow the link and use PPA method- [http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html](http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html)

---

### Post by ukripper on 2009-10-28
To OP: Can you tell which applications you have tried?

---

### Post by running_rabbit07 on 2009-10-28
> **ubuwatson said:**
> I have been a very happy ubuntu user.  For a while I only considered myself a hobbyist and when 9.04 came out I switched to ubuntu completely.  

As the IT Director of my company, I needed to evaluate Windows 7 as many of our XP systems will begin the progression over to Windows 7 sometime next year.  I begin using Windows 7 on a trial basis, and over time I begin to appreciate it.  I installed Windows 7 RC/RTM on several machines and have been evaluating it's performance over the last few months.  It's a great operating system, but only time will tell if it's worthy of it's initial praise.

I recently begin using 9.10 also, dual booting Karmic on the same Windows machines and all have updated to the release candidate as of late.  I really do think that 9.10 is another fantastic release and I have nothing but praise for the fine work that has been done.  That being said one issue I have noticed over and over again (and it existed in past releases as well) is the speed in which applications launch.  Clicking on just about any application or even just opening nautilus shows a delay.  Sometimes the delay lasts just a second, and sometimes the spinning ball of death goes on for a bit longer than normal.  I know folks on the forum tend to blame hardware or drivers, but I think that scapegoat has run its course considering I am using 9.10 on several different machines and all experience the same delays - as such I feel this issue is software dependent, not hardware dependent.

I understand that Ubuntu in many ways is still in it's infancy and I love the project and I am fully dedicated to supporting it so don't take my words as harsh criticism, but running ubuntu on  very current and fast Intel processors with class leading ram and hard drives should *NOT* show delays launching applications.  This to me in all honestly is not acceptable.  Even the resource hogging and typically inefficient kernel of the windows operating system does not suffer from these issues.

I don't plan on giving up on Ubuntu, like I said I love it, but this is 'tough love' in that I don't feel like I am giving back unless I do point out what I consider some important issues. Issues I am willing to deal with, learn about, and hopefully resolve.

If I am the only one who notices this (even though I have it running on four different machines), than I apologize in advance for my cristism.

And you don't notice how long Windows takes to load a program? Simple things like Yahoo mess take at least 5 seconds. Pidgin is a snap of the fingers. Opening MS Word for the first time after startup takes at least ten seconds, Abiword is there almost instantaneously, for me.

---

### Post by ubuwatson on 2009-10-28
> **ukripper said:**
> To OP: Can you tell which applications you have tried?

a rather large number of applications.  Though I will admit, Google chrome loads extremely fast as if there is little to no overhead. It may be dependent upon the coding used in the application, I can't be sure.

Maybe nautilus is the problem.

---

### Post by ukripper on 2009-10-28
> **ubuwatson said:**
> a rather large number of applications.  Though I will admit, Google chrome loads extremely fast as if there is little to no overhead. It may be dependent upon the coding used in the application, I can't be sure.

Maybe nautilus is the problem.

Can you give some examples of applications in question?

---

### Post by ubuwatson on 2009-10-28
> **running_rabbit07 said:**
> And you don't notice how long Windows takes to load a program? Simple things like Yahoo mess take at least 5 seconds. Pidgin is a snap of the fingers. Opening MS Word for the first time after startup takes at least ten seconds, Abiword is there almost instantaneously, for me.

Windows has it's share of issues, but when it comes to performance a finely tuned machine is rather impressive.   The performance degradation in Windows is easily diagnosed: Fragmentation, processes using up to many CPU cycles, etc.  In the same respect I am not sure what the issue is with Ubuntu, even a fresh install shows the same problems: applications are a bit slow to launch.

---

### Post by ubuwatson on 2009-10-28
> **ukripper said:**
> Can you give some examples of applications in question?

Nautilus.
Firefox (but this is pretty much to be expected these days, even under windows).
Terminal
Empathy / Pidgeon

I can go on and on, it happens to every application, though sometimes things seem to load faster than others (and keep in mind this can happen even when nothing else is running) - it's a real odd issue to peg down.  Like someone else stated, even with some slowdown, Ubuntu is well worth it and I couldn't agree more.  I am just trying to understand why an operating system with such low overhead compared to Windows and a more efficient design has issues launching small C++ and Python applications.  There must be a simple answer.  I will not accept defeat nor will I give the horrid and often uneducated response of 'well I am going back to windows' :))))

In prior released of Ubuntu I felt disk performance was the issue, but I have noticed under Karmic I get similar and if not in some cases better performance than Windows 7 reading and writing files.

---

### Post by ubuwatson on 2009-10-28
Maybe this thread should be re-titled and moved.  I actually love 9.10, i just need to get to the root cause of this app loading issue.

---

### Post by vexorian on 2009-10-28
This is just a theory, If you don't notice the delays in chrome, I think I can say something...
windows 7 apps seem to have better multithreading than ubuntu apps (ESPECIALLY firefox is terrible at it)

I think that if your machine has many cores + hyperthreading it would be seriously noticeable.

Mozilla is working on making firefox better at multithreading, but until that... There is also another issue and it is that the  scheduler is not tuned for a desktop computer but for a server/ bussiness computer

So I am thinking that at least for the following months dows7 will feel much faster in things like a core i7 which is what I get when I read "fast and current intel processor".

It will get a serious problem when quad cores become common, we really need our desktop apps recoded to be adept at using 100% of a multicore processor... Right now, the kernel can deal with hundreds of cores just fine, but the apps aren't used to it..

---

### Post by ukripper on 2009-10-28
> **ubuwatson said:**
> Maybe this thread should be re-titled and moved.  I actually love 9.10, i just need to get to the root cause of this app loading issue.

When you used Jaunty (9.04), did you use EXT4 then?

---

### Post by ubuwatson on 2009-10-28
> **ukripper said:**
> When you used Jaunty (9.04), did you use EXT4 then?

No, I was using EXT3.

---

### Post by SunnyRabbiera on 2009-10-28
Yeh your issues are strange, for me applications on linux seem to launch just as fast or faster then on windows.
But yeh I admit I have had issues with the speeds of nautilus and firefoxin the past, but not with Pidgin it loads pretty fast on my machine.
Proves the point that individual mileage may vary, I swear all computers have unique personalities.

---

### Post by ukripper on 2009-10-28
> **ubuwatson said:**
> No, I was using EXT3.

did you have the same problem on 9.04?

---

### Post by ubuwatson on 2009-10-28
> **vexorian said:**
> This is just a theory, If you don't notice the delays in chrome, I think I can say something...
windows 7 apps seem to have better multithreading than ubuntu apps (ESPECIALLY firefox is terrible at it)

I think that if your machine has many cores + hyperthreading it would be seriously noticeable.

Mozilla is working on making firefox better at multithreading, but until that... There is also another issue and it is that the  scheduler is not tuned for a desktop computer but for a server/ bussiness computer

So I am thinking that at least for the following months dows7 will feel much faster in things like a core i7 which is what I get when I read "fast and current intel processor".

It will get a serious problem when quad cores become common, we really need our desktop apps recoded to be adept at using 100% of a multicore processor... Right now, the kernel can deal with hundreds of cores just fine, but the apps aren't used to it..

I guess it's a possibility.  I do know that Windows caches certain applications and many of the core dlls (for windows forms) are most likely loaded into memory when Windows is loaded.

---

### Post by ubuwatson on 2009-10-28
> **ukripper said:**
> did you have the same problem on 9.04?

yes I noticed in 9.04.  I actually find disk performance to be faster under 9.10 than 9.04.  My transfer rates reading and writing to external media is significantly faster under 9.10 so my assumption was that application would also launch faster. Like I said before, the launching of apps is not painfully slow or even problematic, but I am sensitive to it so I notice it.  I also might be more sensitive to the issue than normal because I have been using Windows 7 on and off and love it or hate, the OS feels rather fast - though only time will tell if it maintains this performance.

---

### Post by vexorian on 2009-10-28
> **ubuwatson said:**
> I guess it's a possibility.  I do know that Windows caches certain applications and many of the core dlls (for windows forms) are most likely loaded into memory when Windows is loaded.
Well, there are ways to tweak ubuntu to do that as well and preload commonly used apps, I don't remember exactly but will look for that howto in which I learned it.

---

### Post by ubuwatson on 2009-10-28
> **ubuwatson said:**
> I guess it's a possibility.  I do know that Windows caches certain applications and many of the core dlls (for windows forms) are most likely loaded into memory when Windows is loaded.

> **vexorian said:**
> Well, there are ways to tweak ubuntu to do that as well and preload commonly used apps, I don't remember exactly but will look for that howto in which I learned it.

it's not that important that I would even want to do it.  My real gripe is why there is are delays in loading apps.  My ram usage and cpu cycles are very minimal under Ubuntu, so it bugs me ;)

---

### Post by vexorian on 2009-10-28
hmnn, anyway, maybe this: [http://www.debianadmin.com/load-applications-quicker-in-ubuntu-using-preload.html](http://www.debianadmin.com/load-applications-quicker-in-ubuntu-using-preload.html) ?

---

### Post by HappyFeet on 2009-10-28
Ubuntu 9.10 isn't even released yet. Why the need to jump on 9.10 so soon? No matter what the OS, you are better off waiting at least a couple of months until most of the kinks get worked out. It is your own fault for being impatient. They will update the kernel soon enough.

Btw, I have not noticed the slowness that you have. (9.10 is not my main OS yet, but I test it out for debugging purposes)

---

### Post by HappyFeet on 2009-10-28
> **ubuwatson said:**
> My real gripe is why there is are delays in loading apps.  My ram usage and cpu cycles are very minimal under Ubuntu, so it bugs me ;)

You are the first person I've heard report this. Are all the machines with 9.10 the same hardware wise?

---

### Post by ukripper on 2009-10-28
For me only application showing any slowness at first is firefox and for obvious reasons, once firefox is cached in memory then it opens up instantly. I am running 9.10 64bit for only testing on Core2duo laptop 1.4ghz/2GB RAM and find it really snappy on all applications OP mentioned earlier

---

### Post by running_rabbit07 on 2009-10-28
One of the things I do that helps make things load even faster, is to go into Startup Applications and set my favorites to start on boot. After doing that, they are in the cache and start instantaneously for me. Of course this would only be a workaround and not really the solution you are looking for, but a simple workaround none the less.

BTW this is my 1000nth post!

---

### Post by ukripper on 2009-10-28
> **running_rabbit07 said:**
> 

BTW this is my 1000nth post!

Congrats!:p

---

### Post by running_rabbit07 on 2009-10-28
> **ukripper said:**
> Congrats!:p

Thanx, this is worthy of a fresh cup of java. (Yes, I am a geek.)

---

### Post by ukripper on 2009-10-28
> **running_rabbit07 said:**
> Thanx, this is worthy of a fresh cup of java. (Yes, I am a geek.)

or fresh rolled up python in my cup. I used to be Java fan once

---

### Post by ubuwatson on 2009-10-28
> **HappyFeet said:**
> Ubuntu 9.10 isn't even released yet. Why the need to jump on 9.10 so soon? No matter what the OS, you are better off waiting at least a couple of months until most of the kinks get worked out. It is your own fault for being impatient. They will update the kernel soon enough.

Btw, I have not noticed the slowness that you have. (9.10 is not my main OS yet, but I test it out for debugging purposes)

It's my own fault for being impatient ? - I always download and test alphas and betas of many Operating Systems - it's part of my job.

---

### Post by ukripper on 2009-10-28
> **ubuwatson said:**
> It's my own fault for being impatient ? - I always download and test alphas and betas of many Operating Systems - it's part of my job.

In that case you should have reported bugs to launchpad  for bugs fix if developers thinks there is any they will give you feedback on it.

---

### Post by running_rabbit07 on 2009-10-28
I am using Karmic Ubuntu as my production OS now. I was impatient (more like too excited to get it going) and I am also confident that the Devs were busting "donkey" to make this release competitive with Windows 7.

---

### Post by HappyFeet on 2009-10-28
> **ukripper said:**
> **In that case you should have reported bugs to launchpad**  for bugs fix if developers thinks there is any they will give you feedback on it.

Exactly.

---

### Post by ubuwatson on 2009-10-28
wow, man do i ever feel stupid.

While I was posting this thread I was also installing 9.10 RC on another new T500 (same spec as other).  I ran the very latest updates and rebooted and now I am NOT noticing any lag in launching apps - if anything things feel super snappy.

I have been trying to reproduce the issue as I was going to let someone remote into my machine to see for themselves what i am talking about.

Wow, so i guess i owe an apology to the poster who felt I was being impatient and I guess I owe the community an apology for jumping the gun on this.

Please don't call me crazy, i am already second guessing myself...I have been up programming for the last 15 hours straight and i was a bit cranky (and that is what prompted me to write this thread)....

---

### Post by noelvh on 2009-10-28
I also am a tech, and this is what I know of this. Windows pre-loads as much as it can into memory to speed up the system, so explorer will open fast. Also have you ever looked at the start-up folder under the start menu. if you are not paying attention app put a pre-launcher in there, to make them pre-load into memory. This is a cheap *** way of making your system open app faster. I am sure you can do this with Ubuntu but why. I do not mind the second or to to open an app if the system in not bogged down by apps preloaded into memory.

Another thing I noticed is all 3 of you systems use WD drives. IMO WD drives are the worst drive on the market, to me they are junk (MO). I remember when WD had the best drives, but they sold out, with a cheaper and faster to market approach to drives. I can say this as most of the HD I have replaced over the last 6 years have been WD drives. 

I my self have been running 9.10 since first beta and love it. I have given Win7 the test drive, and it is the same old Windows product, just flashy looking (I hate the new look). I my self will be working on migrating my company to Win7, but I am not looking foreword to this migration. The look and feel is just to different, and requires training for the users. 

SO I can see your point if you work at a blinding speed, but if you can not wait the one or two seconds it takes to open the average app, you should stick to Win7.

Oh and dose any on else see the changes, and new features to Pista and Win7 that have been in OSX, and linux for years?


Noel

---

### Post by ubuwatson on 2009-10-28
man, i don't get it, yesterday things seemed good, but not great.  today things are blazing fast, faster than Windows 7.  I wonder what update between yesterday and today made that happen ?

---

### Post by running_rabbit07 on 2009-10-28
> **ubuwatson said:**
> man, i don't get it, yesterday things seemed good, but not great.  today things are blazing fast, faster than Windows 7.  I wonder what update between yesterday and today made that happen ?

That is the fun with a Beta version. Today "crappy", tomorrow "happy", Saturday "wow"

Not really crappy to me, just showing the possibilities after each new update comes out.

---

### Post by steelcommuter on 2009-10-29
> **ubuwatson said:**
> wow, man do i ever feel stupid.

While I was posting this thread I was also installing 9.10 RC on another new T500 (same spec as other).  I ran the very latest updates and rebooted and now I am NOT noticing any lag in launching apps - if anything things feel super snappy.

I have been trying to reproduce the issue as I was going to let someone remote into my machine to see for themselves what i am talking about.

Wow, so i guess i owe an apology to the poster who felt I was being impatient and I guess I owe the community an apology for jumping the gun on this.

Please don't call me crazy, i am already second guessing myself...I have been up programming for the last 15 hours straight and i was a bit cranky (and that is what prompted me to write this thread)....

I have noticed the same issue, definitely, and I think some of the responses to your observations are tactless and unhelpful.  I use Linux exclusively on all my computers, and occasionally will use a relative's or friend's Windows laptop.  Perhaps it is simply preloading, but I have observed it as well.

---

### Post by humphreybc on 2009-10-29
I'm running Karmic on the computer in my sig, and i've noticed no delays apart from Firefox when opening (which is why I now use Chrome!).

I have noticed that when the HDD is busy (namely, copying files) and also trying to do something else, say, play music, Ubuntu will hang TERRIBLY... like run really, really slow.

But, i'm sure many other operating systems do this, it's unavoidable I guess, you know, trying to read/write from several places at once on the same disk gets a bit taxing :P

---

### Post by 3rdalbum on 2009-10-29
Spinning beach ball of death? Are you sure you're not running Mac OS X?

---

### Post by DouglasAWh on 2009-10-29
> **ubuwatson said:**
> wow, man do i ever feel stupid.

While I was posting this thread I was also installing 9.10 RC on another new T500 (same spec as other).  I ran the very latest updates and rebooted and now I am NOT noticing any lag in launching apps - if anything things feel super snappy.

I have been trying to reproduce the issue as I was going to let someone remote into my machine to see for themselves what i am talking about.

Wow, so i guess i owe an apology to the poster who felt I was being impatient and I guess I owe the community an apology for jumping the gun on this.

Please don't call me crazy, i am already second guessing myself...I have been up programming for the last 15 hours straight and i was a bit cranky (and that is what prompted me to write this thread)....

The only thing you owe anyone an apology about is not filing a bug. :) It seems someone else must have though.

It seems like the Karmic development cycle was rougher than Jaunty.  Maybe I just tried to use it more (as in time) or maybe I just tried to do more with it (as in installed apps).  Either way, the final product is solid.  I honestly don't notice a lot of difference from Jaunty, but I thought Jaunty was leaps and bounds beyond Intrepid.

I read (quickly) through the entire thread.  Other than the machine with 8GB RAM, it wasn't clear to me whether you were using x64 or x86.  Since the problem seems to be cleared up, it's not really worth telling us, but I am curious.

EDIT: I also wanted to mention that though this is not in the scheme of things I think we should all be clear about the difference between Chrome and Chromium.  We don't call Darwin "OS X" now do we?  I think it is an important distinction for libre software.

---

### Post by ukripper on 2009-10-29
> **steelcommuter said:**
> I have noticed the same issue, definitely, and I think some of the responses to your observations are tactless and unhelpful.  I use Linux exclusively on all my computers, and occasionally will use a relative's or friend's Windows laptop.  Perhaps it is simply preloading, but I have observed it as well.

As posted earlier, that is why we have launchpad - [https://launchpad.net/](https://launchpad.net/) to report any potential bugs!

---

### Post by P4man on 2009-10-29
> **ubuwatson said:**
> wow, man do i ever feel stupid.

While I was posting this thread I was also installing 9.10 RC on another new T500 (same spec as other).  I ran the very latest updates and rebooted and now I am NOT noticing any lag in launching apps - if anything things feel super snappy.

I have been trying to reproduce the issue as I was going to let someone remote into my machine to see for themselves what i am talking about.

Wow, so i guess i owe an apology to the poster who felt I was being impatient and I guess I owe the community an apology for jumping the gun on this.

Please don't call me crazy, i am already second guessing myself...I have been up programming for the last 15 hours straight and i was a bit cranky (and that is what prompted me to write this thread)....

Well, Im not sure that solves the issue or not, but before reading this I was thinking there was something else your machines might share, and which we dont have, thats you network. perhaps its somehow related to wins or IPv6 or something? No matter how much I like ubuntu, its networking still isnt quite there imho. Maybe its my ignorance, but I find its often slow and does weird things. Shares not showing up before having refreshed the screen a dozen times, timing out when there is no reason to.. I could see how something like that might slow nautilus, but it wouldnt explain a delay in opening a terminal tho...

---


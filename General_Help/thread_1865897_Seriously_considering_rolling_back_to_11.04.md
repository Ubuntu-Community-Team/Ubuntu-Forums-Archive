---
title: "Seriously considering rolling back to 11.04"
date: 2011-10-20
forum: General Help
---

### Post by niranjan_rao on 2011-10-20
Though I am not what you would call as power user, I have been user of ubuntu since 10.04. Did OS upgrade every time new release came out faithfully and was never disappointed or got into trouble. Everything just worked. I have ubuntu installed on 3 different machines - one lap top and 2 desktops - between my home and work and problems are almost uniform on each machine

All the machines where I have current problems are upgraded from 11.04 and never had any problems with 11.04.

Current release - 11.10 is the one that is giving me LOT of trouble. Things work fine if I start fresh - after reboot. Everything is working as expected.

After some time (don't know exactly how much time), machine starts feeling "heavy" or sluggish. It responds, but slowly becomes very slow in responding. May be there is a memory leak somewhere.

If let machine idle - until screen blacks out or machine suspends, things get lot worst. On one machine, I do get display back, but mouse stops working. I can not even logout unless I reboot machine. Keyboard including unity shortcuts do work. I tried top command and seems like compiz is using max cpu cycles as high as 35%

On other machines, I get garbled display after machine wakes up. I don't know what it's displaying, but I assume it's login prompt since machine is just waking up. I tried entering my password and I get normal display minus mouse not working which makes it effectively useless.

My usage pattern has not changed - still using same applications like firefox/eclipse most of the times.

Looking for ideas/solutions to stay on 11.10. I'll try it for few more days and see if new updates solve my problem otherwise will be forced to go back to previous release - which I liked.

Thanks for any pointers

---

### Post by gunksta on 2011-10-20
Install htop (sudo apt-get install htop). Start a terminal and keep it somewhere easily accessible. Use your desktop, let it sit idle, whatever. When it starts to run sluggishly go back to that terminal and run htop.

Htop is like top, but much nicer and it shows you more stuff. Look for any applications that are taking lots of CPU time or memory. I would start by looking at Firefox and Exclipse, two applications with a on-again off-again track record with memory.

How many tabs do you have open in FF?

---

### Post by niranjan_rao on 2011-10-20
Thanks for the quick reply. I'll install htop as you have suggested. 

As for firefox, today I had only two tabs open - it's rare for me have so few tabs open and that's why I remember. It sill acts up.

And loosing mouse is also big pain the behind.

---

### Post by niranjan_rao on 2011-10-20
To add one more problem - my machine just froze - completely frozen. Ctrl-Alt F2/F3 etc were also not responding - nor was mouse. 

The machine was rebooted ten minutes back and only applications open right now were chrome and eclipse and terminal prompt.

Again never happened in 11.04 on the same box.

---

### Post by LinuxFan999 on 2011-10-20
> **niranjan_rao said:**
> To add one more problem - my machine just froze - completely frozen. Ctrl-Alt F2/F3 etc were also not responding - nor was mouse. 

The machine was rebooted ten minutes back and only applications open right now were chrome and eclipse and terminal prompt.

Again never happened in 11.04 on the same box.
Did you try Ctrl-Alt-Backspace?

---

### Post by niranjan_rao on 2011-10-20
Nope, sorry, never heard of that combination. What does it do?

As I said earlier, I am not a power user

---

### Post by MBybee on 2011-10-20
> **niranjan_rao said:**
> Nope, sorry, never heard of that combination. What does it do?

As I said earlier, I am not a power user

It used to restart the X Server, but it would need to be re-enabled to do so now. Here's an older guide, should still work.
[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)

---

### Post by LinuxFan999 on 2011-10-20
> **MBybee said:**
> It used to restart the X Server, but it would need to be re-enabled to do so now. Here's an older guide, should still work.
[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)
I have heard that the Ctrl-Alt-Backspace combination is disabled by default in Ubuntu, but why?

---

### Post by MBybee on 2011-10-20
> **LinuxFan999 said:**
> I have heard that the Ctrl-Alt-Backspace combination is disabled by default in Ubuntu, but why?

It is disabled by default in the most recent versions. I've never heard a good reason - but then there's no good reason for Unity either ;)

---

### Post by gunksta on 2011-10-21
Once you have installed htop, use it when your system gets run down. Another option is to run it from directly from a tty. To do this, install htop and then hit Control-Alt-F1.

Your screen will go black and things may appear to freeze up for a moment. Don't panic. All will be fine. You will find yourself at a 1980s looking terminal log-in screen. Enter your user name and password (same as you would use to log in normally) and you will log in to the terminal session.

Start htop by issuing the command ```
htop
```. This will show you how well things are running as of right now. You can return to your normal session by hitting Control-Alt-F7. This leaves htop running in the backgorund on the tty and if everything goes haywire on your GUI, you can still back off and get back to the tty and have a look at what is going on. Added bonus, htop lets you kill off offending (or unoffending) applications.

I agree - there is no reason for your machine to run slowly when you have a whopping 2 firefox tabs open. I was just making sure you weren't running around with 102 on a four year old machine with 512MB of RAM. Ubuntu is good, not magic. But, it doesn't sound like this is your problem.

Good luck and let us know if htop shows you anything that looks interesting. It will also show you background stuff, like zeitgeist, so if there is something like that running and eating all of your resources, we should be able to figure it out.

---

### Post by Gatemaze on 2011-10-21
Which version of eclipse are you running? I had major issues over the last few months of the cycle of helios, memory issues... I updated to indigo and seems to be working fine... This is c++ eclipse with pydev and egit packages min install...

---

### Post by techvish81 on 2011-10-21
just do a fresh install of 11.10 and everything will be fine, upgrade is buggy coz it is gtk2 to gtk3 which is very complicated. 
see threads are filled with problems after upgrade, a fresh install will really solve most of your problems, unity is far more improved in 11.10 than it was before, so don't think of going back, it is really polished version of 11.04., u will not regret spending time for backing up your data and doing a fresh install.

---

### Post by niranjan_rao on 2011-10-21
htop running on other terminal as suggested. Will keep posted about the results.

I also have been scratching my head about the problem especially when I never faced any problems while using 11.04. I have 16G ram on this box and memory usage is usually somewhere in the range of 2.6 gb usually. Performance was never a problem for this machine until I upgraded 11.10

On my home machines, I can understand display drivers not waking up correctly after sleeping. It's annoyance, but not a show stopper since I found that I can ignore initially garbled screen and just enter my password and things will be mostly as usual again

Thanks

---

### Post by niranjan_rao on 2011-10-21
@techvish81

I will try to do fresh install, but was hoping to avoid entertainment of reinstalling all the stuff I have collected over the years. Given that I have lots of ram, do you think 64bit will better?

Already, ubuntu upgrade broke somethings that I was dependent upon - e.g. gpass. Granted there are alternatives, but had to struggle first open my encrypted file first with different tool etc.

Thanks,

---

### Post by linuxinstalledfromhdd on 2011-10-21
Whatever you do, don't use 11.10.. I'm having issue where I have never seen them before.  This is way to radical. I can't even change my user after the latest round of updates today. I can't get a confirmation from anyone else here..   I'm going to go to Debian in a minute.

---

### Post by techvish81 on 2011-10-21
yup , i am using 64 bit without any problem since day 1 after the  release , some minor glitches which were sorted out in a week's updates , now its  running better than any os i've tried till date . my specs are - core i3 , 4 gb ram, 500gb sata hdd

---

### Post by linuxinstalledfromhdd on 2011-10-21
Have you updated it today?  Update it today and see if you can still open "User Accounts"?????   Please confirm..

---

### Post by niranjan_rao on 2011-10-22
Ok, was able reproduce it again. Mind you this machine does not have latest updates for 11.10 - which were installed after this incidence and a reboot.

Looks like compiz is extremely busy after coming out of suspension/hibernaion. On my home machine it was hogging all the cpu cyles (99%). This does not happen when machine is rebooted

---

### Post by vasa1 on 2011-10-22
> **linuxinstalledfromhdd said:**
> Whatever you do, don't use 11.10.. I'm having issue where I have never seen them before.  This is way to radical. I can't even change my user after the latest round of updates today. **I can't get a confirmation from anyone else here**..   I'm going to go to Debian in a minute.

I upgraded from 11.04 11.10 already and am not seeing any problems. I look for updates several times a day and accept them whenever they are offered.

---

### Post by masgeeks on 2011-10-22
I'm sure no one wants to hear this, but a clean install is the only way to go - and its not painful and really doesn't take that much longer

I look at it as an opportunity to do house a little house keeping...!!!

Did my primary workstation last weekend and the most painful part of the clean install was offloading 350 GB of data before I could wipe the drives clean, and then copying it back afterwards, lol...

---

### Post by niranjan_rao on 2011-10-22
Doing clean install and re-installing everything twice in a year if you want to stay up to date. Doesn't life gets tedious if you do that.

I can see the value of clean install, it will clean my machine if nothing else. But recreating all the cron jobs, downloading everything that you need again can be really painful.

Interestingly enough, latest problems seem to have solved some of my problems. My machine is actually usable today after last sleep/suspend cycle. Will try it for some more days using the time to ensure I have proper backups before doing the clean install.

---

### Post by cryptotheslow on 2011-10-22
Clean install is not particularly arduous if you have /home in a separate partition. Might just need to back up some service configs from /etc as well.

Then again - why give yourself the headache of jumping on board every single new release anyway? If you are after a stable environment that just keeps working, stick with the LTS releases.

10.04 LTS (Desktop) will be supported until April 2013.
12.04 LTS (Desktop) will release April 2012 and comes with the longer 5 year support until April 2017!

---

### Post by marty331 on 2011-10-24
Hey guys I'm running an i5 processor, 6 gb RAM and 750 GB harddrive.  Computer is only a month old and I had 11.04 on it first, it ran great.  I did a fresh install to 11.10 when it came out and I get 'bogged' down all the time.  The main things that seem to have issues are Eclipse 3.7 and Banshee, oh and Firefox (less than 5 tabs open).  I don't have any idea what I can do to resolve this.  

I am open to suggestions at this point.  And yes I have htop installed.

---


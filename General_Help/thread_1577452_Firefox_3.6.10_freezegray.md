---
title: "Firefox 3.6.10 freeze/gray"
date: 2010-09-18
forum: General Help
---

### Post by bigsmitty64 on 2010-09-18
First things first: 
Ubuntu 10.04 32 bit, 2 gigs ram, Firefox 3.6.10

I looked around here and only found some, "it could be this or that" type answers from a year or 2 ago, so here's my question.

 Does anyone have a definite answer yet, as to why firefox randomly freezes up/turns gray and doesn't respond? It seems to be more like after I've had it open for a good length of time. And seemingly when I use the auto scroll. Any help is greatly appreciated! Thanks
Smitty

---

### Post by bigsmitty64 on 2010-09-19
Quick update, I have noticed that when watching a youtube video, my cpu usage goes up over 85% closer to 90%.

---

### Post by bigsmitty64 on 2010-09-19
bumpity

---

### Post by bigsmitty64 on 2010-09-21
no one?

---

### Post by donut123 on 2010-09-21
> **bigsmitty64 said:**
> no one?
Hello....first open Firefox extentions.

Have you tried :

UN Install the Ubuntu firefox modifications from the add ons of firefox, was a suggestion followed with reboot.
By default Firefox puts its cache in your home partition.You can speed  up Firefox and reduce disk writes by moving this cache into RAM if you  have 1GB RAM or more.

1.Edit /etc/fstab,open terminal from Applications->Accessories menu and type:

    Code:sudo gedit /etc/fstab



Add following into this file and close it.

    tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
    tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0

2.Edit /etc/sysctl.conf:

   Code: sudo gedit /etc/sysctl.conf



add this line and save it:

    vm.swappiness=1

3.
Type  about:config in firefox address bar and click I'll be careful,I  promise!.Right click on blank area and create a new string value called  browser.cache.disk.parent_directory,set its value to /tmp

Now,reboot your system and experience the performance. [IMG]http://www.ultimateeditionoz.com/forum/images/smilies/grin.png[/IMG]

---

### Post by bigsmitty64 on 2010-09-21
Thanks so much for your help. I'll give that a shot and get back in a bit!

---

### Post by donut123 on 2010-09-21
> **bigsmitty64 said:**
> Thanks so much for your help. I'll give that a shot and get back in a bit!
No problem...take all the time you want
[CENTER][COLOR=Purple]-Version- GheTTo

Kernel    : Linux 2.6.31-20-generic (x86_64) 


Default C Compiler    : GNU C Compiler version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) 
Distribution        :Ultimate Edition Ubuntu
Desktop Environment        : GNOME 2.28.1 [/COLOR][CENTER][COLOR=#0040ff]

Ultimate Edition [/COLOR]

[IMG]http://i245.photobucket.com/albums/gg60/Donut_123/Untitled1a.gif[/IMG]



[IMG]http://i245.photobucket.com/albums/gg60/Donut_123/Button-GNOME.png[/IMG]

[IMG]http://i245.photobucket.com/albums/gg60/Donut_123/opera-1.png[/IMG]
[IMG]http://i245.photobucket.com/albums/gg60/Donut_123/flame5.gif[/IMG]

[IMG]http://i245.photobucket.com/albums/gg60/Donut_123/35551.gif[/IMG]
[IMG]http://i245.photobucket.com/albums/gg60/Donut_123/uetheghetto-1.png[/IMG]
[[IMG]http://i245.photobucket.com/albums/gg60/Donut_123/coollogo_com-287193348.png?t=1283266398[/IMG]]("http://my.opera.com/Donut123/blog/")[/CENTER]
[/CENTER]

---

### Post by bigsmitty64 on 2010-09-22
Thank you very much for that info! Worked like a charm so far. No freeze ups all day today!

---

### Post by petrasflorin on 2010-09-22
sudo apt-get install googlechrome

---

### Post by donut123 on 2010-09-22
> **bigsmitty64 said:**
> Thank you very much for that info! Worked like a charm so far. No freeze ups all day today!
good Im glad...i hope it works out all the time!
There is one more thing.
Synaptic..."remove" and then reinstall...
just another option.:mad:

---

### Post by donut123 on 2010-09-22
> **petrasflorin said:**
> sudo apt-get install googlechrome
Yes Google chrome is fast...very fast..
it is an option...
I use Chromium also...and Firefox.
All are options.
Thank you:)

---

### Post by bigsmitty64 on 2010-09-22
> **petrasflorin said:**
> sudo apt-get install googlechrome
Not a fan of chrome.More because of the looks than anything else really. Anywho its sorted now. Thanks for the reply though!

---

### Post by bigsmitty64 on 2010-09-22
> **donut123 said:**
> good Im glad...i hope it works out all the time!
There is one more thing.
Synaptic..."remove" and then reinstall...
just another option.:mad:

day 2, no issues! woohoo!

---

### Post by bigsmitty64 on 2010-09-23
Looks like I spoke too soon! :(  It froze up on youtube just a few mins ago. Same as last time, gray, autoscroll takes over and goes way slow.
I went to synaptic and marked firefox for complete removal, removed it and reinstalled. I haven't seen it repeat yet, BUT I noticed that when I reinstalled firefox, all my settings were still there, bookmarks and all. This tells me I need a more thorough way to uninstall firefox?

---

### Post by donut123 on 2010-09-26
> **bigsmitty64 said:**
> Looks like I spoke too soon! :(  It froze up on youtube just a few mins ago. Same as last time, gray, autoscroll takes over and goes way slow.
I went to synaptic and marked firefox for complete removal, removed it and reinstalled. I haven't seen it repeat yet, BUT I noticed that when I reinstalled firefox, all my settings were still there, bookmarks and all. This tells me I need a more thorough way to uninstall firefox?
Do you have Ubuntu Tweak?
And may want to take it off auto scroll.

---

### Post by bigsmitty64 on 2010-09-27
I do have Ubuntu Tweak, and I really use auto scroll alot. I'd rather not discard it just yet.

---

### Post by donut123 on 2010-09-27
> **bigsmitty64 said:**
> I do have Ubuntu Tweak, and I really use auto scroll alot. I'd rather not discard it just yet.
What are your settings on Ubuntu tweak? 
Do you clean the cache...how is Firefox running now?

---

### Post by Handssolow on 2010-09-27
I assume you are aware of the thread below. My first post comes in at number 1051. Probably there are several different causes for these freezes though I suspect that one issue is the cause of the majority. 

[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

I played a DVD this morning for a couple of hours without a problem. Freezes here only seems to happen when Firefox is open but this may be co-incidental as this is one of the most frequently used programs.

Edit: Still no freezes today and I've been doing my best to provoke one. I expect when my son gets in things will change. Incidentally I've just upgraded to 2.6.32-25-generic a few minutes ago.

---

### Post by donut123 on 2010-09-27
> **Handssolow said:**
> I assume you are aware of the thread below. My first post comes in at number 1051. Probably there are several different causes for these freezes though I suspect that one issue is the cause of the majority. 

[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

I played a DVD this morning for a couple of hours without a problem. Freezes here only seems to happen when Firefox is open but this may be co-incidental as this is one of the most frequently used programs.

Edit: Still no freezes today and I've been doing my best to provoke one. I expect when my son gets in things will change. Incidentally I've just upgraded to 2.6.32-25-generic a few minutes ago.
I didnt know about it...I am running Ultimate Edition...it works great. My firefox hangs once in a while. I usually have no problems unless I cause it myself.

---

### Post by donut123 on 2010-09-28
[CENTER]Here is  a link to Firefox.................................................................................
[http://support.mozilla.com/en-US/search?locale=en-US&q=firefox+freezes&sa=](http://support.mozilla.com/en-US/search?locale=en-US&q=firefox+freezes&sa=)




                                                                                                                 [[IMG]http://i245.photobucket.com/albums/gg60/Donut_123/coollogo_com-287193348.png?t=1283266398[/IMG]]("http://my.opera.com/Donut123/blog/")[/CENTER]

---

### Post by bigsmitty64 on 2010-09-28
> **donut123 said:**
> What are your settings on Ubuntu tweak? 
Do you clean the cache...how is Firefox running now?
First off, thanks for sticking around with me on this!

I may sound dumb here, but I see no settings in Ubuntu Tweak for firefox? 

And yes, I run a pretty tight ship in firefox. I run in private browse mode, frequently clean the cache, and have no more than 45 bookmarks. I rarely have more than a couple tabs open at once. YET this still persists. :(  

I will definately look into the links provided by yourself and [B]Handssolow.

[/B]Thanks again for your help.Smitty

---

### Post by donut123 on 2010-09-28
> **bigsmitty64 said:**
> First off, thanks for sticking around with me on this!

I may sound dumb here, but I see no settings in Ubuntu Tweak for firefox? 

And yes, I run a pretty tight ship in firefox. I run in private browse mode, frequently clean the cache, and have no more than 45 bookmarks. I rarely have more than a couple tabs open at once. YET this still persists. :(  

I will definately look into the links provided by yourself and [B]Handssolow.

[/B]Thanks again for your help.Smitty
You can try to enable Ubuntu Firefox Modifications again...
some things work weired like that.
And  the attach. is what you need to check in Tweak
the ones I have checked.

---

### Post by Handssolow on 2010-09-28
Ubuntu Tweaks? Wouldn't that be in Firefox Tools>Add-ons>Ubuntu Firefox Modifications?

Here with a Freeze the first observable change is the screen dims and goes a grey hue but a web page is still readable. For a few seconds an Ubuntu toolbar box can be opened with the mouse, soon this is unavailable. From my memory, the mouse pointer can be moved around the screen but not do much else. As I posted in the other thread, booting with pci=noacpi has reduced the number of freezes considerably yet retains some of the useful acpi functionality.

I've visual effects turned off. System>Preferences>Appearance>Visual Effects
Power Manager is also disabled which is convenient because this is a desktop PC not a laptop on battery power. System>Preferences>Startup Applications

I've now included the Force Quit in the top toolbar so if I get another freeze I might have a chance to zap Firefox and see if that helps. Having System Monitor>Resources loaded might also give useful information if I can open the window in the few seconds before a complete lockup.

---

### Post by donut123 on 2010-09-28
> **Handssolow said:**
> Ubuntu Tweaks? Wouldn't that be in Firefox Tools>Add-ons>Ubuntu Firefox Modifications?

Here with a Freeze the first observable change is the screen dims and goes a grey hue but a web page is still readable. For a few seconds an Ubuntu toolbar box can be opened with the mouse, soon this is unavailable. From my memory, the mouse pointer can be moved around the screen but not do much else. As I posted in the other thread, booting with pci=noacpi has reduced the number of freezes considerably yet retains some of the useful acpi functionality.

I've visual effects turned off. System>Preferences>Appearance>Visual Effects
Power Manager is also disabled which is convenient because this is a desktop PC not a laptop on battery power. System>Preferences>Startup Applications

I've now included the Force Quit in the top toolbar so if I get another freeze I might have a chance to zap Firefox and see if that helps. Having System Monitor>Resources loaded might also give useful information if I can open the window if the few seconds before a complete lockup.
Ubuntu Tweak is in Applications> system tools.
Ubuntu.  tweak.I also found this.............
[http://ubuntuforums.org/showthread.php?t=1580394...in](http://ubuntuforums.org/showthread.php?t=1580394...in) the forum. Go and check it out.

---

### Post by bigsmitty64 on 2010-09-28
@**Handssolow**

**Ubuntu Tweak is a program on its own**.

Here with a Freeze the first observable change is the screen dims and  goes a grey hue but a web page is still readable
**Exactly what I'm experiencing**,** like if I use auto scroll to go  towards the TOP of a page, the freeze takes over UNTIL it gets to the  top of the page, then it comes out of it.**
 Force Quit   System Monitor
**I was going to use the force quit but noticed that when this happens I have no control over anything, panels included! :(**
**And with system monitor going it just shows an increase of cpu usage, like between 80 to 99**%

---

### Post by bigsmitty64 on 2010-09-28
Ya know, MeerKat is only days away :P  I really wanna figure this out though, so as to help others in the future. I have checked out the links you have provided and to no avail. Including the one supplied by lovinglinux in the other thread. I made the changes in "tweak" so Ill restart Firefox now and give it a shot for a while, I'll be back! Thanks guys.

---

### Post by Handssolow on 2010-09-30
The PC froze yesterday within a minute after login and before Firefox had been opened. Conclusion Firefox isn't the problem here.

After a hard reset there were no further freezes during the session lasting over 2 hours.

---

### Post by donut123 on 2010-10-01
> **Handssolow said:**
> The PC froze yesterday within a minute after login and before Firefox had been opened. Conclusion Firefox isn't the problem here.

After a hard reset there were no further freezes during the session lasting over 2 hours.
Good Im happy to hear that....I hope it works ok now.:)

---

### Post by donut123 on 2010-10-01
I guess the Administarors can decide if this issue is solved or not. I jus help ones...I dont solve anything ...:)

---

### Post by bigsmitty64 on 2010-10-02
After realizing that when mine goes into gray/freeze mode, it affects everything, not just firefox, I swapped out my **ram** with some spare ram my room mate had. Same amount, (2gig) same type, just different brand names. **3 days no issues**. Could it be? Ram issue?
It certainly is appearing that way at the moment.

---

### Post by Handssolow on 2010-10-02
> **donut123 said:**
> Good Im happy to hear that....I hope it works ok now.:)

The problem hasn't gone away, it's just that it seems that here Firefox isn't the cause of the problem. It looks like I've got some ACPI related memory conflicts appearing in the log which I've refereed to in this thread-

[http://ubuntuforums.org/showthread.php?t=1478787&page=110](http://ubuntuforums.org/showthread.php?t=1478787&page=110)

I'm not sure if these conflicts are important and if so what I could do about it. I am using 1.5Gb of DDR 333 with 2 slots of 512Mb and 2 of 256Mb. I think they're all from Crucial. Memory tests lasting a couple of hours didn't show one error so I think the hardware is OK.

These freezes seem to be much more an issue with Lucid. Several have reported getting back to a stable system by reverting to an earlier version of Ubuntu, Heron for example. This may have to be the solution here. Only when I'm confident that I've seen the end these freezes can we use our new PC for something more than just browsing and simple stuff.

---

### Post by donut123 on 2010-10-03
> **handssolow said:**
> the problem hasn't gone away, it's just that it seems that here firefox isn't the cause of the problem. It looks like i've got some acpi related memory conflicts appearing in the log which i've refereed to in this thread-

[http://ubuntuforums.org/showthread.php?t=1478787&page=110](http://ubuntuforums.org/showthread.php?t=1478787&page=110)

i'm not sure if these conflicts are important and if so what i could do about it. I am using 1.5gb of ddr 333 with 2 slots of 512mb and 2 of 256mb. I think they're all from crucial. Memory tests lasting a couple of hours didn't show one error so i think the hardware is ok.

These freezes seem to be much more an issue with lucid. Several have reported getting back to a stable system by reverting to an earlier version of ubuntu, heron for example. This may have to be the solution here. Only when i'm confident that i've seen the end these freezes can we use our new pc for something more than just browsing and simple stuff.
wow !

---

### Post by bigsmitty64 on 2010-10-03
Well, as I stated before, I swapped out my ram with my room mates extra ram, and had no issues for 4+ days. However, I've since moved on to Maverick, (fresh install) also with the new ram and no issues. I think honestly my issue was the ram. I am going to put my old ram back in now that I'm running 10.10 and see what happens.

---

### Post by donut123 on 2010-10-05
> **bigsmitty64 said:**
> Well, as I stated before, I swapped out my ram with my room mates extra ram, and had no issues for 4+ days. However, I've since moved on to Maverick, (fresh install) also with the new ram and no issues. I think honestly my issue was the ram. I am going to put my old ram back in now that I'm running 10.10 and see what happens.
hey Smitty..hows it going now? Is everything resolved?:mad:

---

### Post by cg0191 on 2010-10-06
> **bigsmitty64 said:**
> Well, as I stated before, I swapped out my ram with my room mates extra ram, and had no issues for 4+ days. However, I've since moved on to Maverick, (fresh install) also with the new ram and no issues. I think honestly my issue was the ram. I am going to put my old ram back in now that I'm running 10.10 and see what happens.
I have this same problem with FF 3.6.10 on Ubuntu 10.10 RC (x64) & Pinguy OS (x64).
Will try 10.10 i386.
I had NO problems with FF 4.xb.
I think its flash related in FF 3.6.x but I could be wrong.

---

### Post by bigsmitty64 on 2010-10-06
> **donut123 said:**
> hey Smitty..hows it going now? Is everything resolved?:mad:
I guess it is for me, but I still don't know what the problem ***was*** really. I'll leave this thread unsolved for a few more days and see if anyone else has any ideas? Thanks again..

---

### Post by mariette99 on 2010-10-07
I have the same problems as bigsmitty. Firefox freezes and grays. And I get the message "This is embarressing but Firefox is unable to..." 
I have tried to reinstall, remove (with --purge) and I even did some manual deleting things. But when I reinstall after cleaning I get the same message and the screen freezes. Any suggestions?

---

### Post by donut123 on 2010-10-07
> **mariette99 said:**
> I have the same problems as bigsmitty. Firefox freezes and grays. And I get the message "This is embarressing but Firefox is unable to..." 
I have tried to reinstall, remove (with --purge) and I even did some manual deleting things. But when I reinstall after cleaning I get the same message and the screen freezes. Any suggestions?
yes its your Ram....there are some suggestions
By default Firefox puts its cache in your home partition.You can speed  up Firefox and reduce disk writes by moving this cache into RAM if you  have 1GB RAM or more.

1.Edit /etc/fstab,open terminal from Applications->Accessories menu and type:

    Code:sudo gedit /etc/fstab



Add following into this file and close it.

    Code:tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
    tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0



2.Edit /etc/sysctl.conf:

   Code: sudo gedit /etc/sysctl.conf



add this line and save it:

  Code:  vm.swappiness=1



3.
Type Code:about:config

  in firefox address bar and click I'll be careful,I promise!.Right click  on blank area and create a new string value called  browser.cache.disk.parent_directory,set its value to /tmp

Now,reboot your system and experience the performance. [IMG]http://www.ultimateeditionoz.com/forum/images/smilies/grin.png[/IMG]
---------------------------------------------------------------------------------------
 Code:sudo gedit /etc/fstab

    tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
    tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0

2.Edit /etc/sysctl.conf:

   Code: sudo gedit /etc/sysctl.conf



add this line and save it:

    vm.swappiness=1
------------------------------------------------------------------------------------------------------------------------------------------------------------
OR go here
 
[http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html](http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html)

---

### Post by bigsmitty64 on 2010-10-11
Well, it rears its ugly head again!. With Maverick and the new ram so..........

---

### Post by donut123 on 2010-10-11
WOW I`m not sure Smitty...I wish I could solve your problem..I`m sorry.

---

### Post by macem29 on 2010-10-12
> **donut123 said:**
> yes its your Ram....there are some suggestions
By default Firefox puts its cache in your home partition.You can speed  up Firefox and reduce disk writes by moving this cache into RAM if you  have 1GB RAM or more.

1.Edit /etc/fstab,open terminal from Applications->Accessories menu and type:

    Code:sudo gedit /etc/fstab



Add following into this file and close it.

    [COLOR=Red]Code:tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
    tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0[/COLOR]



2.Edit /etc/sysctl.conf:

   Code: sudo gedit /etc/sysctl.conf



add this line and save it:

  Code: [COLOR=Red] vm.swappiness=1[/COLOR]



3.
Type Code:about:config

  in firefox address bar and click I'll be careful,I promise!.Right click  on blank area and create a new string value called  browser.cache.disk.parent_directory,set its value to /tmp

Now,reboot your system and experience the performance. [IMG]http://www.ultimateeditionoz.com/forum/images/smilies/grin.png[/IMG]
---------------------------------------------------------------------------------------
 Code:sudo gedit /etc/fstab

    tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
    tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0

2.Edit /etc/sysctl.conf:

   Code: sudo gedit /etc/sysctl.conf



add this line and save it:

    vm.swappiness=1
------------------------------------------------------------------------------------------------------------------------------------------------------------
OR go here
 
[http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html](http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html)

thanks for this, one question, prolly a stupid one: the lines I've changed to red,
should they be commented with # when adding? thanks....

---

### Post by donut123 on 2010-10-12
> **macem29 said:**
> thanks for this, one question, prolly a stupid one: the lines I've changed to red,
should they be commented with # when adding? thanks....
sorry...i will make them red if I ever return to this forum ..thank you.

---

### Post by jvhellraiser on 2010-10-12
install chromium web browser:

sudo apt-get install chromium-browser

to make load faster that if your are having problem
open the chromium browser and go to options,under the hood
and uncheck:

use DNS pre-fetching to improve page load performance and close it.

---

### Post by macem29 on 2010-10-12
> **donut123 said:**
> sorry...i will make them red if I ever return to this forum ..thank you.


hmmm, okay...thinking you took that the wrong way....I made them red to point out what in the
quote I was referring to....my question was whether to comment the added lines with a "#" prefix
as most lines in the files appeared to be, or just add them as per your instructions, sorry if I
insulted you man

and I've tried chromium and don't like it, used FF for years and never had any issues until recently

---

### Post by donut123 on 2010-10-13
> **macem29 said:**
> hmmm, okay...thinking you took that the wrong way....I made them red to point out what in the
quote I was referring to....my question was whether to comment the added lines with a "#" prefix
as most lines in the files appeared to be, or just add them as per your instructions, sorry if I
insulted you man

and I've tried chromium and don't like it, used FF for years and never had any issues until recently
No imnot insulted...I just do not trust any one..now that I know ones can come in my account I dont know what to think. 
If you can go on my account..who knows what ones can do on here.
Ones will say I am rude and take things the wrong way...I dont like someone doing things to my posts...you can easily change my wording and make it cursing out people..that is why.

---

### Post by macem29 on 2010-10-15
ok, sounds like something happened in another thread to cause this communication error, hope it gets sorted out


edit: and back on topic, I killed flash and all desktop visual effects and the graying out in FF is almost non-existent now

---

### Post by kkady32 on 2010-10-17
i have the same problem in the last 2 days,and i erase with bleachbit all from firefox,inclusiv bookmarkstab and now my problem is solved.

---

### Post by macem29 on 2010-10-17
> **kkady32 said:**
> i have the same problem in the last 2 days,and i erase with bleachbit all from firefox,inclusiv bookmarkstab and now my problem is solved.


installed bleachbit, the system froze and screen grayed out running the software centre...:confused:

XP on this netbook took over a year to become this useless, happened in 2 months with 10.04

---

### Post by kkady32 on 2010-10-20
to me was problem ,i would use ubuntu one sync for bookmarks from firefox,and this install automatic an addon named bindwood 
in the last days i started firefox and see that the led from hdd is red and i cannot use firefox because this freeze and sometimes block all X and i must go in tty console to kill firefox.

---

### Post by qopi on 2011-03-20
I have a similar problem. Every now and then Firefox just freezes up and grays out.

I don't remember it ever happening before upgrading to 10.10

I've got:
Samsung NC10 netbook 
2GB RAM
Ubuntu 10.10 
Firefox 3.6.15

Would love to know what is causing it. Sounds like perhaps its RAM or some other member issue...

Josef.

---

### Post by qopi on 2011-03-20
> **qopi said:**
> 
Would love to know what is causing it. Sounds like perhaps its RAM or some other member issue...



Er memory, not member.

I just did a memtest, all clear.

---


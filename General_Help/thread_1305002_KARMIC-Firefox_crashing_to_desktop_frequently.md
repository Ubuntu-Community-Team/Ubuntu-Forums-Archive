---
title: "KARMIC-Firefox crashing to desktop frequently"
date: 2009-10-29
forum: General Help
---

### Post by emarkay on 2009-10-29
This is new and strange - I get the "recover" option sometimes and otherwise I reload FF  and was just there before.

I can start debugging, but this is new with Karmic, and only in the last few updates (a few days).  Is anyone else experiencing this?

---

### Post by lovinglinux on 2009-10-29
Are you using a clean Firefox profile or the same one you were using in Jaunty?

Anyway, I'm experiencing some crashes recently too.

---

### Post by emarkay on 2009-10-29
Think think think - it must be a new one, I am sure of it, because this is a clean, reformatted install of Karmic!

---

### Post by lovinglinux on 2009-10-29
> **emarkay said:**
> Think think think - it must be a new one, I am sure of it, because this is a clean, reformatted install of Karmic!

If you have a separate home partition, then no.

---

### Post by slumbergod on 2009-10-29
I am having FF issues in karmic too. Mostly, periodic hangs - sometimes crashing, sometimes requiring me to kill it. 

I've notice the cpu spiking too so I suspect there is something wrong with the flash plugin (again). 

I have a clean install so I can rule out corrupt profiles.

---

### Post by lovinglinux on 2009-10-30
> **slumbergod said:**
> I am having FF issues in karmic too. Mostly, periodic hangs - sometimes crashing, sometimes requiring me to kill it. 

I've notice the cpu spiking too so I suspect there is something wrong with the flash plugin (again). 

I have a clean install so I can rule out corrupt profiles.

I don't have a clean profile, but mine is well maintained. I just had another crash while browsing ubuntuforums.org only. So I guess is not flash.

---

### Post by slumbergod on 2009-10-30
Something is definitely not right with Firefox. I've had to kill it once already this morning. The process jumped to 50% of my CPU and becomes unresponsive. That was just reading a news page (noscript and adblock filtered).

---

### Post by slumbergod on 2009-10-30
I upgraded to the mozilla testing version of FF3.5.4 and downloaded flash directly from Adobe Labs. Haven't had any lock-ups yet and it actually feels more responsive. I'll update my response in a day or so as to whether I am successful or not.

[EDIT] don't need to wait a couple of days cos FF 3.5.4 is still locking up. The screen goes all jerky and the app hangs. CPU on 47% for process. So, it's happening with both 3.5.3 and 3.5.4 and with both the repo non-free flash and the Adobe flash deb.

---

### Post by jordandcarter on 2009-10-31
Yeah me too, crashing.

Have 64 adobe flash plugin.  Firebug and yslow.  Fresh install of Karmic.

Seems to happen when I'm checking my gmail emails.

---

### Post by robinparriath on 2009-10-31
Same here... but in my case, Karmic stops responding completely.  Had to reboot twice due to it...
Its a fresh install too
Seems to happen when loading any web page... and after a lot of time (and I mean a lot), responds

---

### Post by emarkay on 2009-10-31
> **lovinglinux said:**
> If you have a separate home partition, then no.

Nope, "home" is on the same partition and installed in teh default location.

It's not Flash, (I loathe Flash) I have both NoScript and Flashblock and they are both operating normally - I am getting no FF errors.

---

### Post by NCLI on 2009-10-31
Try doing alt+F2, then run the command "firefox -ProfileManager"

This should allow you to create a new profile. Does it still crash?

---

### Post by lovinglinux on 2009-10-31
I can confirm flash crashing. Test the link below and tell me if crashes for you too. 

[http://www.myjoomlaplace.com/new-gallery-demo.html](http://www.myjoomlaplace.com/new-gallery-demo.html)

It's a joomla flash gallery demo site. It crashes 100% of the time.

---

### Post by robinparriath on 2009-11-01
Installed a few updates since yesterday.  Didn't read the descriptions but some of them were related to firefox and xulrunner.

No more crashes since yesterday:D
I'll be watchful though.

---

### Post by robinparriath on 2009-11-01
> **lovinglinux said:**
> Test the link below and tell me if crashes for you too.

Nope.  Not crashing...yet :D

---

### Post by emarkay on 2009-11-01
> **NCLI said:**
> Try doing alt+F2, then run the command "firefox -ProfileManager"
This should allow you to create a new profile. Does it still crash?
I did this, completely restarted and reapplied all add ons and teh like and did see a crash once - will see if that was just a fluke today.

---

### Post by emarkay on 2009-11-01
> **lovinglinux said:**
> I can confirm flash crashing. Test the link below and tell me if crashes for you too. 
[http://www.myjoomlaplace.com/new-gallery-demo.html](http://www.myjoomlaplace.com/new-gallery-demo.html)
It's a joomla flash gallery demo site. It crashes 100% of the time.

I had a crash when I reloaded the page.  Will recreate profile and find out if it still does.

---

### Post by lovinglinux on 2009-11-01
> **emarkay said:**
> I had a crash when I reloaded the page.  Will recreate profile and find out if it still does.

I did that. It doesn't crash with a new profile, but flash flickers a lot in that page.

---

### Post by slumbergod on 2009-11-01
I rolled back to the default FF from synaptic because the problem still existed with the testing version I tried.

This time I tried creating a new profile, just on the off-chance that my brand new default profile was corrupted. 

And it made no difference...just experienced another lock-up with cpu spike requiring a forced killing of the process. 

How the /&/&/&%&/$%%$& can FF work so well in Jaunty with all the latest updates (including the 2.6.31 kernel which I had upgraded manually as well as the latest Intel drivers) then be so hopeless in Karmic. Surely, this was tested??!!!

Can't wait til Chrome is out of testing. FF is starting to annoy me big time.

---

### Post by slumbergod on 2009-11-01
I rolled back to the default FF from synaptic because the problem still existed with the testing version I tried.

This time I tried creating a new profile, just on the off-chance that my brand new default profile was corrupted. 

And it made no difference...just experienced another lock-up with cpu spike requiring a forced killing of the process. 

How the /&/&/&%&/$%%$& can FF work so well in Jaunty with all the latest updates (including the 2.6.31 kernel which I had upgraded manually as well as the latest Intel drivers) then be so hopeless in Karmic. Surely, this was tested??!!!

Can't wait til Chrome is out of testing. FF is starting to annoy me big time.

---

### Post by kvmapr on 2009-11-01
I'll add a me too on this one. I can't even get FF launched before it spikes my CPU and locks up the desktop. Finally uninstalled FF and loaded the Midori browser, which was enough to get me here, where I learned I'm in good company.

Crashes actually seemed to get worse after applying the new upgrades available a couple days ago.

Come on Canonical. What's up with this? Everyone's go-to app is bringing down the house, are you on it yet?

Wish I'd stuck with jaunty.

---

### Post by jhb1608 on 2009-11-01
I have the same problems liek you do. I wish the same!

---

### Post by emarkay on 2009-11-02
Hey, we need some help here... :)

---

### Post by robinparriath on 2009-11-02
Hey everyone,

My issues with firefox crashing are over.  I had problems with a fresh install and the only plugin I've added to firefox is the Adobe swf plugin.

From the number of bug reports on launchpad, it looks many people are having this issue.

Since my issues with the crash have stopped, is there any way in which info about my system configuration can help?  If anyone knows how to get the info, please let me know.

---

### Post by lovinglinux on 2009-11-02
> **kvmapr said:**
> I'll add a me too on this one. I can't even get FF launched before it spikes my CPU and locks up the desktop. Finally uninstalled FF and loaded the Midori browser, which was enough to get me here, where I learned I'm in good company.

See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by kvmapr on 2009-11-02
> **lovinglinux said:**
> See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Cool, thanks.

---

### Post by HalfEmptyHero on 2009-11-03
I'm having the same crashes, happens every time I go to the youtube main page (but not if i go directly to url of a video) and also when I am checking my gmail unless I use html version. Also happens randomly on other sites too.

---

### Post by skylark on 2009-11-03
If you suspect it is flash bringing down firefox then installing something like [**_the Flashblock add-on_**]("https://addons.mozilla.org/en-US/firefox/addon/433") should help. This replaces flash animations with a play button (i.e. it lets you get choose exactly what flash content gets launched).

---

### Post by Nyas on 2009-11-03
Not sure if this is the right thread but my Firefox is pretty messed up too. The only consistent bug seems to be flash videos crashing if I try to go full-screen.
Then there are is some text disappearing in context menus, random font sizes unmanageable by settings, slow loading of an add-on dictionary...

I am not sure where to start, so I think I will just wait for patches and updates. If something persists, then I might look for solutions myself.

<rant>
I find this very ironic since Firefox was the most stable and beautiful piece of software I have been using for many years on Windows. I knew nothing about Ubuntu but all the things relevant to me are working almost perfectly now. Yet the *default* Firefox is the only one causing tons of issues...

Did anybody even try to play a YouTube video before releasing this? Or do a Google search and see how the fonts look like?
</rant>

---

### Post by Jerry N on 2009-11-03
I have been having hangup/crash problems with FF version 3.5.x in Windows too, particularly on downloads.  Actually it doesn't appear to crash unless I start "pounding" on it (pushing keys, mouse buttons, etc) so maybe if I were patient it might catch up and recover.  The fact that FF is up to version 3.5.4 already is probably a clue.

Jerry

---

### Post by flammon on 2009-11-03
Me too. Firefox crashes at least once per day, usually when multiple pages are loading in multiple tabs and I'm switching between the tabs.

---

### Post by HalfEmptyHero on 2009-11-03
After I uninstalled x64 flash plugin and installed flashplugin-nonfree instead I havent been crashing.

---

### Post by emarkay on 2009-11-08
Solved by grabbing 3.6 beta.

---

### Post by marwayusuf on 2009-11-09
> **robinparriath said:**
> Same here... but in my case, Karmic stops responding completely.  Had to reboot twice due to it...
Its a fresh install too
Seems to happen when loading any web page... and after a lot of time (and I mean a lot), responds

It happens to me too, when I try to view youtube videos or play any flash. It's a flash problem I think. It happens with firefox and chrome

---

### Post by grandtoubab on 2009-11-09
Use the standard Firefox
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-firefox-3.5.x-l10n/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-firefox-3.5.x-l10n/)

---

### Post by emarkay on 2009-11-10
> **grandtoubab said:**
> Use the standard Firefox
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-firefox-3.5.x-l10n/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-firefox-3.5.x-l10n/)


What do you mean by "Standard" ???
What is wrong with the Ubuntu Repo version.

Re-marked as  UN-Solved as I still see this in 3.5.x

---

### Post by emarkay on 2009-11-12
This is now also happening in 3.6.b2!

Bug report filed:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/481413](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/481413)

---

### Post by Gridwalker on 2009-11-13
> **jordandcarter said:**
> Yeah me too, crashing.

Have 64 adobe flash plugin.  Firebug and yslow.  Fresh install of Karmic.

Seems to happen when I'm checking my gmail emails.

Me too : I've just come here after the 3rd consecutive time that my FF crashed to desktop when trying to read my GMail.

---

### Post by emarkay on 2009-11-13
Well it also happened in "minefield" (3.7 alpha) so I will continue to address this.

---

### Post by emarkay on 2009-11-13
And I had a crash in "minefield" in safe mode...

"Add-ons: [email]ubufox@ubuntu.com[/email]:0.8,{972ce4c6-7e08-4474-a285-3208198ce6fd}:3.7a1pre
BuildID: 20091113031003
Comments: A safe mode crash in Alpha 3.7.....
CrashTime: 1258156202
EMCheckCompatibility: true
InstallTime: 1258152878
ProductName: Firefox
StartupTime: 1258156038
Theme: classic/1.0
Throttleable: 1
URL: [http://support.mozilla.com/en-US/kb/](http://support.mozilla.com/en-US/kb/)
Vendor: Mozilla
Version: 3.7a1pre

This report also contains technical information about the state of the application when it crashed."

OK, now what?

---

### Post by Infin1ty on 2009-11-16
It looks as it's java related only.
this is weird that opening a new profile fix it, but i need all my stuff with the current profile.
i've got all my settings, saved websies (in history) etc..
so now everytime firefox updates itself i will need to recreate a profile? sounds like not a good workaround for me and if canonical can't fix it then they shouldn't release it as a stable version.
just imagine to get like 100 calls from people complaining firefox crash after we upgraded our ubuntu desktops.

this is really starting to annoy..

---

### Post by emarkay on 2009-11-16
> **Infin1ty said:**
> It looks as it's java related only.
this is weird that opening a new profile fix it, but i need all my stuff with the current profile.
i've got all my settings, saved websies (in history) etc..
this is really starting to annoy..

Actually I got crashing it on a "Safe Mode" profile, too.  I reloaded the OS and am not using the Alpha or Beta at all.  Been a few hours and no crash yet.

---

### Post by DouglasAdams on 2009-11-17
> **slumbergod said:**
> I am having FF issues in karmic too. Mostly, periodic hangs - sometimes crashing, sometimes requiring me to kill it. 
I've notice the cpu spiking too so I suspect there is something wrong with the flash plugin (again). 
I have a clean install so I can rule out corrupt profiles.

i have all the problems, hang, crash, cpu spikes but i don't have flash player installed.
also, i'm completely new to ubuntu. i have previously used the same /home partition for sabayon 5.0 for a couple of weeks.

---

### Post by emaydubya on 2009-11-18
Been getting the freezing after clicking links.
Also addons would not update or add new ones until today for some reason. But could only update them one at a a time. Was same with new profile.

I get one error when starting FF from a terminal, no page loaded,blank page set to begin:

[PHP]*** e = [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/utilityOverlay.js :: getShellService :: line 312"  data: no][/PHP]

No idea. All the java plugins in "Manage Content Plugins" look the same

---

### Post by xtremo on 2009-11-18
Same for me too! Also tested Sea Monkey (same thing) and Opera.....which crashes but not as frequently as the others.

---

### Post by emarkay on 2009-11-23
Pardon my Latin and my COC agreement but "This is royally pissing me off!"  
WHAT IS GOING ON HERE???

---

### Post by morrisminiminor on 2009-11-23
Mine too. When I try to complete surveys, clicking on the next button works about half the time. The rest I have to exit and join the survey again. Listening to ITV player just shuts down FF immediately. Other applications seem to be OK. Almost re-naming Firefox to Fery Fustrating :)

morrisminiminor

---

### Post by DouglasAdams on 2009-11-24
> **DouglasAdams said:**
> i have all the problems, hang, crash, cpu spikes but i don't have flash player installed.
also, i'm completely new to ubuntu. i have previously used the same /home partition for sabayon 5.0 for a couple of weeks.
i've not had one, even slight, problem since i made my above post.
how about a new forum section, "solve your problems, have a good moan"?  ;)

---

### Post by inchkape on 2009-11-26
I've been experiencing the FF3.5/Flash crashing to. I had it in Ubuntu Karmic amd64, Karmic 32bit, then the same in Linux Mint RC1 32 bit.

I just changed to Galeon browser...MUCH less CPU being used, no crashes at all so far :D  I always liked Galeon.

---

### Post by inchkape on 2009-11-26
> **inchkape said:**
> I've been experiencing the FF3.5/Flash crashing to. I had it in Ubuntu Karmic amd64, Karmic 32bit, then the same in Linux Mint RC1 32 bit.

I just changed to Galeon browser...MUCH less CPU being used, no crashes at all so far :D  I always liked Galeon.

Further news: I take back what I said - it crashed

---

### Post by memo82 on 2009-11-29
My Firefox (and Chromium, and less frequently Opera) was randomly crashing to the Desktop every few minutes since the Karmic update. When I started Firefox from the Terminal, the output gave me a "Segmentation fault".
After hours and hours of disabling/enabling/uninstalling/reinstalling plugins and addons, I found this: [https://bugs.launchpad.net/firefox/+bug/477513](https://bugs.launchpad.net/firefox/+bug/477513) . Apparently, there is a conflict with the uim version in the official repositories. I installed the uim version from [https://launchpad.net/~micahg/+archive/ftbfs-test/](https://launchpad.net/~micahg/+archive/ftbfs-test/) yesterday and Firefox has been working fine since.
So if you have uim installed, definitely try this! It worked for me, although there was no apparent connection.

Hope this helps some of you!

---

### Post by DouglasAdams on 2009-11-29
my ff seems to have fixed itself ... unless it came in the koala 64 updates!
i know i've dun nowt lad.

---


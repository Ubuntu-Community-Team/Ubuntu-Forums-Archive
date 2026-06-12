---
title: "Thunderbird 3.0.4 - Ubuntu 10.04 - Lightning Extension?"
date: 2010-04-27
forum: General Help
---

### Post by Roasted on 2010-04-27
I downloaded the Lightning extension from the software center however when I open Thunderbird, it doesn't appear as if I have the calendar function. Any ideas? I had this same setup on 9.10. Not sure if I did anything wrong or what...

---

### Post by empty_spaces on 2010-04-27
I don't think the extension in the repositories (software center) works.
You have to download the extension separately and install it via Tools - Addons.
Are you 32 or 64 bit?

---

### Post by Roasted on 2010-04-27
Tried it through add-ons within thunderbird too. No dice. Gave me an error about the build type isn't right, which I'm assuming is because I'm on 64 bit.

Gah... back to Evolution I suppose. :/

---

### Post by empty_spaces on 2010-04-27
> **Roasted said:**
> Tried it through add-ons within thunderbird too. No dice. Gave me an error about the build type isn't right, which I'm assuming is because I'm on 64 bit.

Gah... back to Evolution I suppose. :/

Actually, you are being a little too quick in jumping to conclusions.

The reason I asked if you were 32 or 64 bit was just so that I could give you the link to the appropriate extensions for your architecture.

Click the following link to get the 64bit lightning extension. Make sure you select the latest date.
[http://www.secudb.de/~seuffert/mozilla/](http://www.secudb.de/~seuffert/mozilla/)

---

### Post by Roasted on 2010-04-27
When I click on it, I expected that I'd be able to download it, then go to thunderbird and install it accordingly. But the only option it gives me is to install it - which it of course errors out because it's not compatible with Firefox since it is a Thunderbird extension...

---

### Post by empty_spaces on 2010-04-27
> **Roasted said:**
> When I click on it, I expected that I'd be able to download it, then go to thunderbird and install it accordingly. But the only option it gives me is to install it - which it of course errors out because it's not compatible with Firefox since it is a Thunderbird extension...

You can't click on it directly, because, as you said, it's a thunderbird extension, and will not install in firefox.
You need to right-click on **lightning.xpi** => "Save Link As" , and save it somewhere.
Then, Go to Thunderbird => Tools => Addons => Extensions. Click on Install, browse to the saved xpi, and install it.

---

### Post by Roasted on 2010-04-27
Nice! That worked. Thanks bro.

Now the question is - why was that so difficult to find the proper lightning extension for the exact version of Thunderbird I got from the repo?

---

### Post by empty_spaces on 2010-04-27
> **Roasted said:**
> Nice! That worked. Thanks bro.

Now the question is - why was that so difficult to find the proper lightning extension for the exact version of Thunderbird I got from the repo?

Probably because these extensions are not yet past the beta stage.

---

### Post by Roasted on 2010-04-27
Looks like there's no "Google Calendar" option in the selection list when linking a network calendar. I tried the other options but my calendar always came up as blank...

---

### Post by empty_spaces on 2010-04-27
> **Roasted said:**
> Looks like there's no "Google Calendar" option in the selection list when linking a network calendar. I tried the other options but my calendar always came up as blank...

Didn't you also install the **gdata-provider.xpi** extension from the above link?
That should give you the ability to sync google calendar into the thunderbird calendar

---

### Post by lidex on 2010-04-27
> **empty_spaces said:**
> Didn't you also install the **gdata-provider.xpi** extension from the above link?
That should give you the ability to sync google calendar into the thunderbird calendar
Unfortunately it's not there. It is [here]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/") however you may need to use the version of lightning there also.

---

### Post by empty_spaces on 2010-04-28
> **lidex said:**
> Unfortunately it's not there. It is [here]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/") however you may need to use the version of lightning there also.

I'm not sure which link you are looking at, but if you click on the one from my earlier post (**[http://www.secudb.de/~seuffert/mozilla/](http://www.secudb.de/~seuffert/mozilla/)**), and then click on the latest folder (Screenshot 1 - highlighted) , you can see the gdata extension (screenshot 2)

---

### Post by leonhook on 2010-04-28
i done a fresh install of lucid and then downloaded thunderbird via synaptic package manager and lightning was already on there?

---

### Post by tarrinho on 2010-04-28
It worked.

Thanks.

---

### Post by lidex on 2010-04-28
> **empty_spaces said:**
> I'm not sure which link you are looking at, but if you click on the one from my earlier post (**[http://www.secudb.de/~seuffert/mozilla/](http://www.secudb.de/~seuffert/mozilla/)**), and then click on the latest folder (Screenshot 1 - highlighted) , you can see the gdata extension (screenshot 2)

OK. Gotcha.

---

### Post by LordNils on 2010-04-29
I upgraded Ubuntu a few weeks ago (beta1 i think) so i could use Thunderbird in a reasonable version with lightning and google-provider. And now someone removed lightning from the repos so we have to stick to some site i never heard of before (what is secudb.de???) and allow them to install a thunderbird-addon on my system? I dont think so, thats just sad.

---

### Post by lidex on 2010-04-29
> **LordNils said:**
> I upgraded Ubuntu a few weeks ago (beta1 i think) so i could use Thunderbird in a reasonable version with lightning and google-provider. And now someone removed lightning from the repos so we have to stick to some site i never heard of before (what is secudb.de???) and allow them to install a thunderbird-addon on my system? I dont think so, thats just sad.

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/")

---

### Post by Vanman106 on 2010-05-02
I was searching and searching until I found this post. 
First I tried the original xpi's from releases.mozilla.org, but these didn't work, so I took a chance and tried the xpi's from secudb.de. These do work on my system:

Upgraded from Karmic to Lucid, installed the XPI-addons and everything is in synch again. Too bad the ones from the official mozilla-site didn't work for me. What could be the difference?

---

### Post by lidex on 2010-05-02
> **Vanman106 said:**
> I was searching and searching until I found this post. 
First I tried the original xpi's from releases.mozilla.org, but these didn't work, so I took a chance and tried the xpi's from secudb.de. These do work on my system:

Upgraded from Karmic to Lucid, installed the XPI-addons and everything is in synch again. Too bad the ones from the official mozilla-site didn't work for me. What could be the difference?
You have to use the correct version for your architecture and t-bird install.

---

### Post by williamson389 on 2010-05-02
Thank you so much for finding a fix.  I was ready to just wait it out, and I rely on that calendar.  Thanks alot, and these forums are why I advocate ubuntu.


=D>=D>=D>

---

### Post by Oilarrak on 2010-05-07
Sorry to reopen the thread, empty_spaces, but could you give a link for the 32-bit version?. 

Thanks!

O.

---

### Post by empty_spaces on 2010-05-07
Try this link:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/linux-i686/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/linux-i686/)

---

### Post by Oilarrak on 2010-05-07
Thanks Empty_spaces!
Unfortunately, it behaves the same as all the other versions I tried: it doesn't show tasks on the main calendar no matter how I tried (I tried already making them show by choosing menu->view->calendar-current view->show tasks, I wonder if there is something I am missing). There were no problems with Sunbird. 

Thanks anyway and I appreciate if you have any suggestions

Oilarrak

---

### Post by empty_spaces on 2010-05-07
> **Oilarrak said:**
> Thanks Empty_spaces!
Unfortunately, it behaves the same as all the other versions I tried: it doesn't show tasks on the main calendar no matter how I tried (I tried already making them show by choosing menu->view->calendar-current view->show tasks, I wonder if there is something I am missing). There were no problems with Sunbird. 

Thanks anyway and I appreciate if you have any suggestions

Oilarrak

Are you trying to view tasks in the Google calendar? Because I believe that might not work.
I don't use tasks, but I did a small experiment with setting up a task, and I was only able to get it to display in the Home calendar, not the Google calendar.

---

### Post by Oilarrak on 2010-05-07
Thanks for your prompt reply. 
No chance. I tried to create a new task in the home calendar and it didn'show up. It does on the right panel but not on the main calendar. However, events do show OK on the main calendar, even new ones.

I am puzzled.

Oilarrak

---

### Post by mmerlone on 2010-05-07
> **Oilarrak said:**
> No chance. I tried to create a new task in the home calendar and it didn'show up. It does on the right panel but not on the main calendar. However, events do show OK on the main calendar, even new ones.

You are luckier than me. I am not tring Google, just local calendars and no luck. Nothing shows up. See my post here:

[http://ubuntuforums.org/showthread.php?p=9254107#post9254107](http://ubuntuforums.org/showthread.php?p=9254107#post9254107)

---

### Post by empty_spaces on 2010-05-07
> **mmerlone said:**
> You are luckier than me. I am not tring Google, just local calendars and no luck. Nothing shows up. See my post here:

[http://ubuntuforums.org/showthread.php?p=9254107#post9254107](http://ubuntuforums.org/showthread.php?p=9254107#post9254107)

Have you tried the lightning extension from the link in my post above (the second one on this page) ? That seems to be working for most people.

---

### Post by mmerlone on 2010-05-07
> **empty_spaces said:**
> Have you tried the lightning extension from the link in my post above (the second one on this page) ? That seems to be working for most people.

Yes, even though I use 32bits kernel. When I try to install it complains about the build type gcc bla bla.

---

### Post by empty_spaces on 2010-05-07
> **mmerlone said:**
> Yes, even though I use 32bits kernel. When I try to install it complains about the build type gcc bla bla.

Since I haven't seen anyone else with build type errors, It's possible that you may have tweaked your thunderbird/lightning install to the point where it would just be easier to reinstall Thunderbird and lightning.

---

### Post by mmerlone on 2010-05-07
> **empty_spaces said:**
> Since I haven't seen anyone else with build type errors, It's possible that you may have tweaked your thunderbird/lightning install to the point where it would just be easier to reinstall Thunderbird and lightning.

No, I'm not. I suppose the mentioned links are 64bits version, and I use 32bits. I have no tweaks, just repos builds. Standard fresh Lucid install (with all repos enabled).

---

### Post by empty_spaces on 2010-05-07
> **mmerlone said:**
> I suppose the mentioned links are 64bits version, and I use 32bits.

That is not correct. Links for both 32 and 64 bit have already been posted in this thread. You need to make sure you are installing the right one.

To avoid further confusion, I am again including the link to 32bit lightning. Note the i686 at the end, which means it is 32bit.

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/linux-i686/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/linux-i686/)

---

### Post by mmerlone on 2010-05-07
> **empty_spaces said:**
> To avoid further confusion, I am again including the link to 32bit lightning. Note the i686 at the end, which means it is 32bit.

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/linux-i686/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/linux-i686/)

I see, I tought you meant [http://www.secudb.de/~seuffert/mozilla/](http://www.secudb.de/~seuffert/mozilla/).
So, I try TB 3.0.4 from official repos, daily build 3.0.5 from Mozilla ppa and still no luck....

Thanks for your efforts, if you have any other idea pls let me know.

---

### Post by lidex on 2010-05-07
> **Oilarrak said:**
> Thanks Empty_spaces!
Unfortunately, it behaves the same as all the other versions I tried: it doesn't show tasks on the main calendar no matter how I tried (I tried already making them show by choosing menu->view->calendar-current view->show tasks, I wonder if there is something I am missing). There were no problems with Sunbird. 

Thanks anyway and I appreciate if you have any suggestions

Oilarrak

Didn't work for me either until I put in a start date **and** a due date. Now it shows.

---

### Post by N8N on 2010-05-10
Hi all... similar yet different problem here :)

I too went to 10.04 primarily so that I could use ffx. and tbird 3.x from the official repos (and not daily builds) went to install lightning... followed instructions here

[https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)

ended up here

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/)

downloaded the two xpi's to my home folder and then tried to install them in t'bird.  lightning.xpi installed OK but I get an error on gdata-provider.xpi

Provider for Google Calendar 0.6pre could not be installed because it is  not compatible with Thunderbird 3.0.4. 

Sooooo...  is Mozilla trying to gently tell me that I really don't need to be running a 64 bit OS?

---

### Post by empty_spaces on 2010-05-10
> **N8N said:**
> Hi all... similar yet different problem here :)

I too went to 10.04 primarily so that I could use ffx. and tbird 3.x from the official repos (and not daily builds) went to install lightning... followed instructions here

[https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)

ended up here

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/)

downloaded the two xpi's to my home folder and then tried to install them in t'bird.  lightning.xpi installed OK but I get an error on gdata-provider.xpi

Provider for Google Calendar 0.6pre could not be installed because it is  not compatible with Thunderbird 3.0.4. 

Sooooo...  is Mozilla trying to gently tell me that I really don't need to be running a 64 bit OS?

Have you tried the xpi files from this link - [http://www.secudb.de/~seuffert/mozilla/2010-03-30%20-%20lightning%201.0b2pre%20x86_64%20linux%20english/](http://www.secudb.de/~seuffert/mozilla/2010-03-30%20-%20lightning%201.0b2pre%20x86_64%20linux%20english/)

These are a little more up to date.

---

### Post by N8N on 2010-05-10
> **empty_spaces said:**
> Have you tried the xpi files from this link - [http://www.secudb.de/~seuffert/mozilla/2010-03-30%20-%20lightning%201.0b2pre%20x86_64%20linux%20english/]("http://www.secudb.de/%7Eseuffert/mozilla/2010-03-30%20-%20lightning%201.0b2pre%20x86_64%20linux%20english/")

These are a little more up to date.

Well I did and they seem to work...  made me a little nervous though.  Me = slightly paranoid.  I was kind of hoping to get them from a site with "mozilla" somewhere in the URL.  You'd think that'd be the place to go to get up to date stuff?

---

### Post by nandelbosc on 2010-05-14
> Well I did and they seem to work... 

+1

Here works too!

---

### Post by Pepe Lebuntu on 2010-05-17
I'm still having trouble with mine, even after putting on that version from Oregon.

Here's what my problem looks like:

[IMG]http://dl.dropbox.com/u/1462498/Lightning.jpg[/IMG]

Also, whenever I try to save anything to it, it won't do it, and will subsequently "lock" the calendar.

---

### Post by neiljansons on 2010-05-17
Does anyone know when Lightning will be in the repos?
If its not too far off I would rather wait than install a beta.

---

### Post by empty_spaces on 2010-05-17
> **Pepe Lebuntu said:**
> I'm still having trouble with mine, even after putting on that version from Oregon.

[COLOR="Blue"]Version from Oregon???
[/COLOR]
> **Pepe Lebuntu said:**
> 
Here's what my problem looks like:
[IMG]http://dl.dropbox.com/u/1462498/Lightning.jpg[/IMG]

[COLOR="blue"]Maybe I'm missing something obvious, but what exactly am I looking for in that screenshot?[/COLOR] 

> **Pepe Lebuntu said:**
> 
Also, whenever I try to save anything to it, it won't do it, and will subsequently "lock" the calendar.

[COLOR="blue"]If you can't save anything to the calendar, how did you get all those entries in the screenshot?[/COLOR]

---

### Post by lidex on 2010-05-17
What do you show in synaptic? Mine below.

---

### Post by Pepe Lebuntu on 2010-05-17
Hi Empty Spaces. Thanks for your willingness to help, and I'm sorry for the ambiguity and confusion. I'll try to be clearer


> **empty_spaces said:**
> [COLOR=Blue]Version from Oregon???[/COLOR]

What I meant was the 32-bit version of the lightning.xpi, dated Dec 14, 2009... the link I went to for that was affiliated with the University of Oregon. Never mind.


> **empty_spaces said:**
> [COLOR=blue]Maybe I'm missing something obvious, but what exactly am I looking for in that screenshot?[/COLOR] 

No worries, mate. It's those multiple entries: See out "INSPECTION" is up in Tuesday 3 times? And see how the FMC appointments at 7pm on Monday and Tuesday occur 3 times? The same with a few things on Wednesday and Saturday? 

They SEEM to have been entered into the "General-Public", "Leanne" and "Due-Date" (my wife's pregnant...) calendars . The point is THEY ARE NOT. They SHOULD occur in ONE CALENDAR ONLY - the Inspection one is from the "General-Public" Calendar on Google, and is shown correctly when I go into Google Calendar on the web. But for some bizarre reason, Thunderbird is multiplying the event, and claiming it's in all three of those Google calendars. It's like it does two things: it can't differentiate between an event in one calendar and another; and it creates multiple - and thus basically unreadable - entries. 

As well as that, this doubling-up seems to SLOW DOWN the whole calendar loading, which consequently slows down Thunderbird entirely.



> **empty_spaces said:**
> [COLOR=blue]If you can't save anything to the calendar, how did you get all those entries in the screenshot?[/COLOR]

These calendars are shared with my wife, and many of these entries were made by her, either into her "Leanne" Calendar (so I know when she's busy, etc), or she has put them into the "General-Public" calendar, or for that matter, one of the othes. As well as that, increasingly I've just gone into Google Calendar on the web myself for any entries I want to do, because Tbird is being so unhelpful. 

This basically turns Lightning into nothing more than a record of my calendars for me to see my appointments, not a place where I can add appointments. And given the doubling-up problem, it's proving to be a pretty lousy record as well.

All of this was working fine under Tbird 2 and Ubuntu 9.10.

Hope this helps clarify things, and I look forward to your help. :)

---

### Post by Pepe Lebuntu on 2010-05-17
> **lidex said:**
> What do you show in synaptic? Mine below.
Hi Lidex, when I check my synaptic, there is no lightning-extension package AT ALL. When I tried to sudo apt-get it, it said that there was no such thing as lightning-extension.

I have used Update Manager to update my system, and I've checked Software Sources, and that's all up-to-date too.

---

### Post by uRock on 2010-05-17
> **empty_spaces said:**
> You can't click on it directly, because, as you said, it's a thunderbird extension, and will not install in firefox.
You need to right-click on **lightning.xpi** => "Save Link As" , and save it somewhere.
Then, Go to Thunderbird => Tools => Addons => Extensions. Click on Install, browse to the saved xpi, and install it.
Thank you for showing us how to do this.

---

### Post by lidex on 2010-05-17
> **Pepe Lebuntu said:**
> Hi Lidex, when I check my synaptic, there is no lightning-extension package AT ALL. When I tried to sudo apt-get it, it said that there was no such thing as lightning-extension.

I have used Update Manager to update my system, and I've checked Software Sources, and that's all up-to-date too.

What I wanted you to see was the actual packages installed and version numbers. If you look to the left you'll see 'local' (origin) selected. Synaptic is showing manually installed items. Do your's match?

---

### Post by razor7 on 2010-05-18
Hi i installed everything following the steps above. 

I get the calendar, no "Calendar" text on calendar tab, can not create calendars, and also can not click next in the create calendar dialog boz, even if a choose google calendar or lDAV.


Please, whate is going on here...please mozilla.org. Support ALL of your products!

Thanks in advice!

---

### Post by Pepe Lebuntu on 2010-05-20
I opened the local section and lightning-extension was not on there, despite me following the path that you suggested.

As it is, I've turned off Lightning for the moment and have just set myself to using the web-based version of Google Calendar, until all these problems can be rectified, hopefully in a future release of Lightning that proves more stable. I'd obviously prefer to use Lightning, but it just not worth the agony of the mess it is making of my Google calendars right now.

---

### Post by 3pinner on 2010-05-23
Empty Spaces:
Thank you for your link to fix this!
Just copied all my settings to a new install of Lucid 64 bit and found this thread. Calendar install went fine.
Vienna VA eh? I'm in Warrenton.

---

### Post by alawson on 2010-05-25
Thanks empty_spaces - solved my probs too!

---

### Post by DrJohn999 on 2010-06-08
Installed 64-bit LIghtning 1.0b1 then added Provider for Google Calender from here:
[http://www.secudb.de/~seuffert/mozilla/2010-03-30%20-%20lightning%201.0b2pre%20x86_64%20linux%20english/]("http://www.secudb.de/~seuffert/mozilla/2010-03-30%20-%20lightning%201.0b2pre%20x86_64%20linux%20english/")

but Google Calender provider won't start up. In the add-ons dialog it says "Provider for Google Calendar 0.6b2pre... Requires additional items."

Yet Lightning seems to work fine other than no Google cal. I did have the previous versions of Lightning x64 and Google Provider x64 installed under T-bird 2. The home calendar and a dead item for the Google Calendar were imported during the upgrade to T-bird 3. 

The Windoze XP x86 versions work just fine over on my machine at work, so...

Uninstalling the Google Provider add-on for now -- but does anyone have a suggestion?

---

### Post by kpprem@gmail.com on 2010-06-21
I installed thunderbird 3.0.4 from Ubuntu software center and added lightning addon using tools->addon option. All calendars including google's are working fine.

---

### Post by Roasted on 2010-06-29
So I added a mozilla PPA to get the latest Firefox, sure enough it upgraded Thunderbird. Sure enough, it disabled my add-ons. The ones on the original page of this thread don't work. I'm sick of these retarded incompatibilities. Doesn't Thunderbird like... work? Is there a link I can download the proper extensions *again*?

---

### Post by thundaraptor on 2010-07-06
having trouble getting 64 bit provider to work.  have lightning for 64bit installed but the only 64bit provider links i have found don't work.  any ideas?

---

### Post by uRock on 2010-07-06
...

---

### Post by empty_spaces on 2010-07-06
It appears that the lightning and gdata-provider plugins that have been working for Thunderbird 3.0.4 are not compatible with the latest update for Thunderbird 3.0.5.
Guess we need to look for updated plugins.

---

### Post by lidex on 2010-07-06
This looks recently updated:
[ftp://ftp.mozilla.org/pub/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/]("ftp://ftp.mozilla.org/pub/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/")

---

### Post by empty_spaces on 2010-07-06
> **lidex said:**
> This looks recently updated:
[ftp://ftp.mozilla.org/pub/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/]("ftp://ftp.mozilla.org/pub/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/")

Thanks for the updated plugins link. But these also do not seem to be compatible with 3.0.5

---

### Post by lidex on 2010-07-06
What exactly is the issue with lightning here? I have TB 3.0.5 working with 1.0b1. It seems to work for what I need, granted I don't do any online syncing.

---

### Post by 3pinner on 2010-07-06
I just went through this and found a solution:

The latest version of Thunderbird from the repositories: 3.0.5 is not compatible with the current version of Lightning offered by Mozilla 1.0b2
But an older version of Lightning will.

Instructions found here:

[https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)

I run 64 bit Lucid. Be sure to install the correct version - 32 bit or 64 bit depending on which OS you have.
Download the correct bit version to Lightning to your desktop.
Open Thunderbird and uninstall the non working version of Lightning (Don't worry - your data is stored elsewhere and will not be disturbed)
Reboot Thunderbird.
go to Add Ons - and install the Lightning you just downloaded.
Reboot Thunderbird - click on Tasks and Events and your calendar should be there with all its data.

On a Lightning community site (sorry don't have the link now) it was explained that developing further updates of Lightning for Thunderbird 3.0.x have been abandoned in favor of developing for Thunderbird 3.1 - Which has been released but is not in the Ubuntu repositories yet. Probably because there is no 64 bit version of Thunderbird 3.1 yet either.

Who cares......... The older version of Lightning in the link above works with what ubuntu gave us. so give it a shot.

There will of course be a fully functional Lightning to work with Thunderbird 3.1 in the near future.

---

### Post by empty_spaces on 2010-07-06
> **3pinner said:**
> I just went through this and found a solution:

The latest version of Thunderbird from the repositories: 3.0.5 is not compatible with the current version of Lightning offered by Mozilla 1.0b2
But an older version of Lightning will.

Instructions found here:

[https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)

I run 64 bit Lucid. Be sure to install the correct version - 32 bit or 64 bit depending on which OS you have.
Download the correct bit version to Lightning to your desktop.
Open Thunderbird and uninstall the non working version of Lightning (Don't worry - your data is stored elsewhere and will not be disturbed)
Reboot Thunderbird.
go to Add Ons - and install the Lightning you just downloaded.
Reboot Thunderbird - click on Tasks and Events and your calendar should be there with all its data.

On a Lightning community site (sorry don't have the link now) it was explained that developing further updates of Lightning for Thunderbird 3.0.x have been abandoned in favor of developing for Thunderbird 3.1 - Which has been released but is not in the Ubuntu repositories yet. Probably because there is no 64 bit version of Thunderbird 3.1 yet either.

Who cares......... The older version of Lightning in the link above works with what ubuntu gave us. so give it a shot.

There will of course be a fully functional Lightning to work with Thunderbird 3.1 in the near future.

I was kinda going in the same direction on reading lidex's post about 1.0b1 working with 3.0.5. 

All this while I was trying to make 1.0b2 work with 3.0.5.

Thanks for the instructions and link. I've got lightning working now, although google calendar is still out. Let me know if there is a working gdata-provider for 64bit.

---

### Post by 3pinner on 2010-07-06
> **empty_spaces said:**
> I was kinda going in the same direction on reading lidex's post about 1.0b1 working with 3.0.5. 

All this while I was trying to make 1.0b2 work with 3.0.5.

Thanks for the instructions and link. I've got lightning working now, although google calendar is still out. Let me know if there is a working gdata-provider for 64bit.

Not yet........
But I'm sure one is coming soon.
As for google calendar compatibility, I think that is one of the features of Lightning 1.02b
When they get all the 32 bit 64bit stuff worked out with 3.1 we'll be in business.

---

### Post by undoIT on 2010-07-06
> **3pinner said:**
> I just went through this and found a solution:

The latest version of Thunderbird from the repositories: 3.0.5 is not compatible with the current version of Lightning offered by Mozilla 1.0b2
But an older version of Lightning will.

Instructions found here:

[https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)


Thanks, worked for me.

---

### Post by lannatwin on 2010-07-06
This thread is about Thunderbird 3.0.4 - Ubuntu 10.04 - Lightning Extension.

---

### Post by 3pinner on 2010-07-07
the latest update I received from update manager was thunderbird 3.0.5
the above procedure will work with any thunderbird 3.0.x.

there is a different Lightning available for Thunderbird 3.1, but no 64 bit support yet.
I've included that info to help anybody that ends up here just trying to figure out what to do with either.

---

### Post by CK1 on 2010-07-07
I've lost my lightning addon like other people with the upgrade to TB 3.0.5. I used it mainly with google calendar, so it looks like I need to re-install the previous version of TB to get back a working solution. How can I re-install the previous version of TB? I'm on 64bit Ubuntu 10.04. Thanks.

---

### Post by tneagle on 2010-07-07
Hi, I just installed version 1.0b1 and it seems to work again with TB 3.0.5. :p Here's the link to the 64 bit version:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1rc1/contrib/linux-x86_64/lightning.xpi](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1rc1/contrib/linux-x86_64/lightning.xpi)

---

### Post by lannatwin on 2010-07-07
> **tneagle said:**
> Hi, I just installed version 1.0b1 and it seems to work again with TB 3.0.5. :p Here's the link to the 64 bit version:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1rc1/contrib/linux-x86_64/lightning.xpi](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1rc1/contrib/linux-x86_64/lightning.xpi)

does it sync with google calendar?

---

### Post by Strubbl on 2010-07-07
> **lannatwin said:**
> does it sync with google calendar?
not in my installation. having the same thunderbird und lightning version... :(

---

### Post by Loconeko on 2010-07-15
<thank you message>
Just upgraded to 10.04 and TB 3.0.5, I had a scare when I saw Lightning was not running, because I sync everything both for my private and business schedule (my calendars are DAV-based)
But thanks to you guys, I was able to install Lightning 1.0b1 and everything is fine now.
So I'd thought I'd sign in these forums just to say thanks ! :D
</thank you message>

---

### Post by thundaraptor on 2010-07-15
I can't make provider work with lightning.  Anyone else having that issue? I get the error message that provider isn't compatible with 3.05 version of lightning.

---

### Post by cyberef on 2010-07-17
Hi, solved the problem, but I would suggest using it at your own risk.

I am now running Lightning + Gdata-provider with Thunderbird 3.0.5

I downloaded them from here (64-bit versions):

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/)

They are simply zip files, so just rename them to .zip, extract it to some directory. Edit the install.rdf with gedit for example. Lookup the lines with <em:minVersion and maxVersion.

Change them to this:

<em:minVersion>3.0.5</em:minVersion>
<em:maxVersion>3.0.5</em:maxVersion>

Save the file and then compress all the files you extracted in the folder. So now you will have for example lightning.zip, rename this file to lightning.xpi. Install this in Thunderbird Add-ons. Check the menu Tools -> Add-ons, then press the install button and locate your .xpi file you made.

---

### Post by empty_spaces on 2010-07-17
> **cyberef said:**
> Hi, solved the problem, but I would suggest using it at your own risk.

I am now running Lightning + Gdata-provider with Thunderbird 3.0.5

I downloaded them from here (64-bit versions):

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/)

They are simply zip files, so just rename them to .zip, extract it to some directory. Edit the install.rdf with gedit for example. Lookup the lines with <em:minVersion and maxVersion.

Change them to this:

<em:minVersion>3.0.5</em:minVersion>
<em:maxVersion>3.0.5</em:maxVersion>

Save the file and then compress all the files you extracted in the folder. So now you will have for example lightning.zip, rename this file to lightning.xpi. Install this in Thunderbird Add-ons. Check the menu Tools -> Add-ons, then press the install button and locate your .xpi file you made.

Awesome, this worked for me, but with a few more edits to the install.rdf file.
I had to change all references of 3.1 to 3.0.5 and also change 1.0b2 to 1.0b1, since I'm running lightning 1.0b1

---

### Post by keithweddell on 2010-07-18
Nice one.  Works for me.

Keith

---

### Post by CK1 on 2010-07-20
Many thanks cyberef, this works for me too.

---

### Post by Ein2015 on 2010-07-21
I used cyberef's method to install from [http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/) on to thunderbird-3.1 from [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa).

Thanks! :D

Edit: Hmm... now Thunderbird won't start up... oh well back to 3.0.7.

---

### Post by zbeckerd on 2010-07-24
I also used cyberef's method.  The lightning link he had did not work for me.  I used the lightning add on from last January.  My local calendar quit working, but I don't use that one anyway.

My how things have changed.  I could always sync my palm to linux.  But know being able to truly sink my phone, my web and desktop calendar/mail/address book is just great.

---

### Post by zbeckerd on 2010-07-28
> **zbeckerd said:**
> I also used cyberef's method.  The lightning link he had did not work for me.  I used the lightning add on from last January.  My local calendar quit working, but I don't use that one anyway.

My how things have changed.  I could always sync my palm to linux.  But know being able to truly sink my phone, my web and desktop calendar/mail/address book is just great.

Today auto update put thunderbird 3.06 on and broke the previous fix.  Just use cyberefs fix with 3.0.6 instead of 3.0.4 or 0.5

---

### Post by coeus on 2010-07-30
I've compiled 1.02b for X86_64 and you can download them here:
[http://rex-bits.redterra.net/](http://rex-bits.redterra.net/)

They work on Thunderbird 3.0.5

---

### Post by Ni85 on 2010-08-03
> **coeus said:**
> I've compiled 1.02b for X86_64 and you can download them here:
[http://rex-bits.redterra.net/](http://rex-bits.redterra.net/)

They work on Thunderbird 3.0.5

it works on Thunderbird 3.0.6 too
thanks

---

### Post by Roasted on 2010-08-03
Well, none of the above worked for me, unfortunately, and here I am trying to fix the same problem I had when I started this thread because of a Thunderbird update I got.

Have I mentioned this is complete ********? I would expect the extensions to work as Thunderbird gets updated, not break it every single time.

---

### Post by DeMus on 2010-08-03
I use T'bird 3.1.1 and Lightning 1.02b. Works great, no problem what so ever.

---

### Post by alawson on 2010-08-22
Thanks coeus, your build worked for me.

10.04 x64 & tbird 3.0.6 from the normal distribution, and lightning 1.0b2pre & gdata-provider 0.6b2pre from your build.

Let's hope it still works after the next upgrade too! Shame the devs make the addons so version specific when they clearly nearly work with the older versions....

---

### Post by HyperFlexed on 2010-08-31
I spent a lot of time ripping my hair out. Whenever I got lightning installed without complaint, any manipulation of the calendar caused TB to lock up and crash.

This is on ubuntu 10.04 with TB 3.0.6 and lightning 1.0b1. It DID NOT work. Seeing as plugins are tied to specific versions of the software (which is dumb, as someone has pointed out) I figured upgrading to TB 3.1 would give me a better chance of having access to the latest fixes.

Unfortunately ubuntu doesn't make it easy for you to upgrade to the latest version, see here:

[http://digitizor.com/2010/06/25/how-to-install-thunderbird-3-1-in-ubuntu-10-04/](http://digitizor.com/2010/06/25/how-to-install-thunderbird-3-1-in-ubuntu-10-04/)

You can see on the chart here:

[https://help.ubuntu.com/community/ThunderbirdLightning#Requirements](https://help.ubuntu.com/community/ThunderbirdLightning#Requirements)

and get what you need. Grab the x86_64 contrib builds of lightning and gdata (1.0b2, not any of the release candidates)

I can say with that all problems are laid to rest.

Ubuntu ought to just upgrade to TB 3.1 and be done with this bullcrap. I'm annoyed at how poorly 64-bit is supported long after it has entrenched itself into our lives. Hopefully with the release of Vista/7 and the lowering costs of 64 bit processors we'll begin to see the inverse trend. It's funny how doing something perceived as "more risky" (taking software from PPAs) is more fruitful than sticking with what they call "stable" releases. The "instable" release is more usable than the "stable" version.

---

### Post by uRock on 2010-08-31
I gave up on it and started using Sunbird, even though the devs removed it from the repos for some stupid reason. A week after I had installed the Lightning extension Thunderchicken did an update that killed Lightning. I am under the impression that Mozilla isn't spending much time or money on keeping Linux users happy anymore because the 64bit Windows version works flawlessly.

---

### Post by lannatwin on 2010-09-01
Those instructions did *not* work for me on a 64 bit system.

Instructions *do* work are here... [http://ubuntuguide.net/install-thunderbird-3-1-from-ppa-in-64-bit-ubuntu-10-04](http://ubuntuguide.net/install-thunderbird-3-1-from-ppa-in-64-bit-ubuntu-10-04)

Lightning and Gdata that work with Thunderbird 3.1.2 can be found here... [http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/)

Finally sucessfully using Thunderbird 3.1.2, Lightning, and Gdata.  What a PITA.

---

### Post by alawson on 2010-09-10
Whatever you do, don't upgrade to TB 3.0.7, cos that breaks it again.

I'm not a developer. I don't want to be a developer. I want to be a user of high quality FOSS.

I need software that works. Maybe I should install Win7. Cos that just mostly works right now.

I need my main PC to show my calendar. My calendar is currently with Google. If that's too hard for Ubuntu x64 right now I'll use something that works instead.

Please make it work on Ubuntu tho. I don't want to pay Microsoft for half-assed solutions.

---

### Post by uRock on 2010-09-10
I am using 3.1.3 and it is working great with Lightning.

---

### Post by lannatwin on 2010-09-10
3.1.4pre is working great with gdata.

---

### Post by empty_spaces on 2010-09-10
> **alawson said:**
> Whatever you do, don't upgrade to TB 3.0.7, cos that breaks it again.

I'm not a developer. I don't want to be a developer. I want to be a user of high quality FOSS.

I need software that works. Maybe I should install Win7. Cos that just mostly works right now.

I need my main PC to show my calendar. My calendar is currently with Google. If that's too hard for Ubuntu x64 right now I'll use something that works instead.

Please make it work on Ubuntu tho. I don't want to pay Microsoft for half-assed solutions.

To anyone who has upgraded to 3.0.7, the instructions in post #71 of this thread are still valid to get lightning / google-calendar working under 3.0.7.

@ uRock, you should probably clarify that you are now using 32bit ubuntu (I believe you mentioned that in another post). So Thunderbird 3.1.3 might be a good option for you, but may not work for people who are sticking to 64bit. :)

---

### Post by uRock on 2010-09-10
> **empty_spaces said:**
> To anyone who has upgraded to 3.0.7, the instructions in post #71 of this thread are still valid to get lightning / google-calendar working under 3.0.7.

@ uRock, you should probably clarify that you are now using 32bit ubuntu (I believe you mentioned that in another post). So Thunderbird 3.1.3 might be a good option for you, but may not work for people who are sticking to 64bit. :)
Very true. I plan to start testing some of this stuff in a 64bit vbox, so that I can make qualified assertions.

---

### Post by uRock on 2010-09-10
Just tried to install the newest thunderbird in 64bit and apparently Mozilla decided not to make a 64bit version for it.:(

---

### Post by lannatwin on 2010-09-10
> **uRock said:**
> Just tried to install the newest thunderbird in 64bit and apparently Mozilla decided not to make a 64bit version for it.:(

If you follow the instructions I linked to above, you will get the latest 64bit version.  I get updates to it nearly every day, and it works perfectly.  Just updated to Lightning/1.0b2 Shredder/3.1.4pre.

---

### Post by uRock on 2010-09-10
I've already destroyed that install by upgrading to Maverick. It is no biggie for me. I use 32bit for production.

---

### Post by Pepe Lebuntu on 2010-09-12
So, wait. I'm using T3.0.7, and 32-bit. And I just want Lightning to work with my Google calendars - what do I do? Do I go to the USC? No. Do I go to Synaptic? No. Do I go to the add-ons section of Mozilla? No.

Do I say stuff it, give up, and just read my calendar straight from Google in Firefox? At the moment, that seems to be the only option.

---

### Post by uRock on 2010-09-13
> **Pepe Lebuntu said:**
> So, wait. I'm using T3.0.7, and 32-bit. And I just want Lightning to work with my Google calendars - what do I do? Do I go to the USC? No. Do I go to Synaptic? No. Do I go to the add-ons section of Mozilla? No.

Do I say stuff it, give up, and just read my calendar straight from Google in Firefox? At the moment, that seems to be the only option.
I'd have to sa that gmail has one of the ugliest websites ever. I have 3.1.3 installed with Lightning and it works great. I am liking having it installed in the /home as I don't have to worry about loosing any settings if and when I reinstall/upgrade ubuntu.

---

### Post by Pepe Lebuntu on 2010-09-13
> **uRock said:**
> I'd have to sa that gmail has one of the ugliest websites ever. I have 3.1.3 installed with Lightning and it works great. I am liking having it installed in the /home as I don't have to worry about loosing any settings if and when I reinstall/upgrade ubuntu.
 Yes, but, that's exactly my point. I used to use Lightning in Thunderbird in previous versions of it, and loved it. It was MUCH better than Google Calendar on the web. But since the upgrades of T'bird, especially to T3, Google Calendars have worked horribly (I've made posts explaining this previously in this thread). I like the new facets of T'bird that occurred with these upgrades (tabs, etc), so I don't want to go back. I just want a version of Lightning that goes with the latest version of T3 for 32-bit that WORKS.

 It is an indication of how badly Lightning now works on T'bird 32-bit, that a person who loved it as much as I did, now feels compelled to slum it with the Google Calendar Website.

It should be simple. You go to the USC, or even Synaptic, or the Mozilla plug-in site, and just get Lightning for Thunderbird, and it works. It doesn't. We have to bend through hoops to make it work, many of which are beyond most users' capabilities or time.

---

### Post by falan on 2010-09-16
It is not hard to find a lightning pre-compiled plug-in for 64bit Ubuntu 10.04 / TB 3.0.4.
What is hard is to get any combination that correctly processes invites from Exchange/Lookout.
I'm considering installing TB 2* because I've heard that this feature worked in the past.

---

### Post by nosmokenofire on 2010-09-21
I have read through this thread but I cant seem to find an answer to my problem, so here goes:

I  have installed ubuntu on a dual boot, installed Tbird from the software  centre, and then copied my profiles from Tbird in windows to my Ubuntu  version. All is well, I then installed lightning as an add-on and then  upon restrarting Tbird I get this message[IMG]http://ubuntuforums.org/attachment.php?attachmentid=170150&stc=1&d=1285089203[/IMG]
in fact I get exactly three of them each time

Can anyone help?
Please...

---

### Post by Roasted on 2010-09-21
Dear Thunderbird Developers:

Until this issue is addressed, I have been forced to use another product that actually... works. Thank you, Evolution developers, for doing a solid job. I'm sorry I ever doubted Evolution.

Your friend,
Roasted

---

### Post by nosmokenofire on 2010-09-21
So Roasted, you recommend Evolution? Is there any way of importing my Tbird profiles and lightning calendar stuff into it. I know the chances are slim but I thought I'd ask...

:)

---

### Post by Roasted on 2010-09-21
> **nosmokenofire said:**
> So Roasted, you recommend Evolution? Is there any way of importing my Tbird profiles and lightning calendar stuff into it. I know the chances are slim but I thought I'd ask...

:)

Not sure. I use Google Calendar, so my calendar is sucked up on the web and I just link to it accordingly. It seemed really easy and I had no issues firing up Evolution with it. I plan to switch my desktop to Evolution too due to its ease of use (comparable to Thunderbird) but also its ease of importing Google calendars. Just my experience anyway. I suppose there was a good reason Evolution is default in Ubuntu - guess I'll just run with it.

---

### Post by r_avital on 2010-09-25
I want to congratulate and thank you all, for all the help you're providing.  Even someone posting just "it worked for me" is helpful.

I'm now on TB 3.08, not because I particularly want to, but because that's what's in the repos as I installed Lucid 64-bit on a new laptop.  Finding a version of lightning was a battle.  Now I've tried 4 versions of the Google-provider and all fail to install, same error, incompatibility with 3,08.

Besides the fact that nobody should be spending more than 2 minutes on all this voodoo (and that's what it is), somebody needs to talk to the TB developers and let them now, their product is now enough in the mainstream, that they can't simply afford to say "don't like it - don't use it, it's free anyway, don't feel entitled."  Every fix works for 15 minutes.  If it's not lightning+google provider, it's clamdrib (the linkage to the clamd antivirus server to scan  your incoming email), or Enigmail, or some other extension we rely on.  Mozilla calls themselves a "corporation" but they don't seem to give a hoot about the dissatisfaction of their users.  Be it windows users or linux or mac users, we were not put on Earth to download and update every other day just to use our systems.  Of course, when you tell them that on mozillazine, you get flamed off the planet.  And yes, all that cr@p "just works" on evolution, but evolution is impacted in other ways.

Sorry for the rant.

Currently using Lucid 64-bit, TB 3.08 from the repos, and lightning 1.01b - incredibly, that older version is the only one I found that will install on this version of TB.  If anyone knows of a version of the google provider that will install under these conditions, I'll be grateful for the info.

My next step is to edit the version compatibility on the rdf file.

Thanks in advance.

---

### Post by nosmokenofire on 2010-10-03
I have finally got round this one with the help of ubuntuzilla: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)
I now have the Mozilla build rather than the Ubuntu build of Thuderbird and the latest version of lightning works fine with it.

Thanks to all for your ongoing support.

---

### Post by alawson on 2010-10-09
Yep. Back to Evolution I go. Shame on you, Thunderbird, shame!

---

### Post by jdevora on 2010-10-27
Now Thunderbird x64 is 3.0.9 and the plugins are incompatible :-(

---

### Post by lidex on 2010-10-27
This seems to work for me (see screen)but I am on development ubuntu - natty.

---

### Post by 3pinner on 2010-10-27
> **jdevora said:**
> Now Thunderbird x64 is 3.0.9 and the plugins are incompatible :-(

actually, mine is still functioning fine with v 3.0.9

---

### Post by DancingFlames on 2010-10-28
Actually guys, when you make a fresh install of the plugins they don't work on TB 3.0.9 x64 ( The one currently in Ubuntu repositories ). I made a lot of tricks, tutorials and "hacks" ... but afterward I had to do it my way. 

I actually spent two hours installing and uninstalling plugins, different versions, different styles. I've made my hack with the gdata provider 0.6pre, from lightning 1.0b1 repository, but it says something like "Components required". I actually wanted to debug this, but before doing that I've tried my magic trick.

[B][COLOR="Red"]
Please note that this is not a solution, it's a hack, use it on your own risk ... but it works : [/COLOR][/B]

1. Download the latest plugin for x64 architecture. What I found is: lightning 1.0b2rc3 and the same for gdata provider ( the actual version is 0.7 )
2. Open the two xpi files with an archive manager and edit the rdf files and modify the Thunderbird version. Only the min version is required to be modified = 3.0.1. Don put * in the min version because it won't work:-({|=.
3. Install the two plugins. Enjoy your Thunderbird magic pack :D

---

### Post by PFrenssen on 2010-11-01
Here this version works fine with TB in Maverick 64 bit:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/)

---

### Post by 3pinner on 2010-11-01
I'm actually giving up on 64 bit.
I'll post back and let everyone know how it works out with TB and Lightning after I 'downgrade'.

---

### Post by DancingFlames on 2010-11-01
> **PFrenssen said:**
> Here this version works fine with TB in Maverick 64 bit:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/)

The explanation is simple: Maverick x64 has TB 3.1.x installed by default, which works with your lightning version (1.0b2). The problem is with the people that have TB 3.0.x x64 version. The plugins are simply incompatible. 

> **3pinner said:**
> I'm actually giving up on 64 bit.
I'll post back and let everyone know how it works out with TB and Lightning after I 'downgrade'. 

Seems that you don't like my workaround. :)

---

### Post by 3pinner on 2010-11-01
> **DancingFlames said:**
> The explanation is simple: Maverick x64 has TB 3.1.x installed by default, which works with your lightning version (1.0b2). The problem is with the people that have TB 3.0.x x64 version. The plugins are simply incompatible. 



Seems that you don't like my workaround. :)

Sorry, but I haven't tried it. In fact, Lightning is working fine with my version of TB. It's other issues I've had to deal with, but I don't want to hijack the thread.
Thanks for the note that TB is part of Maverick. I'm running the LTS version.

---

### Post by DrJohn999 on 2010-11-01
The [x64 version Lightning Extension]("http://ubuntuforums.org/showpost.php?p=10056731&postcount=109") works for me with Thunderbird 3.1.6 x64. Also so does [Provider for Google Calendar 0.7.1]("https://addons.mozilla.org/en-US/thunderbird/addon/4631/"). :)

---

### Post by Roasted on 2010-11-08
I wonder if there's any hope for these extensions to provide better support. It seems like the ever so slightest change of Thunderbird and the thing wigs out. Further adding to my frustration, I installed 10.10 and Thunderbird from the software center which is 3.0.10. Did Lightning work? Yup. Did GData extension? Nope.

I need BOTH to make Thunderbird work with Google Calendar in the way I need. Very frustrating. It's such a shame because, even though I've been bouncing back and forth a lot between Thunderbird and Evolution, I think I'm finally sticking with Thunderbird. It's fast, reliable, and gives me no headaches with GMail whereas Evolution does (it somehow re-sends me emails I intentionally delete...??). Anyway, I just wish there was a better way to handle this.

For now, I found the BEST alternative solution. Whoever did this, thank you. It's Google Calendar Tab... it creates a tab right in Thunderbird and you see Google Calendar as if you were on Firefox. This is nice because then via tab I can bounce from email to calendar and vice versa instead of relying on logging into the actual Google Cal interface in Firefox. Granted, not a big deal, but enough that I'm like, yesssssss we're back in business. Not to mention, doing this way and using the web interface within Thunderbird would also remove any incompatibility bugs that you sometimes see with using a calendar client to "mimic" Google Calendar itself.

Anyways, let's hope for the future of Lightning and Gcal there's a better solution. So far all it's accomplished is making me cringe whenever I install updates.

---

### Post by undoIT on 2010-11-08
I have been eliminating many of the Google services I use because of the following:

[Google Releases Wi-Fi Sniffing Audit, is Accused of 'Criminal Act']("http://www.pcmag.com/article2/0,2817,2364904,00.asp")

[Google: We collected e-mails, passwords]("http://news.cnet.com/8301-13506_3-20020499-17.html")

It is hard to trust a company who does something like that with any personal / important data.

Also, their privacy policy is rather vague when it comes to data retention:

[More on Gmail and privacy]("http://mail.google.com/mail/help/about_privacy.html#data_retention")

> "Google keeps multiple backup copies of users' emails so that we can recover messages and restore accounts in case of errors or system failure, for some limited periods of time. Even if a message has been deleted or an account is no longer active, messages may remain on our backup systems for some limited period of time."

That is legal jargon stating indirectly that they can keep a copy of your all your emails for as long as they want, even after you have permanently deleted them from your account, or even deleted your account.

I have been using the following Firefox addon, which is very handy:

[GoogleSharing]("http://www.googlesharing.net/")

---

### Post by Roasted on 2010-11-08
> **undoIT said:**
> I have been eliminating many of the Google services I use because of the following:

[Google Releases Wi-Fi Sniffing Audit, is Accused of 'Criminal Act']("http://www.pcmag.com/article2/0,2817,2364904,00.asp")

[Google: We collected e-mails, passwords]("http://news.cnet.com/8301-13506_3-20020499-17.html")

It is hard to trust a company who does something like that with any personal / important data.

Also, their privacy policy is rather vague when it comes to data retention:

[More on Gmail and privacy]("http://mail.google.com/mail/help/about_privacy.html#data_retention")



That is legal jargon stating indirectly that they can keep a copy of your all your emails for as long as they want, even after you have permanently deleted them from your account, or even deleted your account.

I have been using the following Firefox addon, which is very handy:

[GoogleSharing]("http://www.googlesharing.net/")

Put yourself in my shoes. You want Thunderbird + a networked calendar. What do you use if Lightning is sucking the big one and you want a calendar integrated to Thunderbird?

---

### Post by undoIT on 2010-11-08
> **Roasted said:**
> Put yourself in my shoes. You want Thunderbird + a networked calendar. What do you use if Lightning is sucking the big one and you want a calendar integrated to Thunderbird?

I don't use online calendars, but I found this:

[http://www.ehow.com/how_6975558_sync-thunderbird-calendar-online.html](http://www.ehow.com/how_6975558_sync-thunderbird-calendar-online.html)

Have you tried Yahoo calendar?

---

### Post by Roasted on 2010-11-09
> **undoIT said:**
> I don't use online calendars, but I found this:

[http://www.ehow.com/how_6975558_sync-thunderbird-calendar-online.html](http://www.ehow.com/how_6975558_sync-thunderbird-calendar-online.html)

Have you tried Yahoo calendar?

Haven't had the best of luck with the Lightning extension.

It breaks after every 0.0.0.0.0.0.1 update.

---

### Post by robgwin on 2010-11-19
Man, this wasn't easy to sort out, but I finally got this combination to work:

64-bit Ubuntu 10.04
Thunderbird 3.0.10
Lightning 1.0b1
Google Provider 0.6b1

Thunderbird I installed directly from Ubuntu packages.

Lightning I got from here:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/)

There's also a gdata-provider.xpi in that same dir, but it did NOT work for me (refused to install based on being incompatible with TB 3.0!)

I eventually found this version which installed and is so far working great:
[https://addons.mozilla.org/en-US/thunderbird/addon/4631/versions/?page=1#version-0.6b1](https://addons.mozilla.org/en-US/thunderbird/addon/4631/versions/?page=1#version-0.6b1)

Hope this saves someone the two hours I just spent on this.

---

### Post by jeff.scott on 2010-11-22
> **robgwin said:**
> Man, this wasn't easy to sort out, but I finally got this combination to work:

64-bit Ubuntu 10.04
Thunderbird 3.0.10
Lightning 1.0b1
Google Provider 0.6b1

Thunderbird I installed directly from Ubuntu packages.

Lightning I got from here:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/)

There's also a gdata-provider.xpi in that same dir, but it did NOT work for me (refused to install based on being incompatible with TB 3.0!)

I eventually found this version which installed and is so far working great:
[https://addons.mozilla.org/en-US/thunderbird/addon/4631/versions/?page=1#version-0.6b1](https://addons.mozilla.org/en-US/thunderbird/addon/4631/versions/?page=1#version-0.6b1)

Hope this saves someone the two hours I just spent on this.

You are my Hero!!!!
Thanks!..been fiddling for more than two hours !

---

### Post by Bluebearbevis on 2010-11-27
Hello fellow Ubuntians,

Sorry to enter this conversation at such a late stage, but my endeavor to find a lightning add-on compatible with both my Thunderbird 3.1.6 and Firefox 3.6.12 64 bit led me here.  I thought eureka! I have found the answer.  However, here's the new issue:  I went to the link site, I "right clicked" and "saved link as" the current file, then opened Thunderbird tools, etc... to install.  The "saved link as" isn't an .xpi file, it's a something.html.part file?, link?, and Thunderbird won't install it.  I'm lost, any suggestions?

Thank you everyone,

Richard

---

### Post by empty_spaces on 2010-11-27
I just tested the xpi files linked in post # 109, and they download just fine. Looks like you did not complete the download correctly, since you have a .part file.

---

### Post by Bluebearbevis on 2010-11-27
Hey empty_spaces,

You were obviously not referring to the area between your ears when you chose a user name.  After reading through All the pages of this thread an clicking the last suggested link, "right clicking" the .xpi file and "saving link as" the file yielded an .xpi file in my downloads folder.  After installing through and restarting Thunderbird, freaking fantastic, I have a calendar!

Many thanks,

Richard

---

### Post by alawson on 2011-01-22
Wow - just installed 10.10 amd64 and noticed that there are now packages for the following;

xul-ext-lightning
xul-ext-gdata-provider

These all seem to work and now I have Thunderbird with Google calendars working straight out of the default repositories. Sweet!

---

### Post by 3pinner on 2011-01-22
Yeah it is sweet!
Nice to see that its finally they're finally in synch...................
for a while anyway:D

---

### Post by alawson on 2011-03-03
I notice that thunderbird has been upgraded to 3.1.8. Can anybody confirm that google provider and lightning still work with it?

---

### Post by 3pinner on 2011-03-03
Haven't installed the upgrade yet. I thought I'd keep my eye online looking for someone brave enough to give it a shot before I mess up my calendar again!

---

### Post by timgood on 2011-03-03
I can confirm that the upgrade breaks lightning. It can be fixed by the .xpi edits mentioned previously.

---

### Post by crazy ivan on 2011-03-03
Just for your interest: Following
[http://ubuntuforums.org/showthread.php?t=540330]("http://ubuntuforums.org/showthread.php?t=540330")
and [https://help.ubuntu.com/community/ThunderbirdLightning]("https://help.ubuntu.com/community/ThunderbirdLightning") has worked perfectly for me on Ubuntu 10.10 64 bit and with vanilla Thunderbird 3.1.6... 

Another interesting question if it will survive further updates. Guess not.. Maybe one should contact the project developers to publish 64bit files, or is there a general 64 laxness in mozilla development?

---

### Post by alawson on 2011-03-14
Finally plucked up the courage and upgraded the two boxes I have running 10.10 64bit, and Thunderbird+Lightning+Google Provider worked fine.

---

### Post by timgood on 2011-03-14
A 64bit version of lightning (1.0b2) has now been released and can be downloaded [here]("ftp://ftp.mozilla.org/pub/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/"). This works with Thunderbird 3.1.8 and looking at the xpi file will continue to work with the rest of the 3.1.* releases. Have fun guys...!

---


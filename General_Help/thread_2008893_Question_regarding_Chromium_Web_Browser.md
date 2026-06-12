---
title: "Question regarding Chromium Web Browser"
date: 2012-06-23
forum: General Help
---

### Post by craig10x on 2012-06-23
I was just wondering....does ubuntu send down updated versions for chromium stable web browser...or do you need to add the ppa in order to get updated versions?

Thanks;)

---

### Post by garyzw on 2012-06-23
You have to add it to the ppa

Open Terminal and enter the following--

sudo add-apt-repository ppa:chromium-daily/stable 
sudo apt-get update
sudo apt-get install chromium-browser

---

### Post by craig10x on 2012-06-23
Thank you very much...i thought that might be the case... ;)

---

### Post by vasa1 on 2012-06-23
BTW, AFAIK, Google doesn't claim that **any** build of Chromium is **stable**. The only stable browser that they release and label as such is **Chrome** stable. I don't know why and how Ubuntu has the "Chromium stable".

---

### Post by garyzw on 2012-06-23
That is true but I have not had any problems with Chromium-- I heard that Google adds some sort of tracking to Chrome so that is why I went with Chromium.

> **vasa1 said:**
> BTW, AFAIK, Google doesn't claim that **any** build of Chromium is **stable**. The only stable browser that they release and label as such is **Chrome** stable. I don't know why and how Ubuntu has the "Chromium stable".

---

### Post by elliotn on 2012-06-23
track or no tracking most browsers tracks our usage anyway

---

### Post by vasa1 on 2012-06-23
> **garyzw said:**
> That is true but I have not had any problems with Chromium-- I heard that Google adds some sort of tracking to Chrome so that is why I went with Chromium.

Yes, we hear about that quite often, don't we.

But I still feel that it is not correct for Ubuntu to have something called Chromium stable when Google (or chromium.org) doesn't have any such thing. It is incorrect, IMO, in the sense that Chrome stable has undergone more stability testing and possible improvements to stability that isn't "backported", if that's the right term, to older Chromium builds.

---

### Post by garyzw on 2012-06-23
Chromium has an add on called Do Not Track Plus-- Google Chrome may have it also I don't know.

> **elliotn said:**
> track or no tracking most browsers tracks our usage anyway

---

### Post by garyzw on 2012-06-23
I agree!

> **vasa1 said:**
> Yes, we hear about that quite often, don't we.

But I still feel that it is not correct for Ubuntu to have something called Chromium stable when Google (or chromium.org) doesn't have any such thing. It is incorrect, IMO, in the sense that Chrome stable has undergone more stability testing and possible improvements to stability that isn't "backported", if that's the right term, to older Chromium builds.

---

### Post by craig10x on 2012-06-24
According to the Chromium development site, the chromium stable is what gets released to chrome for their stable, so it is supposed to be the same as far as stability....

Of course, Chrome does add a few things to it, like the auto updater, the tracker, and the built in pdf reader as well as a flash plug which chromium doesn't include...

I am currently using Chrome, though sometime the flash is a little unstable...i was think of switching to Chromium because i thought flash might be a bit more stable in it (since it doesn't have a separate flash plug in)...

Any thoughts on that? :D

---

### Post by elliotn on 2012-06-24
FF still does it for me, I am so used to Firefox that chrome is just a backup browser in case anything happen with ff

---

### Post by garyzw on 2012-06-24
I have been using chromium for about 4 months now and have never had a problem. I have never used Chrome so I can't compare the 2. 

> **craig10x said:**
> According to the Chromium development site, the chromium stable is what gets released to chrome for their stable, so it is supposed to be the same as far as stability....

Of course, Chrome does add a few things to it, like the auto updater, the tracker, and the built in pdf reader as well as a flash plug which chromium doesn't include...

I am currently using Chrome, though sometime the flash is a little unstable...i was think of switching to Chromium because i thought flash might be a bit more stable in it (since it doesn't have a separate flash plug in)...

Any thoughts on that? :D

---

### Post by vasa1 on 2012-06-24
> **craig10x said:**
> According to the Chromium development site, the chromium stable is what gets released to chrome for their stable, so it is supposed to be the same as far as stability...
**If you don't mind, can you point me to the exact relevant quote and exact link**? I'd appreciate that.
My reason for arguing against that is that, IMO, a Chromium build is taken possibly to Canary first, but definitely to dev and then beta and thus undergoes further testing and improvements.

IMO, it's not that a particular Chromium build is picked up and directly converted to Chrome stable.  

Again, IMO, weeks elapse before what started off as a Chromium build ultimately becomes Chrome stable.

BTW, you can check this, FWIW: [http://productforums.google.com/forum/#!topic/chrome/le35xvI8ZP4](http://productforums.google.com/forum/#!topic/chrome/le35xvI8ZP4)

---

### Post by craig10x on 2012-06-24
This is a bit confusing...are you saying that chromium stable never gets any improvements and updates that chrome makes to it...does chrome actually make any improvements after they get it (other then the features they add on)...

Anyone know anything about this?

Also, regarding the flash issue...has anyone who switched from Chrome to Chromium noted any extra flash stability...

main problems i seem to have with flash in Chrome is when listening to a radio stream (those are flash players) i get an occasional "echo" (where the guy is talking and a word gets repeated twice) and sometimes on you tube videos, there is a drop out of the audio for a second or so)...

Though i never use to get that on gnome 2, so don't know if it is some kind of interaction between gnome 3 and the hardware on my laptop...I have a rather new toshiba laptop with intel i3 core processor and intel graphics card...

This doesn't happen on firefox....but i prefer Chrome myself...

---

### Post by vasa1 on 2012-06-24
> **craig10x said:**
> This is a bit confusing...are you saying that chromium stable never gets any improvements and updates that chrome makes to it...does chrome actually make any improvements after they get it (other then the features they add on)...
...
What I'm staying with right now is the phrase "Chromium stable". **Where does that come from? On what basis does Launchpad refer to "Chromium stable"**?
My understanding is that Chromium builds are automatically generated and that Google picks a build on certain criteria and processes it further to produce a dev version, then a beta version and then a stable version.

---

### Post by vasa1 on 2012-06-24
Those interested can look here:
[https://chromium-build.appspot.com/p/chromium/console](https://chromium-build.appspot.com/p/chromium/console)

If I understand correctly, a certain Chromium build is promoted to "trunk" based on the "waterfall" and that build, after further testing and stabilization, will become Chrome dev, then Chrome beta and finally Chrome stable.

Anyway, until someone shows convincing proof that there is actually something that _is_ Chromium stable and not just called Chromium stable, I'll keep muttering to myself that there's no such thing ;)

---

### Post by craig10x on 2012-06-26
> **vasa1 said:**
> Those interested can look here:
[https://chromium-build.appspot.com/p/chromium/console](https://chromium-build.appspot.com/p/chromium/console)

If I understand correctly, a certain Chromium build is promoted to "trunk" based on the "waterfall" and that build, after further testing and stabilization, will become Chrome dev, then Chrome beta and finally Chrome stable.

Anyway, until someone shows convincing proof that there is actually something that _is_ Chromium stable and not just called Chromium stable, I'll keep muttering to myself that there's no such thing ;)

Actually, it is explained right here: (taken from the chromium builds web page)
The stable ppa (which is not the same ppa as the normal daily builds) matches with chrome's stable channel releases...so they ARE identical...

Chromium - Stable Channel
&#8220;Chromium Builds&#8221; team Chromium - Stable Channel
PPA description

Stable Channel of Chromium for Ubuntu, matching the Google Chrome Stable Channel for Linux


PS: the ppa for chomium stable releases is:

sudo add-apt-repository ppa:chromium-daily/stable

---

### Post by GreatDanton on 2012-06-26
This is a little bit confusing. So Chromium is not browser from Google or it is? As far as I know Google browser is Chrome, but what is Chromium then? Browser like firefox, opera ,...?

---

### Post by craig10x on 2012-06-26
Chromium is the open source version of Chrome on which Chrome is based...
Chomium is what you get from the ubuntu software center...Chrome is what you get from Chrome's website...

Chrome takes Chromium and brands it (changes the icon to the chrome colors) and also adds some extra features like a built in pdf reader in the browser (not on chromium) and adobe flash plug in within the browser (again...not on chromium)

They also add an updater for the latest versions (a ppa in your ubuntu updater)...for chromium, you have to add that in manually...

Those are the main differences...actually, i have decided to stay with Chrome myself (directly from google)...there is no real advantage to using chromium over chrome but the reverse is certainly true (LOL)...

Hope that helps...

---

### Post by 3Miro on 2012-06-26
There is terminology here that needs to be cleared. Chromium never releases "builds" to Chrome. There is source-code and then there is a build. Chromium gives source code to Chrome and then Chrome adds extra stuff and makes the Chrome source code, which is closed, and the Chrome source code is compiled into the Chrome build. My guess is that in many cases different packages can come with different builds, as the code has been compiled with slightly different options or patches and modifications for different packages for different distributions.

There is a Chromium channel that comes straight form the Chromium project and provides some builds for some distributions. I don't know if they call those builds stable or beta.

Ubuntu and other distributions (i.e. Arch) take the Chromium source code, usually patch it in one way or another and then make their own Chromium builds. At this point, they can call it whatever they feel like, Chromium stable is the most stable version of Chromium that is coming from Canonical.

When the software is open, the difference between Stable and Beta is very blurry. Many projects have only released "beta" versions of their products, while at the same time distributions market builds as "stable". Ultimately, stable vs beta is not determined by the number of bugs present, but rather whether or not the software has been released as a "final version" or not. Ultimately, the distinction is very arbitrary.

---

### Post by GreatDanton on 2012-06-27
Thank you for your explanation. Now I see the difference.

---

### Post by craig10x on 2012-06-27
No problem...glad to clear that up for you! :D

I prefer to use Chrome myself..because of the extra features it can provide (since they can include certain licensed stuff like the built in pdf reader which can be very handy if you just want to view a pdf file without actually downloading to your hard drive...of course that option is still available if you want to by right clicking on it)...the built in flash plug in and some other codecs that chromium is not allowed to include...plus the auto-updater of course...

---

### Post by vasa1 on 2012-06-27
> **craig10x said:**
> ...plus the auto-updater of course...
Does the "auto-updater" work?

---

### Post by craig10x on 2012-06-27
It sure does...what happens is that when you originally downloaded Google Chrome's deb file and installed it, it also adds a ppa to your Update Manager in ubuntu...it is a Google Chrome repo and you get each new stable version of Google Chrome, within your update manager, as soon as it is released...

For example, today, when my updates came in, there was the new version on the update list and i got the new version when i did all my updates in the update manager...;)

---

### Post by vasa1 on 2012-06-27
> **craig10x said:**
> It sure does...what happens is that when you originally downloaded Google Chrome's deb file and installed it, it also adds a ppa to your Update Manager in ubuntu...it is a Google Chrome repo and you get each new stable version of Google Chrome, within your update manager, as soon as it is released...

For example, today, when my updates came in, there was the new version on the update list and i got the new version when i did all my updates in the update manager...;)
AFAIK, that's just conventional updating via apt-get. Auto-updates can be seen if one installs Firefox directly from Mozilla and not via a ppa. The updates are differential (delta) and are usually much smaller than a full-size download.
To my knowledge, Chrome doesn't support auto-updating on Linux systems but it does so on Windows.

---

### Post by 3Miro on 2012-06-27
If you install Google-Chrome .deb file, it will automatically add a ppa that will alert your or updates via the regular Ubuntu Update Manager. In the same way, if you use Chromium ppa, you will get Chromium updates. This is the Linux proper and consistent way to do things.

If Firefox is doing something different for the versions added directly from mozilla, then Firefox is not following the standards.

Windows is naturally a different story, there is no ppa or central repository, every program needs to do its own updates.

Chrome adds flash and .pdf reader, but those are not Freedom programs. The only time I would use restrictive software is when there is no freedom alternative. Even when I use restrictive software, I still treat it as if it is released under GPL. I would say there are definite advantages to using Chromium.

---

### Post by vasa1 on 2012-06-28
> **vasa1 said:**
> AFAIK, that's just conventional updating via apt-get. **Auto-updates can be seen if one installs Firefox directly from Mozilla and not via a ppa.** The updates are differential (delta) and are usually much smaller than a full-size download.
To my knowledge, Chrome doesn't support auto-updating on Linux systems but it does so on Windows.
The part in bold should be "Auto-updates can be seen if one installs Firefox directly from Mozilla **in one's home folder** and not via a ppa."

---

### Post by daKoolaid on 2012-07-18
Have any of you used snapshots from this link?
[http://commondatastorage.googleapis.com/chromium-browser-continuous/index.html](http://commondatastorage.googleapis.com/chromium-browser-continuous/index.html)

How's the stability with the continuous builds? It seems the Ubuntu and Chromium PPAs are indefinitely frozen at Chromium 18. :(

---

### Post by malspa on 2012-07-18
> **garyzw said:**
> You have to add it to the ppa

Open Terminal and enter the following--

sudo add-apt-repository ppa:chromium-daily/stable 
sudo apt-get update

> **daKoolaid said:**
> It seems the Ubuntu and Chromium PPAs are indefinitely frozen at Chromium 18. :(

Wondering about this myself. Still at 18.0.1025.168~r134367-0ubuntu0.12.04.1 here.

---

### Post by Hungry Man on 2012-07-18
The auto-updater is not packaged in the Linux version. That's Windows/OSX Only. There's no need on Windows.

The Chromium PPAs are frozen - don't use them. There have been significant security measures taken and lots of patches since those releases. It's kinda irresponsible for Ubuntu to leave them in but outside of them compiling it themselves there's nothing to do.

Anyways, Chrome is Chromium but with Flash, PDF, and proprietary codecs support. So I see absolutely no reason to choose Chromium over it.

---

### Post by malspa on 2012-07-18
I would prefer to use Chromium, but not if it receives no updates. I disabled the Chromium PPA and installed Chrome.

---

### Post by 3Miro on 2012-07-18
Ubuntu does provide security updates for Chromium, what you don't get is the next version. This is just like Firefox, Ubuntu 10.04 is still using Firefox 3.5 and if you want a newer version, then you need to add a ppa.

---

### Post by malspa on 2012-07-18
Well, ppa:chromium-daily/stable is still at the same version that's in the Precise repos. Latest upload May 1st, according to this page: [https://launchpad.net/~chromium-daily/+archive/stable](https://launchpad.net/~chromium-daily/+archive/stable)

---

### Post by daKoolaid on 2012-07-18
> **3Miro said:**
> Ubuntu does provide security updates for Chromium, what you don't get is the next version. This is just like Firefox, Ubuntu 10.04 is still using Firefox 3.5 and if you want a newer version, then you need to add a ppa.
Ok, that's fine then for me. I don't have any problem with using version 18 as long as it keeps up with security updates.

---

### Post by Tommy on 2012-07-18
> **3Miro said:**
> Ubuntu does provide security updates for Chromium, what you don't get is the next version. This is just like Firefox, Ubuntu 10.04 is still using Firefox 3.5 and if you want a newer version, then you need to add a ppa.

I'm running Ubuntu 10.04 and it has been being updated beyond 3.x. Today it just updated to Firefox 14.0.1. 

I believe Ubuntu changed their policy on updates for some special packages, such as Firefox and Thunderbird, and of course the LTS versions (such as Ubuntu 10.4 Lucid Lynx and the current 12.04 Precise Pangolin) get extra special treatment, with security updates for all "main" packages, and full update treatment for a few packages, for a longer time than the non-LTS releases.

---

### Post by 3Miro on 2012-07-18
> **Tommy said:**
> I'm running Ubuntu 10.04 and it has been being updated beyond 3.x. Today it just updated to Firefox 14.0.1. 

I believe Ubuntu changed their policy on updates for some special packages, such as Firefox and Thunderbird, and of course the LTS versions (such as Ubuntu 10.4 Lucid Lynx and the current 12.04 Precise Pangolin) get extra special treatment, with security updates for all "main" packages, and full update treatment for a few packages, for a longer time than the non-LTS releases.

Good to know. I heard they are going to change their policy for 12.04 as it will be supported for 5 long years, but I didn't know they had done this for 10.04 as well.

Security updates are included for all packages in the repos, I guess some packages will also see version updates, but there will probably be a delay before you see the updates. This isn't bad, as packages will be tested before shipped.

---

### Post by vasa1 on 2012-07-18
> **daKoolaid said:**
> Ok, that's fine then for me. I don't have any problem with using version 18 as long as **it keeps up with security updates**.
It doesn't. Unfortunately, there's a whole bunch of misconceptions floating about ...

---

### Post by daKoolaid on 2012-07-18
> **vasa1 said:**
> It doesn't. Unfortunately, there's a whole bunch of misconceptions floating about ...
Erm, ok...this is confusing. So then builds from commondatastorage link would be a better idea to use? That's Chromium 23 or something like that, I think. It seems like there's no ppa so I guess it's just download, extract and run.

---

### Post by Lyfang on 2012-07-19
Can be misleading since Ubuntu does release security patches if needed(?) & vulnerabilities are often fixed in what some perceive as "old" packages. However I'm unshure if patches from Ubuntu get directly back upstream (i.e. the Chromium project). Sometimes new or unfixed packages introduce new vulnerabilities. Complete analysis of the source code could probably find some vulnerabilities but could be a subject too often overlooked as a lack of resources.

---

### Post by vasa1 on 2012-07-19
> **Lyfang said:**
> Can be misleading since Ubuntu does release security patches if needed(?) & vulnerabilities are often fixed in what some perceive as "old" packages. However I'm unshure if patches from Ubuntu get directly back upstream (i.e. the Chromium project). Sometimes new or unfixed packages introduce new vulnerabilities. Complete analysis of the source code could probably find some vulnerabilities but could be a subject too often overlooked as a lack of resources.
Is the implication that Chromium 18 is being patched and is on par in terms of security with more recent versions of Chromium?

---

### Post by Frogs Hair on 2012-07-19
There are a number of browsers based on the open source Chromium project . I have tried Chromium (Ubuntu), Iron , and Commando Dragon, (Windows) and Chrome . Chrome stable includes coedecs the others don't and updates automatically in Ubuntu.Commando(Windows) is the only one that _might_offer any real privacy advantage.

---

### Post by vasa1 on 2012-07-19
> **Frogs Hair said:**
> There are a number of browsers based on the open source Chromium project . I have tried Chromium (Ubuntu), Iron , and Commando Dragon, (Windows) and Chrome . Chrome stable includes coedecs the others don't and updates automatically in Ubuntu.Commando(Windows) is the only one that _might_offer any real privacy advantage.
Comodo Dragon.

---

### Post by epikvision on 2012-07-19
I also run Chrome on Ubuntu, but the open source variant is just as strong, despite not having the word "stable" appended to it.  Since Chromium is linked to the ppa, you can expect more updates from it than from Chrome. 

I for one will consider making the move back to Chromium soon...

---

### Post by Lyfang on 2012-07-19
> **vasa1 said:**
> Is the implication that Chromium 18 is being patched and is on par in terms of security with more recent versions of Chromium?
From my understanding the Chromium package is maintained as long as you are using an updated & supported version of Ubuntu, security patches should be released if needed(?). Hopefully all vulnerability are fixed. E.g. Ubuntu 10.04 LTS security update: USN-1509-1: Firefox vulnerabilities - 17th July 2012 Source: [http://www.ubuntu.com/usn/lucid/](http://www.ubuntu.com/usn/lucid/) Ubuntu 10.04 LTS was released April 29, 2010 & received an update for Firefox 17th July 2012. I have updated Adobe Flash Player on Chromium to version 11.3.31.103. See: [Re: Chromium Flash Pepper on precise, how?]("http://ubuntuforums.org/showpost.php?p=12072504&postcount=13")

---

### Post by Lyfang on 2012-07-23
Security related issues update from the official repository? (Some text in Swedish, sorry for the inconvenience)
chromium-browser (version 18.0.1025.151~r130497-0ubuntu1) kommer uppgraderas till version 18.0.1025.168~r134367-0ubuntu0.12.04.1

Ändringar för versionerna:
Installerad version: 18.0.1025.151~r130497-0ubuntu1
Tillgänglig version: 18.0.1025.168~r134367-0ubuntu0.12.04.1

Version 18.0.1025.168~r134367-0ubuntu0.12.04.1: 

  * New upstream release from the Stable Channel (LP: #992352)
    - [106413] High CVE-2011-3078: Use after free in floats handling. Credit to
      Google Chrome Security Team (Marty Barbella) and independent later
      discovery by miaubiz.
    - [117110] High CVE-2012-1521: Use after free in xml parser. Credit to
      Google Chrome Security Team (SkyLined) and independent later discovery by
      wushi of team509 reported through iDefense VCP (V-874rcfpq7z).
    - [117627] Medium CVE-2011-3079: IPC validation failure. Credit to PinkiePie
    - [121726] Medium CVE-2011-3080: Race condition in sandbox IPC. Credit to
      Willem Pinckaers of Matasano.
    - [121899] High CVE-2011-3081: Use after free in floats handling.
      Credit to miaubiz.

---

### Post by vasa1 on 2012-07-23
**Lyfang, I appreciate your last post**. You've actually given specifics.
However, I request you to look at this page:
[http://googlechromereleases.blogspot.com/search?updated-max=2012-07-12T21:26:00-07:00&max-results=7](http://googlechromereleases.blogspot.com/search?updated-max=2012-07-12T21:26:00-07:00&max-results=7)
and to look at the entries for _Chrome_ Stable dated July 11, 2012. You'll see that the security fixes mentioned there, one of them is high, aren't in the list your provided.

There is also this caveat: *Note that the referenced bugs may be kept private until a majority of our users are up to date with the fix*.

I don't mean to downplay the efforts of the Community and I have no right to do so, but in such a fast-paced field, my personal feeling is that the actual developers of the browser should be entrusted with the "security" aspect.

The Community could focus on an extension that ensures that a browser integrates well with the desktop environment.

We should keep in mind that the community-modded browser, generally speaking, was manageable in the past when development was rather leisurely. Now, development is hectic.

---

### Post by vasa1 on 2012-07-23
A little more ...
The list Lyfang put up can also be found here: [http://www.release-note.com/internet/browser/chrome/2996-google-chrome-18-0-1025-168.html](http://www.release-note.com/internet/browser/chrome/2996-google-chrome-18-0-1025-168.html) and that's "Created on Monday, 30 April 2012 21:57"

---

### Post by vasa1 on 2012-07-23
> **Lyfang said:**
> From my understanding the Chromium package is maintained as long as you are using an updated & supported version of Ubuntu, security patches should be released if needed(?). Hopefully all vulnerability are fixed. E.g. Ubuntu 10.04 LTS security update: USN-1509-1: Firefox vulnerabilities - 17th July 2012 Source: [http://www.ubuntu.com/usn/lucid/](http://www.ubuntu.com/usn/lucid/) Ubuntu 10.04 LTS was released April 29, 2010 & received an update for Firefox 17th July 2012. I have updated Adobe Flash Player on Chromium to version 11.3.31.103. See: [Re: Chromium Flash Pepper on precise, how?]("http://ubuntuforums.org/showpost.php?p=12072504&postcount=13")

A comparison of patching Firefox and Chromium may not be appropriate as has been pointed out [here]("http://askubuntu.com/a/166939/25656"): the former is in Main and is directly supported by Canonical; the latter is in Universe and is dependent on the effort of Community volunteers.

---

### Post by oslub on 2012-07-24
I read all five pages of replies to the thread and I am still very confused about this.

My default browser is Firefox, however while it is great running on  Ubuntu, it is a bit problematic with me on Windows, where Chrome has better performance. However I switched to Comodo Dragon, preventing privacy issues and keeping the same quality. I wish Comodo could make a solid version of Dragon for Linux soon enough.

Anyway, I would like to know about  Chromium because not only it is by far the second best browser on Linux  after Firefox (Opera is good as browser but some websites do not display  correctly on it), but also because it is always useful to have a  secondary browser, in case of failure of the default browser and most  importantly, because Adobe will no longer support Flash for Linux,  leaving it for Google Chrome releases via pepper, whereas Firefox apparently will not have the same treatment, leaving us dependent on Chrome only to enjoy latest Flash updates, which is not good at all, because Flash will still be around the web for quite some years, thus forcing us to use Google Chrome. That is not nice.

I understand that Firefox is main and Chromium is universe, the latter is dependent on the community, and as far as I know, Firefox has special treatment on 12.04 LTS version because it will get full updates, same with Thunderbird I guess. 

A bit off topic, but is that the same reason why Gimp hasn't been updated to version 2.8 yet on Ubuntu? Because it is not main? Does it mean that for 5 years of LTS period, I have to use Gimp 2.6? If so, how do I upgrade Gimp to the latest version?

Returning to Chromium, the version which is present now on Ubuntu 12.04 updated to latest is 18.0.1025.168 (Programmer Compilation 134367 Linux) Built on Ubuntu 12.04.

How updated is this version of Chromium? Are the features and the security at the same level as the ones provided by Google Chrome? Does the current version of Chromium have security vulnerabilities that are already fixed on latest Google Chrome Stable? Is Chromium provided by Ubuntu the latest version of Chromium builds available and the one used on Google Chrome stable, or is it used on developers version first and only then on Beta and Stable? What is the current involvement of Ubuntu team in Chromium?
  
These are very frequently asked question on askubuntu, someone really should make this clear, specially about the level of security of Chromium, we need to know if it is completely safe to use Chromium browser.

About privacy issues, I have some too, I know that Google Chrome gives each user a unique ID, enabling them to do profiling and also everything we submit on the url bar is sent to Google, even if it is not a search on Google engine, so yes, a stripped version of Chrome but equally safe and with the new features added by Google (not the tracking ones) would be welcome.

---

### Post by Lyfang on 2012-07-24
> **oslub said:**
> I read all five pages of replies to the thread and I am still very confused about this.

My default browser is Firefox, however while it is great running on  Ubuntu, it is a bit problematic with me on Windows, where Comodo Dragon  is having better performance. I wish Comodo makes a version of their  browser for Linux soon enough. 

Anyway, I would like to know about  Chromium because not only it is by far the second best browser on Linux  after Firefox (Opera is good as browser but some websites do not display  correctly on it), but also because it is always useful to have a  secondary browser, in case of failure of the default browser and most  importantly, because Adobe will no longer support Flash for Linux,  leaving it for Google Chrome releases via pepper, whereas Firefox apparently will not have the same treatment, leaving us dependent on Chrome only to enjoy latest Flash updates, which is not good at all, because Flash will still be around the web for quite some years, thus forcing us to use Google Chrome. That is not nice.
"Comodo Dragon. – A Chromium technology-based Browser". Why not use Chromium on Linux with Pepper Flash?
> **oslub said:**
> I understand that Firefox is main and Chromium is universe, the latter is dependent on the community, and as far as I know, Firefox has special treatment on 12.04 LTS version because it will get full updates, same with Thunderbird I guess. 

A bit off topic, but is that the same reason why Gimp hasn't been updated to version 2.8 yet on Ubuntu? Because it is not main? Does it mean that for 5 years of LTS period, I have to use Gimp 2.6? If so, how do I upgrade Gimp to the latest version?
Ubuntu is a stable-release distribution. Search for a GIMP PPA for your distribution, use at your own risk (as usual).
> **oslub said:**
> Returning to Chromium, the version which is present now on Ubuntu 12.04 updated to latest is 18.0.1025.168 (Programmer Compilation 134367 Linux) Built on Ubuntu 12.04.

How updated is this version of Chromium? Are the features and the security at the same level as the ones provided by Google Chrome? Does the current version of Chromium have security vulnerabilities that are already fixed on latest Google Chrome Stable? Is Chromium provided by Ubuntu the latest version of Chromium builds available and the one used on Google Chrome stable, or is it used on developers version first and only then on Beta and Stable? What is the current involvement of Ubuntu team in Chromium?
  
These are very frequently asked question on askubuntu, someone really should make this clear, specially about the level of security of Chromium, we need to know if it is completely safe to use Chromium browser.

About privacy issues, I have some too, I know that Google Chrome gives each user a unique ID, enabling them to do profiling and also everything we submit on the url bar is sent to Google, even if it is not a search on Google engine, so yes, a stripped version of Chrome but equally safe and with the new features added by Google (not the tracking ones) would be welcome.
It's  probably quite safe to use the Chromium browser. I pretty shure that Chromium as well as other web browsers currently have security vulnerabilities. As mentioned before I choosed to update Adobe Flash Player on Chromium. My guess is Google Chrome is more secure than Chromium in this case, because Google will update their repository more often than the universe repository & they will also update Pepper Flash for you too, automatically.

---

### Post by Lyfang on 2012-07-30
> **Lyfang said:**
> Google will update their repository more often than the universe repository
Use a PPA for a more up to date version of Chromium: [For all you Chromium fans]("http://ubuntuforums.org/showthread.php?t=2035166")

---

### Post by Lyfang on 2012-09-22
The Chromium package is maintained and was updated from the official repository to Chromium 20.0.1132.47 Ubuntu 12.04 (chromium-browser --version). I have updated Adobe Flash Player on Chromium to version 11.3.31.232. See how at: [Re: Chromium Flash Pepper on precise, how?]("http://ubuntuforums.org/showpost.php?p=12072504&postcount=13")

---

### Post by malspa on 2012-09-22
> **Lyfang said:**
> The Chromium package is maintained and was updated from the official repository to Chromium 20.0.1132.47 Ubuntu 12.04 (chromium-browser --version).

chromium-browser 21.0.1180.89 is available from the ppa that was mentioned here: [http://www.webupd8.org/2012/09/new-chromium-stable-and-development.html](http://www.webupd8.org/2012/09/new-chromium-stable-and-development.html)

---

### Post by Lloydb39 on 2012-09-22
My two cents worth. I use Chrome in Windows because it is faster and better than Firefox. I was using Firefox in Ubuntu 12.04 but switched to Chromium. Everything -- especially Facebook -- slowed down considerably. In fact, some Facebook functions wouldn't work at all. I went back to Firefox.

---

### Post by Lyfang on 2012-10-11
Google Chrome 22.0.1229.94 patched after SVG compromise exploit at Pwnium 2 [http://googlechromereleases.blogspot.se/2012/10/stable-channel-update_6105.html](http://googlechromereleases.blogspot.se/2012/10/stable-channel-update_6105.html). I'm running Chromium 20.0.1132.47 Ubuntu 12.04 (chromium-browser --version) from the official repository. Do I need to add the PPA for a security fix as soon as possible?
> **Hungry Man said:**
> The Chromium PPAs are frozen - don't use them. There have been significant security measures taken and lots of patches since those releases.
Which PPA to choose for a security patch today?

Chromium - Stable Channel (20.0.1132.47~r144678-0ubuntu0.12.04.1)
```
sudo add-apt-repository ppa:chromium-daily/stable 
sudo apt-get update
sudo apt-get install chromium-browser
```

[NEW CHROMIUM STABLE AND DEVELOPMENT PPAS FOR UBUNTU 12.04]("http://www.webupd8.org/2012/09/new-chromium-stable-and-development.html")

Stable PPA (22.0.1229.79~svn20121006r160576-0ubuntu1~precise1)
```
sudo add-apt-repository ppa:a-v-shkop/chromium
sudo apt-get update
sudo apt-get install chromium-browser
```

Latest dev builds PPA (23.0.1271.10~r158896svn20121001-0ubuntu1~precise1)
```
sudo add-apt-repository ppa:a-v-shkop/chromium-dev
sudo apt-get update
sudo apt-get install chromium-browser
```

---

### Post by Lyfang on 2012-10-29
> **Lyfang said:**
> Google Chrome 22.0.1229.94 patched after SVG compromise exploit at Pwnium 2 [http://googlechromereleases.blogspot.se/2012/10/stable-channel-update_6105.html](http://googlechromereleases.blogspot.se/2012/10/stable-channel-update_6105.html). I'm running Chromium 20.0.1132.47 Ubuntu 12.04 (chromium-browser --version) from the official repository. Do I need to add the PPA for a security fix as soon as possible?

Which PPA to choose for a security patch today?
The official Ubuntu repository has been updated. I'm using Chromium Version 22.0.1229.94 Ubuntu 12.10 (161065). Synaptic package manager shows version 22.0.1229.94~r161065-0ubuntu1.

---

### Post by Lyfang on 2012-11-20
> **Lyfang said:**
> Google will update their repository more often than the universe repository
As of today I ran Google Chrome 23.0.1271.64 stable with Adobe Pepper Flash Player 11.5.31.2
> **vasa1 said:**
> Again, IMO, weeks elapse before what started off as a Chromium build ultimately becomes Chrome stable.
I don't know if Chromium is experiencing the same problem but I have a problem on Facebook with Chrome.
> **Lloydb39 said:**
> Facebook -- slowed down considerably. In fact, some Facebook functions wouldn't work at all. I went back to Firefox.
Facebook layout on Chrome didn't work as expected.

Maybe there is no problem with testing each Chromium build a little bit more before releasing the browsers as "stable" (interpretation of the word stable on Chromium builds)?

---

### Post by Lyfang on 2012-12-04
> **Lyfang said:**
> The official Ubuntu repository has been updated. I'm using Chromium Version 22.0.1229.94 Ubuntu 12.10 (161065). Synaptic package manager shows version 22.0.1229.94~r161065-0ubuntu1.

Quote from October 30th, 2012. I'm still using Version 22.0.1229.94 Ubuntu 12.10 (161065). It's a long time since last (Ubuntu repository) Chromium update. However I have manually updated Pepper Flash to 11.5.31.2 with Chromium. See how to at: [http://ubuntuforums.org/showpost.php?p=12388167&postcount=19](http://ubuntuforums.org/showpost.php?p=12388167&postcount=19)

---

### Post by Lyfang on 2012-12-12
> **Lyfang said:**
> Quote from October 30th, 2012. I'm still using Version 22.0.1229.94 Ubuntu 12.10 (161065). It's a long time since last (Ubuntu repository) Chromium update. However I have manually updated Pepper Flash to 11.5.31.2 with Chromium. See how to at: [http://ubuntuforums.org/showpost.php?p=12388167&postcount=19](http://ubuntuforums.org/showpost.php?p=12388167&postcount=19)
I was still using version 22.0.1229.94 from the official Ubuntu repository today, so I did the following:
```
sudo add-apt-repository ppa:a-v-shkop/chromium
sudo apt-get update
sudo apt-get install chromium-browser
```
I'm using Chromium version 23.0.1271.64 Ubuntu 12.10 (165188) now, Synaptic shows version: 23.0.1271.64~svn20121110r165188-0ubuntu1~quantal1.

---


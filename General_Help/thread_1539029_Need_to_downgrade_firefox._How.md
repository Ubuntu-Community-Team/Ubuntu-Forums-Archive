---
title: "Need to downgrade firefox. How?"
date: 2010-07-26
forum: General Help
---

### Post by Demented666 on 2010-07-26
Not sure how, but update manager ran and installed new files. My back-up file also got deleted, so I can't even revert to how things were last night, unless there is a way I don't know of to return the computer to a previous time before major updates.

Anyway, how on earth do you go from FireFox 3.6.7 to 3.5.x? I've searched other threads, but all are useless in explaining how. This is in Ubuntu 9.10

---

### Post by kmsalex on 2010-07-26
If i remember correctly 9.10 does'nt upgrade to the 3.6 line, when i had it i waited almost a month and eventually had to install it my self. but regardless of that why would you want to stay with the 3.5 line anyway? the only difference is a slight speed increases and  now as of 3.6.4 the plug-ins like flash run as a separate process. I'd stay with 3.6.7 my self.;)

---

### Post by lovinglinux on 2010-07-26
> **kmsalex said:**
> If i remember correctly 9.10 does'nt upgrade to the 3.6 line, when i had it i waited almost a month and eventually had to install it my self. but regardless of that why would you want to stay with the 3.5 line anyway? the only difference is a slight speed increases and  now as of 3.6.4 the plug-ins like flash run as a separate process. I'd stay with 3.6.7 my self.;)

In fact [Firefox 3.6 has been pushed to all supported Ubuntu versions]("http://ubuntuforums.org/showthread.php?t=1500861").

> **Demented666 said:**
> Anyway, how on earth do you go from FireFox 3.6.7 to 3.5.x? I've searched other threads, but all are useless in explaining how. This is in Ubuntu 9.10

Before trying to downgrade, please explain your problems so we can try to fix them. Keep in mind the current version of Firefox available in the repositories, which is 3.6.7 has stability issues and Mozilla already released version 3.6.8, which should be available soon.

---

### Post by Demented666 on 2010-07-26
I dislike it, have issues on a few sites, and can't get the majority of the addons that I used to work.

I don't care for even attempting to "fix" any issues, other then downgrading.

---

### Post by NFblaze on 2010-07-26
I'm at work (and using Windows), but if memory serves correctly

In Administration > Synaptic

1.Type Firefox.
2.Mark for Removal.
3.Apply Changes
4.Type Firefox
5.Select Firefox (do not install yet)
6.Look at the Tab Row should be something like Information, Dependencies, Installed Files, Package Version
7.Select Package Version tab
8.In theory it should list available packages. You should be able to right click and FORCE a version to install.

After that. you can install.

---

### Post by Demented666 on 2010-07-26
> **NFblaze said:**
> I'm at work (and using Windows), but if memory serves correctly

In Administration > Synaptic

1.Type Firefox.
2.Mark for Removal.
3.Apply Changes
4.Type Firefox
5.Select Firefox (do not install yet)
6.Look at the Tab Row should be something like Information, Dependencies, Installed Files, Package Version
7.Select Package Version tab
8.In theory it should list available packages. You should be able to right click and FORCE a version to install.

After that. you can install.
I just tried that but no luck. The ubufox package keeps breaking, and when I go to install it after forcing 3.5.3, it still tries to install 3.6.7 but fails because nothing can be authenticated. Tried about 5 times with the same result.

---

### Post by lovinglinux on 2010-07-26
> **Demented666 said:**
> I dislike it, have issues on a few sites, and can't get the majority of the addons that I used to work.

I don't care for even attempting to "fix" any issues, other then downgrading.

Firefox 3.6 is not much different than 3.5.  There aren't many reasons why an extension that work with Firefox 3.5 should not work with 3.6. Have you tried to update them? If you are using extensions from the repositories and they are not updated, grab the newest version from Mozilla site. If they still don't work, because the developers didn't update them, then you can force installation by disabling compatibility check. The easiest way of doing that is to install [Add-on Compatibility Reporter](https://addons.mozilla.org/en-US/firefox/addon/15003/).

Can you post some the sites that aren't working? 

If you have serious issues with it, then instead of going through the trouble of downgrading, grab 3.6.8 from Mozilla or whatever version rock your boat, extract it and run it from your home directory, until a better version come through the official repositories. More info on how to install Firefox versions manually are available at [http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html).

Also, please check this thread: [http://ubuntuforums.org/showthread.php?t=1539100](http://ubuntuforums.org/showthread.php?t=1539100)

---

### Post by Demented666 on 2010-07-26
I'd rather just downgrade to what I had, what I liked, and what was working, then go through this headache of trying to fix things to get this update to work right for me.'

That link to manually install doesn't help much. No matter what I do, I can only get 3.6.7 on.

---

### Post by NFblaze on 2010-07-26
Well, you can always do the manual compile of 3.5 by downloading 3.5.11 from Firefox website. Probrably your best bet.

(Another thing are the 3.5 .debs off of packages.ubuntu.com)

Just thought of one more. I dont know what version your using but if you have the LiveCD with 3.5, still. You can try removing all of firefox. Open your Update Manager settings, change them to only update/install from that LiveCD, then try apt-get install firefox.

---

### Post by Demented666 on 2010-07-26
> **NFblaze said:**
> Well, you can always do the manual compile of 3.5 by downloading 3.5.11 from Firefox website. Probrably your best bet.

(Another thing are the 3.5 .debs off of packages.ubuntu.com)

The only .debs off of packages.ubuntu.com are showing the dummy files, so still it's only 3.6.7. 

I've tried getting 3.5.11 off of Firefox's website as well. I follow the instructions on [http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html). Extract it to the home folder, but when I open it with ~/firefox/firefox, 3.6.7 opens.

---

### Post by Demented666 on 2010-07-26
Nevermind. Guess I'll just have to get used to this 3.6.7 crap. I give up.

---

### Post by mkvnmtr on 2010-07-26
You were told how to uninstall what you have and reinstall from the installation disk. It is easy to do but not as easy as getting this crap version of Firefox working.

---

### Post by lovinglinux on 2010-07-26
> **Demented666 said:**
> The only .debs off of packages.ubuntu.com are showing the dummy files, so still it's only 3.6.7. 

I've tried getting 3.5.11 off of Firefox's website as well. I follow the instructions on [http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html). Extract it to the home folder, but when I open it with ~/firefox/firefox, 3.6.7 opens.

Make sure Firefox is closed and the process firefox-bin is not running, otherwise it will load the version that is still running in the background.

---

### Post by Cavsfan on 2010-07-26
I do not understand anyone wanting to go back from 3.6.7! The latest version is always the best.
I have had absolutely no problems with it and don't understand why other people are and I have 64 bit too.
No flash, java or any other problems...

I was pretty amazed that windows 7 upgraded to FF 3.6.7 about 2 days (at the most) before Ubuntu did!

I do not like bleeding edge beta crap, but I like the latest and greatest. Why not? :o

---

### Post by lovinglinux on 2010-07-26
> **Cavsfan said:**
> I do not understand anyone wanting to go back from 3.6.7! The latest version is always the best.
I have had absolutely no problems with it and don't understand why other people are and I have 64 bit too.
No flash, java or any other problems...

I was pretty amazed that windows 7 upgraded to FF 3.6.7 about 2 days (at the most) before Ubuntu did!

I do not like bleeding edge beta crap, but I like the latest and greatest. Why not? :o

Because you and I are using Lucid Lynx. Most users wanting to downgrade are those who have Hardy, Jaunty and Karmic. See [this](http://ubuntuforums.org/showthread.php?t=1539100).

---

### Post by 98cwitr on 2010-07-26
```
sudo apt-get autoremove
```

After you uninstall firefox...then install the version you want per NFblaze's instructions.

---

### Post by Cavsfan on 2010-07-26
> **lovinglinux said:**
> Because you and I are using Lucid Lynx. Most users wanting to downgrade are those who have Hardy, Jaunty and Karmic. See [this]("http://ubuntuforums.org/showthread.php?t=1539100").

Oh, I see. Thanks for pointing that out. Maybe everyone should be on Lucid...
No, I guess that is everyone's preference. :D

On another thread, I pointed someone to use your Flash-Aid.
I thought it was this thread, but it wasn't.

---

### Post by lovinglinux on 2010-07-26
> **Cavsfan said:**
> Oh, I see. Thanks for pointing that out. Maybe everyone should be on Lucid...
No, I guess that is everyone's preference. :D

On another thread, I pointed someone to use your Flash-Aid.
I thought it was this thread, but it wasn't.

Thanks for that. I have released a new version yesterday.

---

### Post by Cavsfan on 2010-07-26
> **lovinglinux said:**
> Thanks for that. I have released a new version yesterday.

You are most welcome! Does that mean I should also upgrade too?

I am using the most recent version of flash.

---

### Post by lovinglinux on 2010-07-26
> **Cavsfan said:**
> You are most welcome! Does that mean I should also upgrade too?

No. Just make sure you recommend my web site link, because the version on Mozilla site, which is 1.0.5, has some issues that could affect some first-time users (mainly 32bit). It takes some time before the new version appears to the public, because Mozilla needs to review it. It seems whenever I upload a new version, the extension goes to the end of the review queue. Since I have released 1.0.5/6/7/8/9 and 1.0.10 in a short period of time, then it is still unapproved. Version 1.0.10 will take about a week to show up in Mozilla site, if I don't release any new version, which seems unlikely.

---

### Post by Cavsfan on 2010-07-26
> **lovinglinux said:**
> No. Just make sure you recommend my web site link, because the version on Mozilla site, which is 1.0.5, has some issues that could affect some first-time users (mainly 32bit). It takes some time before the new version appears to the public, because Mozilla needs to review it. It seems whenever I upload a new version, the extension goes to the end of the review queue. Since I have released 1.0.5/6/7/8/9 and 1.0.10 in a short period of time, then it is still unapproved. Version 1.0.10 will take about a week to show up in Mozilla site, if I don't release any new version, which seems unlikely.

Thanks! And I will recommend your app for sure! I have it book marked. But I have the Firefox addon page bookmarked! 
I will revise it to this: [U][http://flash-aid-extension.blogspot.com/2010/07/flash-aid-1010-released.html](http://flash-aid-extension.blogspot.com/2010/07/flash-aid-1010-released.html)
[/U] temporarily[U].
[/U]

---

### Post by lovinglinux on 2010-07-26
> **Cavsfan said:**
> Thanks! And I will recommend your app for sure! I have it book marked. But I have the Firefox addon page bookmarked! 
I will revise it to this: [U][http://flash-aid-extension.blogspot.com/2010/07/flash-aid-1010-released.html](http://flash-aid-extension.blogspot.com/2010/07/flash-aid-1010-released.html)
[/U] temporarily[U].
[/U]

Thanks.

---

### Post by Cavsfan on 2010-07-26
> **lovinglinux said:**
> Thanks.

No Problem! I know I have the latest version of Flash as Adobe test says I do, but when I need to 
update I should get your latest Flash-Aid version correct?

Everyone should just get this very useful tool you have created. It is simple to use!

---

### Post by lovinglinux on 2010-07-26
> **Cavsfan said:**
> No Problem! I know I have the latest version of Flash as Adobe test says I do, but when I need to 
update I should get your latest Flash-Aid version correct?

Everyone should just get this very useful tool you have created. It is simple to use!

Is better to get the latest version, since I will make sure that the extension will prompt for flash installation if there is a new version of flash available. Nevertheless, flash is currently installed from the repositories, so it will be updated by the package manager if needed.

---

### Post by Cavsfan on 2010-07-26
> **lovinglinux said:**
> Is better to get the latest version, since I will make sure that the extension will prompt for flash installation if there is a new version of flash available. Nevertheless, flash is currently installed from the repositories, so it will be updated by the package manager if needed.

Think I'll just wait until it is added to FireFox addons, it asked me for a sandbox password when I clicked "Automatic Install".

No biggie a week will be fine for me.

---

### Post by dnguyen1963 on 2010-07-26
> **Cavsfan said:**
> Oh, I see. Thanks for pointing that out. Maybe everyone should be on Lucid...
No, I guess that is everyone's preference. :D

On another thread, I pointed someone to use your Flash-Aid.
I thought it was this thread, but it wasn't.

I have had no trouble running the latest version of Firefox on 8.04 LTS.  BTW, not everyone should upgrade to Lucid...see random freezes thread in this forum.  I have had nothing but trouble with Lucid.

---

### Post by jeight on 2010-09-01
> **Cavsfan said:**
> I do not understand anyone wanting to go back from 3.6.7! The latest version is always the best.
I have had absolutely no problems with it and don't understand why other people are and I have 64 bit too.
No flash, java or any other problems...

I was pretty amazed that windows 7 upgraded to FF 3.6.7 about 2 days (at the most) before Ubuntu did!

I do not like bleeding edge beta crap, but I like the latest and greatest. Why not? :o

You are thinking small. For example, I use the x2go plugin ([www.x2go.org)which]("http://www.x2go.org%29which") works great on 3.5 and even 3.6, but it's not compatible YET with 3.6.7 so I need to downgrade firefox or wait for the updated plugin. You see, not all upgrades are the latest and greatest for everyone. 
And the windows 7 thing... Microsoft doesn't check the source code before allowing programs to be updated, but many Linux distros, aka Ubuntu, do.

---

### Post by Cavsfan on 2010-09-01
> **jeight said:**
> You are thinking small. For example, I use the x2go plugin ([www.x2go.org)which]("http://www.x2go.org%29which") works great on 3.5 and even 3.6, but it's not compatible YET with 3.6.7 so I need to downgrade firefox or wait for the updated plugin. You see, not all upgrades are the latest and greatest for everyone. 
And the windows 7 thing... Microsoft doesn't check the source code before allowing programs to be updated, but many Linux distros, aka Ubuntu, do.

Guess I'll have to think larger in the future... :roll:

I googled **firefox old version linux** and found this -

[[COLOR=blue]_Mozilla Firefox 3.5_[/COLOR]]("http://www.mozilla.com/en-US/firefox/all-older.html")

But, I also found this: "**Jan 26, 2010 ****... Previous *versions* of *Firefox* have public security problems. You could be exposed to viruses, phishing, and other attacks by running *old* ****..."**

---


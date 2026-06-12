---
title: "Update Totally Hosed My Firefox"
date: 2010-04-10
forum: General Help
---

### Post by motsteve on 2010-04-10
I did my normal morning update and one of the items being updated was Firefox (3.6.4).  I accepted the update and when I went to launch Firefox, it launched like normal, but if I tried to go to a web page that required more than a second or two to load, the thumper icon would stop and the window would darken (meaning it was freezing) and I had to force quit the app because it wasn't responding.  I then went and I "rm -rf" the ~/.mozilla directory and relaunched Firefox.  Same result.  I then went through several different ways of reinstalling and removing Firefox using "sudo apt-get install", etc, using Synaptic Package Manager, and using the software center, making sure each time to remove the .mozilla directory.  Same old result.  I finally got desperate and installed epiphany using Synaptic to just  have a browser and it worked like the normal pain it is.

I'm using Karmic 32bit and Firefox 3.6.4 (according to the package manager).

Anyone else having this problem after updating?  I know many hate and blame Flash for Firefox problems, so should I rm the plugins directories containing the files in /usr/lib along with the alternative file in /etc?:confused:

---

### Post by budhi1976 on 2010-04-10
Yes I am experiencing the same problem here, need a solution ASAP.


> **motsteve said:**
> I did my normal morning update and one of the items being updated was Firefox (3.6.4).  I accepted the update and when I went to launch Firefox, it launched like normal, but if I tried to go to a web page that required more than a second or two to load, the thumper icon would stop and the window would darken (meaning it was freezing) and I had to force quit the app because it wasn't responding.  I then went and I "rm -rf" the ~/.mozilla directory and relaunched Firefox.  Same result.  I then went through several different ways of reinstalling and removing Firefox using "sudo apt-get install", etc, using Synaptic Package Manager, and using the software center, making sure each time to remove the .mozilla directory.  Same old result.  I finally got desperate and installed epiphany using Synaptic to just  have a browser and it worked like the normal pain it is.

I'm using Karmic 32bit and Firefox 3.6.4 (according to the package manager).

Anyone else having this problem after updating?  I know many hate and blame Flash for Firefox problems, so should I rm the plugins directories containing the files in /usr/lib along with the alternative file in /etc?:confused:

---

### Post by ATMA3weapon on 2010-04-10
I'm experiencing the same problem over here

---

### Post by warfacegod on 2010-04-10
Try:

```
sudo apt-get purge firefox
```

```
sudo apt-get install firefox
```

That should give you 3.5

---

### Post by motsteve on 2010-04-10
I did that and I got 3.6 again.  I also can't find my Firefox menu item under Applications>internet
:confused:

---

### Post by motsteve on 2010-04-10
I have a feeling that the repository has 3.6 in it if you have recently updated your sources.  I know mine are up to date as I do an update, clean, upgrade periodically during the day via the terminal.

---

### Post by ATMA3weapon on 2010-04-10
> **motsteve said:**
> I did that and I got 3.6 again.  I also can't find my Firefox menu item under Applications>internet
:confused:

Same thing going on for me also, purge it, and it just reinstalls 3.6 and still freezes up.

---

### Post by motsteve on 2010-04-10
This is freaking me out.  I'm going into Firefox withdrawl. :)

---

### Post by warfacegod on 2010-04-10
My sources are up to date and I even have backports enabled and ...install firefox offered me 3.5. If you have pre-release updates enabled that would likely be the reason it gives you 3.6 instead. I use Swiftfox instead of Firefox. Find a .deb for that and give it a try. It's the same thing as Firefox but with optimized code. The F.F. add-ons you already have will work with it. I'm pretty sure it's in Synaptic.

---

### Post by eMJayy on 2010-04-10
I'm having the same issue as of 10 minutes ago when I applied the firefox update...but I found that it's caused by the flash plugin. I disabled the plugin from within Firefox and the browser stopped freezing. In fact, I'm using it right now to type this. Hopefully, another update will come later in the day to fix this flash issue. The reason I thought it was flash from the beginning was that this version 3.6.4 is going to be the one that adds flash process isolation to firefox. That makes flash the logical cause of any issues we may have during this particular period of firefox development.

---

### Post by motsteve on 2010-04-10
Thanks guys.  I'll try the other browser and I'll disable my Flash.  I suspected that also, but I'm no expert here and didn't want to break the limbs of my directory tree. :)

---

### Post by budhi1976 on 2010-04-10
Thanks very much,

I disabled the plugins and my firefox back in action.

Once again, thanks very much.

Hope another update will come really soon.

> **eMJayy said:**
> I'm having the same issue as of 10 minutes ago when I applied the firefox update...but I found that it's caused by the flash plugin. I disabled the plugin from within Firefox and the browser stopped freezing. In fact, I'm using it right now to type this. Hopefully, another update will come later in the day to fix this flash issue. The reason I thought it was flash from the beginning was that this version 3.6.4 is going to be the one that adds flash process isolation to firefox. That makes flash the logical cause of any issues we may have during this particular period of firefox development.

---

### Post by TheSqueak on 2010-04-10
Aah, thankyou. Disabled the flash plugin and mine seems to be stable again.

Now I can stop having cold sweats :D

---

### Post by motsteve on 2010-04-10
To avoid the cold sweats next time, I installed Opera and SwiftFox.  SwiftFox still hangs like Firefox with the Flash enabled, but Opera runs like a champ. I never used it before, but I had heard of it on the forums for years.:P

I also fixed my menu problem, but I had to do it manually.  If anyone is interested in the details of that, just email me.

---

### Post by EARNEST on 2010-04-10
i have the same issue :/

---

### Post by lovinglinux on 2010-04-10
Next Firefox version will come with a feature that prevents the browser from crashing or locking when viewing crazy flash content. It is awesome. If you don't want to wait, you can test it already. See [this](http://ubuntuforums.org/showthread.php?t=1450678).

---

### Post by MattP220 on 2010-04-10
I'm getting this problem myself. Gmail crashes it every time without question, and it's happened on a few other pages that didn't seem so JS/flash happy. Facebook and Twitter web interfaces work just fine, so I have no idea what's doing it.

I'm using the daily updates repo, with Namoroka 3.6.4pre

---

### Post by misterbk on 2010-04-10
These facepalm moments are what keeps me from recommending Ubuntu as a regular OS...

Isn't there a process where someone would test this before it went into the repository?

I'm doing some 'computer fixin' for a friend who only does internet, facebook, email and word processing, running on an ancient Dell with failing hard drive and no OS reinstall media.  I was about to recommend an Ubuntu install but...  yeah.

Is this an issue that affected all Ubuntu installs, or is it like warfacegod said and you had to have turned on pre-release updates?

---

### Post by eMJayy on 2010-04-10
Ok, I've figured out what's going on. 

Basically, it's what I suspected all along. Firefox developers have started to add the code for process isolation to Namoroka 3.6.4 but it's not working properly yet. 

Since version 3.6.2, I've observed that Firefox on Linux now has 2 processes while running - firefox and firefox-bin. Today, however, I noticed that since the update, whenever a site with flash components is loaded, a third firefox-bin process is loaded, presumably to contain and isolate the flash data. Whenever this process loads,however, the browser freezes. 

I was able to find out which settings in about:config control the flash isolation behavior. Here goes:

Type about:config in the address bar
In the filter pane, type ipc

The filter should produce the following four config lines - 

dom.ipc.plugins.enabled;false
dom.ipc.plugins.enabled.libflashplayer.so;true
dom.ipc.plugins.enabled.libnptest.so;true
dom.ipc.plugins.timeoutSecs;10


To turn off the flash process isolation, change the second line (libflashplayer.so) to false and restart the browser. Then re-enable flash and the browser should be able to load flash pages and play flash video as usual.

---

### Post by misterbk on 2010-04-10
So if it is not working, why was it rolled out?

Is this an issue that will affect a "default" install of Ubuntu, or does the user need to have modified a repository setting to be given the new, broken Firefox?

---

### Post by eMJayy on 2010-04-10
> **misterbk said:**
> These facepalm moments are what keeps me from recommending Ubuntu as a regular OS...

Isn't there a process where someone would test this before it went into the repository?

I'm doing some 'computer fixin' for a friend who only does internet, facebook, email and word processing, running on an ancient Dell with failing hard drive and no OS reinstall media.  I was about to recommend an Ubuntu install but...  yeah.

Is this an issue that affected all Ubuntu installs, or is it like warfacegod said and you had to have turned on pre-release updates?

This issue only affects persons (like myself) who have chosen to use the daily builds version of Firefox, which provide pre-released code that's still undergoing modification and testing on a daily basis. This version of Firefox isn't the default (stable) one that you get when you install Ubuntu. 

Basically, this pre-release browser is the one that they're working on for release in May. Obviously, because they're sometimes making big modifications to the code, some things will break occasionally. This is actually the first time that I've had any issue with the pre-release code since I started using this version in January. I could actually have avoided this issue entirely by turning off automatic updates to the browser, but I chose to let the browser update daily so that I could observe how the browser was developing.

---

### Post by misterbk on 2010-04-10
> **eMJayy said:**
> This issue only affects persons (like myself) who have chosen to use the daily builds version of Firefox, which provide pre-released code that's still undergoing modification and testing on a daily basis. This version of Firefox isn't the default (stable) one that you get when you install Ubuntu. 

Basically, this pre-release browser is the one that they're working on for release in May. Obviously, because they're sometimes making big modifications to the code, some things will break occasionally. This is actually the first time that I've had any issue with the pre-release code since I started using this version in January. I could actually have avoided this issue entirely by turning off automatic updates to the browser, but I chose to let the browser update daily so that I could observe how the browser was developing.

OK that makes me feel much better about recommending an Ubuntu install to this person.  She likes the idea of trashing Microsoft, but I'd feel bad if she paid me to set all this up and it broke right away.  

Please pardon my being wary of Ubuntu...  I've caught a few nasty surprises in the updates myself, and this is a very nontechnical user.

---

### Post by eMJayy on 2010-04-10
> **misterbk said:**
> OK that makes me feel much better about recommending an Ubuntu install to this person.  She likes the idea of trashing Microsoft, but I'd feel bad if she paid me to set all this up and it broke right away.  

Please pardon my being wary of Ubuntu...  I've caught a few nasty surprises in the updates myself, and this is a very nontechnical user.

That's ok. There's nothing wrong with having a cautious attitude. 

Ubuntu's a great OS for newbies. I've used Ubuntu for 2 years now (I started as a Linux newbie myself) and can safely say that it's progressed in leaps and bounds from when I started using it at version 8.04. It's extremely stable...and I'm not even exaggerating. The OS hasn't crashed once since I started using it...heck, I don't even know what a Ubuntu OS crash looks like! With Windows I was used to at least a few crashes a year, so I was really surprised that a free OS could be more stable than a proprietary OS. I think she'll like the new experience. 

Here's a very helpful and easy guide that I use for putting the finishing touches on new installations of Ubuntu. 

[http://sites.google.com/site/easylinuxtipsproject/](http://sites.google.com/site/easylinuxtipsproject/)

Hopefully, your friend will read the Ubuntu help manual at some point. I found that really helped me to see just what Ubuntu had to offer that was different from Windows. It's easy to use Ubuntu just like Windows, but it has several unique features of its own (including ways of using the mouse and keyboard) that make the overall experience even better.

---

### Post by budhi1976 on 2010-04-11
Thanks very much,

I did the instruction below and yes, now my FF is working as usual.
 
> **eMJayy said:**
> Ok, I've figured out what's going on. 

Basically, it's what I suspected all along. Firefox developers have started to add the code for process isolation to Namoroka 3.6.4 but it's not working properly yet. 

Since version 3.6.2, I've observed that Firefox on Linux now has 2 processes while running - firefox and firefox-bin. Today, however, I noticed that since the update, whenever a site with flash components is loaded, a third firefox-bin process is loaded, presumably to contain and isolate the flash data. Whenever this process loads,however, the browser freezes. 

I was able to find out which settings in about:config control the flash isolation behavior. Here goes:

Type about:config in the address bar
In the filter pane, type ipc

The filter should produce the following four config lines - 

dom.ipc.plugins.enabled;false
dom.ipc.plugins.enabled.libflashplayer.so;true
dom.ipc.plugins.enabled.libnptest.so;true
dom.ipc.plugins.timeoutSecs;10


To turn off the flash process isolation, change the second line (libflashplayer.so) to false and restart the browser. Then re-enable flash and the browser should be able to load flash pages and play flash video as usual.

---

### Post by mal205 on 2010-04-11
> **eMJayy said:**
> Ok, I've figured out what's going on. 

Basically, it's what I suspected all along. Firefox developers have started to add the code for process isolation to Namoroka 3.6.4 but it's not working properly yet. 

Since version 3.6.2, I've observed that Firefox on Linux now has 2 processes while running - firefox and firefox-bin. Today, however, I noticed that since the update, whenever a site with flash components is loaded, a third firefox-bin process is loaded, presumably to contain and isolate the flash data. Whenever this process loads,however, the browser freezes. 

I was able to find out which settings in about:config control the flash isolation behavior. Here goes:

Type about:config in the address bar
In the filter pane, type ipc

The filter should produce the following four config lines - 

dom.ipc.plugins.enabled;false
dom.ipc.plugins.enabled.libflashplayer.so;true
dom.ipc.plugins.enabled.libnptest.so;true
dom.ipc.plugins.timeoutSecs;10


To turn off the flash process isolation, change the second line (libflashplayer.so) to false and restart the browser. Then re-enable flash and the browser should be able to load flash pages and play flash video as usual.

This has fixed it for me. 

Will I need to go back and re-enable the setting once the stability has been sorted out? Or will a future round of updates over write it back to the enabled state? I assume I will.

---

### Post by MattP220 on 2010-04-11
Got me sorted here too.

Cheers eMJayy

---

### Post by lovinglinux on 2010-04-11
> **eMJayy said:**
> Ok, I've figured out what's going on. 

Basically, it's what I suspected all along. Firefox developers have started to add the code for process isolation to Namoroka 3.6.4 but it's not working properly yet. 

Since version 3.6.2, I've observed that Firefox on Linux now has 2 processes while running - firefox and firefox-bin. Today, however, I noticed that since the update, whenever a site with flash components is loaded, a third firefox-bin process is loaded, presumably to contain and isolate the flash data. Whenever this process loads,however, the browser freezes. 

I was able to find out which settings in about:config control the flash isolation behavior. Here goes:

Type about:config in the address bar
In the filter pane, type ipc

The filter should produce the following four config lines - 

dom.ipc.plugins.enabled;false
dom.ipc.plugins.enabled.libflashplayer.so;true
dom.ipc.plugins.enabled.libnptest.so;true
dom.ipc.plugins.timeoutSecs;10


To turn off the flash process isolation, change the second line (libflashplayer.so) to false and restart the browser. Then re-enable flash and the browser should be able to load flash pages and play flash video as usual.


I don't see such third process using [Firefox Lorentz](http://ubuntuforums.org/showthread.php?t=1450678) from Mozilla and it works like a charm. I have tested it with a bad flash video and the browser doesn't crash or grey out, just gives the warning that flash crashed. So perhaps this problem is affecting only ubuntu-mozilla-daily users.

[IMG]http://wwww.ubuntuforums.org/attachment.php?attachmentid=152925&stc=1&d=1270996391[/IMG]

---

### Post by kendoori on 2010-04-11
This worked for me too. Thanks for the easy fix. Interestingly, other than changing the setting in about:config and restarting my browser, I didn't have to do anything else. I went to the nytimes.com site (which has flash on the home page) and it just worked. I'm attaching a list of my plugins, and I didn't have to re-enable anything to play flash properly.

[IMG]http://www.tpchealthcare.com/downloads/ff-plugins.png[/IMG]

---

### Post by lovinglinux on 2010-04-11
> **kendoori said:**
> This worked for me too. Thanks for the easy fix. Interestingly, other than changing the setting in about:config and restarting my browser, I didn't have to do anything else. I went to the nytimes.com site (which has flash on the home page) and it just worked. I'm attaching a list of my plugins, and I didn't have to re-enable anything to play flash properly.

[IMG]http://www.tpchealthcare.com/downloads/ff-plugins.png[/IMG]


Why do you have multiple plugins for video content? This could cause problems, even if you disable some of them.

---

### Post by kendoori on 2010-04-11
@Lovinglinux--not sure why the all the plugins, these have just accumulated, in many case without me explicitly installing them. The tweaks detailed in this thread did fix the issues that others have described in this thread.

---

### Post by lovinglinux on 2010-04-11
> **kendoori said:**
> @Lovinglinux--not sure why the all the plugins, these have just accumulated, in many case without me explicitly installing them. The tweaks detailed in this thread did fix the issues that others have described in this thread.

I would pick up the gecko-mediaplyer and uninstall the others. See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by eMJayy on 2010-04-11
> **lovinglinux said:**
> I don't see such third process using [Firefox Lorentz](http://ubuntuforums.org/showthread.php?t=1450678) from Mozilla and it works like a charm. I have tested it with a bad flash video and the browser doesn't crash or grey out, just gives the warning that flash crashed. So perhaps this problem is affecting only ubuntu-mozilla-daily users.



I'm not familiar with Lorentz, but I would expect that the process behavior of Namoroka should be mirroring Lorentz, since Lorentz is essentially the final product. In light of what you said, the third process I observed might be some sort of artifact that wasn't supposed to be generated and might represent a bug. While I was observing the system monitor during the crash, the extra process became a 'zombie' process a couple of times. Other times, it was accumulating data as the page loaded.

---

### Post by lovinglinux on 2010-04-11
> **eMJayy said:**
> I'm not familiar with Lorentz, but I would expect that the process behavior of Namoroka should be mirroring Lorentz, since Lorentz is essentially the final product. In light of what you said, the third process I observed might be some sort of artifact that wasn't supposed to be generated and might represent a bug. While I was observing the system monitor during the crash, the extra process became a 'zombie' process a couple of times. Other times, it was accumulating data as the page loaded.

Yes, that's what I think. But I still believe this bug could be affecting only some installations, depending on the source of the packages. Try to download Lorentz from Mozilla and run it to see if the problem persists.

---

### Post by eMJayy on 2010-04-11
> **lovinglinux said:**
> Yes, that's what I think. But I still believe this bug could be affecting only some installations, depending on the source of the packages. Try to download Lorentz from Mozilla and run it to see if the problem persists.

I'll do that and report back soon.

---

### Post by eMJayy on 2010-04-11
I'm running Lorentz 3.6.3plugin1 right now. I had to undo the about:config changes I made yesterday to Namoroka's process isolation settings, but Lorentz is running perfectly with flash isolation turned on. 

In addition to the two processes, *firefox* and *firefox-bin*, Lorentz is loading a third process called *mozilla-runtime* which definitely contains the flash data. Now that I know what to look for, I'll check Namoroka to see if *mozilla-runtime* initializes.

---

### Post by MattP220 on 2010-04-11
Making eMJayy's changes allows Namoroka to work, but it cripples Flash in Lorentz (no browser crashes, the plugin just doesn't load). I'm guessing that changing the settings back to default would create the opposite effect.

---

### Post by lovinglinux on 2010-04-11
> **eMJayy said:**
> I'm running Lorentz 3.6.3plugin1 right now. I had to undo the about:config changes I made yesterday to Namoroka's process isolation settings, but Lorentz is running perfectly with flash isolation turned on. 

In addition to the two processes, *firefox* and *firefox-bin*, Lorentz is loading a third process called *mozilla-runtime* which definitely contains the flash data. Now that I know what to look for, I'll check Namoroka to see if *mozilla-runtime* initializes.

Indeed mozilla-runtime loads when view a page with flash content.

---

### Post by eMJayy on 2010-04-11
> **MattP220 said:**
> Making eMJayy's changes allows Namoroka to work, but it cripples Flash in Lorentz (no browser crashes, the plugin just doesn't load). I'm guessing that changing the settings back to default would create the opposite effect.

I didn't get that result just now when I tested them both. On my machine, turning off plugin isolation in Namoroka turned off the feature in Lorentz (since they're sharing the same configuration settings), but Lorentz was able to playback flash video with the isolation feature turned off, just as Namoroka did. 

I also confirmed that Namoroka isn't loading the mozilla-runtime process for flash containment as Lorentz is doing. Instead, it loads another firefox-bin process when flash is detected and then the browser freezes seconds later.

---

### Post by wd5gnr on 2010-04-14
> **eMJayy said:**
> Ok, I've figured out what's going on. 



Well done. My FF was crashing this morning and I figured out it was libflash (not so shocking) so I came here and found this post. Worked for me. Of course, I've been slowly weaning over to Chrome anyway ;-)

Thanks!

---

### Post by lovinglinux on 2010-04-14
> **wd5gnr said:**
> Well done. My FF was crashing this morning and I figured out it was libflash (not so shocking) so I came here and found this post. Worked for me. Of course, I've been slowly weaning over to Chrome anyway ;-)

Thanks!

Don't think you will be free of problems with Chrome. Until Lucid, it didn't even work for several users with KDE. Keep in mind that the problem you are experiencing with Firefox is affecting those who use *ubuntu-mozilla-daily* ppa, which does not install only stable versions. Firefox is very stable for me and works like charm, even with 51 extensions installed.

---

### Post by wd5gnr on 2010-04-14
Oh yeah Chrome has its problems too. Just saying, I've been enjoying it. Variety, after all, is the spice of life.

---

### Post by lovinglinux on 2010-04-15
> **wd5gnr said:**
> Oh yeah Chrome has its problems too. Just saying, I've been enjoying it. Variety, after all, is the spice of life.

Indeed :)

---

### Post by tiggsy on 2010-04-16
Everybody seems to be talking about firefox 3.6.4, but I checked and the one I'm using is 3.5.9, and that is all that synaptic is offering, as well. I'm running Karmic, it's plain ubuntu, but for some reason I have an opening kubuntu splash (which i like better anyway, so I'm content with that). I do have some kubuntu apps like kalarm, so that may account for that, i guess. I have 3gb RAM and there is no issue with too much memory being used, as system showed i wasn't even using half of it when I checked it a few days ago with ALL my normal apps running.

My firefox has started crashing today. It was working fine, then I logged into my cpanel, went into mysql and selected a table and it crashed. 

I had 44 tabs open, and I also have lots of addons. However, **these don't make any difference**, as when I start in safe mode, using a new session and with plugins disabled, if I login to cpanel, go to mysql and select a table it crashes again. So i can't do my work. Or not in firefox anyway.

I updated this morning.

The about:config fix won't work for me as none of the entries appear when I type in **ipc**

---

### Post by lovinglinux on 2010-04-16
> **tiggsy said:**
> Everybody seems to be talking about firefox 3.6.4, but I checked and the one I'm using is 3.5.9, and that is all that synaptic is offering, as well. I'm running Karmic, it's plain ubuntu, but for some reason I have an opening kubuntu splash (which i like better anyway, so I'm content with that). I do have some kubuntu apps like kalarm, so that may account for that, i guess. I have 3gb RAM and there is no issue with too much memory being used, as system showed i wasn't even using half of it when I checked it a few days ago with ALL my normal apps running.

My firefox has started crashing today. It was working fine, then I logged into my cpanel, went into mysql and selected a table and it crashed. 

I had 44 tabs open, and I also have lots of addons. However, **these don't make any difference**, as when I start in safe mode, using a new session and with plugins disabled, if I login to cpanel, go to mysql and select a table it crashes again. So i can't do my work. Or not in firefox anyway.

I updated this morning.

The about:config fix won't work for me as none of the entries appear when I type in **ipc**

Please start a new thread, so we can deal with your problem separately from the current 3.6.4 issues posted on this thread.

---

### Post by eMJayy on 2010-04-17
The developers have resolved the Namoroka flash process isolation issue that was affecting users of the daily PPA version from mozilla. 

I just got a Namoroka update which appropriately isolates the flash plugin without crashing the browser. When the flash process isolation feature is turned on, the browser moves the flash data to a separate process called *plugin-container*, which prevents flash from bringing down the whole browser session. 

Those persons who turned off flash process isolation to fix the freezing issue should now apply this latest update and can now re-enable flash isolation if they choose to.

---

### Post by lovinglinux on 2010-04-17
> **eMJayy said:**
> The developers have resolved the Namoroka flash process isolation issue that was affecting users of the daily PPA version from mozilla. 

I just got a Namoroka update which appropriately isolates the flash plugin without crashing the browser. When the flash process isolation feature is turned on, the browser moves the flash data to a separate process called *plugin-container*, which prevents flash from bringing down the whole browser session. 

Those persons who turned off flash process isolation to fix the freezing issue should now apply this latest update and can now re-enable flash isolation if they choose to.

Great news. Thanks for sharing.

---


---
title: "YouTube Problems Mega Thread"
date: 2011-07-07
forum: General Help
---

### Post by lovinglinux on 2011-07-07
Due to recent problems on YouTube, I decided to create this thread.

> 
**IMPORTANT EDIT:** Just updated [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") to get the new Flash 11 Betas, for both 32bit and 64bit. If you already use Flash-Aid, all you need is to execute the Wizard to install. Hardware acceleration and the performance tweak "Override GPU validation" is working on YouTube again. No more black screen

If you are experiencing flash problems only on YouTube in fullscreen and instead of video you get only audio, then you need to install Flash 11 Beta (you can do that with using [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")) or disable hardware acceleration. You can do that by right-clicking on a video, selecting "Settings", then the "Display" tab. If you are using Flash-Aid and don't want to use Flash 11 Beta, you can alternatively untick the option to Override GPU validation in the tweaking options step. 

If YouTube videos doesn't work on the main site, but works embedded on other sites, then delete the YT cookies, clear the cache, then block YT cookies in Firefox Privacy preferences - you need to select "Use custom settings for History", then click the "Exceptions" button, then add a "Block" rule for youtube.com

If that doesn't work, try [https:///www.youtube.com](https:///www.youtube.com)

---

### Post by childe joseph on 2011-07-07
Followed all steps mentioned above. Flash-Aid installed everything, and still nothing. I can play embedded YouTubes on facebook. Luckily I'm a pretty patient guy. I'll keep looking elsewhere and checking back. If I find something, I'll be sure to post it here, but I'm stumped!

---

### Post by lovinglinux on 2011-07-07
> **childe joseph said:**
> Followed all steps mentioned above. Flash-Aid installed everything, and still nothing. I can play embedded YouTubes on facebook. Luckily I'm a pretty patient guy. I'll keep looking elsewhere and checking back. If I find something, I'll be sure to post it here, but I'm stumped!

Try [https://www.youtube.com](https://www.youtube.com)

---

### Post by whatthefunk on 2011-07-07
> **childe joseph said:**
> Followed all steps mentioned above. Flash-Aid installed everything, and still nothing. I can play embedded YouTubes on facebook. Luckily I'm a pretty patient guy. I'll keep looking elsewhere and checking back. If I find something, I'll be sure to post it here, but I'm stumped!

What exactly does your screen look like when you try to play youtube videos?  Do you get any error message?

(This should be a sticky...)

---

### Post by childe joseph on 2011-07-07
That link worked lovinglinux! But open another window and go to [www.youtube.com]("http://www.youtube.com"), and Nothing! What's going on?
@whatthefunk No error messages, just a black screen in the tube, the rest of the page is loaded.

---

### Post by lovinglinux on 2011-07-07
> **childe joseph said:**
> That link worked! But open another window and go to [www.youtube.com](www.youtube.com), and Nothing! What's going on?

Just another YouTube/Flash issue. Happens from time to time.

---

### Post by mastablasta on 2011-07-07
is this a DE specific or browser specific issue? 
 
Or is it a flash issue or you tube site issue?

---

### Post by lovinglinux on 2011-07-07
> **mastablasta said:**
> is this a DE specific or browser specific issue? 
 
Or is it a flash issue or you tube site issue?

Is not DE specific. I have KDE and I am also suffering problems. 

**EDIT:** It also affects Chrome here.

---

### Post by childe joseph on 2011-07-07
> **mastablasta said:**
> is this a DE specific or browser specific issue? 
 
Or is it a flash issue or you tube site issue?

I'm using Linux Mint Isadora Gnome. It's definitley not browser specific, problem exists on Firefox and Chromium.

---

### Post by childe joseph on 2011-07-07
> **lovinglinux said:**
> Try [https://www.youtube.com](https://www.youtube.com)


What's the difference in this youtube link you provided?

---

### Post by lovinglinux on 2011-07-07
> **childe joseph said:**
> What's the difference in this youtube link you provided?

It is the encrypted version, hence the http**s** instead of http.

[http://en.wikipedia.org/wiki/Https](http://en.wikipedia.org/wiki/Https)

A few months ago there was also [noparse]http://www.youtube-nocookie.com[/noparse], which didn't save any cookies on your machine and worked great.

---

### Post by mastablasta on 2011-07-07
it's HTTPS not HTTP
 
This means that connection between you and youtube is encrypted.
 
also perhaps Google is moving You tube to Google Video :-)

---

### Post by childe joseph on 2011-07-07
> **lovinglinux said:**
> It is the encrypted version, hence the http**s** instead of http.

[http://en.wikipedia.org/wiki/Https](http://en.wikipedia.org/wiki/Https)

A few months ago there was also [noparse]http://www.youtube-nocookie.com[/noparse], which didn't save any cookies on your machine and worked great.

Yes I noted the 's' right after posing the question. I opened up Chromium and used the same address YouTube cookies ENABLED, and was able to still see the video. From your Wiki link, I'm gathering it's a certificate problem, maybe? In any case I can see video's so technically problem solved!....BUT (you had to know that was coming) it seems we Linux users are great at work around's, by only partially identifying the problem. But truth be told, the problem still to some extent exists!

---

### Post by Linux_Man on 2011-07-07
Thank you so much for this!

---

### Post by PTOPedro on 2011-07-07
Thank you! This help me out so much!
Thanks again!

---

### Post by lovinglinux on 2011-07-07
> **Linux_Man said:**
> Thank you so much for this!

> **PTOPedro said:**
> Thank you! This help me out so much!
Thanks again!

You are welcome.

---

### Post by childe joseph on 2011-07-07
Thanks lovinglinux your fix did help solve my problem. I want to be good at Linux so my extra questions and comments were only upon further analysis of the issue, plus I had a handful of other problems this morning. I run 3 hobby machines. In no way did I mean to sound unappreciative, which I did even to myself, after coming back and looking. Sorry I'm just a Geek. So thank you lovinglinux I am now able to see YouTube. In both Browsers! Sorry waay too many forums today

---

### Post by lovinglinux on 2011-07-07
> **childe joseph said:**
> Thanks lovinglinux your fix did help solve my problem. I want to be good at Linux so my extra questions and comments were only upon further analysis of the issue, plus I had a handful of other problems this morning. I run 3 hobby machines. In no way did I mean to sound unappreciative, which I did even to myself, after coming back and looking. Sorry I'm just a Geek. So thank you lovinglinux I am now able to see YouTube. In both Browsers! Sorry waay too many forums today

No problem. I didn't respond to your previous question, because I simply don't know the answer. This problem with YT happened before and went away with updates on their side.

---

### Post by pebuha on 2011-07-07
Hey, 

I'm running 11.04 on 64-bit PC. And youtube doesn't work with Chrome, all other flash content does. I've tried everything; disabling hardware acceleration prevents the youtube videos from loading (before, I'd only get sound without the player), I've changed the original Chrome plugin for the "Flash Square" plugin with 64bit support, I've tried https (no help), deleting cookies, preventing cookies, everything. The desperation is starting to kick in. Can you help me, please?

---

### Post by lovinglinux on 2011-07-07
> **pebuha said:**
> Hey, 

I'm running 11.04 on 64-bit PC. And youtube doesn't work with Chrome, all other flash content does. I've tried everything; disabling hardware acceleration prevents the youtube videos from loading (before, I'd only get sound without the player), I've changed the original Chrome plugin for the "Flash Square" plugin with 64bit support, I've tried https (no help), deleting cookies, preventing cookies, everything. The desperation is starting to kick in. Can you help me, please?

Install [Flash-Aid]("http://www.webgapps.org/add-ons/flash-aid") on Firefox, run the Wizard, but disable the option to "Override GPU validation". Close Firefox and restart Chrome.

---

### Post by ortaa23 on 2011-07-08
Hello,

I have been experiencing Youtube problems with Natty/Firefox. Yesterday I had a black screen, today a message telling me to download a plugin, which Ubuntu tells me I already have (installed 'Restricted extras package' yesterday). Tried following lovinglinux's instructions but no change. Now I am trying to install Flash-aid, can't quite work out what to do (noob). Downloaded the xpi file from their website, but opening install.rdf doesn't do it. Do I need to open it with another programme? Software centre doesn't seem to have it...

---

### Post by lovinglinux on 2011-07-08
> **ortaa23 said:**
> Hello,

I have been experiencing Youtube problems with Natty/Firefox. Yesterday I had a black screen, today a message telling me to download a plugin, which Ubuntu tells me I already have (installed 'Restricted extras package' yesterday). Tried following lovinglinux's instructions but no change. Now I am trying to install Flash-aid, can't quite work out what to do (noob). Downloaded the xpi file from their website, but opening install.rdf doesn't do it. Do I need to open it with another programme? Software centre doesn't seem to have it...

Don't extract the xpi file. Just drag it to a Firefox Window to install. You can also install automatically from Mozilla site: [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/)

---

### Post by pebuha on 2011-07-08
> **lovinglinux said:**
> Install [Flash-Aid]("http://www.webgapps.org/add-ons/flash-aid") on Firefox, run the Wizard, but disable the option to "Override GPU validation". Close Firefox and restart Chrome.

Thanks for response, but nothing. :-k Doesn't help. I've tried both possible drivers (adobe labs and the stable one), without and with overriding GPU, and still nothing. Firefox works with no problems, but Chrome's youtube (only youtube) isn't working.

Interestingly enough, the videos are working when I open the channel/person's account, or once in a while. Sometimes, it changes to a black frame. The http5 version is working, unfortunately only for a handful of videos. 

PS: I've tried disabling AdBlock, no luck. ](*,)

---

### Post by lovinglinux on 2011-07-08
> **pebuha said:**
> Thanks for response, but nothing. :-k Doesn't help. I've tried both possible drivers (adobe labs and the stable one), without and with overriding GPU, and still nothing. Firefox works with no problems, but Chrome's youtube (only youtube) isn't working.

Interestingly enough, the videos are working when I open the channel/person's account, or once in a while. Sometimes, it changes to a black frame. The http5 version is working, unfortunately only for a handful of videos. 

PS: I've tried disabling AdBlock, no luck. ](*,)

**EDIT:** I just saw you are using the 64bit, so the instructions below don't apply.

If you are using Chrome 32bit, then disable the plugin that is bundled with it, otherwise it won't use the one installed by Flash-Aid. You can do that by typing **about[noparse]:[/noparse]plugins** in the address bar, then the "Details" on the top-right, then disable the one that is stored at /opt/google/chrome/libgcflashplayer.so

---

### Post by lovinglinux on 2011-07-08
> **pebuha said:**
> Thanks for response, but nothing. :-k Doesn't help. I've tried both possible drivers (adobe labs and the stable one), without and with overriding GPU, and still nothing. Firefox works with no problems, but Chrome's youtube (only youtube) isn't working.

Interestingly enough, the videos are working when I open the channel/person's account, or once in a while. Sometimes, it changes to a black frame. The http5 version is working, unfortunately only for a handful of videos. 

PS: I've tried disabling AdBlock, no luck. ](*,)

When you visit YouTube are you logged in?

---

### Post by pebuha on 2011-07-08
> **lovinglinux said:**
> **EDIT:** I just saw you are using the 64bit, so the instructions below don't apply.

If you are using Chrome 32bit, then disable the plugin that is bundled with it, otherwise it won't use the one installed by Flash-Aid. You can do that by typing **about[noparse]:[/noparse]plugins** in the address bar, then the "Details" on the top-right, then disable the one that is stored at /opt/google/chrome/libgcflashplayer.so

OK..... no luck. I've played with all flash plugins there, none of them works (not even the one from mozilla). Btw, the plugin is named "libflashplayer.so", not "libgcflashplayer.so", if that information will help you.

Is there any hope for my Chrome? :-?

EDIT: Just saw the second post and tried logging out. Does not work in both situations.

---

### Post by lovinglinux on 2011-07-08
> **pebuha said:**
> OK..... no luck. I've played with all flash plugins there, none of them works (not even the one from mozilla). Btw, the plugin is named "libflashplayer.so", not "libgcflashplayer.so", if that information will help you.

Is there any hope for my Chrome? :-?

EDIT: Just saw the second post and tried logging out. Does not work in both situations.

Install flash 64bit again using Flash-Aid, making sure GPU override is not selected. Close Firefox and Chrome. Rename ~/.config/google-chrome to something else if you need to recover the data later. Reboot. Start Chrome and visit YouTube. If it doesn't work, try to reload the page.

BTW I just tested Chrome 64bit on a VM and it works perfectly. So, there is hope.

---

### Post by pebuha on 2011-07-08
It works. Didn't work after reboot, changing plugins, etc. but then I've looked into one thing not touched before - extensions - and uninstalled nyan cat loader and magic youtube actions. These ones use http5, which was enabled on youtube, however looks like it's causing problems for regular youtube videos.

Thank you very much for your support :))) 
Now it's time to watch some videos:popcorn: !

---

### Post by lovinglinux on 2011-07-08
> **pebuha said:**
> It works. Didn't work after reboot, changing plugins, etc. but then I've looked into one thing not touched before - extensions - and uninstalled nyan cat loader and magic youtube actions. These ones use http5, which was enabled on youtube, however looks like it's causing problems for regular youtube videos.

Thank you very much for your support :))) 
Now it's time to watch some videos:popcorn: !

You are welcome.

---

### Post by Oldhacker on 2011-07-08
Of late, my YouTube in Firefox has only shown blank black screens. Going through all of these threads on the subject suggested many different approaches to solving the situation.
However, almost by accident I solved my own problem:

I went to the Add-ons manager and it showed that I had TWO different instances of Shockwave Flash installed!
I disabled the older of the two and now YouTube plays normally just like it did in former days. I hope that this may help some others experiencing similar problems.

---

### Post by stevedude on 2011-07-09
This is ironic. A few days ago I couldn't watch Youtube only videos using FF5 in Ubuntu Natty. I installed the FlashVideoReplacer and all was well - - - until a couple of days ago.

Youtube stopped working for me. Nothing was changed on my system. I read about OldHacker's comment about extensions. I decided to disable the FlashVideoReplacer extension and try Youtube again. Now it works with no issues.

Thanks for this thread though, it is a great community service and is the first place I check if I have issues.

---

### Post by lovinglinux on 2011-07-09
> **stevedude said:**
> This is ironic. A few days ago I couldn't watch Youtube only videos using FF5 in Ubuntu Natty. I installed the FlashVideoReplacer and all was well - - - until a couple of days ago.

Youtube stopped working for me. Nothing was changed on my system. I read about OldHacker's comment about extensions. I decided to disable the FlashVideoReplacer extension and try Youtube again. Now it works with no issues.

Thanks for this thread though, it is a great community service and is the first place I check if I have issues.

What exactly happened when you clicked the video using FlashVideoReplacer? There is no current issue with that extension in regard to YouTube that I know about.

---

### Post by stevedude on 2011-07-09
This is pretty wild. I re-enabled the extension so I could give you an informative feedback. It is now working again for Youtube!? *EDIT* To answer your question, the screen for the video just appeared black. 

I also use Yahoo alot and even though I know that this extension does not work for that site, it seems to be messing with me on my system. This is a random link I tried and the enclosed screenshot shows the result with your extension enabled.

[http://shine.yahoo.com/event/momentsofmotherhood/sarah-michelle-gellar-urges-us-to-read-2508562](http://shine.yahoo.com/event/momentsofmotherhood/sarah-michelle-gellar-urges-us-to-read-2508562)

If I disable the extension and play the above video it works.

---

### Post by stevedude on 2011-07-09
Screenshot of extension disabled running the Yahoo video from the previous link.

Notice the FlashVideoReplacer icon is not shown in the upper-right corner where it is shown on my previous screenshot.

---

### Post by lovinglinux on 2011-07-09
> **stevedude said:**
> This is pretty wild. I re-enabled the extension so I could give you an informative feedback. It is now working again for Youtube!? *EDIT* To answer your question, the screen for the video just appeared black. 

I also use Yahoo alot and even though I know that this extension does not work for that site, it seems to be messing with me on my system. This is a random link I tried and the enclosed screenshot shows the result with your extension enabled.

[http://shine.yahoo.com/event/momentsofmotherhood/sarah-michelle-gellar-urges-us-to-read-2508562](http://shine.yahoo.com/event/momentsofmotherhood/sarah-michelle-gellar-urges-us-to-read-2508562)

If I disable the extension and play the above video it works.

> **stevedude said:**
> Screenshot of extension disabled running the Yahoo video from the previous link.

Notice the FlashVideoReplacer icon is not shown in the upper-right corner where it is shown on my previous screenshot.

Thanks for providing this info and screenshots. 

I couldn't reproduce the problem here. What version of FVR do you have? There was a bug in version 2.1.11 that could lead to bad interaction with another extension. I suspect that could be the case. If you have it, get version 2.1.12.

If you don't mind, would be very helpful if you could test it on a clean Firefox profile and try to reproduce the problem. If you doesn't experience the same problem, please provide a list of extensions you have, so I can find which one is conflicting.

---

### Post by ortaa23 on 2011-07-10
Hello again, 

Installed Flash-Aid as instructed, yet still no luck. Add-ons manager shows only Flash-Aid when 'flash' keyword is searched. This is really starting to get rather dull, think I'm going to try Opera...

Update: Opera doesn't work either. Zzzzzzzzzzzzz

---

### Post by lovinglinux on 2011-07-10
> **ortaa23 said:**
> Hello again, 

Installed Flash-Aid as instructed, yet still no luck. Add-ons manager shows only Flash-Aid when 'flash' keyword is searched. This is really starting to get rather dull, think I'm going to try Opera...

Update: Opera doesn't work either. Zzzzzzzzzzzzz

I suppose you are searching the add-ons database and not the installed add-ons. Anyway, after installation, you don't need to go to the add-ons manager. Flash-Aid ads an icon to the Navigation toolbar, from where you can execute the Wizard and acess the preferences. If you don't see that icon, right-click on any toolbar, select "Customize", then drag Flash-Aid to the toolbar.

---

### Post by ortaa23 on 2011-07-10
Hi, 

Believe it or not I managed to do all of that (installation, disable GPU), and searched installed-plug ins, and it's there...

---

### Post by lovinglinux on 2011-07-10
> **ortaa23 said:**
> Hi, 

Believe it or not I managed to do all of that (installation, disable GPU), and searched installed-plug ins, and it's there...

Does it work?

Have you seen my reply above?

---

### Post by ortaa23 on 2011-07-10
Yes, did see your reply; I had already installed the programme before. I hope we understand each other...

Sorry, I should add, no Youtube still doesn't work.

---

### Post by lovinglinux on 2011-07-10
> **ortaa23 said:**
> Yes, did see your reply; I had already installed the programme before. I hope we understand each other...

:-)

---

### Post by ortaa23 on 2011-07-10
I don't think you understand me. Youtube still not working after doing these things. Nor did it work on Opera when I installed that. So presumably this is not a Firefox thing. Any more suggestions?

---

### Post by lovinglinux on 2011-07-10
> **ortaa23 said:**
> I don't think you understand me. Youtube still not working after doing these things. Nor did it work on Opera when I installed that. So presumably this is not a Firefox thing. Any more suggestions?

Sorry. I am a little bit slow today :-)

Please got to Flash-Aid help menu and generate a report and post it here.

It started with the black screen problem, but now it doesn't work at all and YouTube keeps saying you don't have the necessary plugin right?

---

### Post by ortaa23 on 2011-07-10
Report is attached. What you say is correct, black screen before, now getting message. Thanks for your help...

---

### Post by lovinglinux on 2011-07-10
> **ortaa23 said:**
> Report is attached. What you say is correct, black screen before, now getting message. Thanks for your help...

The flashplugin-installer package is installed, but the plugin is missing.

Run Flash-Aid again, but select Adobe Beta from Adobe Labs in the installation options. Don't worry, there is actually no beta available right now, so it will install the current stable version. The only difference is that it will grab it from Adobe directly and it won't be updated by the package manager. Don't forget to disable the option to "Override GPU validation".

---

### Post by lovinglinux on 2011-07-10
> **lovinglinux said:**
> The flashplugin-installer package is installed, but the plugin is missing.

Run Flash-Aid again, but select Adobe Beta from Adobe Labs in the installation options. Don't worry, there is actually no beta available right now, so it will install the current stable version. The only difference is that it will grab it from Adobe directly and it won't be updated by the package manager. Don't forget to disable the option to "Override GPU validation".

On a side note, looks like you have VLC plugin and Totem. VLC is not a good plugin. I recommend removing it. Besides, Totem can handle VLC stuff. Totem is fine, but I prefer gecko-mediaplayer.

---

### Post by ortaa23 on 2011-07-10
I think Beta was set as default, so that's probably what I installed last time. But tried again, now noticing that Terminal says:

Connecting to updates.webgapps.org|1.0.0.0|:80... failed: No route to host.
***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************

Then asks for password, which I enter, after which it tells me it's finished.

---

### Post by ortaa23 on 2011-07-10
Well my VLC player doesn't work properly either, so I might take you up on your recommendation.

---

### Post by lovinglinux on 2011-07-10
> **ortaa23 said:**
> I think Beta was set as default, so that's probably what I installed last time. But tried again, now noticing that Terminal says:

Connecting to updates.webgapps.org|1.0.0.0|:80... failed: No route to host.
***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************

Then asks for password, which I enter, after which it tells me it's finished.

Weird. The site is not down and I just tested it and it worked.

Anyway, select the Stable version then. It will not contact my site.

---

### Post by ortaa23 on 2011-07-10
Done all that, restarted whole computer, still nothing. Attaching report.

---

### Post by lovinglinux on 2011-07-10
> **ortaa23 said:**
> Done all that, restarted whole computer, still nothing. Attaching report.

Please use the Advanced Mode, select the stable version, then click the Script tab, copy the contents and paste here.

Then execute it and paste the terminal output.

---

### Post by stevedude on 2011-07-10
> **lovinglinux said:**
> Thanks for providing this info and screenshots. 

I couldn't reproduce the problem here. What version of FVR do you have? There was a bug in version 2.1.11 that could lead to bad interaction with another extension. I suspect that could be the case. If you have it, get version 2.1.12.

If you don't mind, would be very helpful if you could test it on a clean Firefox profile and try to reproduce the problem. If you doesn't experience the same problem, please provide a list of extensions you have, so I can find which one is conflicting.

I feel like an idiot :P

I use the "NoScript" extension to block harmful scripts. It was my NoScript blocking the site. (Notice my 4th icon on the left in the 1st screenshot - It has a red-slash blocking some scripts. The 2nd screenshot there is no red-slash)

Thanks for spending your time with me and the other posters here. We value and appreciate your responsiveness!

---

### Post by lovinglinux on 2011-07-10
> **stevedude said:**
> I feel like an idiot :P

I use the "NoScript" extension to block harmful scripts. It was my NoScript blocking the site. (Notice my 4th icon on the left in the 1st screenshot - It has a red-slash blocking some scripts. The 2nd screenshot there is no red-slash)

Thanks for spending your time with me and the other posters here. We value and appreciate your responsiveness!

You are welcome. I am glad you figured it out and that is not FVR causing the problem.

---

### Post by Plasma_NZ on 2011-07-10
I had all of those problems + more regarding flash videos on youtube and other media websites... none of the fixes worked too well... 

Decided to try the mozilla ppa version of firefox + flash-aid (due to being 11.04 64bit)
and the problems are all resolved.

Sure some plugins dont work, but majority of the good ones do, like ad-block plus, flash-got, flash-aid, compactmenu 2 etc....

---

### Post by lovinglinux on 2011-07-10
> **Plasma_NZ said:**
> I had all of those problems + more regarding flash videos on youtube and other media websites... none of the fixes worked too well... 

Decided to try the mozilla ppa version of firefox + flash-aid (due to being 11.04 64bit)
and the problems are all resolved.

Sure some plugins dont work, but majority of the good ones do, like ad-block plus, flash-got, flash-aid, compactmenu 2 etc....

Are you using Firefox 6.0b1? It does really look great. I tried it and it feels snappier. However, I need some extensions that don't even work with compatibility check disabled.

---

### Post by Plasma_NZ on 2011-07-11
> **lovinglinux said:**
> Are you using Firefox 6.0b1? It does really look great. I tried it and it feels snappier. However, I need some extensions that don't even work with compatibility check disabled.

Nope, 

Firefox Nightly
8.01a ( 2011-07-08 )
Conical - 1.0

Extenstions in uses are...

Ad-block +
Compact Menu 2

And one other extention that is install with compad off - simpleclock - works fine but u cant add a location lol....

---

### Post by ortaa23 on 2011-07-11
***EDIT: NOW FIXED***

Script:

#!/bin/bash

sudo apt-get update
sudo apt-get --yes install flashplugin-nonfree
cat /etc/adobe/mms.cfg | sed '/OverrideGPUValidation=true/d' | sudo tee /etc/adobe/mms.cfg
cat /etc/adobe/mms.cfg | sed '/EnableLinuxHWVideoDecode=1/d' | sudo tee /etc/adobe/mms.cfg

---

### Post by ortaa23 on 2011-07-11
Well, this time it appears to have worked. Who knows what happened last time. Thank you kindly for your help.

---

### Post by lovinglinux on 2011-07-11
> **ortaa23 said:**
> Script:

#!/bin/bash

sudo apt-get update
sudo apt-get --yes install flashplugin-nonfree
cat /etc/adobe/mms.cfg | sed '/OverrideGPUValidation=true/d' | sudo tee /etc/adobe/mms.cfg
cat /etc/adobe/mms.cfg | sed '/EnableLinuxHWVideoDecode=1/d' | sudo tee /etc/adobe/mms.cfg

Everything looks fine. Just to make sure, please generate a new report, restart Firefox and test if it works.

---

### Post by lovinglinux on 2011-07-11
> **ortaa23 said:**
> Well, this time it appears to have worked. Who knows what happened last time. Thank you kindly for your help.

You are welcome.

I think you had some issue in your connection, since it was trying to download from my site using IP 1.0.0.0:80. I suppose it didn't download the package from the repositories as well. I don't know why it did that. Do you have any local server, proxy or something else?

---

### Post by ortaa23 on 2011-07-11
I'm on a normal modem, so see no reason why connection should be strange. Not that I know a lot about this subject though.

One thing I did do since my last attempt was use Synaptic Package Manager to completely remove the Flash installer that was on there before...

---

### Post by lovinglinux on 2011-07-11
> **ortaa23 said:**
> I'm on a normal modem, so see no reason why connection should be strange. Not that I know a lot about this subject though.

One thing I did do since my last attempt was use Synaptic Package Manager to completely remove the Flash installer that was on there before...

Flash-Aid always purge the Flash installer package when you execute it, so it is probably a network issue. A corrupted package could have been saved in the apt cache, due to such network issues.

Anyway, your report is fine now.

---

### Post by mastablasta on 2011-07-12
has this been resolved? i still haven't installed the flash updates because of this as my wife is wathingn you tube and streaming TV on that computer.
 
btw it seem only linux has this youtube issue.

---

### Post by lovinglinux on 2011-07-12
> **mastablasta said:**
> has this been resolved? i still haven't installed the flash updates because of this as my wife is wathingn you tube and streaming TV on that computer.
 
btw it seem only linux has this youtube issue.

It seems to be resolved for some users. If you are using Flash-Aid, you still need to disable "Override GPU validation".

---

### Post by con-f-use on 2011-07-13
Lately (a week or so) I have this incredibly annoying bug: **Every once in a while I get to the point were youtube and other .flv-videos play for two seconds and then stop**. If I press start/stop again or skip to another position in the video, I get another two seconds out.  **The problems occurres in totem as well**. *Restarting gnome helps it for a while, resta*rting firefox/totem doesn't help. VLC is fine as always.
    Gnash seems to help the problem but creates others: With Gnash there  are a few webplayers that simply don't work anymore. The 64bit-nonfree  has the same problems as the 32bit-nonfree (2 seconds then stop). The  problem is independent of gpu validation. Clearing cookies and cache makes no difference.

---

### Post by lovinglinux on 2011-07-13
> **con-f-use said:**
> Lately (a week or so) I have this incredibly annoying bug: **Every once in a while I get to the point were youtube and other .flv-videos play for two seconds and then stop**. If I press start/stop again or skip to another position in the video, I get another two seconds out.  **The problems occurres in totem as well**. *Restarting gnome helps it for a while, resta*rting firefox/totem doesn't help. VLC is fine as always.
    Gnash seems to help the problem but creates others: With Gnash there  are a few webplayers that simply don't work anymore. The 64bit-nonfree  has the same problems as the 32bit-nonfree (2 seconds then stop). The  problem is independent of gpu validation. Clearing cookies and cache makes no difference.

Have you noticed if the videos continues to be buffered when it stops playing?

I saw th additional info on Ask Ubuntu. I would suggest creating a new Ubuntu user, just for testing. Check if the problem persists or not with a clean user account.

---

### Post by lovinglinux on 2011-07-13
Just updated [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") to get the new Flash 11 Betas, for both 32bit and 64bit. If you already use Flash-Aid, all you need is to execute the Wizard to install. Hardware acceleration and the performance tweak "Override GPU validation" is working on YouTube again. No more black screen.

If you already use Flash-Aid, you probably will receive an alert tomorrow, since it only checks for updates once a day. But if you run the Wizard today, you can ignore that alert.

---

### Post by ColeTurner on 2011-07-28
What do I do about jerky Youtube videos? I use Ubuntu 10.10 (Maverick Meerkat).

---

### Post by lovinglinux on 2011-07-28
> **ColeTurner said:**
> What do I do about jerky Youtube videos? I use Ubuntu 10.10 (Maverick Meerkat).

Have you tried Flash-Aid?

---

### Post by ColeTurner on 2011-07-29
I am now using Flash Video Replacer. It is awesome!!

---

### Post by lovinglinux on 2011-07-29
> **ColeTurner said:**
> I've installed it. How do I use it?

Click the Flash-Aid icon in the Navigation Toolbar and select the Wizard from the menu. Follow the wizard.

See Flash-Aid documentation at [http://www.webgapps.org/add-ons/flash-aid/documentation](http://www.webgapps.org/add-ons/flash-aid/documentation)

---

### Post by ColeTurner on 2011-07-29
I can never find the icon in the navigation bar. 
I would rather get Flash Video Replacer to work. It worked beautifully before. But now, it won't play anything. When I try to play the video in Video Player, it tells me I might not have to permission to open the file. It won't play embedded either. I get some stupid message which says something like: The URL is too long to play when I play in a new tab. Nothing happens when I try to open a new window.

---

### Post by lovinglinux on 2011-07-29
> **ColeTurner said:**
> I can never find the icon in the navigation bar.

Right-click on any toolbar, select "Customize", then drag Flash-Aid to any toolbar.

> **ColeTurner said:**
> I would rather get Flash Video Replacer to work. It worked beautifully before. But now, it won't play anything. When I try to play the video in Video Player, it tells me I might not have to permission to open the file. It won't play embedded either. I get some stupid message which says something like: The URL is too long to play when I play in a new tab. Nothing happens when I try to open a new window.

Looks like YouTube changed their site again and broke the extension. I will need to update the extension to make it work again.

---

### Post by ColeTurner on 2011-07-29
Why would Youtube do something so stupid?!

---

### Post by lovinglinux on 2011-07-29
> **ColeTurner said:**
> Why would Youtube do something so stupid?!

They do that from time to time :-)

---

### Post by ColeTurner on 2011-07-29
You as well as everyone else on this forum are super helpful. I am extraordinarily grateful.

---

### Post by lovinglinux on 2011-07-29
> **ColeTurner said:**
> You as well as everyone else on this forum are super helpful. I am extraordinarily grateful.

You are welcome.

---

### Post by ColeTurner on 2011-07-29
The Flash Video Replacer is brilliant!

---

### Post by lovinglinux on 2011-07-29
> **ColeTurner said:**
> The Flash Video Replacer is brilliant!

Thanks.

---

### Post by eurekabru on 2011-07-31
I've tried everything in this thread and the only thing working in Chrome is https but that's not a long term solution. It happened after I did Ubuntu updates. 

Chromium and Firefox work fine.

Any idea?

Edit: Nevermind, didn't clear the cache properly.

---

### Post by ColeTurner on 2011-08-01
I don't want to go back to using Flash Player again! I hate it!

---

### Post by ColeTurner on 2011-08-23
The Flash Video Replacer won't recognize my BS Player. Why is this? What can I do about it? It is giving me problems on Windows 7. What should be done? Will you help me?

---

### Post by lovinglinux on 2011-08-23
> **ColeTurner said:**
> The Flash Video Replacer won't recognize my BS Player. Why is this? What can I do about it? It is giving me problems on Windows 7. What should be done? Will you help me?

If BSPlayer is not listed, select Custom in the settings and then browse the player exe file.

---

### Post by ColeTurner on 2011-08-24
Custom isn't listed either.

---

### Post by lisungroup001 on 2011-08-24
do not extract the xpi file

---

### Post by ColeTurner on 2011-08-24
Okay. I've figured it out. I thank you for the help.

---

### Post by lovinglinux on 2011-08-24
> **ColeTurner said:**
> Okay. I've figured it out. I thank you for the help.

You are welcome.

---

### Post by ortaa23 on 2011-09-05
This has just happened to me again. Black screen, nothing. I did manage to get one video to load but no more. https doesn't work either. Anyone have a suggestion as to what to do?

---

### Post by lovinglinux on 2011-09-05
> **ortaa23 said:**
> This has just happened to me again. Black screen, nothing. I did manage to get one video to load but no more. https doesn't work either. Anyone have a suggestion as to what to do?

Have you tried to disable hardware acceleration? Have you tried Flash 11 beta?

---

### Post by ortaa23 on 2011-09-05
Seems to work again now. Very strange. Sorry, and thanks.

---

### Post by ortaa23 on 2011-09-05
Ok, so this is again not working. I ran update manager, which had something relating to Flash player, but it failed to get the file so I stopped it. Now it seems I can't restart it to try and get the things it failed to the first time round. I have Flash aid. Why does this have to be so hard?

---

### Post by ortaa23 on 2011-09-06
Can anyone please advise me what I need to do to get my flash player working again? Would be most grateful.

---

### Post by ortaa23 on 2011-09-06
Pretty please?

---

### Post by SpindizZzy on 2011-10-08
Ok, so i read through the whole thread and tried a lot of different solutions posted here.
 I still cannot view Youtube-movies.  :(

 Here's my generated 'report' from Flash-aid.

I'm hoping someone has time to take a look at this...
Thx in advance !!

---

### Post by lovinglinux on 2011-10-10
> **ortaa23 said:**
> Pretty please?

I don't now why this didn't appear in my thread list.

What is your current situation?

---

### Post by lovinglinux on 2011-10-10
> **SpindizZzy said:**
> Ok, so i read through the whole thread and tried a lot of different solutions posted here.
 I still cannot view Youtube-movies.  :(

 Here's my generated 'report' from Flash-aid.

I'm hoping someone has time to take a look at this...
Thx in advance !!

You are using a custom version of Firefox, installed in the opt folder. You need to create a symbolic link in that folder, pointing to the mozilla plugin folder.

```
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins
```

If you receive an error that the folder already exists and you haven't manually saved any plugin there then delete it before creating the symbolic link:

```
sudo rm -fr /opt/firefox/plugins
```

---

### Post by ColeTurner on 2011-10-11
Will a version which is compatible with Firefox 8 be made of my beloved plug in (Flash Video Replacer)?

---

### Post by lovinglinux on 2011-10-12
> **ColeTurner said:**
> Will a version which is compatible with Firefox 8 be made of my beloved plug in (Flash Video Replacer)?

Yes. I was unable to work on it recently, but I will start working on the new version next week. Meanwhile, I have changed the compatibility on Mozilla site. You should be able to install it soon. You shouldn't experience any errors, but let me know if you do.

---

### Post by ColeTurner on 2011-10-13
So, I was thinking. Flash Player is not a good player. I want to make a video sharing site which uses a different player (most likely VLC) for playing video. Is this doable? Is this a good idea?

---

### Post by lovinglinux on 2011-10-13
> **ColeTurner said:**
> So, I was thinking. Flash Player is not a good player. I want to make a video sharing site which uses a different player (most likely VLC) for playing video. Is this doable? Is this a good idea?

Nope. VLC isn't a good plugin either. I recommend using html5, particularly WebM.

See [http://videojs.com/](http://videojs.com/)

---

### Post by FLCL on 2011-10-16
Flash problem here, specifically related to YouTube and Chrome. 

When I try to load a video all i see is a black box, I do have audio though. 
Hardware acceleration disabled, installed Flash-Aid and ran the wizard, deselected "Override GPU verification" and restarted. No difference.
I have to refresh the page anywhere from 1-10 times before getting video.
Firefox works without a problem though

---

### Post by lovinglinux on 2011-10-17
> **FLCL said:**
> Flash problem here, specifically related to YouTube and Chrome. 

When I try to load a video all i see is a black box, I do have audio though. 
Hardware acceleration disabled, installed Flash-Aid and ran the wizard, deselected "Override GPU verification" and restarted. No difference.
I have to refresh the page anywhere from 1-10 times before getting video.
Firefox works without a problem though

If you are using Chrome 32bit, it comes with a bundled plugin. You need to disable it  to use the one installed by Flash-Aid. You can do that by typing [noparse]about:plugins[/noparse] in the address bar. However, I believe this is more a YouTube cookie problem. Have you tried to clean your cache and delete the cookies? Have you tried the https address?

---

### Post by FLCL on 2011-10-18
I've tried clearing all cookies, completely removing Chromium and flash from repo's and reinstalling with Chrome straight off Google's page. Same issue. Uninstalled and reinstalled with Chromium from repo's with flash off adobe

Edit: Tried removing all flash and using flash-aid, same issue.

---

### Post by lovinglinux on 2011-10-18
Have you tried the https address?

---

### Post by KBD47 on 2011-10-20
Hi, I was using Ubuntu 11.04 and flash worked fine on my computer. I installed 11.10 on the same computer and flash works but it is now slow and choppy on both Chromium and Firefox, though it is slightly better on Firefox. I uninstalled flash and then reinstalled it, but that didn't help. Any help appreciated.
KBD47
PS--I installed flash aid, but not sure what to do with it.

---

### Post by KBD47 on 2011-10-20
Just wanted to add that I did find the button and used the wizard to install the latest flash. I tried with the setting enabled and disabled, and disabled seems to work a bit better, but the flash is still slow and choppy. Anything else worth trying to improve the video?
Thanks!
KBD47

---

### Post by lovinglinux on 2011-10-21
> **KBD47 said:**
> Just wanted to add that I did find the button and used the wizard to install the latest flash. I tried with the setting enabled and disabled, and disabled seems to work a bit better, but the flash is still slow and choppy. Anything else worth trying to improve the video?
Thanks!
KBD47

Make sure you have the proprietary driver for you video card installed. You check that through *Additional Drivers* application.

---

### Post by KBD47 on 2011-10-21
Yeah, I checked additional drivers, but nothing there. I'm curious what Ubuntu or the Kernal changed that made my video go from great in 11.04 to rather horrible in 11.10
KBD47

---

### Post by lovinglinux on 2011-10-21
> **KBD47 said:**
> Yeah, I checked additional drivers, but nothing there. I'm curious what Ubuntu or the Kernal changed that made my video go from great in 11.04 to rather horrible in 11.10
KBD47

I suppose your card is blacklisted. I would recommend creating a thread with the model of your card in the title, if you cannot find a solution in the existing threads.

---

### Post by Mr. Jay on 2011-10-21
Hm.. rather a flash than a youtube problem, but anyway:

I built 2 similar boxes for my gf and me, i3-2130 with H61 chipset for her and i5-2500k with Z68 for me. Both using HD2000 resp. HD3000 IGP. Fresh 11.04 installation for her, fresh 11.10 installation for me. The i3 is running at stock speed 3.3 and the unlocked i5 at 4.2 GHz (CPU multiplier only, all other clocks including IGP are stock).

On her machine, one CPU core is at <40%. On mine, it was ~85% with the 32-bit plugin installed by default, while it's even ~92% with the latest 64-bit plugin installed manually. 
Since the system hardware is so similar, it looks like a regression from 11.04 to 11.10 to me.

I'm not complaining because after all it IS working and I didn't even have that %!(§%# flash for years, silly unfree plugin.. but I thought I'd remark it.

---

### Post by lovinglinux on 2011-10-21
> **Mr. Jay said:**
> Hm.. rather a flash than a youtube problem, but anyway:

I built 2 similar boxes for my gf and me, i3-2130 with H61 chipset for her and i5-2500k with Z68 for me. Both using HD2000 resp. HD3000 IGP. Fresh 11.04 installation for her, fresh 11.10 installation for me. The i3 is running at stock speed 3.3 and the unlocked i5 at 4.2 GHz (CPU multiplier only, all other clocks including IGP are stock).

On her machine, one CPU core is at <40%. On mine, it was ~85% with the 32-bit plugin installed by default, while it's even ~92% with the latest 64-bit plugin installed manually. 
Since the system hardware is so similar, it looks like a regression from 11.04 to 11.10 to me.

I'm not complaining because after all it IS working and I didn't even have that %!(§%# flash for years, silly unfree plugin.. but I thought I'd remark it.

Try Flash-Aid. It has an option to override GPU validation, which will probably reduce YouTube CPU usage. Also check if you have the proprietary video driver installed on your machine.

---

### Post by Mr. Jay on 2011-10-21
There is no proprietary driver, Intel IGPs had official open drivers from the start.
I'll try Flash-Aid when I get home.

---

### Post by pqwoerituytrueiwoq on 2011-10-21
> **lovinglinux said:**
> Try Flash-Aid. It has an option to override GPU validation, which will probably reduce YouTube CPU usage. Also check if you have the proprietary video driver installed on your machine.
they disabled hardware acceleration completely in the last release
[http://forums.adobe.com/thread/911321#3963295](http://forums.adobe.com/thread/911321#3963295)

---

### Post by Mr. Jay on 2011-10-22
Disabled because of concerns for their non-existant security, lol.
Then the explanation is probably that the 11.04 installation runs version 10 with HW support.

I tried the option Flash-Aid sets, but it makes it even worse.
But I can live with 90% CPU load for YT fullscreen. A browser is not a media player, in spite of all the unnerving attempts to turn it into one.

---

### Post by owenll on 2011-10-22
I have problems with videos on youtube slow and choppy in fullscreen. They work fine with minitube which is in the software centre.

---

### Post by lovinglinux on 2011-10-22
> **pqwoerituytrueiwoq said:**
> they disabled hardware acceleration completely in the last release
[http://forums.adobe.com/thread/911321#3963295](http://forums.adobe.com/thread/911321#3963295)

Indeed. I just tested GPU validation on YT and it doesn't change performance.

---


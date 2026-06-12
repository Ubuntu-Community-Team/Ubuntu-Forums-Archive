---
title: "Firefox 100% CPU for 30 minutes on Startup"
date: 2012-03-31
forum: General Help
---

### Post by held7over on 2012-03-31
Ubuntu 10.10, Firefox (canonical - 1.0)

I have been having this problem since Ubuntu 10.04. I have about 20 open tabs to ordinary webpages pages opened in my firefox browser when I start it up. This was no problem at first as it would quickly open up and be ready to go, then after some updates, when I open up Firefox, the CPU goes to 100% and Firefox is unusable for about 30 minutes and finally releases the CPU. Browsing some new sites will cause it to go back to 100% for a while, but most new sites thereafter, don't.

I found a fix that said to change my video drivers. I did that. And the problem was solved....and stayed solved for about two weeks. Then, Ubuntu had another update session, and the problem has returned. Changing the video drives back and forth doesn't work now, and searching the net hasn't given me a solution that works either.

This is a real pain. Does anyone have any suggestions???  Thanks!

---

### Post by lovinglinux on 2012-03-31
First, tr starting Firefox in safe mode to see if the problem persists.

```
firefox -safe-mode
```

Also, test Firefox in normal conditions, but without any open tabs, except for a forum page.

Let me know the results.

---

### Post by held7over on 2012-04-01
Hi lovinglinux,

Here is what I get executing "firefox -safe-mode" with all the tabs still in place:

[ Well, this is embarrassing. Firefox is having trouble recovering your windows and tabs. This is usually caused by a recently opened web page.You can try:
Removing one or more tabs that you think may be causing the problem. Starting an entirely new browsing session. ]

Instead, I picked "RESTORE":  Firefox only used, at max, 60% of the processor at the beginning this time and that dropped off in the first couple of minutes to about 17%.....which is still quite high for when it was working correctly. I saw xorg up as high as 35% at the very beginning, but it too rapidly dropped off to about 5% at the last, although it bounces up to 30% or so as I watch TOP. All through this, though, I was at least able able to click on the tabs and instantly have access to them...and able to open new URL's in new tabs and able to scroll down. 

OK. Second test -- I deleted all the tabs and restarted Firefox. The home page is Google. The CPU usage went to 100% for a couple of seconds and rapidly dropped off. The usage was between Firefox and xorg. Firefox quickly dropped down and stabilized at about.3%, but xorg seems to be jumping from time to time to 45% or more, and then back down to a low of 8.3%. 

Giving Firefox the Ubuntu Community Forum, Top reports Firefox using .3% after it has loaded the forum, and xorg is running between 4% and 16%.

What do you think?

---

### Post by zombifier25 on 2012-04-01
How many addons do you have installed? Some of them may be responsible for this.

---

### Post by held7over on 2012-04-01
I have 28 that are active, and 4 which Firefox has disabled because they are no longer compatible with this version of Firefox...I left them in the list, although they are disabled so I could watch for their newer compatible versions when they come out.....is that a mistake?

---

### Post by zombifier25 on 2012-04-01
28? It's a little too much IMO..
You should list the addons you have installed here. Of course, if you don't want to, then you don't need to.

---

### Post by HiImTye on 2012-04-01
28? wow! that's not a browser, that's an operating system!

---

### Post by lovinglinux on 2012-04-01
> **held7over said:**
> Hi lovinglinux,

Here is what I get executing "firefox -safe-mode" with all the tabs still in place:

[ Well, this is embarrassing. Firefox is having trouble recovering your windows and tabs. This is usually caused by a recently opened web page.You can try:
Removing one or more tabs that you think may be causing the problem. Starting an entirely new browsing session. ]

Instead, I picked "RESTORE":  Firefox only used, at max, 60% of the processor at the beginning this time and that dropped off in the first couple of minutes to about 17%.....which is still quite high for when it was working correctly. I saw xorg up as high as 35% at the very beginning, but it too rapidly dropped off to about 5% at the last, although it bounces up to 30% or so as I watch TOP. All through this, though, I was at least able able to click on the tabs and instantly have access to them...and able to open new URL's in new tabs and able to scroll down. 

OK. Second test -- I deleted all the tabs and restarted Firefox. The home page is Google. The CPU usage went to 100% for a couple of seconds and rapidly dropped off. The usage was between Firefox and xorg. Firefox quickly dropped down and stabilized at about.3%, but xorg seems to be jumping from time to time to 45% or more, and then back down to a low of 8.3%. 

Giving Firefox the Ubuntu Community Forum, Top reports Firefox using .3% after it has loaded the forum, and xorg is running between 4% and 16%.

What do you think?

I think you had a web page one of those tabs with a bad javascript.

Install [NoScript](https://addons.mozilla.org/en-US/firefox/addon/noscript/), [Flashblock](https://addons.mozilla.org/en-US/firefox/addon/433/) and [Ghostery](https://addons.mozilla.org/en-US/firefox/addon/9609/) and you will block most unwanted stuff.

> **held7over said:**
> I have 28 that are active, and 4 which Firefox has disabled because they are no longer compatible with this version of Firefox...I left them in the list, although they are disabled so I could watch for their newer compatible versions when they come out.....is that a mistake?

I usually have 60 add-ons active in my Firefox. Last time I did a clean up, I was able to reduce to 45.

The more add-ons you have, more memory Firefox will use and it will take more time to start. More add-ons also increases the chance of bugs and incompatibilities, but if you do a decent maintenance from time to time and keep an eye on the overall performance and extensions errors, then you can live with 28 add-ons perfectly fine.

Make a new test, with just Google page open in 1 tab, but this time don't use safe mode. Check if you see any difference in CPU and HD usage. If you do, then you might have a problem with one of your extensions.

> **zombifier25 said:**
> 28? It's a little too much IMO.

Is definitely much more than average, but not too much for my standards. I usually have twice that amount.

---

### Post by held7over on 2012-04-01
Changing Drivers:  System/Administration/Additonal Drivers-
Shows only two choices for me:

Nvidia accelerated graphics driver (ver 173) RECOMMENDED (which is currently installed)-

and

Nvidia accelerated graphics driver (ver 96)

I originally switched to the version 96 and that fixed it a very long time ago, however, it only lasted 2 weeks, to the next UPDATE, and thereafter, it had the same problem again I am describing...although, I did swap in the recommended, hoping that then it would solve the problem...but it didn't.

Hmmm. Upon listing my addon's, I discovered it is actually 8 addons that are disabled...which I listed below last in the list--

Adblock Plus 2.0.3
Adblock Plus Pop-up Addon 0.3
BetterPrivacy 1.68
Colorful Tabs 10.0
DownloadHelper 4.9.9
Download StatusBar 0.9.10
FlagFox 4.1.13
Flash Aid 2.2.2
ForecastFox 2.0.21
Hard Refresh 1.0
Lazarus: Form Recovery 2.3
NoScript 2.3.5
PDF Download 3.0.0.2
Print Edit 8.2
Read It Later 2.1.4
Redirect Remover 2.6.4
RightToClick 2.8.9
SearchBar Autosizer 1.5.7
Server Spy 0.2.1
Session Manager 0.7.8.1
Toolbar Buttons 1.0
Ubuntu Firefox Modifications 0.9.4
User Agent Switcher 0.7.3
Add to Searchbar 2.0  <-----------DISABLED
Auto Timer 1.7 <-----------DISABLED
CheckPlaces 2.6.2 <-----------DISABLED
ClearCache Button 0.9f <-----------DISABLED
Fisson 1.0.9  <-----------DISABLED
QuickRestart 1.1.6   <-----------DISABLED
Rewind/FastForeward Buttons 2.1.2009091201 <-----------DISABLED
Simple Timer + Clocks 1.4.1  <-----------DISABLED

---

### Post by held7over on 2012-04-01
I removed ALL the extensions except Ubuntu Firefox Modifications 0.9.4, which was already disabled (I hadn't noticed that before), and restarted firefox WITH ALL THE TABS I originally had open. It fairly quickly went from 100% CPU usage down to stabilizing at 1.3% with xorg jumping between 8% and 10%.

So, I will next start adding the extensions back, one by one, and restarting, to see if I can determine what might be causing the super long delay.  But....it is kind of strange that in the past, that I didn't have the long drawn out delay with the same extensions loaded...

I will let you know what I discover. Maybe there is a webpage that is doing this....but almost all the tabs are on linux sites, like OpenVZ information or LXC information, or IPtables info, etc...things I am trying to study.

---

### Post by lovinglinux on 2012-04-01
> **held7over said:**
> I removed ALL the extensions except Ubuntu Firefox Modifications 0.9.4, which was already disabled (I hadn't noticed that before), and restarted firefox WITH ALL THE TABS I originally had open. It fairly quickly went from 100% CPU usage down to stabilizing at 1.3% with xorg jumping between 8% and 10%.

So, I will next start adding the extensions back, one by one, and restarting, to see if I can determine what might be causing the super long delay.  But....it is kind of strange that in the past, that I didn't have the long drawn out delay with the same extensions loaded...

I will let you know what I discover. Maybe there is a webpage that is doing this....but almost all the tabs are on linux sites, like OpenVZ information or LXC information, or IPtables info, etc...things I am trying to study.

Sometimes extensions updates can cause conflicts with other extensions. Sometimes Firefox updates can cause extension errors.

Best way to find out is what you are doing. I would also open the Error console (SHIF+CTRL+J), click the ERROR filter and observe if any extension produces an error.

---

### Post by held7over on 2012-04-01
I had all my tabs loaded. I added the extensions back in, one by one, then with each install, killed Firefox from the commandline, and timed the start up to the point the CPU dropped off like falling off a cliff. Times ranged randomly ranged from as little as 52 seconds to 1 minute and 8 seconds. Then, after having added them all back in, except for those that Firefox had disabled. I rebooted the system, waited for it to drop to minimal CPU, and then launched Firefox. It timed out at 1 minute and 12 seconds to a CPU stabilized idle point....so to speak. That is a LOT BETTER THAN 30 MINUTES at 100% CPU!!! 

Color me very happy! Also, the startup of Firefox is no longer a solid 100% CPU draw, either, allowing one to be scrolling webpages and even launching new URL's in new tabs.

I will play with the Error console (SHIF+CTRL+J). That is new to me. And will make a reminder note, for the next this happens!

It sure looks like you assessment concerning extension and firefox updates causing conflicts is correct!!! As that seems to me to be the only answer indicated by my experiments and timing data...

I want to thank everyone for your help. This has been frustrating me a lot for a long time! Ha! Thanks!

---


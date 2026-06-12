---
title: "Firefox 4 flash glitch(s)"
date: 2011-04-22
forum: General Help
---

### Post by HappyLinux on 2011-04-22
I've got a problem with Firefox and Flash plugin. As you can see from the attached image, it doesn't render flash images/video properly and creates random white blocks over the image.

This isn't the only flash problem. On another website like [http://www.newgrounds.com]("http://www.newgrounds.com/") it tends to make the image flicker and/or reshow a previous frame for a split second and usually frequently and rapidly.

Youtube has a similar problem as the first one, but only on embedded clips. When a third-party website is using a Youtube clip with the Youtube player. (you know what I mean.) For example, the rotating circle in the centre is basically 4 white squares rotating in its place. When its buffering the image, the progress bar at the bottom it a white bar in its place.

On the Youtube website directly, it doesn't buffer any clips at all. After a few seconds, it instantly fills the progress bar with red and then plays the clip.

I've tried googling this problem, and apparently it's well known, and not isolated to just Linux. However, it is isolated to just Firefox 4. Chrome racks up similar errors in its log as FF4 does, but Chrome still renders Flash properly without any visual glitches.

However, for me, even though I can use Opera without this problem, the problem doesn't duplicate on FF4 under Windows7.

I've tried several things to try and solve this problem. Disabling FF4 hardware rendering, and increasing the local storage setting in Flash. Apparently one solution works for one person, but not another. Usually the case of the solution only works on 32bit systems. I'm running 64bit.

Can anyone help? Or should I just stick with using Opera until Adobe and Mozilla can solve this problem?

---

### Post by Vaphell on 2011-04-22
which version of flash do you use? 64bit beta or 32bit from repos?

---

### Post by HappyLinux on 2011-04-22
The one from the repos. Could never get the supposedly 64bit one from Adobe to install.

---

### Post by wojox on 2011-04-22
Have you tried the Firefox add-on from lovinglinux in my signature.

---

### Post by HappyLinux on 2011-04-22
> **wojox said:**
> Have you tried the Firefox add-on from lovinglinux in my signature.

Nice. That works great. Thanks.

---

### Post by wiltk on 2011-05-03
> **wojox said:**
> Have you tried the Firefox add-on from lovinglinux in my signature.

Just wanted to chime in and say that this extension worked for me also.  I was having a slightly different problem, where the progress bar of a flash video would blink black even when the bar is hidden.  Thanks wojox.

---

### Post by maverick280857 on 2011-05-10
The following link might help:

[http://danielj.se/2011/01/06/how-to-fix-flickering-flash-videos-in-firefox-4-in-ubuntu-64-bit/](http://danielj.se/2011/01/06/how-to-fix-flickering-flash-videos-in-firefox-4-in-ubuntu-64-bit/)

This made the flickering go away for me (after restarting firefox).

---

### Post by helgesdk on 2011-05-23
> **maverick280857 said:**
> The following link might help:

[http://danielj.se/2011/01/06/how-to-fix-flickering-flash-videos-in-firefox-4-in-ubuntu-64-bit/](http://danielj.se/2011/01/06/how-to-fix-flickering-flash-videos-in-firefox-4-in-ubuntu-64-bit/)

This made the flickering go away for me (after restarting firefox).
Installing flashplugin64-installer seems to work great!
I hope the Ubuntu team will make a generic fix soon.

---

### Post by HappyLinux on 2011-05-25
I already have the Flash 10.3 version installed, and it doesn't solve my problems.

---

### Post by trizrK on 2011-06-25
> **wojox said:**
> Have you tried the Firefox add-on from lovinglinux in my signature.
Can you please specify it so future readers(like me) can see it?
Thank you:D

---

### Post by lovinglinux on 2011-06-25
> **trizrK said:**
> Can you please specify it so future readers(like me) can see it?
Thank you:D

Flash-Aid is an extension that I develop, that is designed to solve issues and install the latest versions of flash. Essentially, it is a script generator that detects which flash plugins you have installed and other system settings, then generates a script to remove flash completely, install the latest version and apply some common tweaks that improve performance and solve common issues. The extension can execute the generated script for you or export to your desktop. 

More info at [http://www.webgapps.org/add-ons/flash-aid](http://www.webgapps.org/add-ons/flash-aid)

---

### Post by trizrK on 2011-06-25
> **lovinglinux said:**
> Flash-Aid is an extension that I develop, that is designed to solve issues and install the latest versions of flash. Essentially, it is a script generator that detects which flash plugins you have installed and other system settings, then generates a script to remove flash completely, install the latest version and apply some common tweaks that improve performance and solve common issues. The extension can execute the generated script for you or export to your desktop. 

More info at [http://www.webgapps.org/add-ons/flash-aid](http://www.webgapps.org/add-ons/flash-aid)
Thanks a bunch!:-)

---

### Post by lovinglinux on 2011-06-25
> **trizrK said:**
> Thanks a bunch!:-)

You are welcome.

---

### Post by Alasjo on 2011-06-26
Installed Flash-aid yesterday. Now my flash problems in Firefox are gone! Thank you!

However, I stille experience buggy flash in Chrome, does anyone have any idea how I can solve this problem? It is mostly connected to flash ads that messes up the screen when scrolling.

See [http://imgur.com/qMsMx](http://imgur.com/qMsMx) for a screenshot.

---

### Post by lovinglinux on 2011-06-26
> **Alasjo said:**
> Installed Flash-aid yesterday. Now my flash problems in Firefox are gone! Thank you!

However, I stille experience buggy flash in Chrome, does anyone have any idea how I can solve this problem? It is mostly connected to flash ads that messes up the screen when scrolling.

See [http://imgur.com/qMsMx](http://imgur.com/qMsMx) for a screenshot.

If you are running Chrome 32bit, then type [noparse]about:plugins[/noparse] in the address bar, then click the details button in top-right corner, then scroll to Shockwave Flash section and disable the version bundled with Chrome. This will make Chrome use the same version of Flash used by Firefox and installed by Flash-Aid.

---

### Post by Enigmapond on 2011-06-26
> **lovinglinux said:**
> If you are running Chrome 32bit, then type [noparse]about:plugins[/noparse] in the address bar, then click the details button in top-right corner, then scroll to Shockwave Flash section and disable the version bundled with Chrome. This will make Chrome use the same version of Flash used by Firefox and installed by Flash-Aid.

+1 In support of my good friend and this add-on. It solved all my issues.

Cheers!

---

### Post by Alasjo on 2011-06-26
> **lovinglinux said:**
> If you are running Chrome 32bit, then type [noparse]about:plugins[/noparse] in the address bar, then click the details button in top-right corner, then scroll to Shockwave Flash section and disable the version bundled with Chrome. This will make Chrome use the same version of Flash used by Firefox and installed by Flash-Aid.

In [noparse]about:plugins[/noparse] it seems i only have one flash player installed:
```
Namn: Shockwave Flash
Version: 10.3 d162
Plats: /usr/lib/mozilla/plugins/libflashplayer.so
```

Same version as Firefox uses..? Inactivating it makes flash unavailable (partially solving the graphics problem :rolleyes:). 
So is my problem GPU related? I am running Sandy Bridge internal grapics (Intel HD2000).

---

### Post by lovinglinux on 2011-06-26
> **Alasjo said:**
> In [noparse]about:plugins[/noparse] it seems i only have one flash player installed:
```
Namn: Shockwave Flash
Version: 10.3 d162
Plats: /usr/lib/mozilla/plugins/libflashplayer.so
```

Same version as Firefox uses..? Inactivating it makes flash unavailable (partially solving the graphics problem :rolleyes:). 
So is my problem GPU related? I am running Sandy Bridge internal grapics (Intel HD2000).

Are you sure you are using Chrome 32bit and not 64bit or Chromium?

Make sure all your browsers are the same architecture of your system.

---

### Post by Alasjo on 2011-06-26
> **lovinglinux said:**
> Are you sure you are using Chrome 32bit and not 64bit or Chromium?

64bit Natty / 64bit Chrome... :neutral:

---

### Post by lovinglinux on 2011-06-26
> **Alasjo said:**
> 64bit Natty / 64bit Chrome... :neutral:

Chrome 64bit doesn't have a bundled flash plugin. If the 64bit version installed by Flash-Aid isn't working, try the stable version from the repositories. Just execute Flash-Aid again, but changing the installation option to the stable version. Keep in  mind it is 32bit with a 64bit wrapper.

---

### Post by HappyLinux on 2011-06-27
Ever since I switched from Ubuntu 10.10 up to Kubuntu/Ubuntu 11.04, I've been having problems with flash. I've been using flash-aid for a while now, making sure to run it on a regular basis as it doesn't want to let me know when a new flash version is available (the setting is on to notify me of updates). At one point, their was an update, at it never told me about it.

My problem with Flash is this, whenever viewing videos, it has a habit of crashing the browser. More specifically, when viewing in fullscreen. Although some flash flicker a bit now and then on sites like newgrounds, it tends to mainly crash when viewing YouTube.

My browsers basically freeze/stall whenever viewing flash videos fullscreen.

---

### Post by stevation on 2011-06-27
> **lovinglinux said:**
> Flash-Aid is an extension that I develop, that is designed to solve issues and install the latest versions of flash. Essentially, it is a script generator that detects which flash plugins you have installed and other system settings, then generates a script to remove flash completely, install the latest version and apply some common tweaks that improve performance and solve common issues. The extension can execute the generated script for you or export to your desktop. 

More info at [http://www.webgapps.org/add-ons/flash-aid](http://www.webgapps.org/add-ons/flash-aid)
LovingLinux, you are a GOD! I'm only a month into using Ubuntu, and this flash thing was driving me crazy. Your fix is perfect! Thank you very much!

---

### Post by lovinglinux on 2011-06-27
> **stevation said:**
> LovingLinux, you are a GOD! I'm only a month into using Ubuntu, and this flash thing was driving me crazy. Your fix is perfect! Thank you very much!

You are welcome.

---

### Post by HappyLinux on 2011-06-28
Flash-Aid doesn't solve my Fullscreen issues.

---

### Post by lovinglinux on 2011-06-28
> **HappyLinux said:**
> Ever since I switched from Ubuntu 10.10 up to Kubuntu/Ubuntu 11.04, I've been having problems with flash. I've been using flash-aid for a while now, making sure to run it on a regular basis as it doesn't want to let me know when a new flash version is available (the setting is on to notify me of updates). At one point, their was an update, at it never told me about it.

My problem with Flash is this, whenever viewing videos, it has a habit of crashing the browser. More specifically, when viewing in fullscreen. Although some flash flicker a bit now and then on sites like newgrounds, it tends to mainly crash when viewing YouTube.

My browsers basically freeze/stall whenever viewing flash videos fullscreen.

> **HappyLinux said:**
> Flash-Aid doesn't solve my Fullscreen issues.

Flash-Aid only checks for updates once a day and I must change the date of update on the server. Sometimes it takes a couple of days until I do it, after a new version release.


About the fullscreen, try to disable hardware acceleration in Flash settings.

---

### Post by Alasjo on 2011-06-28
> **lovinglinux said:**
> Chrome 64bit doesn't have a bundled flash plugin. If the 64bit version installed by Flash-Aid isn't working, try the stable version from the repositories. Just execute Flash-Aid again, but changing the installation option to the stable version. Keep in  mind it is 32bit with a 64bit wrapper.

Yeah, the 32bit plugin is not helping either. So I guess flash is not the culprit here. I've had other graphics related issues with my Sandy Bridge system and **I hope they will be resolved with coming updates**...

Edit: Toggled Flash-aid back to beta and yesterday came an updated Xorg server as well as xorg-edgers driver. As of now, I'm not experiencing any graphics issues related to flash ads in Chrome anymore. Yay!

---

### Post by HappyLinux on 2011-06-29
> **lovinglinux said:**
> Flash-Aid only checks for updates once a day and I must change the date of update on the server. Sometimes it takes a couple of days until I do it, after a new version release.


About the fullscreen, try to disable hardware acceleration in Flash settings.

Ticked and not ticked, it doesn't matter, but that setting just doesn't seem to want to work.

---

### Post by lovinglinux on 2011-06-29
> **HappyLinux said:**
> Ticked and not ticked, it doesn't matter, but that setting just doesn't seem to want to work.

Type **about:config** in the address bar, then type **extensions.flashaid.flashbetaupdate** in the filter, right-click the resulting preference, select "Copy Value" and paste here.

Then type **extensions.flashaid.lastflashupdate** in the filter, right-click the resulting preference, select "Copy Value" and paste here.

---

### Post by HappyLinux on 2011-07-03
> **lovinglinux said:**
> Type **about:config** in the address bar, then type **extensions.flashaid.flashbetaupdate** in the filter, right-click the resulting preference, select "Copy Value" and paste here.

Then type **extensions.flashaid.lastflashupdate** in the filter, right-click the resulting preference, select "Copy Value" and paste here.

Here it is.

{ "flashbeta32" : "20110308", "flashbeta64" : "20101230"}

---

### Post by lovinglinux on 2011-07-03
> **HappyLinux said:**
> Here it is.

{ "flashbeta32" : "20110308", "flashbeta64" : "20101230"}

Indeed. Can you reach [http://updates.webgapps.org/flashbeta](http://updates.webgapps.org/flashbeta) ?

---

### Post by HappyLinux on 2011-07-04
> **lovinglinux said:**
> Indeed. Can you reach [http://updates.webgapps.org/flashbeta](http://updates.webgapps.org/flashbeta) ?

Yes, I can reach it. I saved the file. Now what?

---

### Post by lovinglinux on 2011-07-04
> **HappyLinux said:**
> Yes, I can reach it. I saved the file. Now what?

Don't need to save it. I just wanted to know if you had any connection issue with the file.

Try this:

[LIST]
[*]open Flash-Aid Preferences and make sure the option to check for updates is selected
[*]type **about:config** in the address bar,
[*]then type **extensions.flashaid.lastflashupdate** in the filter, right-click the resulting preference, select "Reset"
[*]restart the browser
[/LIST]

Check if you get an alert. If not, type **about:config** in the address bar, then type **extensions.flashaid.lastflashupdate**, copy the value and paste here.

---

### Post by HappyLinux on 2011-07-06
> **lovinglinux said:**
> Don't need to save it. I just wanted to know if you had any connection issue with the file.

Try this:

[LIST]
[*]open Flash-Aid Preferences and make sure the option to check for updates is selected
[*]type **about:config** in the address bar,
[*]then type **extensions.flashaid.lastflashupdate** in the filter, right-click the resulting preference, select "Reset"
[*]restart the browser
[/LIST]

Check if you get an alert. If not, type **about:config** in the address bar, then type **extensions.flashaid.lastflashupdate**, copy the value and paste here.

OK, I've done that. Now to see if it updates with the most recent version and the settings correct any problems.

---

### Post by lovinglinux on 2011-07-06
> **HappyLinux said:**
> OK, I've done that. Now to see if it updates with the most recent version and the settings correct any problems.

Keep in mind Flash-Aid only alerts you. You still need to run the Wizard again to install the newest version of flash. However, they haven't changed the version for while, so you already have the latest version if you executed Flash-Aid this month.

The alert test was just to see if it was actually checking for updates.

---

### Post by HappyLinux on 2011-07-12
> **lovinglinux said:**
> Keep in mind Flash-Aid only alerts you. You still need to run the Wizard again to install the newest version of flash. However, they haven't changed the version for while, so you already have the latest version if you executed Flash-Aid this month.

The alert test was just to see if it was actually checking for updates.

Fair enough

---

### Post by HappyLinux on 2011-07-14
Flash-Aid popped up saying there is a flash update available, so I installed the update.

However, I've isolated the problems with flash to within Firefox itself. There's no problem with flash under Chrome and Opera.

---

### Post by lovinglinux on 2011-07-14
> **HappyLinux said:**
> Flash-Aid popped up saying there is a flash update available, so I installed the update.

However, I've isolated the problems with flash to within Firefox itself. There's no problem with flash under Chrome and Opera.

Are you still having problems, even with Flash 11?

---

### Post by HappyLinux on 2011-07-15
> **lovinglinux said:**
> Are you still having problems, even with Flash 11?

Will get back to you on that. I'm currently using Chrome for my usual browsing.

---

### Post by Bleak888 on 2011-07-16
lovinglinux, I have flash-aid. It has worked great in the past but currently my flash has not worked for the past 3 days. I do not get the updates available notices that HappyLinux mentioned and I verified that option is checked in my preferences. Basically when Adobe makes their updates I don't have Flash for a week. Is there something I need to do differently? Any help appreciated.

---

### Post by HappyLinux on 2011-07-16
Flash 11 is working great. I just spent over an hour watching youtube longplay of Sonic the Hedgehog (Sad, I know), and not once did it freeze, crash etc.

---

### Post by lovinglinux on 2011-07-16
> **Bleak888 said:**
> lovinglinux, I have flash-aid. It has worked great in the past but currently my flash has not worked for the past 3 days. I do not get the updates available notices that HappyLinux mentioned and I verified that option is checked in my preferences. Basically when Adobe makes their updates I don't have Flash for a week. Is there something I need to do differently? Any help appreciated.

Get [Flash-Aid 2.2.0]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/"). I have changed the way it updates. Even if the update fails, you will be able to get the current Flash Beta 11 with that version of Flash-Aid.

---

### Post by Bleak888 on 2011-07-16
Thanks lovinglinux! I now have 11,0,1,60 installed and working.

---

### Post by lovinglinux on 2011-07-16
> **Bleak888 said:**
> Thanks lovinglinux! I now have 11,0,1,60 installed and working.

You are welcome.

---


---
title: "YouTube in Google Chrome"
date: 2010-09-06
forum: General Help
---

### Post by pipesville on 2010-09-06
When I try to watch a YouTube video using Google Chrome I get a black box that says "Missing Plug-in".  It doesn't ask if I want to install one, it just says it's missing.  How do I install the proper plug-in and where do I get it from?  I'm using Ubuntu 10.04 on a HP laptop with an AMD Turion X2 processor.  Thanks!

---

### Post by howefield on 2010-09-06
Try installing the package flashplugin-installer with System > Administration > Synaptic Package Manager or the Ubuntu Software centre.

---

### Post by pipesville on 2010-09-06
Checked and it was already installed.  I re-installed it and it still doesn't work.

---

### Post by fabyouless on 2010-09-24
Is there no solution for this problem that i, too, am experiencing? I search Google and come across a bunch of old solutions that are related to the 10.04 version that i am using. Can somebody point me to the right place to find solutions to the common problems i am coming against?

---

### Post by andymorton on 2010-09-24
Download the Ubuntu Restricted Extras package from the software centre and see if it works then. 

andy :)

---

### Post by gandaran on 2010-09-24
> **fabyouless said:**
> Is there no solution for this problem that i, too, am experiencing? I search Google and come across a bunch of old solutions that are related to the 10.04 version that i am using. Can somebody point me to the right place to find solutions to the common problems i am coming against?
which version of google chrome and if 32-bits or 64-bits?

---

### Post by 7h3d4rk0n3 on 2010-09-24
Are you using Google Chrome, or Chromium?

---

### Post by Mike Krall on 2010-09-27
I have same/similar problem... "missing plug-in" at YouTube and a lot of other places.

10.04 32bit... Chromium 6.0.472.53~r57914-

Mike

---

### Post by gandaran on 2010-09-27
> **Mike Krall said:**
> I have same/similar problem... "missing plug-in" at YouTube and a lot of other places.

10.04 32bit... Chromium 6.0.472.53~r57914-

Mike
do you have one or both of the following packages installed?
flashplugin-installer
ubuntu-restricted-extras
check with synaptic package manager.
if you don't have how did you install flash for firefox?

---

### Post by 0N3 on 2010-09-27
This flash plugin solved it for me:

[https://launchpad.net/~sevenmachines/+archive/flash/+packages](https://launchpad.net/~sevenmachines/+archive/flash/+packages)

---

### Post by Mike Krall on 2010-09-27
> **0N3 said:**
> This flash plugin solved it for me:

[https://launchpad.net/~sevenmachines/+archive/flash/+packages](https://launchpad.net/~sevenmachines/+archive/flash/+packages)

Maybe I'm not understanding... those all look like 64bit solutions.

Mike

---

### Post by Mike Krall on 2010-09-27
> **gandaran said:**
> do you have one or both of the following packages installed?
flashplugin-installer
ubuntu-restricted-extras
check with synaptic package manager.
if you don't have how did you install flash for firefox?

10.04 32bit... Chromium 6.0.472.53~r57914-

Don't have Ubuntu Restricted Extras and neither "flashplugin-nonfree" (transitional and removable) nor "flashplugin-installer".

My understanding is the Chromium version I have has flash embodied. Also, it looks like "flashplugin-installer" is for Netscape/Mozilla type. I didn't think Chromium was a Netscape/Mozilla based browser?

Have messed around a little with synaptic looking into Gstreammer pieces. Somewhere got the idea there may be a solution in that but don't understand well enough.

So you know... on 10.04, FF has the same "missing plug-in" problem. FF offers to install and it installs "gstreamer0.10-plugins-bad". Then YouTube, etc., work on FF but still not on Chromium or Opera, though there is a change to the later two... "missing plug-in" gone and first frozen frame showing but will not play.

Last, and not surprising really, on Win7-64bit (same machine), Chrome (not Chromium) plays YouTube, etc.

Mike

---

### Post by Banned. on 2010-09-27
try:
sudo aptitude install gsfonts gsfonts-x11 flashplugin-nonfree


How I solved this problem was quite stupid.

I went to youtube and when it said to install plug in, I installed flash player. Then I refreshed the page. It asked to install plug-in again. So I installed Gnash player. Then I uninstalled Gnash (onlt gnash, not official flash player) from Ubuntu software center. Restarted firefox and voila, the videos worked for me!

---

### Post by gandaran on 2010-09-27
> **Mike Krall said:**
> 10.04 32bit... Chromium 6.0.472.53~r57914-

Don't have Ubuntu Restricted Extras and neither "flashplugin-nonfree" (transitional and removable) nor "flashplugin-installer".

My understanding is the Chromium version I have has flash embodied. Also, it looks like "flashplugin-installer" is for Netscape/Mozilla type. I didn't think Chromium was a Netscape/Mozilla based browser?


Have messed around a little with synaptic looking into Gstreammer pieces. Somewhere got the idea there may be a solution in that but don't understand well enough.

So you know... on 10.04, FF has the same "missing plug-in" problem. FF offers to install and it installs "gstreamer0.10-plugins-bad". Then YouTube, etc., work on FF but still not on Chromium or Opera, though there is a change to the later two... "missing plug-in" gone and first frozen frame showing but will not play.

Last, and not surprising really, on Win7-64bit (same machine), Chrome (not Chromium) plays YouTube, etc.

Mike
chromium doesn't have built in flash (only google chrome has built in flash, for linux 32-bit version only) chromium uses the same system installed flash like firefox, install the flashplugin-installer package.

---

### Post by Mike Krall on 2010-09-27
> **gandaran said:**
> chromium doesn't have built in flash (only google chrome has built in flash, for linux 32-bit version only) chromium uses the same system installed flash like firefox, install the flashplugin-installer package.

Do you (or anyone) know what Gstreamer0.10, run in Synaptic, has for original configuration in 10.04? In my "messing around" I think I got "ffmpeg" and "ugly" installed as additional to standard. 

It looks to me like I need to install "flashplugin-nonfree" first, then "flashplugin-installer". Is that how it needs to go?

So you know, last night (running 10.04 and using Chromium) went to a Chromium (not Chrome) link to flash... said it was embodied in the Chromium I'm running. Not disagreeing with you, just saying what it looked like to me.

Mike

---

### Post by gandaran on 2010-09-28
> Do you (or anyone) know what Gstreamer0.10, run in Synaptic, has for original configuration in 10.04? In my "messing around" I think I got "ffmpeg" and "ugly" installed as additional to standard.
you will need to install all gstreamer codecs plugins except the debbuger ones. 
installing just the ubuntu-restricted-extras package would install all gstreamer codecs, open-java, microsoft fonts and adobe flash in one go.
> It looks to me like I need to install "flashplugin-nonfree" first, then "flashplugin-installer". Is that how it needs to go?
installing both could result in conflicting flash plugins, just choose one, any one will work.
> So you know, last night (running 10.04 and using Chromium) went to a Chromium (not Chrome) link to flash... said it was embodied in the Chromium I'm running. Not disagreeing with you, just saying what it looked like to me.
I am using chromium 6.0.472.53 (57914) and it doesn't have built in flash, if there is some version that does have I don't know about it, I also have google chrome installed in my netbook and this one has built in flash.

---

### Post by 7h3d4rk0n3 on 2010-09-28
That's odd, I don't know why it's telling you that it is embedded. All I had to do to get Chromium working is to install one of the plugins that were found when I tried to play a YouTube video. I think I installed the first one in the list.

---

### Post by Mike Krall on 2010-09-28
gandaran...

Is the "ubuntu-restricted-packages" and "flashplugin-installer" and either/or... or are both necessary?

Mike

---

### Post by Mike Krall on 2010-09-28
> **7h3d4rk0n3 said:**
> That's odd, I don't know why it's telling you that it is embedded. All I had to do to get Chromium working is to install one of the plugins that were found when I tried to play a YouTube video. I think I installed the first one in the list.

Where on YouTube or Chromium did you find a list of plugins? 

I've messed with putting "about-then a colon-then-plugins" (no spaces) into address bar on both FF and Chromium. Get different things, of course. FF shows "yes" to all in the list. Chromium shows a list and either "enable" or "disable". 

Is solving this problem as simple as enabling any/all in the Chromium list?

Mike

---

### Post by 7h3d4rk0n3 on 2010-09-28
I believe it's just one that is necessary.

---

### Post by 7h3d4rk0n3 on 2010-09-28
It just popped up the "require missing plugins" for me.

---

### Post by Mike Krall on 2010-09-28
> **7h3d4rk0n3 said:**
> I believe it's just one that is necessary.

Just "enable" the flash?

Mike

---

### Post by 7h3d4rk0n3 on 2010-09-29
That's all I had to do.

---

### Post by Mike Krall on 2010-09-29
> **7h3d4rk0n3 said:**
> That's all I had to do.

Just enabled "Shockwave Flash"... no change at YouTube

Tried enabling all on "about<colon>plugins" at Chromium... no change at YouTube

Mike

---

### Post by Mike Krall on 2010-10-14
> **gandaran said:**
> you will need to install all gstreamer codecs plugins except the debbuger ones. 
installing just the ubuntu-restricted-extras package would install all gstreamer codecs, open-java, microsoft fonts and adobe flash in one go.

installing both could result in conflicting flash plugins, just choose one, any one will work.

Well, I solved my problem by installing "Ubuntu restricted extras". I've no idea whether I needed to go that route or not but maybe I'll get more understanding down the road.

Thanks for your help, gandaran...

Mike

---


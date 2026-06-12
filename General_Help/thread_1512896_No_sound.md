---
title: "No sound"
date: 2010-06-18
forum: General Help
---

### Post by thehuman beard on 2010-06-18
I turned the computer on and I got nothing. The speakers are fine, I've reset and still nothing.

I've only been using Ubuntu for maybe 3 weeks, what sort of info do you need and where do I get it?

Sorry for not being more helpful, I've been trying to fix it myself but I keep hitting walls as the help pages get more in-depth.

---

### Post by Sin@Sin-Sacrifice on 2010-06-18
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by thehuman beard on 2010-06-18
> **Sin@Sin-Sacrifice said:**
> [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

ugh, been through this already and keep getting to things I don't understand but I'll take your posting of this link as a raised hand to explain to me what I don't understand.

---

### Post by thehuman beard on 2010-06-18
At step 2 my sound card is listed, even if it is on board. says access denied.

I'm supposed to click the link to search adn download alsa drivers but the link leads to a broken directory:

> Index of /alsa-doc

 Name                    Last modified      Size  Description
 Parent Directory                             -   
 alsa-lib/               16-Apr-2010 13:18    -   
Apache/2.2.3 (Linux/SUSE) Server at [www.alsa-project.org](www.alsa-project.org) Port 80

clicking any links here just stumps me as there isn't very much that resembles a list of sound drivers.

---

### Post by thehuman beard on 2010-06-18
I'm done, I don't know what to do and I am getting no help. Yes I've read your link, no it doesn't help me.

Reinstalling Ubuntu is the only way I can think of fixing this, but there must be a better way cos I can't imagine having to do this every time it decides not to work.

---

### Post by Deadite81 on 2010-06-18
In my personal experience I've never had a problem with Alsa.  When I was having problems I went through the same tutorials as well to no avail.

You say you've been using Ubuntu for 3 weeks...was the sound previously working?  It just quit out of the blue?

My proplems have always been with Pulseaudio being screwed up.  Pulseaudio is the sound server that allows for multiple applications to use sound at once.  With just Alsa you can only use one app at a time, and if some program "grabs" alsa and doesn't let it go nothing else will work.

Anyway, you can see if it's running in your system monitor.  There should be an entry in your for Pulseaudio in your Startup Applications as well.

If it was working fine for weeks and now it's not all of a sudden, it's probably not Alsa unless an update broke it somehow imo.  Alsa pretty much stays the same.  If it Never worked, that's a different story, it probably is Alsa then.

Unless you've found a solution elsewhere, it may be best to start small before going and editing config files and running crazy commands.  Is Pulseaudio running?  When you go to Sound setting in your menu what's listed in the "Applications" tab?  What does it say under the "Hardware" tab?

---

### Post by thehuman beard on 2010-06-19
> **Deadite81 said:**
> In my personal experience I've never had a problem with Alsa.  When I was having problems I went through the same tutorials as well to no avail.

You say you've been using Ubuntu for 3 weeks...was the sound previously working?  It just quit out of the blue?

My proplems have always been with Pulseaudio being screwed up.  Pulseaudio is the sound server that allows for multiple applications to use sound at once.  With just Alsa you can only use one app at a time, and if some program "grabs" alsa and doesn't let it go nothing else will work.

Anyway, you can see if it's running in your system monitor.  There should be an entry in your for Pulseaudio in your Startup Applications as well.

If it was working fine for weeks and now it's not all of a sudden, it's probably not Alsa unless an update broke it somehow imo.  Alsa pretty much stays the same.  If it Never worked, that's a different story, it probably is Alsa then.

Unless you've found a solution elsewhere, it may be best to start small before going and editing config files and running crazy commands.  Is Pulseaudio running?  When you go to Sound setting in your menu what's listed in the "Applications" tab?  What does it say under the "Hardware" tab?

It's gone beyond sound now, last night I couldn't even get the computer to shut down. kept logging out instead, I think some update has broken my OS. I'm going to backup everything and then reinstall.

---

### Post by thehuman beard on 2010-06-19
scratch that, sound works now. my drive is mounting. all i did last night was shut it down at the power button rather than the shutdown command.

this is so bizzar.

---


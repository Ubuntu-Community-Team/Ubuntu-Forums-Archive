---
title: "Really Really REALLY need help..."
date: 2009-07-23
forum: General Help
---

### Post by KFwLsKvVAs on 2009-07-23
I have almost no idea how to describe this...

I am running ubuntu 8.10, dual booting with xp.  Usually when I'm at work, Ubuntu is running and during the work week I just use it to play music and videos and such.  So basically during the week, I don't do any maintenance on it, aside from the occasional update.  

So What a surprise it was for me to randomly have cairo-dock stop working (when it opens up, it asks whether or not to enable openGL.  If I say yes, it brings up the preferences screen and when I close it it just asks to enable openGL again.  If I say no, cairo-dock starts but with no animations and a black box around it where there should be transparency).  I figure, what the hell, it's just a launcher, I can fix it some other time.  I go to open Banshee.  Banshee throws some error (I don't recall which, but it closed right afterwards.  Its working now so I don't know what the error was).  I try to open firefox, nothing happens.  When I ran it in the terminal, the error was....something like "something failed"   (I don't remember what the something was).  Opera gave the same error in terminal.  

So I looked, and my hard drive was nearly full.  I freed up about 30 gigs of space, rebooted, booted into recovery mode and tried fix broken packages and fix xserver.  Then I rebooted, and booted into this current session.  I didnt get any error messages right away, aside from the cairo-dock thing.  Tried opening banshee, banshee worked.  Tried opening firefox, it wanted to update to 3.0 (which I have already installed and upgradeded to 3. something else).  So I figure I should let it try to upgrade, it does, and now firefox is all...........bizarro.  I lost all my bookmarks from the bookmark bar, I think I lost most of my addons, and strangest of all I can't go back from any page, it's like it thinks there is no page to go back to.  On top of that, none of the "file  edit  view  history  etc..." are able to be clicked on, they are just grey and if I move my mouse over them they highlight but when I click nothing happens.  

Lastly, not sure if this is part of all that up there, but for a while I've gotten this error when I start up:

Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

So I click "run this action now" and get 

Failed to run synaptic '--non-interactive' '--update-at-startup' '--hide-main-window' as user root.

Unable to copy the user's Xauthorization file.



If I try to run nautilus as root, I get:

Failed to run nautilus as user root.

Unable to copy the user's Xauthorization file.


So..........basically everything was working fine for weeks, and then last night all this **** was just suddenly broke.  I've got the whole day to sit here and try to fix it, but I need someone to point me in the right direction.  Any help anybody could provide would be amazing.  Thanks...

---

### Post by KFwLsKvVAs on 2009-07-23
Ok, more strange-ness.   I closed firefox, and when I reopened it my bookmarks are back and my addons are working again.

---

### Post by KFwLsKvVAs on 2009-07-23
And I can now navigate back and forward in pages again...

---

### Post by KFwLsKvVAs on 2009-07-23
Oh, and here's something else.  When I try to download anything, firefox says 

There is not enough room on the disk to save "blahblah.whatever".

Remove unnecessary files from the disk and try again, or try saving in a different location.

This is AFTER I freed up space, according to nautilus, I have...38.5 GB free.

---

### Post by KFwLsKvVAs on 2009-07-23
I restarted, and now firefox doesnt think that I have no space on my computer.  So that's fixed...somehow.

---

### Post by KFwLsKvVAs on 2009-07-23
Well even though nobody helped, for some reason restarting a couple of times ended up fixing almost everything.  Still have some weird **** with packages not authenticated, but the system is running fine again.

---

### Post by CrusaderAD on 2009-07-23
Maybe you lost power or something during an update? Things get nasty when updates get interuptted.

---

### Post by Soul-Sing on 2009-07-23
> **murderape said:**
> Well even though nobody helped, for some reason restarting a couple of times ended up fixing almost everything.  Still have some weird **** with packages not authenticated, but the system is running fine again.

What is the outcome of
```
sudo apt-get update
```
is it a medibuntu key error?

---


---
title: "Maverick, disabling onboard video, Metacity, Update Manager..."
date: 2010-10-14
forum: General Help
---

### Post by qyot27 on 2010-10-14
Most of these issues are interrelated, except for the Update Manager part.

As usual with new releases, I did a fresh install of Maverick a couple days ago.  Installed the proprietary nvidia drivers through Additional Drivers, and then attempted to activate desktop effects...only to be told they couldn't be enabled.  So I looked for a solution and found compiz-check, which revealed that 10.10 was seeing both the GeForce 6200 I have in here and my original Intel i810e onboard video as active.  Under Lucid and Karmic, I didn't have issues with the two conflicting, as the Desktop Effects dialog worked correctly and never gave me any trouble in switching compiz on and off (that I couldn't attribute to user error, anyway).

I saw posts from July or thereabouts about this being a problem with compiz not recognizing the blacklist in /etc/modprobe.d or something to do with SKIP_CHECK, but the information seemed a bit scattered.  Adding 'blacklist agppart' and 'blacklist intel_agp' to /etc/modprobe.d/blacklist.conf didn't do a thing, and the other solution that involves hex-editing the compiz binary is out of the question.  Not because I'm uncomfortable doing it, I just don't want to have to repeat that every time an update for compiz comes down the pipeline.

I have no way to disable the onboard video through the BIOS.  This is a 9-year-old eMachines then-stock motherboard, and there is nothing to do with the onboard video hardware at all in the BIOS, only a single option about the onboard audio.  There's something about switching between PCI and AGP for add-on cards (which I have set to PCI...there are no AGP ports on this thing), but nothing about disabling onboard video.

So I decided to look through gconf, since I remembered Metacity's 'compositing manager' option.  That works fine, obviously.  But there's a small problem:

Upon reboot, the Gnome Panel loses its drop shadow, although menus and window borders have them.  Doing an Alt+F2 and running 'metacity --replace' refreshes the desktop and gets everything displaying correctly, but that's an extra step.  Unfortunately, adding that to the Startup Applications doesn't make it work on logging in.



Basically, the above can be boiled down to two things: any suggestions on how to disable/blacklist the onboard video in Maverick, and when using Metacity as a compositing manager, how to make sure the drop shadow is properly applied to the Panel on login without me having to run additional commands manually.





The problem I've been having with the Update Manager is that while it displays the updates and I can use Check to refresh the repo lists, when I click Install it looks like it's working and then stops and goes back to the list without installing any of the updates.  No error message dialogs pop up, it just doesn't install and then loads the list again.  Running a 'sudo apt-get update' 'sudo apt-get upgrade' from the Terminal works fine, though, and loading Update Manager after that shows no updates.

---


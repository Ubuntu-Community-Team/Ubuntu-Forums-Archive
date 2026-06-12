---
title: "Absolute Beginner having trouble with Wine &amp; Mangler!"
date: 2009-12-30
forum: General Help
---

### Post by Philosofen on 2009-12-30
Hey! I'm totally new to Linux, installed it yesterday night, and I've got a few problems.

First off, I got troubles with Wine. I'm trying to get Spotify & World of Warcraft to work.
I seem to have the same problems with both applications, the sound. The sound in Wow is horrible, just noise! In spotify when I try to play a song, sometimes it won't play at all & sometimes it will make the same noise as in World of Warcraft.

In winecfg -> Audio, I got "ALSA Driver" checked, none of the others.
Hardware Acceleration: Emulation
Default Sample Rate: 44100
Default Bits Per Sample: 16
Driver Emulation: Unchecked

When I try to press "Test Sound", it says "Error! Audio test failed!". I've tried to check all drivers (OSS, JACK etc etc), and the audio test still wont work.

So I thought I would uninstall Wine and reinstall it and see if that would work.
I uninstalled both Wow & Spotify from "Uninstall Wine Software", found Wine in Ubuntu Software Center. But there are no uninstall button there, onle "Upgrade". So I though, ah maybe that's the problem. But when I try to upgrade Wine, after 3% it says 
"Package dependencies cannot be resolved - This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time."
so I can't upgrade it. I really don't know how to solve all this! Please help me!

The other problem I've got is with Mangler (ventrilo like client)

I downloaded it from Manglers homepage, installed it, pressed server config. 
Then I filled in the right IP & port, filled in Server & User name and then Save.

Then when I press "Connect" it gives me "Server Error Message - could not authenticate server: timed out waiting for auth server." At this time there were other people on the ventrilo server, so the problem is not the server.

I would really appreciate some help with these problems. And since I'm new to Ubuntu, im having some difficulties with Linux terms etc, so please try to explain as much as you can.

Thank you

---

### Post by Tulth on 2010-01-07
From my experiences, this error
"Server Error Message - could not authenticate server: timed out waiting for auth server." 

just means it can't connect to the server.  I'd make sure there are no typos on the server name, and also try pinging the server.

---


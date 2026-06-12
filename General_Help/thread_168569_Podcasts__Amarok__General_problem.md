---
title: "Podcasts / Amarok / General problem?"
date: 2006-04-30
forum: General Help
---

### Post by Sarisar on 2006-04-30
So if you want the full story read this or skip to bottom for error.  Not sure if more info helps or not though...

OK so I was trying to find something to replace iTunes on Ubuntu - been on Ubuntu a little over a week and trying to not have to boot into windows except for games and mostly it's going fairly well.

However, I tried to find something to run as an iTunes replacement.  Something to grab podcasts off the net and download them and play them, and play the rest of my MP3s.  Found a thread talking about various programs and tried some of them.  Unless stated otherwise these were all from the official repositories (I'm still a little scared to go outside and play!)  Have listed what I think I did in the correct order just in case that helps.

iPodder - gets podcasts fine but doesn't play them itself.  This in my mind is pointless - I can use opera to RSS get the files anyway.  Uninstalled.

gPodder - does not run because my version of Python is too new - wasnt pre 2.2 I have 2.4 or something.  Uninstalled.

Amarok - after reading small print about not needing KDE to run a KDE application ran this, grabbed iPodSlave as have iPod so lets use that.  No sound at all.  Changed to the xine engine and finally got sound.  Seems to crash almost randomly so got annoyed and left it for a bit.  Did not uninstall as installed a few others while I was here anyway, so lets try those and see if they are better.

Banshee - had MAJOR problems here.  No sound at all.  Nothing.  Nada.  Found out (finally after an hour of trying) that it was because the gstreaming engine it uses hadn't got the MP3 library to decode it.  Downloaded those (gstreamer and it has gstreamer0.8-lame) and got sound, however still no way to download podcasts automatically.  Uninstalled.

Amarok (pt 2) - Maybe it was the drivers as per banshee and xine causing problems.  So reloaded up, changed back to gstreaming.  Sound now works.  Connect iPod.  Crashes.  Reload  Tried to download podcasts.  Tried to download too much - hangs and crashes.  Load up again.  Have to re-enter podcasts again but files still appear there... well some there some part but can resume downloads.  Listen to one podcasts, seems fine.  Pause it, try to do .. oh it's hung and crashed again.  Now I can't listen to any of these podcasts.  Try several different ones.  Always hangs.  Getting angry now.

Listen - again looks interesting but no way to download podcasts, plus had to download and install package from untested repository.  Did some updates (glibc perhaps?).  Uninstalled.

Amarok (pt3) - read about newer versions in KDE repositories so added that and downloaded the newest one there.  Same problems still occur.  Search boards find out about running through console.

Problem states:
*** glibc detected *** double free or corruption (!prev): 0x08a316e0 ***

Can't find much about this.  I also can't find an obvious glibc package in package manager (probably just me though).  Is there a simple 'install xxx package' to fix?

Thanks

---


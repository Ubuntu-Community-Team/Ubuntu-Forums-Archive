---
title: "Some Karmic Issues"
date: 2009-12-25
forum: General Help
---

### Post by Fernando Hernandez on 2009-12-25
Hello,

I just got a new laptop for Christmas, and the first thing I did was burn Karmic 9.10 to a live CD and install it on my machine (erasing the pre-installed Vista entirely).  I'd been using Jaunty before now, but I wanted to give the new version a spin...and already I'm having a few issues that I can't tell if are due to Karmic, the new machine, or some combination between the two and my general incompetence.  Any help would be greatly appreciated, otherwise I think I'll just go back to Jaunty, even though I really like some of the new features...

The main thing is that I can't get any audio to play from Flash, like YouTube and elsewhere.  Video is fine, but no sound.  Amarok is still playing MP3's for me, and I'm getting the startup and shutdown sounds, so I do have audio...I've googled numerous times to see people have had similar issues over the years, but none of the advice to fix the issue is really of any help.  What do I need to uninstall/reinstall/etc to get audio from Flash video again?

I also can't seem to play .mkv video files.  If this was Windows I'd say 'oh I need to go get the codecs' but I never recall having to do much of that such thing on Linux...Banshee played these files out of the box for me, as far as I remember at least.  What kind of support do I need to get various filetypes to work?  How do I get them?

One more issue that's really bugging me is that my system refuses to reboot or log me out.  The shut down command is working just fine, but when I click to restart or log out, nothing happens.  It's getting really annoying to have to shut my system down any time I want to log off...is this a known problem or might it just be my machine?

Sorry if my questions aren't very helpful.  I'm still learning the ropes of this OS and there are a lot of finer details like drivers and hardware issues that I know very little about.  Also, I'm not super experience with the terminal, so dumb it down as much as possible when it comes to necessary commands.  :)

Any help would be greatly appreciated.  I do like the overall feel of Karmic so far, so I'd hate to have to wipe it and start over with Jaunty again - it'd be nice to have a slightly new OS to experience with my new PC, but if it can't be helped then it can't be helped.  Still, though, I thought I may as well ask.  :)

---

### Post by Mahngiel on 2009-12-25
> **Fernando Hernandez said:**
> 
One more issue that's really bugging me is that my system refuses to reboot or log me out.  The shut down command is working just fine, but when I click to restart or log out, nothing happens.  It's getting really annoying to have to shut my system down any time I want to log off...is this a known problem or might it just be my machine?


I haven't seen any bug reports about the restart, but there is a bug report for the suspend feature.  I don't recommend using it if you aren't ready to hard reboot.

Only thing i can comment on elsewise is perhaps the flash issue.  Check your ALSA settings and make sure they're turned up. And check the plugins you're using. sometimes the non branded plugins are better for your machine.

---

### Post by Fernando Hernandez on 2009-12-27
Thanks for the reply, I managed to get the audio problem fixed, and while Banshee still won't play my video files I set up VLC and haven't had any problems.  The logout/restart issue is still occurring, though.  I'm wondering if this is an issue with the hardware if it's a problem that no one else has reported yet.  Shutdown works just fine, but restart and logout do nothing.

---

### Post by Kat of Zion on 2009-12-28
> **Fernando Hernandez said:**
> Thanks for the reply, I managed to get the audio problem fixed, and while Banshee still won't play my video files I set up VLC and haven't had any problems.  The logout/restart issue is still occurring, though.  I'm wondering if this is an issue with the hardware if it's a problem that no one else has reported yet.  Shutdown works just fine, but restart and logout do nothing.

How exactly was the audio problem resolved? I too possess Karmic on a new computer. Im using the Nvidia chipset and an Intel HDA sound card.  My audio does not play on YouTube (but visuals work fine).  Same goes for trying to play flash (flv) in MPlayer or VLC, rather than from the browser.  

In addition, VLC and Mplayer wont deal with MP3s (although lame is installed.

---


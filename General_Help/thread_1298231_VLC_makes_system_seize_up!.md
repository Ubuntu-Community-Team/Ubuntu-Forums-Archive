---
title: "VLC makes system seize up!"
date: 2009-10-22
forum: General Help
---

### Post by t0p on 2009-10-22
I'm using Hardy on my desktop computer.  It all worked fine yesterday.  But today, after a bunch of software updates, I'm getting some strange behaviour from the machine.

When I log in, everything seems to be working.  I get the login sound, I get sound playing videos in Firefox (eg Youtube videos), and I get sound if I play videos in Totem.

But if I try to play something in VLC: first of all I get no sound.  Then VLC begins to become unresponsive.  I click buttons and nothing happens.  Then buttons won't work in *anything*.  I have to press Ctrl+Alt+Backspace to logout. Then if I log back in straight away, the desktop won't load and it's all unresponsive again.  I have to actually restart the computer if I want it to work.  Everything is okay again... until I try to use VLC.

I know, maybe I should just stop using VLC, right?  But I *like* VLC when it's working properly.  I'd much rather use VLC than Totem. I can't remember if any of the updates yesterday were for VLC.  But *something* has clearly broken VLC, which in turn is breaking the entire system. Anyone know what's going on, and how to fix it?

---

### Post by prem1er on 2009-10-22
Have you launched VLC from the terminal and watched for errors? If so, what are they?

---

### Post by t0p on 2009-10-22
> **prem1er said:**
> Have you launched VLC from the terminal and watched for errors? If so, what are they?

Hmm... I started VLC in the terminal, played a video which played without audio, but there was no error message in the terminal.  Then I went to Tools > Preferences > Audio to change some settings as this is one of the actions that seems to trigger the seize-ups.  But this time it didn't become unresponsive, and when I changed the audio output type to Pulseaudio and started a new video, the sound worked.

This is very confusing.  I was able to make the fault start several times by doing that.  And now it's "fixed" all by itself? I don't know...

I shall post again if/when the problem returns...

---

### Post by prem1er on 2009-10-22
Were there any updates to VLC when you ran your update/upgrade to your system?

---

### Post by t0p on 2009-10-23
> **prem1er said:**
> Were there any updates to VLC when you ran your update/upgrade to your system?

I think there were, but I am not sure.  But the problem arose after the update so I suspected it as the cause.

I'm keeping an eye on the situation, and shall return if it returns.

---

### Post by P4man on 2009-10-23
Ive had issues with both VLC and SMplayer when the sound output was set to Alsa instead of Pulse. Most commonly, and quite frequently the video playback would just pause until I did a fast rewind or fast forward. I found that weird as SMplayer and VLC share next to nothing (since VLC has all its own codecs builtin) and I see no reason why they would not work with alsa, but switching to pulse did solve it for me.

---


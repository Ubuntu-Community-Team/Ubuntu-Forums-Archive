---
title: "Video Capturing/Editing/syncing in Ubuntu - best programs?"
date: 2012-07-18
forum: General Help
---

### Post by johnsmoke on 2012-07-18
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]I'm very much a beginner when it comes to any sort of video editing, but if anyone here can offer any kind of insight, I'll take it. I'm going to be filming some rock shows with a Sony Handycam mini DV camcorder. The built-in mic on the camera may not be up to my standards as far as quality, recording the loud show (and there is no external mic jack on it), so I'm recording audio separate on my Sony Hi-Md recorder.
 
Now, I've never done this before, but I will have to sync up my external audio to the mini dv video that I get from the show. So I will have to capture the video onto my computer via Firewire to get the raw AVI file(s) of my video - I browsed around and it looks like there are a few programs for Ubuntu out there that can do that, if anyone recommends a particularly good one, please do suggest.
 
The main thing and what seems to me like the most difficult task, will be to sync-up my separate audio to the AVI of the show. With Hi-Md I can rip it onto the computer as a wav file. Now, I'm open for suggestions; does anyone know what the absolute easiest program would be for Ubuntu that would allow me to sync-up my separate audio to my AVI video? I've heard AVIDEMUX can do this and it's a fairly bare-bones program that has gotten good feedback. I've read that to adjust the syncing of the audio in AVIDEMUX there's options to add/subtract it in milliseconds - so I guess to make this task as simple as possible, when I film the show I should try and hit record on my Hi-Md recorder and the video camera at the same time, or as close as I can possibly get it - and this should minimize the difficulty a bit when it comes to syncing?
 
Once I'm able to get that task complete, I'd like to make the finished AVI into a full DVD - and from what I understand "Devede" is a decent program that allows you to do this? 
 
This is all new to me, any insight you guys may have would be appreciated! Thanks.
[/SIZE][/FONT][/SIZE][/FONT]_[COLOR=#0066cc][/COLOR]_

---

### Post by JC Cheloven on 2012-07-18
Hi, first of all, video editting is a qualified profession, and the sync problem you mention is not at all easy in the insides. Many otherwise "good" video editors may have problems with that when kidding around with different formats of audio&video, even with the "original" audio tracks. So please, be prepared to cope with a mess of formats, codecs, containers, etc, you won't understand ;)

Well, what I used for some of your target tasks:

To take out the videos from your camcorder via firewire (IEEE-1394), Kino is probably the best, if not the one and only.

To add audio to the videos and sync them together, I've hheard good things about cinelerra. You might read [this article]("http://crazedmuleproductions.blogspot.com.es/2010/01/best-practices-to-alleviate-audio-sync.html") first, to get an idea.
EDIT: perhaps I'm overcomplicating things (you said you have little experience, and cinelerra is quite advanced). Please try out OpenShot as a more basic and easier solution. It can manage audio clips and video clips, you can cut and move them around... you'll probably find it suitable.

To make dvd's with menus, etc, and burn to disk, I used dvdstyler with quite some fun.

Hope it helps
JC

---


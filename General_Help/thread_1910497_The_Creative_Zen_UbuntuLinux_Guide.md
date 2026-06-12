---
title: "The Creative Zen Ubuntu/Linux Guide"
date: 2012-01-17
forum: General Help
---

### Post by wildcard_seven on 2012-01-17
Hi all. The internet has given me a lot, so I decided I'd finally give something back. I have an odd propensity for working with outdated technology. The details on how to use that technology are often lost in the wastelands of the internet, or spread across farflung locations. So, without further ado, here is (to my mind) the last word on using the Creative Zen in Ubuntu:

Exhibit A:

[IMG]http://reviews.cnet.com/sc/32589080-2-440-OVR-1.gif[/IMG]

The above is what I'm talking about: The plain Creative Zen...not Creative Zen M or other variants, although I suspect much of what I will say is still applicable.

WHAT YOU NEED: 

Rhythmbox (sudo apt-get install rhythmbox)
mtpfs (sudo apt-get install mtpfs)
mtp-tools (sudo apt-get install mtp-tools)
mencoder (sudo apt-get install mencoder)

WHAT HAPPENS WHEN YOU PLUG YOUR ZEN INTO YOUR COMPUTER VIA USB:

Nothing. It will "mount" but you won't be able to access it like a regular mass storage device (flashdrive, etc). It will show up on your desktop, but to move files to your Zen you will have to use Rythmbox or mtp-tools.

MUSIC:

Rhythmbox provides support for the Zen. Banshee does too, but it's sketchy in my opinion. Make sure you've done the following, first off:

                   
[LIST=1]
[*]                       Install the [**mtpfs**]("apt:mtpfs")                  and [**mtp-tools**]("apt:mtp-tools") packages.
[*]                       Open Applications &#8594; Sound & Video &#8594; Rhythmbox Music Player.
[*]                       Click Edit &#8594; Plugins
[*]                       Tick the *Portable Players - MTP* plugin.
[*]                       Click **Close**.
[/LIST]
                 
(from [https://help.ubuntu.com/10.04/musicvideophotos/C/music-portable.html](https://help.ubuntu.com/10.04/musicvideophotos/C/music-portable.html))

Okay, now here's how you connect with your Zen via Rhythmbox:

 1. Open Rhythmbox BEFORE plugging in your Zen.
 2. Plug in your Zen.
 3. Your Zen should appear in the left panel.

(note: occasionally it will say unknown device after following the above steps. Leave rhythmbox open, unplug Zen, plug it in again. Usually won't take more than two tries) 

Now you can drag and drop tracks as you please. It will say 0% the whole time (track transfer progress) while file is transferring, but when the message disappears, transfer is complete. It's pretty simple. When you're done, unplug your Zen while leaving rhythmbox open (I've gotten funny errors that required a Zen reset from unplugging after closing the application.

VIDEOS:

This is the real pain. You have two options: transfer video directly to the device, or to SD card which you can subsequently plug into your device (if you have one). But first, we'll cover getting your video into a format that the Zen will swallow.

I'll keep this short and sweet: proper video conversion for the Zen is a pain the butt. Outside of using the Zen software via Windows or windows via virtualbox, I've only had consistent success by one method: using mencoder (command line converter), with the below settings.

mencoder inputfile.avi -oac mp3lame -ovc xvid -xvidencopts bitrate=-1 -vf scale -zoom -xy 320 -o outputfile.avi

to use as a shell script:

mencoder $1 -oac mp3lame -ovc xvid -xvidencopts bitrate=-1 -vf scale -zoom -xy 320 -o $2

The above will give you a letterbox version of your movie, and should convert from multiple formats to the touchy Zen avi format. I'd prefer fullscreen videos on the small Zen screen, but at least the video looks good and video and audio sync properly. I've tried other methods, including the program winFF which has Zen presets, and several other mencoder variants, but the rest have been hit or miss.

TRANSFER VIDEO TO YOUR DEVICE:

1. Via SD Card

Easy as pie. Simply plop your converted video onto your card, plug it into your device, and call it a day. 

However, DO NOT...I REPEAT...DO NOT select the option "import all" option on your Zen from your SD card, thinking you can transfer the video to your main device. As far as I know, you can only transfer pictures this way. What will happen, is that the Zen will actually transfer the video to your device, but it will be INACCESSIBLE (you won't find it anywhere). Congratulations, you've just wasted several hundred MB of space on your Zen and you have no way to play your video or find and delete your file. If you make this mistake, you'll have to go in through mtp-tools or mount the Zen on windows where you can navigate the file system, and track down the inaccessible file so you can delete it.

There is one major drawback to the SD card method: you won't be able to pick up where you left off on your video. In other words, if you leave your video, you'll have to seek back to the previous spot where you were watching. I tend to find that a little annoying. It's just one of the many quirks of the Zen.

2. Via mtp-tools (directly to the device)

This is, in my opinion, the superior method. As long as you're watching one video at a time (which you *probably* will), if you exit your video, your location will be saved. However, you will have to use a funny bit of trickery to pull this off. We will use one of the mtp-tools command line tools, namely "mtp-sendtr". It goes like this:

1. Plug in your Zen (make sure Rhythmbox is not open).
2. Open a terminal and enter the command "mtp-connect". You should get a funny message but it will basically say that it recognizes your Zen.
3. enter command "mtp-sendtr yourvideo.avi Video/yourvideo.avi" to send your video to your device. Now, you are actually sending your video as  "music" track, which is going to prompt a funny dialogue. This is necessary though, because if you simply attempt a straight forward file transfer (mtp-sendfile), your video won't have any track information and you won't be able to seek forward and backward.

The dialogue goes like this (with your participation as indicated--in quotes. Don't actually type the quotes on the command line though):

Sending track yourfile.avi to Video/yourfile.avi
type:avi,8
Title> "anything you want here (really, anything)"
Album> "anything"
Album artist> "anything"
Artist> "anything"
Writer or Composer> "anything"
Genre> "anything"
Track number> "anything you want, but I always enter a number, to be safe--just type 1"
Year> "anything you want, I enter a number"
Length> "This is the important one--you need to enter the number of seconds 
              for the video: So for a movie that is 1 hr 55 minutes 30 sec = 6930. 
              Enter the number by itself."

...after you enter the length, it will say "sending track" and the rest will take care of itself.

(from [http://www.linuxquestions.org/questions/linux-hardware-18/creative-zen-4gb-video-not-searchable-670845/](http://www.linuxquestions.org/questions/linux-hardware-18/creative-zen-4gb-video-not-searchable-670845/))

CONCLUSION:

Well, that's all I've got. I don't really use the Zen for pictures, so I can't speak on that. Hopefully this saves some other weirdo using yesterday's devices some trouble. Mods, please move if this is in the wrong place.

---

### Post by lykeion on 2012-01-20
Thanks for a good guide wildcard_seven.

Since I also own, and still use a Creative Zen device I can add this:
Instead of Rhythmbox you can use Banshee (with MTP Media Player Support extension enabled) to import audios/videos onto the device. 

It works like a charm. Just plug in the device, make sure Rhythmbox isn't running, then start Banshee.

To convert videos to be playable in the device I use the same mencoder command-line options as wildcard_seven, with one small difference:
```
mencoder inputfile.avi -oac mp3lame **[COLOR="Red"]-vf scale=320:240[/COLOR]** -ovc xvid -xvidencopts bitrate=-1 -o outputfile.avi
```

Even though this device is quite old I'm still happy with it.

P.S I'm using Banshee 1.6.1 in Ubuntu 10.04

---

### Post by dmzamora on 2012-03-30
Hi to both of you! 
I have a creative zen (4gb), I tried to reformat it in win (crazy me!)...

Now, it does not detect the 4gb memory, only 50mb.
Is there a fix for this? I have tried installing the firmware, reformat, hard reset.. to no avail -- of course the reinstallation was done in win and not ubuntu...

Now I dont have a player!!!! :(

Maybe someone can help me how to fix it.
Oh there's another thing, my player's screen only shows white screen... it has been like this for so long but it still plays music so I did not bother at all...

Thanks!

---

### Post by stanbx on 2012-04-01
Thank you so much for posting this.  I still use the creative zen too.  Lost cable, couldn't charge it for awhile but just got it running again.

Really appreciate the how-to's

thanx,

s

---

### Post by Bhawani007 on 2012-04-01
Thanks wildcard_seven for this awesome how-to. I still have creative zen and was unable to mount it. This guide will save a day for me.

---

### Post by gyyug78fg87ogguiioioioioi on 2012-11-20
rythmbox on my computer closes itself automaticly when i try to transfer any songs to creative zen why!!

---


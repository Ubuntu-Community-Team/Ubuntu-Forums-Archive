---
title: "Can't get my Blue Snowball Mic to work with Ubuntu. :("
date: 2010-12-20
forum: General Help
---

### Post by TheNerdAL on 2010-12-20
It was working fine when I bought it. I think it was an update or something that made it stop. I don't think the Mic is broken, at least I hope not. Can anyone help? 

Please? I need it before tommorrow. I'm working on a video. 

Thanks.

EDIT: I mean Blue Snowflake.

---

### Post by TheNerdAL on 2010-12-21
I tested it on a Windows computer and it said it couldn't recognize it either, do you think it's the microphone?

---

### Post by SaberCat on 2011-03-19
I recently purchased a Blue Snowball from Best Buy (~$99) and have it running under Ubuntu 10.04 LTS (Lucid Lynx) on my desktop (Dell Inspiron 570) and laptop (Dell Inspiron 1501). This unit has a three position switch on the back for selecting gain/pattern (in researching it I got the impression that earlier models had a two position switch). I am running it in position one. Here's what I had to do to get Audacity to work with it for recording (I am using it to record piano music):

First, plug it into a USB port!

Edit|Preferences...|Devices|Recording|Device: Blue Snowball :...|Channels: 1(Mono)|OK

Edit|Preferences...|Recording|Sound Activated Recording|(check the box and set the level to -33db.|OK

Edit|Preferences...|Quality|Default Sample Format: (select 16-bit)|OK
(actually, you can do all of these and then press OK)

Next, you have to raise the audio input level: Click the speaker icon at the upper right of the desktop screen and select Sound Preferences...|Input|(set the button for Blue Snowball). Then move the Input volume: slider to the far right (full volume).

Now you should be able to record. But before you start, use the Zoom Out to increase the display timescale to beyond the time that you expect to record (so that Audacity does not have to redraw the display and possibly drop some audio samples). Press the red button on Audacity and then play some music (or make some noise!). You should see a plot of your audio. Press the yellow square to stop recording. Then press the green triangle to play it back. This all worked for me. Hope it does for you. It took me awhile to figure out how to set the input volume. That was the only problem I had...

I also have it working with Audacity under Windows 7 on my Dell 570. I had problems with skips (dropped samples). I solved this by raising the process priority of Audacity to 'High' and using Zoom Out to extend the display timeline beyond my record time.

---

### Post by CaroleKorea on 2011-05-05
Thanks Sabercat.  I'm a total newb and it worked for me.

---


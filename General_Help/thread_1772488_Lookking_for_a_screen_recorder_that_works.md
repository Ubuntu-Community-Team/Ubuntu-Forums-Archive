---
title: "Lookking for a screen recorder that works"
date: 2011-05-31
forum: General Help
---

### Post by bubbabeernuts on 2011-05-31
I've tried using recordmydesktop, Istanbul, XvidCap, and RecordItNow.  I can get video, but no audio.  I tried them on Ubuntu 10.04.  

On 10.04, recordmydesktop never saved.  It just hung, and then I needed to reboot.

I just tried recordmydesktop on Ubuntu 11.04 Gnome with no luck.  The video saved, but there was no audio.

Is there something I'm doing wrong?  Hope someone can help.

---

### Post by DinoT1985 on 2011-05-31
With Xvidcap did you tick Enable Audio in preferences?

[IMG]http://www.kabatology.com/wp-content/uploads/2007/10/preferences.png[/IMG]

Edit: seems its a version issue.

> The version in Ubuntu Software Center does not support audio.  To record audio as well as video you must first download the Sourceforge version of Xvidcap, then lock in the version .  After that, you must run it via the terminal as PADSP XVIDCAP.  Even so, it is clunky to configure sound and very, very frustrating to use.  You must download PULSE AUDIO VOLUME CONTROL.  There are different settings in pulse for recording the sound of a video you are playing and there is another setting for recording from a microphone.  Nor are the settings persistent.  Getting it to work twice in a row is difficult.  If someone who knows how to program could alter this program for easy use, it would be a great benefit to Ubuntu.  There are other programs in Ubuntu that can capture audio and video, but they are not as good as xvidcap.  The fact is, there is room in Linux and Ubuntu for a good. easy to use video and audio capture program.  Xvidcap is the best of several programs, none of which are very good.  I have two YouTube videos showing the settings for 10.10.  However, since upgrading to 11.04 I have not been able to get Xvidcap to work, despite having made 30 YouTube videos.  YouTube videos with sound are the BEST way to show how a program works and also to show bugs.

---

### Post by bubbabeernuts on 2011-05-31
Thanks for the response!  I already have Pulse Audio installed.  I'll give it another whirl tomorrow & let you know how it goes.

---

### Post by coldraven on 2011-06-01
I used Kazam on 10.10 and had no problems.
See [URL="http://www.omgubuntu.co.uk/2010/12/record-screen-linux/"]http://www.omgubuntu.co.uk/2010/12/record-screen-linux/
[/URL]

---

### Post by sbraz on 2011-06-01
> **coldraven said:**
> i used kazam on 10.10 and had no problems.
See [url="http://www.omgubuntu.co.uk/2010/12/record-screen-linux/"]http://www.omgubuntu.co.uk/2010/12/record-screen-linux/
[/url]

+1

---

### Post by bubbabeernuts on 2011-06-01
> **DinoT1985 said:**
> With Xvidcap did you tick Enable Audio in preferences?

[IMG]http://www.kabatology.com/wp-content/uploads/2007/10/preferences.png[/IMG]

Edit: seems its a version issue.

Yeah, Enable Audio is checked.

I tried it again, but still no love.  Anything in particular I should be doing with the settings in Pulse Audio?

One thing I noticed in Pulse Audio under the Recording tab while I was running a capture.  The message "No application is currently recording audio" is display, all grayed out.  Is this significant?

---

### Post by bubbabeernuts on 2011-06-01
> **sbraz said:**
> +1

OK, so I installed Kazam as well.  Looked promising.  But when I go to save the screen capture, I run into problems.

I get the "What do you want to do now?" dialog box.  I tick "Save for later use...", and click Continue. The Save Screencast dialog pops up, and I click Save.  It then bounces back to the "What do you want to do now?" box.  And that's all it does; it just goes back & forth.  It won't let me save.  This is on my 10.04 box.

And I just tried Kazam on my 11.04 box.  The video will save there.  But there's still no audio.   Help?

---

### Post by Habitual on 2011-06-01
Vlc

---

### Post by coldraven on 2011-06-04
I don't know if this is relevant but maybe worth a try.
Run```
alsamixer
```
Press F4

Check your internal mic. and capture levels

---

### Post by bubbabeernuts on 2011-06-13
> **Habitual said:**
> Vlc

Thanks, but all the tutorials I found online weren't very helpful.  If you could point me to an Ubuntu-friendly tutorial, I'd appreciate it a lot.

---

### Post by bubbabeernuts on 2011-06-13
> **coldraven said:**
> I don't know if this is relevant but maybe worth a try.
Run```
alsamixer
```
Press F4

Check your internal mic. and capture levels

Are there any Alsamixer tutorials?

---

### Post by celem on 2011-06-24
I don't believe that loading the Sourceforge version is still required. As I understand it, there was a period when the audio support was missing in the repo version. The audio support is now there. I was unable to get xvidcap to record audio from my microphone until I changed the audio codec in preferences to PCM16. Works great with that setting.

---

### Post by Eyore15 on 2011-06-24
> **bubbabeernuts said:**
> I've tried using recordmydesktop, Istanbul, XvidCap, and RecordItNow.  I can get video, but no audio.  I tried them on Ubuntu 10.04.  

On 10.04, recordmydesktop never saved.  It just hung, and then I needed to reboot.

I just tried recordmydesktop on Ubuntu 11.04 Gnome with no luck.  The video saved, but there was no audio.

Is there something I'm doing wrong?  Hope someone can help.

I've never used it, but I recall someone recommending "wink" (I think that's correct); it was supposed to be in the repositories.

---

### Post by aneganov on 2011-07-09
I think the best app for screencasting is XVidcap, but i'm unable to record audio. Wasted 2 hours trying to get in working - no luck. 
I launch xvidcap using padsp with device set to /dev/dsp. This is what I get once I start recording:

**xtoffmpeg.c add_audio_stream(): Can't initialize fifo for audio recording**

It seems to me, that nobody in the Internet knows how to fix this.

==

Kazam looks good, but it can't capture windows, part of screen, has no mouse-follow abilities etc. In other words - its too primitive.

---

### Post by haqking on 2011-07-09
Kazam rocks, so much better than the others

---

### Post by aneganov on 2011-07-09
> **haqking said:**
> Kazam rocks, so much better than the others

Well, I've just tested it. It captured whole my screen, including parts which I don't want to show to public - like my username, open tabs etc. And then it exported video to videobin.org, auto resizing (reducing) it to the values which made screencast unreadable. Sorry, I just can't get - what exactly were so rocking?

EDIT. Ah, I've got a thought! Kazam is the TRUE screencaster - it casts X screens, not windows ;-)

---

### Post by bubbabeernuts on 2011-07-09
> **celem said:**
> I don't believe that loading the Sourceforge version is still required. As I understand it, there was a period when the audio support was missing in the repo version. The audio support is now there. I was unable to get xvidcap to record audio from my microphone until I changed the audio codec in preferences to PCM16. Works great with that setting.

Tried resetting audio codec to PCM16 - still no love.  Oh, screen capture apps, why is it you taunt me so by failing to capture audio?

---

### Post by aneganov on 2011-07-09
> **bubbabeernuts said:**
> Tried resetting audio codec to PCM16 - still no love.  Oh, screen capture apps, why is it you taunt me so by failing to capture audio?

+1
What's wrong with them?
Actually, I would pay for a right screencasting app...

---

### Post by raiden82 on 2011-07-29
Hi, i've tried every software myself and none works, at all, no video neither audio any suggestions?

thanks

Ubuntu 11.04

---

### Post by ElanCompaq on 2012-06-12
Kazam Screencaster is a good one i think, simple layout but good quality

---

### Post by ElanCompaq on 2012-06-12
WHats preventing you from using the programs?

---

### Post by elliotn on 2012-06-12
recordMyDesktop works for me

---


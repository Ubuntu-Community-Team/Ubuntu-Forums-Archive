---
title: "New Phone feature via Google / Gmail"
date: 2010-08-27
forum: General Help
---

### Post by mdouble on 2010-08-27
Wednesday of this week Google added a new feature to Gmail. The feature allows users to call any phone in North America directly a standard phone rom their computer free of charge.  I don't know if this includes cell phones, but it does work with a land line.

My son, using his Mac, called my home phone to alert me to the feature.  The feature appears as a new option in the Gmail, which, as memory serves is a new item under the chat menu.  

On learning of the new feature, I immediately logged into my Gmail account to check it out.  However, it appears that to work, the feature requires the download of a small application.

Once the application has downloaded a the feature appears as a new option in the Gmail menu.    

I run XP in a dual boot set up on my main computer but use Ubuntu exclusively on my netbook.  I was able to install the application under XP and it works perfectly.  However it does not seem to work under Ubuntu.

Google does provide a message that indicates that the new feature will work on Window's Mac's and Linux.  However this seems not to be the case for Ubuntu.  

Does anyone out there have experience with using this new feature under Ubuntu.  If yes, please advise about how you got it to work.

Being that this is an entirely free service offered by Gmail, it would be very useful to have.    

Thanks in advance

---

### Post by cambot on 2010-08-27
I noticed it actually available from Canada today, which they said it was only available from the US. Maybe it's an anomaly.

I used it on Ubuntu. Installed the plug-in, called my cell, however the quality is garbage. Not impressed yet. I'll keep tweaking to see if it's something on my system/headset/whatever. I really want this to be a Skype replacement though.

---

### Post by LowSky on 2010-08-27
Works for me... if the gmail plugin isn't working for you, it could be a problem with your browser's net policies.

Aslo You could always just use the google voice website.
[http://www.google.com/googlevoice/landing/index.html#utm_source=en-ha-na-us-sk&utm_medium=ha&utm_term=google%20voice&utm_campaign=en](http://www.google.com/googlevoice/landing/index.html#utm_source=en-ha-na-us-sk&utm_medium=ha&utm_term=google%20voice&utm_campaign=en)

---

### Post by mdouble on 2010-08-27
Hi and thanks for your reply.  I just got mine working.  I discovered that I need to download the, plug-in which I previously had not done.  I just called my cell phone using the feature and the quality was very respectable.  I've used Magic Jack and Skype for long distance calls, but this new Gmail feature should be more convenient.  I think it's pretty cool.  Since I use Gmail all the time, this is a really nice additional feature.

---

### Post by mdouble on 2010-08-27
> **mdouble said:**
> Wednesday of this week Google added a new feature to Gmail. The feature allows users to call any phone in North America directly a standard phone rom their computer free of charge.  I don't know if this includes cell phones, but it does work with a land line.

My son, using his Mac, called my home phone to alert me to the feature.  The feature appears as a new option in the Gmail, which, as memory serves is a new item under the chat menu.  

On learning of the new feature, I immediately logged into my Gmail account to check it out.  However, it appears that to work, the feature requires the download of a small application.

Once the application has downloaded a the feature appears as a new option in the Gmail menu.    

I run XP in a dual boot set up on my main computer but use Ubuntu exclusively on my netbook.  I was able to install the application under XP and it works perfectly.  However it does not seem to work under Ubuntu.

Google does provide a message that indicates that the new feature will work on Window's Mac's and Linux.  However this seems not to be the case for Ubuntu.  

Does anyone out there have experience with using this new feature under Ubuntu.  If yes, please advise about how you got it to work.

Being that this is an entirely free service offered by Gmail, it would be very useful to have.    

Thanks in advance  

I got it working by installing the voice chat plug in which I previously had not done.

---

### Post by mdouble on 2010-08-27
> **LowSky said:**
> Works for me... if the gmail plugin isn't working for you, it could be a problem with your browser's net policies.

Aslo You could always just use the google voice website.
[http://www.google.com/googlevoice/landing/index.html#utm_source=en-ha-na-us-sk&utm_medium=ha&utm_term=google%20voice&utm_campaign=en](http://www.google.com/googlevoice/landing/index.html#utm_source=en-ha-na-us-sk&utm_medium=ha&utm_term=google%20voice&utm_campaign=en)
Thanks for the additional info re the Google Voice website, I will be sure to check it out.  You may note from replies I've already posted that I got the service working by installing the required plug-in, which I had not previously done.  I used the feature to call my cell phone and it seemed to work pretty well.

---

### Post by cambot on 2010-08-31
Can I ask if you've had any success/problems with the call quality on the Google Phone? My VoIP experience on Ubuntu has been garbage. However the same feature on a Windows machine on the same network is fine. I suspect the issue is PulseAudio. However, recording from the same mic in Ubuntu is fine. It only seems to be VoIP. My voice is garbled, chunky and broken up.

---

### Post by damontallen on 2010-09-07
> **cambot said:**
> Can I ask if you've had any success/problems with the call quality on the Google Phone? My VoIP experience on Ubuntu has been garbage. However the same feature on a Windows machine on the same network is fine. I suspect the issue is PulseAudio. However, recording from the same mic in Ubuntu is fine. It only seems to be VoIP. My voice is garbled, chunky and broken up.

Cambot did you ever get Google Phone to work?  I am having the same problems as you.

---

### Post by cambot on 2010-09-07
No. It's still garbled. It's a base install as well- I haven't done anything to change the PulseAudio Settings. The mic is fine in recording locally, but as soon as an acutal VoIP call is made it's garbled and inaudible. Same with Skype. However a Windows machine on the same network is fine.

---

### Post by brimlar on 2010-09-07
Just thought I'd verify what you guys were talking about:

Often enough, the call quality through Gmail Phone is garbage.  Echoes, fuzziness, distortion -- but when I switch over to my Windows 2008 R2 partition on the same computer, it works perfectly.

There is something funny going on with Google's .deb plugin and something else.

---

### Post by cambot on 2010-09-07
Yes..however it only happens with VoIP calls. Local recording is fine. However Skype is also buggered. I still maintain it's a PulseAudio problem.

---

### Post by brimlar on 2010-09-17
True, I haven't noticed any problems recording sound locally.  It's only when using Google's phone.  I haven't tried Skype however to see if it happens with that, too.

I've used voice chat in Ubuntu (non-VOIP) using different programs and that worked fine, even Ventrilo over WINE.

---

### Post by Tom Collier on 2010-09-17
I just started using Google's VoIP phone with no problems (well, except one minor one that is the subject of this post)...excellent quality locally and long distance.

However, under the Sound Preferences, I can't get the input and output settings to persist. I have to designate my USB headset/mic each time I open Google phone from Gmail in the Chrome browser. Default has the audio coming out of the netbook's speakers and (presumably, although I've never used it a built-in mic. Come to think of it, there may not be a built-in mic since my netbook does not have a built-in webcam.)

Using a generic USB headset/mic on an eeePC 1000HD running Karmic 9.10, NOT the netbook remix version.

Any ideas how to get the settings to persist?

Back after an experiment:  Interesting....the settings persist in Gmail in Firefox, but not Gmail in Chrome.

UPDATE: This forum is amazing! Not 20 minutes after I post this problem, the audio settings start to persist in Chrome, too! Howja do that???

---

### Post by cambot on 2010-12-16
I think I might have found a fix for this issue...it's not pretty but testing with my Cell has gotten some much better results...

Here is the link from Google's pages:

[http://www.google.com/support/forum/p/Talk/thread?tid=6b8c03ea307a92af&hl=en](http://www.google.com/support/forum/p/Talk/thread?tid=6b8c03ea307a92af&hl=en)

---


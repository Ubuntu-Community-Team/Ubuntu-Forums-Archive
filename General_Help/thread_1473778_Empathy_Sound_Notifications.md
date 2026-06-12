---
title: "Empathy Sound Notifications"
date: 2010-05-05
forum: General Help
---

### Post by haydemon on 2010-05-05
I've recently upgraded to Ubuntu Lucid from Karmic, and although I've been pretty happy with both versions overall, I cannot seem to resolve this problem since Empathy became the IM client of choice: I can't get sound notifications when IM's come in. I keep missing my chats this way and it's no fun. Usually I'm involved in a task and don't think to look up to see if anyone has tried to reach me, and often I realize too late when someone has. I'm becoming anti-social without meaning to! Can someone provide some guidance? Please no overly technical instructions, because I'm still somewhat of a novice. Thanks!

---

### Post by GilbertEvanG on 2010-05-06
This same problem is happening to me too.

---

### Post by jatoo on 2010-05-10
Yes, I am having the same problems, it's a real pain.  I like having the integration with Ubuntu's panel but this bug does make me want to change to another program for the sounds. 

I've tried changing settings in Empathy but nothing works.

Anyone have any idea?

---

### Post by agarciamog on 2010-05-11
I'm having the same issue.

---

### Post by kokonobs on 2010-05-12
Same here.

Also my video and voice chats are not active.

---

### Post by Joseph Schwenker on 2010-05-20
I am having the same problem.  Can someone fix this?

---

### Post by SeanBlader on 2010-05-27
Looks like after a long list of posts that there is no solution it's very annoying.

---

### Post by JoeGoalie on 2010-06-16
Also having the same issue right now...  Would love to see someone offer some sort of solution.

---

### Post by warfacegod on 2010-06-16
Try Pidgin.

---

### Post by CaptSpify on 2010-08-15
> **warfacegod said:**
> Try Pidgin.

Yeah, if you like your passwords being stored in Plaintext...

[http://developer.pidgin.im/wiki/PlainTextPasswords](http://developer.pidgin.im/wiki/PlainTextPasswords)

Anyone else have any ideas on how to fix the issue?

---

### Post by Aearenda on 2010-08-15
I reckon this works:
1. In the sound preferences, make sure you have a sound theme selected other than 'no sounds'. Push the Alert volume all the way up and unmute it. 
2. In Empathy's settings, make sure you have selected which events you want sounds for, and make them happen whether you are away or not.

---

### Post by haydemon on 2010-08-16
> **Aearenda said:**
> I reckon this works:
1. In the sound preferences, make sure you have a sound theme selected other than 'no sounds'. Push the Alert volume all the way up and unmute it. 
2. In Empathy's settings, make sure you have selected which events you want sounds for, and make them happen whether you are away or not.

Tried it. It doesn't.:confused:

---

### Post by Aearenda on 2010-08-16
I wonder what's different on your system from mine! I assure you it does work for me in Empathy, even though I'm normally a Pidgin user, occasional worry over plain text passwords being overridden by the extra features it offers.

Do you get any sounds from Ubuntu if you try clicking on different alert sounds in the sound control panel? On mine, each sound (sonar, bark etc) plays when selected, though it is necessary to reselect the Ubuntu theme after testing them.

Before the annoying login sound had a setting, some people deleted the sounds from /usr/share/sounds/ubuntu/stereo to get rid of it. If you did this, make sure message-new-instant.ogg is present in that folder. Can you play that sound from Nautilus?

Also see the last comments in [this bug]("https://bugs.launchpad.net/ubuntu/karmic/+source/ubuntu-sounds/+bug/400485").

---

### Post by narchy81 on 2011-01-21
> **haydemon said:**
> I've recently upgraded to Ubuntu Lucid from Karmic, and although I've been pretty happy with both versions overall, I cannot seem to resolve this problem since Empathy became the IM client of choice: I can't get sound notifications when IM's come in. I keep missing my chats this way and it's no fun. Usually I'm involved in a task and don't think to look up to see if anyone has tried to reach me, and often I realize too late when someone has. I'm becoming anti-social without meaning to! Can someone provide some guidance? Please no overly technical instructions, because I'm still somewhat of a novice. Thanks!

Had the same problem.

I've found a workaround for this:

- Go to: System > Synaptics
- Type in the search box: freedesktop
- Mark the "sound-theme-freedesktop" package for installation
- Click "Apply"

You should not miss your IM's anymore! ;)
Simply your default installation lacked sounds to play.

---

### Post by haydemon on 2011-01-24
Thanks, but it's already been installed.:(

---


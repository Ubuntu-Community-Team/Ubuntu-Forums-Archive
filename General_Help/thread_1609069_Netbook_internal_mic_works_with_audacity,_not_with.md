---
title: "Netbook internal mic works with audacity, not with skype."
date: 2010-10-29
forum: General Help
---

### Post by Silentzor on 2010-10-29
Hello,

as the title says, my netbook's (Aspire One A0351h-0Bk) works perfectly with audacity (I am using ALSA, tried OSS and other Sound Systems as well), therefore drivers are fine and hardware is not malfunctioning, but it just won't work with skype.

When I connect an external mic and switch devices on alsamixer (Mic -> Front Mic), the external mic works fine (with a bit of noise). Other than that, on skype options I have not checked "Allow skype to configure audio levels", and I have tried all Microphone sound devices provided on the list, with the only one sort-of-working being HDA Intel, ALC272 Analog (hw:0,0), but the sound produced is not understandable (too much distortion). 

I do realize that this is not a skype forum, but any help/workaround would be much appreciated.

Thanks in advance.

P.S. I am using backtrack and Skype 2.1.0.81 BETA, but this is not a backtrack problem (more like a skype problem?).

---

### Post by requeth on 2010-10-29
Ironically I can't get my mic to work at all, but I have some help for you based on what I had to do with last laptop.

a) make sure in Skype the box "Allow Skype to automatically adjust my mixer levels" is not checked.

b) try the following (which I scammed off of a different post here: [http://ubuntuforums.org/showthread.php?t=1601922](http://ubuntuforums.org/showthread.php?t=1601922)  )
sudo apt-get install pavucontrol

pavucontrol


Then:

    * Click the "input devices" tab. Click the lock icon to unlock channels. Set the front right channel to silence.

Once in pavucontrol I just silenced the right channel mic and it worked immediately. I tested in Skype and all seems fine.

c) go to System: Preferences: Sound: input and make sure the mic didn't get muted. If it did blame step a above.

---

### Post by Silentzor on 2010-10-31
Hey mate, thanks for your reply.

Unfortunately it did not help. I mentioned above that I am running Backtrack 4 Pwnsause (Ubuntu 8.04 based), so this might be a bit different than ubuntu.

pavucontrol did not execute (gave an error)

As I said, mic works fine with Audacity, therefore it should be a skype problem.

---

### Post by trikster_x on 2010-10-31
It is a problem with skype.  I had a similar problem with google voice and the only solution is to find a way to mute one of the input channels.  This is due to the auto leveling feature.  In my case, it was the left that needed muting.  

If backtrack has any forums I would ask what backtrack uses for it's sound architecture, ALSA, OSS, or if pulse-audio is present.  If it is pulse-audio, then pavucontrol is the program you need to do this.  Alsamixer doesn't allow the control you need, at least not on my system.

But if my experience with the internal mic on an aspire one is anything to go by, it is completely useless for voice chat.  The audio is so broken that nothing can be understood on the other end.

---


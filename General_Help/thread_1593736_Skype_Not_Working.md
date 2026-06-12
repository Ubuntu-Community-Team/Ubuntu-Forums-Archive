---
title: "Skype Not Working"
date: 2010-10-11
forum: General Help
---

### Post by gerowen on 2010-10-11
Ok, I know there's probably tons of topics about this out there on the internet, but I just wanted to ask if anybody has gotten Skype to work correctly on Ubuntu 64 bit?  Any time I call a telephone with my Skype the person on the other end is unable to hear me at all, just intermittent static and broken clips of my voice.  When I use the Ubuntu Sound Recorder or something else, it works fine.  The only available audio devices in the Skype config are the Pulseaudio server.  I tried and even paid for time from Diamondcards because they do the same kind of thing with some native Linux software.  I moved away from that because after I made the purchase some guy called me from his cell phone and said, "Who is this?".  After a minute or so it came out that he was the contact for Diamondcards and he was supposed to call me to verify the purchase of call time.  After he realized what was going on he broke into his commercial for Diamondcards USA.  This made me "really" nervous that the customer service rep was some dude on his cell phone.

So long story short, are there any good, reliable alternatives to Skype that have a good user interface and some semblance of professionalism behind their customer service?

---

### Post by emoguitarist06 on 2010-10-11
Skype works great on Ubuntu 10.04 amd64

I found the problem you described is usually fixed by opening the properties of skype and "unchecking" the box that says something similar to "allow skype to adjust microphone volume"
**basically do not allow skype to adjust the mic**

---

### Post by techunit on 2010-10-11
I should work fine. I have it running in Lucid at the moment.

---

### Post by tapori2010 on 2010-10-11
I don't have a problem running skype either.

---

### Post by IndyGunFreak on 2010-10-11
> **emoguitarist06 said:**
> Skype works great on Ubuntu 10.04 amd64

I found the problem you described is usually fixed by opening the properties of skype and "unchecking" the box that says something similar to "allow skype to adjust microphone volume"
**basically do not allow skype to adjust the mic**

Same issue I had... once I set it manually it worked fine.

---

### Post by gerowen on 2010-10-11
So it seems to work fine as long as I'm doing skype to skype calls.  My skype test call worked great.  However it still breaks up whenever I call somebody's actual telephone.  Sound coming in from the telephone sounds good on my end, but not the other way around.  Hmmm...

---

### Post by sendblink23 on 2010-10-11
> **gerowen said:**
> So it seems to work fine as long as I'm doing skype to skype calls.  My skype test call worked great.  However it still breaks up whenever I call somebody's actual telephone.  Sound coming in from the telephone sounds good on my end, but not the other way around.  Hmmm...

Its mentioned already - what you need to fix for the *mic(above)

---

### Post by gerowen on 2010-10-11
> **emoguitarist06 said:**
> Skype works great on Ubuntu 10.04 amd64

I found the problem you described is usually fixed by opening the properties of skype and "unchecking" the box that says something similar to "allow skype to adjust microphone volume"
**basically do not allow skype to adjust the mic**

Still a no-go on skype to phone calls, :-(

---

### Post by gerowen on 2010-10-11
So I've narrowed it down to my microphone.  I hooked in the USB headset that I normally use on my PS3 and everything works great, so I will go ahead and mark this as solved.  I "think" it has something to do with the fact that Ubuntu sees my mic as a stereo mic, because it specifies "mono" on the headset and it works with no issues.

---


---
title: "I have 2 problems and I'm desperate for help"
date: 2009-07-29
forum: General Help
---

### Post by KillerKael on 2009-07-29
The first, and main, problem is (wait for it) Pulseaudio. I've reinstalled Jaunty twice now because of getting no sound, and it seems to always relate to Pulseaudio. Here's the thing...

I would fix and configure Pulseaudio to try and get sound from it, but every single FixPulseaudio HowTo out there doesn't work. I can either go through the whole thing fine, but just have nothing happen, or not be able to finish it due to some kind of issue or another. 

So when I finally decide to give up and remove Pulseaudio, sound works for a couple days, then starts to only work every other bootup, then stops working altogether. This has happened twice. The first time I had ESound, the second I just removed Pulseaudio and went with ALSA. (Btw, all the ESound HowTo's say that when you remove Pulseaudio and that one file you're supposed to back up, Pulseaudio should no longer be in the devices list in Preference/Sound, but it is for mine....any idea what that's about?)

The second problem is more of an annoyance/concern than anything. Everytime I shut down or restart Ubuntu, my computer beeps anywhere between 2 to 6 times while shutting down. Any ideas?

Like I said in the title, I'm desperate for help. I don't want to have to reinstall Ubuntu every week, and I really don't want to have to go back to using solely Windows XP. I'm willing to provide any information you might need (although I'm still quite a newbie, so you might have to walk me through some stuff). 

Thanks in advance!

---

### Post by Jago6060 on 2009-07-29
> **KillerKael said:**
> The first, and main, problem is (wait for it) Pulseaudio. I've reinstalled Jaunty twice now because of getting no sound, and it seems to always relate to Pulseaudio. Here's the thing...

I would fix and configure Pulseaudio to try and get sound from it, but every single FixPulseaudio HowTo out there doesn't work. I can either go through the whole thing fine, but just have nothing happen, or not be able to finish it due to some kind of issue or another. 

So when I finally decide to give up and remove Pulseaudio, sound works for a couple days, then starts to only work every other bootup, then stops working altogether. This has happened twice. The first time I had ESound, the second I just removed Pulseaudio and went with ALSA. (Btw, all the ESound HowTo's say that when you remove Pulseaudio and that one file you're supposed to back up, Pulseaudio should no longer be in the devices list in Preference/Sound, but it is for mine....any idea what that's about?)

The second problem is more of an annoyance/concern than anything. Everytime I shut down or restart Ubuntu, my computer beeps anywhere between 2 to 6 times while shutting down. Any ideas?

Like I said in the title, I'm desperate for help. I don't want to have to reinstall Ubuntu every week, and I really don't want to have to go back to using solely Windows XP. I'm willing to provide any information you might need (although I'm still quite a newbie, so you might have to walk me through some stuff). 

Thanks in advance!

What's the need for Pulseaudio or any sound driver in particular?  Does the default sound driver not work for you?

---

### Post by philinux on 2009-07-29
1. Sounds like a hardware problem maybe?

2. The beeps can drive you mad. Check this out.
[http://eric.biven.us/2007/07/08/disabling-your-pc-speaker-in-ubuntu/](http://eric.biven.us/2007/07/08/disabling-your-pc-speaker-in-ubuntu/)

---

### Post by Jago6060 on 2009-07-29
> **philinux said:**
> Sounds like a hardware problem maybe?
^^^
That's kind of what I was thinking.

---

### Post by HappyFeet on 2009-07-29
Buy a cheap sound (soundblaster live or something) card off of craigslist or ebay, and disable the current one. Sometimes you have no choice but to change hardware. It's a small price to pay to free yourself from MS.

---

### Post by fullarton16 on 2009-07-29
Hey, I'm new to linux and i can't seem to install anything even adobe flash player its giving me different error codes.....PLEASE HELP! thanks..

---

### Post by Jago6060 on 2009-07-29
Start a new thread under the General Help forum.  This thread is more about fixing sound than program installation.

---

### Post by philinux on 2009-07-29
> **fullarton16 said:**
> Hey, I'm new to linux and i can't seem to install anything even adobe flash player its giving me different error codes.....PLEASE HELP! thanks..

Please start your own thread in this forum [AbT]("http://ubuntuforums.org/forumdisplay.php?f=326") . It gets very confusing if threads get hijacked.

---

### Post by KillerKael on 2009-07-29
> **Jago6060 said:**
> What's the need for Pulseaudio or any sound driver in particular?  Does the default sound driver not work for you?

It's either that or Pulseaudio won't remove fully/properly. Jaunty comes with Pulseaudio (as I'm sure you already know) but when I remove it, it's still there in the devices list in Preferences/Sound, and sound only works for a couple days.

> **philinux said:**
> 1. Sounds like a hardware problem maybe?

2. The beeps can drive you mad. Check this out.
[http://eric.biven.us/2007/07/08/disabling-your-pc-speaker-in-ubuntu/](http://eric.biven.us/2007/07/08/disabling-your-pc-speaker-in-ubuntu/)

I honestly think it's a problem with Pulseaudio not removing properly/fully, but it could be. Thanks for the beeps thing, though! :D

> **HappyFeet said:**
> Buy a cheap sound (soundblaster live or something) card off of craigslist or ebay, and disable the current one. Sometimes you have no choice but to change hardware. It's a small price to pay to free yourself from MS.

If it comes to that, I will. I still think it's a Pulseaudio problem, but it doesn't hurt to try...I might have a spare sound card somewhere....
(Newbie question) MS??:confused:

---

### Post by hyperAura on 2009-07-30
@philinux

By using the instructions given on this website, will it stop the beep sound, or every single output from the speakers?
[http://eric.biven.us/2007/07/08/disa...ker-in-ubuntu/]("http://eric.biven.us/2007/07/08/disabling-your-pc-speaker-in-ubuntu/")

---


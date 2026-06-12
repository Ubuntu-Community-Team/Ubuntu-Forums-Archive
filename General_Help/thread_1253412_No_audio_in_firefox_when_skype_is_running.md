---
title: "No audio in firefox when skype is running"
date: 2009-08-30
forum: General Help
---

### Post by akber on 2009-08-30
I am sorry if this has been addressed before, I looked around the forums and googled this one a bit but i couldnt find anything about it. 

When i am running skype and firefox at the same time (regardless of whether i am in a call or not) firefox cannot play any audio. usually on youtube, but i am sure the problem extends to all audio on firefox. When i close skype and restart firefox the problem is gone. 

If it matters at all, i used to have the problem on skype where there was a problem with audio playback and it wouldnt let me make any calls. I changed the device settings (i selected a different device in the drop down boxes and it seemed to work) and the problem was fixed. 

Wondering if this is a problem with the apps, config, or something is wrong with the laptop i am using (hp pavillion dv2000)

thanks for any help you are able to provide.

---

### Post by P4man on 2009-08-30
Are you using pulseaudio? If not, you probably should (and hope skype still works heh). i think skype monopolizes alsa audio.

---

### Post by akber on 2009-08-30
yes i am already using pulseaudio

---

### Post by P4man on 2009-08-30
If you're already using pulse, then you might try going back to alsa.

Or rry this:

[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

other than that, complain to Skype they take 2+ years to release an updated linux client that supports pulseaudio.

oh, and you could also try skype's oss version..

Hey, just as I"m typing this, I went to skype's website and noticed there is a new client with support for pulseaudio.. woohoohoo ! lol

[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

Are you using that version?

---

### Post by akber on 2009-08-30
alright sweet, i downloaded the first audio package from synaptic on the first link and then the new skype version and now it all seems to be working, thanks for your help.

---

### Post by akber on 2009-08-30
ok wait, very new problem. my audio works in firefox and skype BUT now when i make calls in skype my friends cant hear me, and when i did the test call to see if it was working or not all that came back to me was loud static.

---


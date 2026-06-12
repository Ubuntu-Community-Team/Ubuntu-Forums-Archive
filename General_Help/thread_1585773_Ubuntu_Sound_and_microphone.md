---
title: "Ubuntu Sound and microphone"
date: 2010-10-01
forum: General Help
---

### Post by su-37 on 2010-10-01
I have an acer aspire laptop and for some reason i cant get any sound from the speakers and the microphone wont pick up anything. Ive tried maxing the volums but the only way i can get any sound is to plug it my (wait for it) microsoft headset. Any ideas?

---

### Post by mrhhug on 2010-10-01
so your saying that your 3.5mm audio jacks are somehow discriminatory to only accept Microsoft hardware? is the MS hardware indeed a 3.5mm jack or is it usb? are you not sure that all usbs wouldn't produce sound? 

```
alsamixer
```

is good software

---

### Post by su-37 on 2010-10-01
The microsoft is a usb headset. I dont have any 3.5mm speakers.

---

### Post by mrhhug on 2010-10-01
so did ```
alsamixer
``` show non-usb devices were muted?

---

### Post by su-37 on 2010-10-01
they are all at 100

---

### Post by mrhhug on 2010-10-01
hey man , have you tried this? ```
ubuntu-bug audio
```

---

### Post by su-37 on 2010-10-01
Thanks. I sent the report off.

---

### Post by su-37 on 2010-10-01
Well sending the report seems to have scared ubuntu into getting the speakers to work. The microphones now pick up sound but i sound like a drunken darleck with a sore throat. Any ideas? 


Thanks for all the help so far.

---

### Post by mrhhug on 2010-10-01
i never really meant for you to submit the bug report, that little script tries to correct settings on your system.

my voice always sounds like that to when i hear it replayed!!!

just kidding, you think there is another issue? learning to properly use a mic is a course all on its own, search google for differnet tips and see what works

---

### Post by su-37 on 2010-10-01
I tried making a skype call but the other half coudnt hear me.

---

### Post by mrhhug on 2010-10-01
the linux skype is really bare bones, i would say check your skype sound device options
this mic is built into the webcam or seperare on these MS headphones?
if the webcam and mic are on different devices you might need to let skype know, check you pulse audio settings

REALLY good pulse audio walkthrough
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by su-37 on 2010-10-01
The mic that doesnt work is in the computer, the one that does in with the microsoft headset.

---


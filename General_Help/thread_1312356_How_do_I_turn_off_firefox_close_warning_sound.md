---
title: "How do I turn off firefox close warning sound?"
date: 2009-11-03
forum: General Help
---

### Post by lavinog on 2009-11-03
I updated from jaunty to karmic (64bit).
When I close firefox, I get the message asking if I want to close all tabs.
When I get this message I get a loud bongo sound (The old default for the login window)
Where do I turn this sound off?  Turning off all sounds in the sound preferences works, but of course it turns off all sounds.

I haven't done a fresh install on any machines yet to see if this is a default behavior.

---

### Post by Nachoo on 2009-11-03
Same thing here, it is annoying... I couldn't find the option anywhere...

---

### Post by samepate on 2009-11-04
Hello,

I have the same problem, I have searched for a while but I have not found any solution. Any idea would be appreciated! Thx.

---

### Post by samepate on 2009-11-05
up

---

### Post by lavinog on 2009-11-05
> **samepate said:**
> up

???

---

### Post by jimmy the saint on 2009-11-05
System>preferences>sounds.

Set the sound theme to "none"

---

### Post by lavinog on 2009-11-05
yes that turns off all sounds though...I just want to turn off or change the firefox sound, because it is louder and more annoying than any other sound.
If that is the only method to turn it off, then Ubuntu needs to have all sounds off by default...not a good option.

---

### Post by v1ctorsag3 on 2009-11-23
I wasn't able to find an option to disable the warning sound but I was able to find a work around until somebody smarter figures out how to turn off it just on Firefox.  The change I'm suggesting will affect the entire system but it works...

First, you will need to run Nautilus as Super User.  From the terminal, type in:

**gksudo nautilus**

Enter your password...

After Nautilus opens, navigate to **/usr/share/sounds/ubuntu/stereo**

The file causing that annoying sound is **dialog-question.ogg**.  What I did is renamed this file to **dialog-question-old.ogg**.  Now you will no longer a noise when Firefox wants to close multiple tabs (or from any other app wants to use this file).

If you want to just *change* the noise, the easiest way I've found is to make a copy of **dialog-warning.ogg** (or whatever sound file you'd like to use) in the same directory then rename the copy to **dialog-question.ogg**.

Hope this helps!

---


---
title: "Issues with Sound, Sony Vaio"
date: 2011-09-16
forum: General Help
---

### Post by GradeZero on 2011-09-16
I've been trying this issue my my laptop for days.  What is happening is that my laptop's speaker stays on when I put something into the headphone port.  Headphone port does not turn on either.  Basically sound is only coming from my speakers.

I have tried to  add this line to alsa-base.conf,
options snd-hda-intel model=<model>
     -Tried model as vaio and sony[FONT=Verdana]
and it didn't work.  I have also checked alsa mixer and sound preferences for a headphone slider, nothing  came up.  I also tried to see if headphone jack was named something else as well.

Can I get some help please?
[/FONT]

---

### Post by Toz on 2011-09-16
Hello and welcome to the forums.

What model of Sony Vaio do you have? Also, open a terminal window, type in the following command, and post back the results:
```
cat /proc/asound/card*/codec\#* | grep Codec
```

---

### Post by GradeZero on 2011-09-17
> **Toz said:**
> Hello and welcome to the forums.

What model of Sony Vaio do you have? Also, open a terminal window, type in the following command, and post back the results:
```
cat /proc/asound/card*/codec\#* | grep Codec
```

sorry for the late reply but i will check on it right now

Edit: So the model is PCG-71913L and the codecs are Conexant CX20590 and Intel CougarPoint HDMI.
I notice you are from Toronto as well so you are probably sleeping.

---

### Post by Toz on 2011-09-17
Run this command in the terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```
...and post back the link for the results.

---

### Post by GradeZero on 2011-09-17
> **Toz said:**
> Run this command in the terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```...and post back the link for the results.

[http://www.alsa-project.org/db/?f=cb839d3922bd0280c97c6ba3016fc63f6f3ef35c](http://www.alsa-project.org/db/?f=cb839d3922bd0280c97c6ba3016fc63f6f3ef35c)

These are the results.

---

### Post by GradeZero on 2011-09-17
Inglorious bump.

---

### Post by Toz on 2011-09-17
See: [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/168960]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/168960").

Post #6 identifies a solution.

---

### Post by GradeZero on 2011-09-17
Thank you so much, I've been searching for a solution for a week and I couldn't find anything.  Thank you again for your help.

---


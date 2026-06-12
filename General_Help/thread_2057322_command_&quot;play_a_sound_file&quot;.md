---
title: "command: &quot;play a sound file&quot;"
date: 2012-09-13
forum: General Help
---

### Post by Cotopaxi on 2012-09-13
I installed the countdown timer from the widgets bar.

In the "Timer Settings" under "Actions on Timeout" I can check the option "Run a command:" Here I would like to instruct the program to play a sound file.

Can anyone tell me how I do that?

Thanks!

---

### Post by Statia on 2012-09-13
play sound.ogg

---

### Post by Cotopaxi on 2012-09-13
Statia,

Thanks very much for your feedback. It works! :popcorn:

The only problem: it only plays a short "Ding" sound.

Is there a chance to instruct the system to play a given sound file?

Thanks again!

---

### Post by Vaphell on 2012-09-13
i guess you need to replace *sound.ogg* with the file of choice ;-)

---

### Post by Cotopaxi on 2012-09-13
Vaphell,

Thanks for your reply.

I typed the command:

> play /usr/share/sounds/freedesktop/stereo/phone-outgoing-busy.oga

No luck.

Any ideas?

Thanks again!

---

### Post by Vaphell on 2012-09-13
any output of that command in terminal?
*play* works fine with any .ogg/.oga file in /usr/share/sounds on my end.

---

### Post by Cotopaxi on 2012-09-13
Vaphell,

The execution of this command in terminal gave me the output that the program "sox" was not installed. So, after typing:

> sudo apt-get install sox

and rebooting it works now!

Thanks very much indeed to all of you for your help!

---


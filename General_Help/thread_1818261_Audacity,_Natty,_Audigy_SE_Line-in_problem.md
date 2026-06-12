---
title: "Audacity, Natty, Audigy SE Line-in problem"
date: 2011-08-04
forum: General Help
---

### Post by cscj01 on 2011-08-04
I am running Ubuntu 11.04 and Audacity 1.3.13.  I have been using Audacity to digitize my 33 1/3 albums since Ubuntu 8.04 with no problems.  After upgrading to Natty, I am unable to get this working.  I have tried every combination of devices in Audacity.  I have checked Volume Control.  At this point I am lost.  Any ideas on what I can check?

---

### Post by gordintoronto on 2011-08-04
Have you run alsa-mixer from the command line?

---

### Post by cscj01 on 2011-08-05
I just ran alsamixer from the CLI.  It shows the capture volume at 0 for Line-in and Mic.  I increased the volume for Line-in and Mic.  I still can't get Audacity to recognize any Line-in selection for input device.

---

### Post by SoylentSteak on 2011-08-05
Audacity can be very fussy with this type of thing. See if you can use another recording program to capture the music on your Linux box. Once it's on there, you can always open up the files in Audacity to do stuff like separating the tracks.

---

### Post by cscj01 on 2011-08-05
Well, I have resolved this issue.  Although I had checked the Sound settings a number of times before, after going through the alsamixer and force reloading alsa a number of times, somehow the input got muted.  I unchecked the mute box, and all is well with Audacity again.

I really prefer Linux over Windows, but sometimes things that should just work can be a challenge.  If I had a decent fax solution, I would get rid of my dual boot of Ubuntu and XP by blowing XP away.  Well, there is one more thing; GBonds doesn't work either, so I need Savings Bond Wizard.  I haven't tried it with Wine, so maybe that will work.

Anyway, thanks for the responses.  Without alsamixer, I would not have resolved this.

---

### Post by cscj01 on 2011-08-13
Perhaps I spoke too soon.  I occasionally have to force reload alsa between Audacity sessions to get things working.  Why this is, I do not know.  Perhaps someone else has an idea?

---


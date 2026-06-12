---
title: "Software Which Alerts Every Half Hour?"
date: 2011-11-21
forum: General Help
---

### Post by Alaksandu on 2011-11-21
Hello Forum,

I'm running 10.04 Lucid Lynx and suffering from Carpal tunnel syndrome.

I got medical advice saying that I must avoid long uninterrupted computer sessions. Therefore I'm looking for an application that alerts every half hour or so.

A visual rather than sound alert would be nice. Other than that there are no requirements - any flexible time settings are welcome but I basically just want the machine to bop me automatically from time to time so I don't forget about pauses. I've done some searches but my search terms have been either too broad or too specific.

---

### Post by Zill on 2011-11-21
Alaksandu:  You could try [GNOME Timer Applet]("http://eastasiastudent.net/study/gnome-timer-applet/") - it's in the repos.
```
sudo apt-get install timer-applet
```
Caveat:  I have no need for this applet myself and have not used it so cannot comment on its effectiveness but thought it may be worth a look.

ps.  It seems that this may not work with later versions of Ubuntu as it may not be compatible with Unity.

---

### Post by rewyllys on 2011-11-21
You could use the Synaptic Package Manager to install "alarm-clock-applet".  

Once SPM has finished its work, left-click on Applications, then right-click on Alarm Clock, and either set it up as a desktop icon or add it to your panel.

---

### Post by Alaksandu on 2011-11-21
Thank you, this will work well.

---

### Post by Alaksandu on 2011-11-21
Ah, concurrent posts. I should clarify that I already tried the alarm clock applet and it's geared more towards waking you up.

For general-purpose use like this the timer has a much better featureset.

---

### Post by kaspar_silas on 2011-11-21
I had exactly this same thing and found overtime I tended to ignore prompts. If like me you find you lapse into bad habits try looking up "workrave". 

It's more configurable all the way from just prompting to locking input and screen and listing exercises.

---

### Post by Zill on 2011-11-21
> **kaspar_silas said:**
> ...If like me you find you lapse into bad habits try looking up "workrave"...
A good find!  Taking a quick look at the [Workrave]("http://www.workrave.org/") website, it looks like it may be more appropriate for the OP than my suggestion of timer-applet. ;-)

Again, it is in the repos so no need to download from the website.
```
sudo apt-get install workrave
```

---


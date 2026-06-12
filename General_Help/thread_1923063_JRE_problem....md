---
title: "JRE problem...?"
date: 2012-02-09
forum: General Help
---

### Post by robert shearer on 2012-02-09
I am trying to run some of the audio applications from this site...
[http://www.hotto.de/software](http://www.hotto.de/software)
specifically..
[http://www.hotto.de/software/audiomasteringsuite.html](http://www.hotto.de/software/audiomasteringsuite.html)

They are said to be multi-platform using the JAVA Runtime Environment.

I can install and run but when I attempt to load a sound file the app will recognise it (reports the bit depth and sample rate) but the playback controls remain greyed out.

Does this have something to do with the current JRE Ubuntu is using (running 11.04) ??  and if so can I install another version without breaking the current set-up.

Thanks for looking,
Cheers Bob.

---

### Post by sammiev on 2012-02-09
> **robert shearer said:**
> I am trying to run some of the audio applications from this site...
[http://www.hotto.de/software](http://www.hotto.de/software)
specifically..
[http://www.hotto.de/software/audiomasteringsuite.html](http://www.hotto.de/software/audiomasteringsuite.html)

They are said to be multi-platform using the JAVA Runtime Environment.

I can install and run but when I attempt to load a sound file the app will recognise it (reports the bit depth and sample rate) but the playback controls remain greyed out.

Does this have something to do with the current JRE Ubuntu is using (running 11.04) ??  and if so can I install another version without breaking the current set-up.

Thanks for looking,
Cheers Bob.

Hi Bob, just tried the addies with no problems. I'm using 12.04 but likely the problem is an older java version. Try [this]("http://sites.google.com/site/easylinuxtipsproject/java") and update your java to see if the problem still persist. :)

---

### Post by robert shearer on 2012-02-09
Thanks, that fixed the playing of files..!

Unfortunately I do not seem to have the resources to run as all I am getting is burbled-garble.(tried several file formats and rates)
Some sort of latency issue..?

AMD Athlon64 3000+ and 1 Gig Ram.

Maybe I will try a lighter desktop..see if I can't free up some processing.??

Cheers.

---

### Post by sammiev on 2012-02-09
Can you be also having a flash problem as well? What's your latest flash version?

---

### Post by robert shearer on 2012-02-09
version **11.1.102.55**.
  Just checked it at..
[http://kb2.adobe.com/cps/155/tn_15507.html](http://kb2.adobe.com/cps/155/tn_15507.html)
Where that is listed as the latest for Linux.

However, from your link to the JRE install walk through I got as far as removing the iced-tea plugin and trying to cd /opt only to be told there was no opt.... and there wasn't !
So I did the plan b and used the ppa option reccommended there which seemed to work ok.

I shall now go and check if I need iced-tea plugin back or try the firefox flash-aid tool...????

---

### Post by robert shearer on 2012-02-10
Nope, none of the above. :-(

Just booted into my XP install on the same machine and the apps work fine there so **not** a resources issue after all...

What now...? Pulse audio ?.....
 oh the pain of Linux audio configuration in all its manifest discombobulation...

EDIT... something to do with file headers/descriptors ?  just made some new recordings at 24/96 and these play fine whereas everything else I've tried has had timing/buffering artifacts. 
Those same problem files play fine in XP...
I **am** guessing here so any guesses as to a fix would be entertained..:-)

Edit #2... I am marking this as solved because sound files made since this app was installed seem to play without problem.  Existing files and/or those that have been edited/resampled are still problematic though I feel this is an Ubuntu/Pulse audio glitch rather than the application.  ???

---


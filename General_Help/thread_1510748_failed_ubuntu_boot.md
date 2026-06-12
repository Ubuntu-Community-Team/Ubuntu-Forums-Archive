---
title: "failed ubuntu boot"
date: 2010-06-15
forum: General Help
---

### Post by launchy on 2010-06-15
when i boot to ubuntu (dual booting with windows vista) i get a black screen with text like this:

"(process:252): GLib-WARNING**: getpwuid_r()- failed due to ubuntu user id(0)"

i had to force it to shutdown by pressing the powerbutton. after that it was all normal boot up. this has never happened on bootup to me. can anyone explain why this happened? and how can i fix it? thanks.

---

### Post by quixote on 2010-06-17
Root is the user whose id is 0, and in ubuntu you can't use the graphical method to login as root unless you do specific things to make the system allow that.  My guess is that somehow, during that bootup the system decided you were trying to login as root.  Since root can't log in and neither can anyone else, nobody is logged in, so there's nobody who can send the command to shutdown the machine.  The only solution is what you did: hit the power button.

Did this just happen once?  If so, write it off as some random glitch and don't worry about it.  If it's happening repeatedly, then we should go deeper into it to try to fix it.

---

### Post by launchy on 2010-06-20
ok i just experienced it twice today. after ubuntu hanged i tried pressing ctrl+alt+f1 (i tried logging in but i couldnt) then i went back to the desktop ctrl+alt+f7. ubuntu wasnt responding at all so i forced it to shutdown. when i ws booting ubuntu up there was the "GLib Warning" again.

---

### Post by wieman01 on 2010-06-22
There is another thread concerning this problem:

[http://ubuntuforums.org/showthread.php?t=1505418&highlight=getpwuid_r]("http://ubuntuforums.org/showthread.php?t=1505418&highlight=getpwuid_r")

---


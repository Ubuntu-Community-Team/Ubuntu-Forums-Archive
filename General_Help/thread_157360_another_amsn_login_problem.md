---
title: "another amsn login problem"
date: 2006-04-09
forum: General Help
---

### Post by passbe on 2006-04-09
Ok, i installed 0.95 amsn on Ubuntu 5.10 amd64 system, running perfectly for months now, woke up this morning and it keeps giving me the error on any hotmail a/c "Error: username or password incorrect". first thing i do is go to hotmail and login, pefect password still the same and everything, next i go to windows and check msn runs fine, it does. 

So after hours of googling and 5 reinstalls of amsn, the error continues. If anyone could be of any help that would be great. ?

ps: i have deleted the ~/.amsn directory several times but to no solution

---

### Post by TheSandman on 2006-04-11
Yes!
I have the exact same problem.
I installed amsn a couple of weeks ago to get webcam support via MSN which Gaim doesn't have.
It worked, although buggy, every day for weeks.
Then one day it just gave me this login error. I figured that it was a temporary network error or that the protocols had changed.
But Gaim can log on fine with the same old protocols, so i guess not. And no update was available either.
I go to amsns homepage expecting to see a post or something about this saying "It's iffed but we're fixing it", nothing.
So i figure... er, is it just me?
I wait for a couple of days, and now... still doesn't work! I can't log in, just tells me my password is incorrect.

So i log on here expecting tons of other people to have the problem and a thread going.

Either i didn't find it... or it's just us?

This was all i found [http://amsn.sourceforge.net/forums/viewtopic.php?t=750](http://amsn.sourceforge.net/forums/viewtopic.php?t=750)
And that problem doesn't apply to me, i got those packets when i installed and i've always used SSL

---

### Post by Ramses de Norre on 2006-04-11
I had it too, deleting /home/ramses/.amsn/email_adress and recreating the profile worked. The error was caused by the config.xml file inside that folder.

---

### Post by TheSandman on 2006-04-17
*facepalm*

That actually worked!

Thank you.

---


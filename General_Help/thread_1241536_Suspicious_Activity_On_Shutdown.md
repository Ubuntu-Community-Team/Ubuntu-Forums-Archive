---
title: "Suspicious Activity On Shutdown"
date: 2009-08-16
forum: General Help
---

### Post by Wataru8675 on 2009-08-16
The last couple of days, when I've gone to shut down my computer, a window comes up and asks me for "authentification" in the form of a password before it will shut down.  I was suspicious of this window's motives, so I haven't shut my computer down (but set it to hibernate instead) since it came up.  Just now, however, I decided to put in a fake password and see what happens.  So I put in a password that ISN'T the one I log in with or download anything with, and it reset the first time, so I put in the same fake password again, and it just accepted it.  I can now shut down my computer.  I should've probably taken a screenshot of the window, but i didn't think of it.  Any ideas as to what this is?

---

### Post by Wataru8675 on 2009-08-16
Wow, no one's replied...any ideas AT ALL as to what it could be?  I'm worrying that I've picked up some rare breed of Linux malware or something...because if it was actually from my system, it should've known I was giving it a bogus password, right?

---

### Post by oboedad55 on 2009-08-17
> **Wataru8675 said:**
> Wow, no one's replied...any ideas AT ALL as to what it could be?  I'm worrying that I've picked up some rare breed of Linux malware or something...because if it was actually from my system, it should've known I was giving it a bogus password, right?

Not a clue. Doesn't sound like anything devious. My first reaction was that it sounded like a Windows problem. :P Apparently there are Linux viruses, which this doesn't sound like, but I have yet to run into one. Windows? Absolutely. But never Linux, and I've been running Linux most of the last ten years.

Jon

---

### Post by P4man on 2009-08-17
I susbcribed to the thread when I saw it, cause it makes me curious. I also doubt its malware though. more likely some app wanting permission to access something, and giving the wrong the password just made it fail to do that.

Did you install anything outside the repo's? Have a look in "janitor". Thing is, it is *extremely* unlikely there is malware in the repo's.

---

### Post by tomasrey88 on 2009-08-17
from the repositories, install clamav, clamav-freshclam, and clamav-base. From terminal type: sudo freshclam ,then sudo clamscan -r --bell -i /  

Let me know what the output is. But tell me this: Did you try to install some software or do anything else that may require you to put in your password just before shut down? Linux viruses, the probability is low, but still possible. Less than 1% of viruses are Linux viruses, if I remember correctly. ( # of Linux viruses: [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware) ) / (# of viruses in Clamav database) = less then 1%. 

BTW, can anybody tell me why my USB Flash cannot be overwritten? [http://ubuntuforums.org/showthread.php?t=1242310](http://ubuntuforums.org/showthread.php?t=1242310)
Thanks,
:-)

P.S. You might want to install checksums in your hard drive and check them periodically to verify integrity of the hard drive if you are concerned.

If you backed up your date prior to the incident, then don't touch that backup to avoid contamination. Backup your data to another external drive.

If the checksum's integrity has not been compromised in a week of frequent daily computer use and if clamav had not found anything clammy or fishy, then you're ok. It is just an errant app.

Look at this thread, as it might help you: 
[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

---

### Post by Wataru8675 on 2009-08-17
I'm running the clamscan right now...not sure how long it's supposed to take, but if I finish typing all this before it's done, I'll edit in with it.

The only programs I've installed recently are MuseScore, JACK Audio, and Blender, none of which I would imagine would need my password, much less specifically on shutdown.  I have downloaded (I think) exclusively from the repositories (just to be sure I'm using this word right, I've only downloaded from Add/Remove... and sudo apt-get's).  And I haven't added anything to the list of programs I'd like to run on startup, either, which is the next thing that comes to my mind.

Another funny thing with this program is that it's pretty hit-and-miss...  It came on only about 80% of the time when I tried to shutdown, so it doesn't happen EVERY time.  And it also still hasn't popped up since I fed it the bogus pass (which stinks, because I wanted to post a screencap of it).

Also, thanks for the post to that thread.  I'll install those later...I only have a couple minutes right now.

clamscan didn't give me a single thing except for a message saying that my version was out of date, even though when I install from the terminal, it says that everything is, in fact, up to date.

---

### Post by Jon Monreal on 2009-08-17
> **Wataru8675 said:**
> clamscan didn't give me a single thing except for a message saying that my version was out of date, even though when I install from the terminal, it says that everything is, in fact, up to date.

The thought that came to my head as I was reading this thread was that if it was something that new, a virus scanner might not be able to detect it.

At any rate, can you remember what the window said?can you remember what the window said? Was there anything that might distinguish it as a fake?

EDIT: You could try going to System>Administration>Authorizations and looking at entries such as "Shut down the system" under "power-management". What you should look for is "Active Console" under "Implicit Authorizations".

---

### Post by Soul-Sing on 2009-08-17
Really strange...
You are not in the "recovery mode" working?
Not "worked" with visudo?

---

### Post by tomasrey88 on 2009-08-17
If you use clamav, be sure you're using the latest version so no security possible loopholes can be taken advantage of.

To install latest clamav:
Goto: system, administration, software sources.
Make sure you're set-up to receive;
universe software, 
URL of clamav updates for main and source code, 
security and recommended updates,
and authentication key for the clamav team to download updates onto your computer automatically. 

Details on how to do it;
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

BTW, I think I might've found a serious bug in Ubuntu 8.04. I invite you to check it out: 
[http://ubuntuforums.org/showthread.php?t=1242310](http://ubuntuforums.org/showthread.php?t=1242310)

It doesn't sound like a virus or malware. The older version of clamav works fine as long as you updtated your virus database before you used it (sudo freshclam). I think it is just an ap that you tried to install and it required you typing in your password. Since you did not type in the correct one, it did not install properly. When you try to use an ap that you recently installed and it doesn't work right, then try to install it again and see if the popup window comes up again. In any case, since you typed in a bogus password, it should not be able to do anything bad to your system if it is malware. Therefore, no worries, be happy. [solved] 

Enjoy,
:P

---


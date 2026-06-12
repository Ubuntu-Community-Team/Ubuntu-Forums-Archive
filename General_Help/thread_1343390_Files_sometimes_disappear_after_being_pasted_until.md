---
title: "Files sometimes disappear after being pasted until restart"
date: 2009-12-01
forum: General Help
---

### Post by TheOnlyMrK on 2009-12-01
I've been really going though my /home recently and organizing my files, deleting ones I don't need anymore, and so on, one problem I have is when I cut then paste files somewhere else they will appear in the new location but *sometimes* the previews for them won't load (text file icon shows text that's in the file, picture icon shows the picture, etc.), I wait a few seconds figuring they're still moving to the new location then click refresh and they disappear. At first it scared me because I thought I lost the files but I restarted and they were right in the spot I pasted them to, now it's been a couple weeks and I'm used to this happening but am hoping their is a way to fix this so I don't have to restart every time it happens, as I said it doesn't happen every time but is annoying having to worry about it.

---

### Post by TheOnlyMrK on 2009-12-02
Update: Now after pasting some files into a folder I opened the folder a few minutes later to find it completely empty, normally only the files I paste into the folder disappear. The usual restart fixed it. Does anyone have any idea yet? I have a feeling this is more a bug then something I did myself because I've had this problem both times I installed Ubuntu 9.10 on this computer and my laptop has 9.10 on it and does it too.

---

### Post by u.b.u.n.t.u on 2009-12-02
1. How is the health of your hard drive?

2. Are background services interfering with the file transfer?

3. Are you able to open a resource window to monitor the CPU and RAM during a stress test file transfer?

4. What operating system do you use?

5. How much RAM is installed?

6. Is the transfer on the same hard drive and or to a second hard drive?

---

### Post by ed-koala on 2009-12-02
I had a similar problem today, but just once.  Some files I downloaded seemed to vanish, but were actually still there.

Turns out I had an invisible Nautilus running somehow.  It showed up in System Monitor but I couldn't see Nautilus on my screen anywhere, and opening a second Nautilus didn't see those files for some reason.  Ending the hidden one fixed the problem.

If that is your problem, the question then is ... how is that Nautilus problem happening?  That I do not know.

---

### Post by u.b.u.n.t.u on 2009-12-02
> **ed-koala said:**
> If that is your problem, the question then is ... how is that Nautilus problem happening?  That I do not know.

It may be as simple as nautilus running as multi instances. As innocent as clicking nautilus too many times and thinking only one instance is open.

---

### Post by ed-koala on 2009-12-02
Multiple instances yes, but how did it get invisible to me? It didn't show up on my screen, or minimized in the panel as it always does usually.

---

### Post by TheOnlyMrK on 2009-12-02
> **ed-koala said:**
> I had a similar problem today, but just once.  Some files I downloaded seemed to vanish, but were actually still there.

Turns out I had an invisible Nautilus running somehow.  It showed up in System Monitor but I couldn't see Nautilus on my screen anywhere, and opening a second Nautilus didn't see those files for some reason.  Ending the hidden one fixed the problem.

If that is your problem, the question then is ... how is that Nautilus problem happening?  That I do not know.
Well that was the problem. o.0 As you said, I looked in the System Monitor and it was running, I've seen it running so many times before I thought it was an important part of the operating system, thus I was a little afraid of clicking End, but I ended it and then went to the folder where the files "disappeared" and they were all there.
So that answers what's causing the error... but I don't understand what's making the error start or how to fix it? But thank you for pointing that out.

---

### Post by u.b.u.n.t.u on 2009-12-02
> **ed-koala said:**
> Multiple instances yes, but how did it get invisible to me? It didn't show up on my screen, or minimized in the panel as it always does usually.

That is suggestive of a bug. I think I encountered similar the other day. The open application failed to register on the panel as being open.

---

### Post by ed-koala on 2009-12-02
Nor do I know how my Nautilus actually disappeared.  Normally even if 3 or 4 file browsers are open you see each in the panel, but that one was just plain gone.

Any ideas on how it could have disappeared from sight yet still be running? It only happened to me the one time, but obviously you are having a more serious issue.

---

### Post by u.b.u.n.t.u on 2009-12-02
> **TheOnlyMrK said:**
> I've seen it running so many times before I thought it was an important part of the operating system

Nautilus is a file manager. It is part of Gnome. On windows the file manager is known as "windows explorer". (Though a brilliant windows stand alone file manager alternative is Explorer++)

---

### Post by u.b.u.n.t.u on 2009-12-02
> **ed-koala said:**
> Any ideas on how it could have disappeared from sight yet still be running?

Common garden variety bug. That complex I would think. Nautilus should present itself on the panel to indicate it is open.

I would think waiting for a bug fix update is the best move forward.

---

### Post by TheOnlyMrK on 2009-12-02
> **u.b.u.n.t.u said:**
> 1. How is the health of your hard drive?

2. Are background services interfering with the file transfer?

3. Are you able to open a resource window to monitor the CPU and RAM during a stress test file transfer?

4. What operating system do you use?

5. How much RAM is installed?

6. Is the transfer on the same hard drive and or to a second hard drive?

1. Like new, not even 2years old.
2. Not that I can tell, I'm not real sure how to check for that, the only things I have running that arn't from the default Ubuntu install are aMSN and Skype.
3. I haven't tried that now that I tried what "ed-koala" said and it fixed it.
4. Ubuntu 9.10 32bit
5. 5GiB (3.2GiB usable)
6. Same hard drive.

---

### Post by TheOnlyMrK on 2009-12-02
So should I submit a bug on launchpad? Or does anyone know if someone already submitted it?

---

### Post by u.b.u.n.t.u on 2009-12-02
> **TheOnlyMrK said:**
> So should I submit a bug on launchpad? Or does anyone know if someone already submitted it?

Yes, an excellent proposal. If a bug report already exists just add a comment to the effect that you can verify it. It should be relatively easy to determine if the bug has already been reported.

Conversely, create a new bug report.

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by Grenage on 2009-12-02
A bug report will likely exist, I've seen the issue on and off since 9.04.  If a file doesn't appear, F5 (refresh) normally fixes it for me.

---

### Post by TheOnlyMrK on 2009-12-02
Bug posted, [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/491305](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/491305)
Wish I could of put a bit more detail but I don't know much to describe about it. Though I think I should of waited till I wasn't half asleep.

---

### Post by u.b.u.n.t.u on 2009-12-02
> **TheOnlyMrK said:**
> Bug posted, [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/491305](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/491305)
Wish I could of put a bit more detail but I don't know much to describe about it. Though I think I should of waited till I wasn't half asleep.

Good work! I added a comment that I have experienced this bug too.

---


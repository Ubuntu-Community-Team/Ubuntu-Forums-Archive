---
title: "Please:  I NEED to backout a change to X Server that is crashing my system"
date: 2012-07-07
forum: General Help
---

### Post by jcobban on 2012-07-07
I have not received any reply to my post.  I cannot use GIMP because every time I do anything with it the X server crashes.  I NEED to back out the last change that was made by Ubuntu Update.

---

### Post by Paddy Landau on 2012-07-08
It would make better sense to find out what is crashing your GIMP. Did you post a thread for that? If so, please post a link here so we can see it.

To find out what was updated last, go to Synaptic Package Manager (if you don't have it, install [synaptic]("apt:synaptic")). Go to File > History to see your history. Then you can, if you want, back out.

---

### Post by jcobban on 2012-07-08
> **Paddy Landau said:**
> It would make better sense to find out what is crashing your GIMP. Did you post a thread for that? If so, please post a link here so we can see it.

To find out what was updated last, go to Synaptic Package Manager (if you don't have it, install [synaptic]("apt:synaptic")). Go to File > History to see your history. Then you can, if you want, back out.

It is not GIMP that is crashing it is the X Server.  It is simply that I am able to consistently crash the server by running GIMP and therefore cannot run GIMP until I can fix the X Server.  The X server **was** changed by the last update according to the history.  Hence my request that somebody tell me how to backout the change!

I google for "ubuntu backout change" and other various synonyms (you cannot do a google search containing the word "out") and I get no hits on how to perform a backout, and can find nothing related.  Synaptic is not used in 12.04.  Its replacement, Ubuntu Software Center, does provide the history display, but appears to provide no mechanism for removing a fix.  I can uninstall an entire package, but not an individual fix.  For example I cannot do anything with the line of the history recording the installation of the fix, so why I am permitted to highlight the line in the history totally escapes me.

Obviously I cannot remove the entire X server from my system and still do anything.

So I get back to my problem:  How do I back out the last fix?

---

### Post by Paddy Landau on 2012-07-09
> **jcobban said:**
> It is not GIMP that is crashing it is the X Server.
Sorry, I should have worded that better. It would be a better idea to find out how to fix the problem of GIMP crashing the X Server. It may be a bug that needs to be reported; or it may be something a bit wonky that can be fixed.

> **jcobban said:**
> Synaptic is not used in 12.04.
Well, it's really that Synaptic is not installed by default. It still works. That's why I suggested you install it from the Repository.

> **jcobban said:**
> How do I back out the last fix?
I'm not entirely sure that you can easily back out something like the X Server, but you can try. This is how to do it.

[LIST]
[*]Start Synaptic Package Manager (yes, you'll need to [install synaptic]("apt:synaptic")).
[*]Find the package (or packages) that you want to revert.
[*]For each package, highlight it > Package > Force Version > select the version you want. Note the warnings, if any, in case of an unwanted change.
[*]Apply.
[/LIST]
In case you are left with a non-functioning system, please back up your data and create a Live CD (or USB) before doing this.

However, I repeat: You'd probably do **much better** to **start a new thread** asking for help to fix your GIMP problem, rather than backing out the update. Backing out the update is a sticky plaster that won't stay stuck and does not solve the problem. I suggest either the [Absolute Beginner Talk forum]("http://ubuntuforums.org/forumdisplay.php?f=326") or the [General Help forum]("http://ubuntuforums.org/forumdisplay.php?f=331"). Post a link to your new thread here so we can see it.

---

### Post by jcobban on 2012-07-09
> **Paddy Landau said:**
> 

However, I repeat: You'd probably do **much better** to **start a new thread** asking for help to fix your GIMP problem, rather than backing out the update. Backing out the update is a sticky plaster that won't stay stuck and does not solve the problem. I suggest either the [Absolute Beginner Talk forum]("http://ubuntuforums.org/forumdisplay.php?f=326") or the [General Help forum]("http://ubuntuforums.org/forumdisplay.php?f=331"). Post a link to your new thread here so we can see it.

Thank you.
[LIST]
[*]I agree that it is generally better to move forward than to move backward.
[*]However I believe that it is highly important that X.org server not be capable of crashing as a result of something done by an application, as that crash causes all graphical applications to be shut down, even though they did not contribute to the problem.
[*]The last change made to the system was to X.org, so there is clearly a problem in that change that must be addressed ASAP.
[/LIST]
I have a lot of technical experience, indeed I first worked on a platform using X11 almost 20 years ago, but I am a user of Linux, not a guru. I do not know how to get this problem fixed.  

Before I posted this thread, and its less emphatic sibling, I had already posted a request for help on the GIMP forum, but the only response I got there was to try doing the image processing I was trying to do with a different program!

Also before I posted this thread I searched for information on how to debug the X.org crash, but I could find nothing useful.

---

### Post by jcobban on 2012-07-09
Also see [http://ubuntuforums.org/showthread.php?p=12088389]("http://ubuntuforums.org/showthread.php?p=12088389")

---

### Post by Paddy Landau on 2012-07-09
> **jcobban said:**
> ... I am a user of Linux, not a guru.
Me too. That's why these forums; I find that most (not all) problems can be solved with help here.

> **jcobban said:**
> ... I had already posted a request for help on the GIMP forum, but the only response I got there was to try doing the image processing I was trying to do with a different program!
That's funny! I would suspect that the GIMP people would not know the answer, as their program runs on the three main platforms (Windows, Mac and Linux), and many different distros of Linux. It is most likely to do with your hardware, as that is what is different from other Ubuntu users, unless you have inadvertently changed something important.

> **jcobban said:**
> Also see [http://ubuntuforums.org/showthread.php?p=12088389](http://ubuntuforums.org/showthread.php?p=12088389)I see that Redblade has answered there with a request for information. I'll follow the thread and let's hope you get an answer soon.

---

### Post by haresear on 2012-07-09
Post #4 in the following thread describes a method for downgrading to an older version of xorg-xserver:
[http://ubuntuforums.org/showthread.php?t=1986601]("http://ubuntuforums.org/showthread.php?t=1986601")

---


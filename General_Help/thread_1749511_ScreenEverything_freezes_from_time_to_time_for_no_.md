---
title: "Screen/Everything freezes from time to time for no reason in Natty"
date: 2011-05-04
forum: General Help
---

### Post by inameiname on 2011-05-04
Ever since I installed Ubuntu Natty, from time to time, for no particular reason, the entire computer screen freezes, and I am forced to hold the power button on my laptop to restart things with a hard reset. I cannot explain why it happens.

Such an issue never occurred in any of the past installations and versions of Ubuntu. This is a fresh installation of Natty by the way. 

Also, I can currently be running a lot or nothing and it does this. Thus, it does not matter what I am actually doing (ie, what programs I might be running).

It has occurred about 10 times since I freshly installed Natty 6 days ago.

---

### Post by inameiname on 2011-05-05
Bump.

It happened again for no apparent reason. :(

---

### Post by CountryFan on 2011-05-05
I used to have a similar problem. It can be caused by an incompatibility between the screen compositor and some graphics chips. (This is certainly possible if you have an Intel graphics chip)

I avoided the problem by turning off screen effects (which are only visual enhancements and don't effect normal use of the computer.)

This is one way to do that:

1. Click on the shut down button, which is in the far top right corner of the screen)

2 A menu should drop down, and the bottom item should be "system settings". Click on this

3 On the screen that appears next, find "log in screen" and click on this

4 Click on "unlock"

5 It will then ask you for your password - after which, click on "authenticate"

6 The next screen that appears will have an item "select....as default session" Choose "Ubuntu classic (no effects)|"

7 Finally, reboot your computer


(Hopefully, this should solve the problem of the screen hanging - it did for me. However, it also has the effect of getting rid of the "unity" desktop, and returning to the Gnome graphic interface. I much prefer this - but if you really prefer Unity, there are probably other ways of eliminating screen effects. I'm not using Unity, but maybe others can suggest alternative methods

---

### Post by inameiname on 2011-05-05
I do not use Unity either. It is too limiting for me. 

I was told it may be the desktop effects with another problem I had as well, with the inability to drag and drop from one tab on the taskbar to another. There was a solution (at least for a while) to this problem, though, is to type: "compiz --replace" in the terminal after startup.

Anyway, it really sucks these two problems are due to the same thing, desktop effects. I never had that issue before with my laptop, from Jaunty to Maverick.

Sounds like I should try running things without the desktop effects and see if all of my problems disappear. At least then I will know for sure it is that. Wish there was a fix though, as I really do like the Genie Effect.

---

### Post by floydian_slip on 2011-05-11
I'm having the same problem, and it's really frustrating. I've tried switching to Ubuntu Classic, and it still freezes.

One thing I've noticed is that, as long as I'm actually *using* my computer, it doesn't freeze. It only freezes when I stop for a while. Sometimes (though not always) it freezes when I close up my laptop and immediately re-open it (I have it set to "Blank screen" when I close it), so maybe it has something to do with going to a blank screen...?

By the way, the screen doesn't *completely* freeze. I can still move the cursor around, and in fact sometimes the pointer turns into a hand, as if it can still see links, even though when I click, nothing happens. In other words, it seems like the computer itself, as well as the mouse, still works, but the screen never updates.

Also, instead of holding the power button, you can more safely restart your computer by doing the following: while holding Alt + Prt Sc, slowly type R E I S U B, which stands for **R**aw (take control of keyboard back from X), t**E**rminate (send SIGTERM to all processes, allowing them to terminate gracefully), k**I**ll (send SIGKILL to all processes, forcing them to terminate immediately), **S**ync (flush data to disk), **U**nmount (remount all filesystems read-only), and re**B**oot. ([source]("http://www.bamweb.nl/computer/linux/217"))

Edit: Just found this: [https://bugs.launchpad.net/ubuntu/natty/+source/compiz/+bug/740126](https://bugs.launchpad.net/ubuntu/natty/+source/compiz/+bug/740126)

---

### Post by inameiname on 2011-05-12
Okay, thanks for the info. That is the issue I am having, and I am glad somebody else is too. And yes, it does seem to freeze mainly when the computer is sitting and running, and I am not doing anything. However, not always. A couple of times it has frozen when I am trying to do something.

Something to note is that I have begun to test Ubuntu Classic (No Effects), just to see if the issues still comes up. And so far, I have not run across it.

Also to note is when my screen freezes, everything is frozen, including the mouse. Although, I am using a laptop and no mouse, and maybe it is the touchpad the is frozen, not the cursor. If it happens again, maybe I could try using a usb mouse and see if and when it freezes the mouse still works. IDK.

That's an interesting thing. I was not aware of that key combination to restart things. I am curious though, why would that be any safer than just holding the power button? 


And finally, that bug report you linked does sound like the bug we are experiencing. Though, looking at the dates of the issue, it sounds like its been around for some months, and no fix. :(

---

### Post by timgood on 2011-05-12
There is some evidence that this might be related to a Kernel problem with the default install. Upgrading the kernel has been reported to work and details can be found here: [http://ubuntuguide.net/ubuntu-11-04-...el-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-...el-to-2-6-39-0) but I can't vouch for this as I don't have the problem. 

Hope this helps.

---

### Post by inameiname on 2011-05-13
Thanks for the tip, but unfortunately, I do not use the default Natty kernel and I still get this problem. 

My kernel is: 2.6.39-0-generic.

Oh, and that link you gave is dead.

---

### Post by timgood on 2011-05-13
> **inameiname said:**
> Thanks for the tip, but unfortunately, I do not use the default Natty kernel and I still get this problem. 

My kernel is: 2.6.39-0-generic.

Oh, and that link you gave is dead.

Try [this]("http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0").

---

### Post by floydian_slip on 2011-05-13
I upgraded kernels yesterday and haven't had a problem since. Thanks, timgood.

inameiname, it could be that you and I are experiencing different problems, given that our symptoms are in fact slightly different, e.g. when my screen freezes, I can still move the mouse around.

---

### Post by inameiname on 2011-05-13
Timgood:

Yeah, that's the kernel and PPA I use, and that very kernel version has been updated on my computer since beginning, and the issue has been persistent.

Although, I have not noticed this issue for several days now, ever since I have logged in under the scheme: Ubuntu Classic (No Effects). Perhaps it actually fixed things.

Floydian_slip:

Maybe. We do seem to have a slightly different issue, so who knows. Let me know if updating the kernel to the current on in the PPA fixes things for you.

---

### Post by nrundy on 2011-05-13
when it freezes, can you tap Ctrl + Alt + F2 (bring up the Terminal)? Then "restart" the desktop environment without having to reboot? Does this work?

---

### Post by inameiname on 2011-05-14
I haven't tried using that key combination for opening the terminal when the problem arises, but I have tried my shortcut key for opening a terminal, 'Super L' (Left Windows Key), but to no avail. So IDK; I will have to try that the next time around.

---

### Post by floydian_slip on 2011-05-17
It looks like upgrading the kernel has only partly solved my problem, oddly enough. Now, it never freezes as long as the computer lid is open (even when, after some time, it goes to a blank screen), but it does freeze occasionally when I close the lid.

But not always. For example, I just now opened and closed the lid 5 times in a row, and it's fine, whereas yesterday it was working fine, I closed the lid, opened it up a second later, and it was frozen (mouse still movable, as usual). Very strange.

---

### Post by floydian_slip on 2011-05-17
OK so I was able to get it to freeze again (by opening and closing the lid more slowly, letting it sit closed for slightly longer). This time, I successfully brought up the terminal with alt+ctrl+F2, and then restarted the desktop with

```
sudo /etc/init.d/gdm restart
```

That worked just fine and is much faster (and safer, I assume) than restarting the entire computer.

Of course, there's still the problem of *why* it's freezing in the first place. I'm going to try switching to Ubuntu Classic (no effects) and see if it gets rid of the problem like for inameiname.

---

### Post by inameiname on 2011-05-17
So you are saying when this happens, do the following?:

```

Tap Ctrl + Alt + F2 (bring up the Terminal)

sudo /etc/init.d/gdm restart

```

Glad there is something that might work. I will test it if and when the issue returns.

I would like to say, however, I have not had the issue in a while, largely due to running the desktop under the scheme: Ubuntu Classic (No Effects). This seems to have resolved the issue altogether. However, due to that, I do not have any effects. This solution also resolves two other issues for me (almost with 100% success): 1. occasional default grey theme at startup and 2. ability to drag and drop items to and from taskbar items. So perhaps a good testing method is to try this and see if it fixes things for you.

---

### Post by inameiname on 2011-05-24
I decided to try using Ubuntu Classic again, not Ubuntu Classic (No Effects), and as before, the many issues I get returned. 

My computer screen now freezes nearly every time I let it sit for a few minutes, and like others, it does still let me use my cursor. And like others, I can get into a full screen (like DOS prompt) terminal window upon entering Ctrl + Alt + F2. Unfortunately, typing 'restart' or 'login' merely asks me for my username and password, and then goes back to Command prompt. 

I will keep Ubuntu Classic on a little longer to see what can be done, and when it happens again, I will try:

sudo /etc/init.d/gdm restart


UPDATE:

Okay, so that above code does work in essentially logging me out and back in, however, ever since I tried logging in Ubuntu Classic, EVERY TIME I turn the display off using the following code, I get the freeze. It is EVERY TIME. Perhaps the code below can shed some light on what might be causing it, as it occurs every time I let it sit for more than 10 seconds. Regardless, I have to go back to Ubuntu Classic (No Effects), even though it has its own problems. 

```

#!/usr/bin/python

import time
import subprocess
from Xlib import X
from Xlib.display import Display

display = Display(':0')
root = display.screen().root
root.grab_pointer(True,
        X.ButtonPressMask | X.ButtonReleaseMask | X.PointerMotionMask,
        X.GrabModeAsync, X.GrabModeAsync, 0, 0, X.CurrentTime)
root.grab_keyboard(True,
        X.GrabModeAsync, X.GrabModeAsync, X.CurrentTime)

subprocess.call('xset dpms force off'.split())
p = subprocess.Popen('gnome-screensaver-command -i'.split())
time.sleep(1)

while True:
    print display.next_event()
    p.terminate()
    break

```

---

### Post by floydian_slip on 2011-05-26
I got a bit fed up with this problem and decided to try out Xubuntu, since the problem seemed to be effects-related. (Plus I had been meaning to try out Xubuntu for a while anyway.) Needless to say, I no longer have the problem.

However, what I can say is that, before switching to Xubuntu, I noticed that the freeze occurred to a particular X session, namely tty7 (Ctrl + Alt + F7), and not to the computer as a whole. That's why starting a terminal with Ctrl + Alt + F1, i.e. switching to tty1, is allowable.

Oddly enough, when I ran the command

```
sudo /etc/init.d/gdm restart
```

it did *not* restart the current, frozen session (tty7), but actually started a *new* session in tty8.

In other words, it only looked, on the surface, as if it restarted the session. But in fact, once inside the new session, if I pressed Ctrl + Alt + F7, I would return to the frozen session (tty7).

I'm not sure what would've happened if tty8 had also frozen. Would the restart command have started yet another session in tty9? Or replaced tty7 / tty8? Kind of weird.

---

### Post by inameiname on 2011-05-26
Sorry to hear that. I wish I could just figure out the main culprit behind this and go from there.

Does anybody think it might be a Compiz issue here? On WebUpd8 they have a fix to downgrade Compiz, as many are having issues with it, and I am currently looking into whether this issue is a result of the current buggy Compiz version.

[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

---

### Post by inameiname on 2011-05-27
As an update to this thread, I am close to marking it as solved after downgrading Compiz as per these instructions:

[http://www.webupd8.org/2011/05/how-t...iz-086-in.html]("http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html")


This issue seems to disappear. Before I was using Ubuntu Classic (No Effects) to not have to deal with the whole thing freezing almost 100% upon sitting for some seconds, but now, with Compiz being back to Maverick version, I can log into Ubuntu under Ubuntu Classic, and it hasn't come up yet.

Thus, it may very well be a Compiz issue after all. I will test it further.

---

### Post by inameiname on 2011-06-18
I found a 'fix' that seems to resolve things for me.

The 'fix' is to downgrade Compiz, as per these instructions. I have done  this some hours ago and have restarted, and this issue does not come  up. Further test will be needed, but it seems Compiz was to blame all  along. Very buggy in general I hear.
 
 [http://www.webupd8.org/2011/05/how-t...#disqus_thread]("http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html#disqus_thread")

Ill mark this as solved, even though its not really a fix, but a workaround. Whatever.

---

### Post by dougalkerr on 2011-06-18
Just to add, I have always found the problem related to the present graphics driver installed with the system and it's ability to run with Compiz.
The last time I had this problem (ages ago now) I realized that I did not have enough Graphics memory to run the effects and so did without.
Nowadays I run a laptop with an ATI card (seems they are more reliable with Linus than NVidia cards) and at least 128 Mb graphics memory.
I run the Ultimate Edition of Ubuntu and have no problem running with Desktop effects whether I have the card drivers installed or the Linux ones.
I also always check that the Window manager is Emerald when running Compiz. If the graphics cannot handle Compiz and Emerald together then try Metacity as the compositing manager and Metacity as the Window manager too.
Hope your system runs fine for you from now on.

---

### Post by inameiname on 2011-06-18
Didn't even know Ubuntu Ultimate Edition was still being made. hehe And also, I've never used Emerald before.

Anyway, I'm sure it was something between Compiz and certain graphics cards. My laptops fast enough and has enough memory to handle things, so I don't believe it was entirely that. And since Compiz has caused enough issues lately (as per that link I put) for many, its probably some combination of something. 

Like you said, whatever, so long as its working for me now. Hopefully it'll stay that way on all of my machines.

---


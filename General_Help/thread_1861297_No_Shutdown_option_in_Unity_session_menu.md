---
title: "No Shutdown option in Unity session menu"
date: 2011-10-15
forum: General Help
---

### Post by ctdahle on 2011-10-15
OK, I am making a serious effort here to learn to like Unity, but I'm really bugged that I can't find any way to shutdown !

The Help system makes reference to a "session menu" at the right side of the top panel. The only thing I have there is the item that shows my user name and drops down into a menu that shows:

Switch User Account...
Guest Session
[my list of users]
Online Accounts...
User Accounts...

I expected to see either "Shutdown" as an option in this menu, or else a power button icon in the upper right, but either way, the only method I have to shut down is to go to a terminal and enter "sudo shutdown now". Even when I do that, the system just freezes and gives me a dimmed out screen. It doesn't return any of the usual linux indications that the system is actually shutting down.

And another thing. Is there any way to pin preferred applications to this start bar thing down the left side of the desk top?

---

### Post by Is Mise on 2011-10-15
There should be a gear/power icon to the right of your name, that's where the shutdown option is.

To pin an application to the launcher, you can either drag its icon from the dash to the launcher bar, or right-click on the program's icon while it's running and select "Keep in launcher."

---

### Post by ctdahle on 2011-10-15
OK I figured out how to pin an application to the launcher. (With the application open, go to the launcher, right click on the application icon, and then select "pin to launcher".

I'm still very puzzled though that there is no way to shutdown the computer. Surely the Unity people don't expect GUI users to go back to a command line just to shut down.

I think I can get used to the rest of the idiosyncrasies of Unity if I can just get it to start up and shut down properly. Right now the only way I have to shut it down is by holding down the power switch.

---

### Post by ctdahle on 2011-10-15
Is Mise, I agree, there SHOULD be a gear shaped icon there. I've even seen a screen shot so I know what it is supposed to look like and where to look for it. But *it's not there!*

---

### Post by Is Mise on 2011-10-15
I had a problem with the power menu disappearing occasionally when using the beta version of 11.10, I was able to get it back by pressing Alt-F2 and entering: unity --replace

---

### Post by ctdahle on 2011-10-15
Any other ideas? I tried alt F2 and entered the command: unity --replace

The screen blanked out, then my wallpaper screen came up and the system froze. I gave it a couple of minutes but nothing happened. I had to do a hard restart.

But I'm glad to know that I can get a command line by hitting Alt-F2.

I'm getting a bit frustrated, I'd planned to spend the morning playing with my Arduino.

---

### Post by mc4man on 2011-10-15
When the referred to bug was active the power indicator was still there - the icon was just not seen. but could be accessed by..

To see if the same is affecting you try this - 
click on your username, then slide your cursor to far right edge of screen keeping it in the top panel - does the power dropdown show up?

---

### Post by ctdahle on 2011-10-15
Well this is really strange, there is still no icon, but I found that if I veeeerrry caaarrefully hold the mouse pointer in the extreme upper right corner of the screen, there is an area about 2 pixels wide and about 12 pixels high where I can click to make the power menu open up.

If you have any ideas how to make the icon appear however, that would be better!!!

I see that Alt-F2 doesn't really access a terminal, but it does let me launch an application...if I only knew the commands to enter.

---

### Post by ctdahle on 2011-10-15
Yeah, I cross posted you. Is there a fix to bring up the icon?


> **mc4man said:**
> When the referred to bug was active the power indicator was still there - the icon was just not seen. but could be accessed by..

To see if the same is affecting you try this - 
click on your username, then slide your cursor to far right edge of screen keeping it in the top panel - does the power dropdown show up?

---

### Post by Is Mise on 2011-10-15
A couple of other ideas are:

sudo apt-get install --reinstall indicator-session

From a terminal and then then restart the computer.

Or try:

unity --reset

From Alt-F2.

---

### Post by mc4man on 2011-10-15
Try the above in post 10
This bug was fixed - how old is your install?

If still no go I'll look up the bug report..

---

### Post by ctdahle on 2011-10-15
I tried Alt-F2:  unity --reset   but didn't work.

I'll try   sudo apt-get install --reinstall indicator-session

from a terminal in a minute or two here.


Is there a keyboard shortcut that will open up a terminal window?

Is there a really good way to learn how to work, like exclusively, from a terminal window, or is that secret knowledge reserved for the elite priesthood?

---

### Post by ctdahle on 2011-10-15
mc4man,

I tried both fixes suggested in post 10. No success.

My install was new at 1100 GMT today.

---

### Post by ctdahle on 2011-10-15
OK, this is good, I have learned several new things from this morning's frustration:

1) Alt-F2 brings up a command line
2) Ctrl-Alt-T brings up a terminal window
3) If I have an application running, I can pin it to the launcher by right clicking its icon in the launcher.
4) sudo gives me the power of root for one command without logging in as an administrator (OK I sort of knew that one).
5) The shutdown command only brings the system to a halt, it does not trip the relay that kills the power entirely...and there is probably a way to get around that if I can learn a bit of code.

Still would like to get that silly power menu icon but at least I can shut the machine down.

Thank you both for your help.

---

### Post by mc4man on 2011-10-15
ctrl+alt+t will open a terminal

Here's a link to the previous bug - the actual circumstances were a bit different, involved apt-get & update manager & the 'restart required' in the indicator, but the symptom is the same - it's there but not seen
[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/854292](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/854292)

I've a 3 day old install - haven't seen this

What happens if you create a new 'standard' user, log out & into that user - is the indicator visible?
(you can get rid of the user afterwards

On the login screen is the power button there?

(you could also try purging the indicator, restarting  & then re-installing. After purging use ctrl+alt+delete to get a logout or below to go directly to a restart prompt
```
sudo apt-get purge indicator-session
```
```
/usr/lib/indicator-session/gtk-logout-helper --restart
```

---

### Post by ctdahle on 2011-10-15
Thank you for your efforts mc4man. I found another thread discussing the same problem.

[http://ubuntuforums.org/showthread.php?p=11348859#post11348859](http://ubuntuforums.org/showthread.php?p=11348859#post11348859)

I tried the solution there, which was to change the desktop theme. I changed mine from "Ambiance" to "Radiance" and then back again and the power icon blinked on. I'm going to power down and see if it remains. If not, I'll try your solution.

---

### Post by ctdahle on 2011-10-15
All seems to be working. I'm gonna mark this *solved!*

---

### Post by mc4man on 2011-10-15
Good to know about the theme reset for this ...
Sorta surprised that was needed on a fresh install - something that generally is coming up  only on upgrade installs

---

### Post by ctdahle on 2011-10-15
Oh, maybe I didn't answer your question correctly, this morning was an upgrade, not a clean install of Oneiric.

I've steadily upgraded since starting with Karmic, so maybe that was the the problem, and maybe I screwed something up when I was trying and failing to grok Unity last spring.

---


---
title: "firefox randomly crashing, taking entire system with it."
date: 2010-07-25
forum: General Help
---

### Post by mrfnuts on 2010-07-25
I'm running Ubuntu 10.4, 64-bit version and find firefox seems to randomly crash out, and I can't fix the problem without rebooting (and system won't shutdown without power off either).

Essentially the firefox-bin process goes into an 'Uninterruptible' status, and the 'waiting channel' says 'rtnl_lock'.  The firefox window itself goes 'greyed out'.

If I try to kill the process, all that happens is it goes from 'Uninterruptible' to 'Zombie'.  But, the process itself never dies.

After this firefox can't be restarted, for that matter, applications start going bad.  Even terminal.

If I try to restart (while still having control over the OS) I get a notice that firefox is still running, and I can either 'cancel' the shutdown, or continue (or is it 'force shut down' forgetting the exact text right now).

I chose to force the shut down, and it looks like Ubuntu goes to the shut down screen, but, never shuts down.  A power cycle is in fact needed (I have waited 20 minutes, the time to take a shower and come back)

Has any one seen such behavior?

I will also add that I tried another version of firefox, I also installed the 32-bit version because so many flash sites still run better with it, however, my 32-bit firefox also crashes in the same way now.

If there is 'any' common thing going on when firefox crashes, is I believe it is it happens when the screen saver is activated.  I have never had firefox crash when I'm sitting and using the computer, but, if I go away for as short as 10 minutes and the screensaver kicks in, it seems there is a good chance firefox will be 'grey' when I return.

Any help/advice would be appreciated.

---

### Post by lovinglinux on 2010-07-26
Turn of screensaver. Make the monitor go off instead.

If you are using Firefox 3.6.7, then that could be the fault, since Mozilla already released 3.6.8 to fix instability issues. Nevertheless, seems to me the problem lies in the screensaver. I have seen various reports of screensaver issues, not just with Firefox.

You could also check if it happens with a clean profile or when running firefox in safe mode, to determine if it isn't an issue with some extension or profile settings. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---


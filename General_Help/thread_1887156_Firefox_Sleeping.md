---
title: "Firefox Sleeping"
date: 2011-11-26
forum: General Help
---

### Post by pstefanini on 2011-11-26
I run 10.04 LTS and though I like Firefox perfectly well, recently added Chrome to check it out.  

Firefox is now acting up.  When I close Firefox and reopen it, an error message comes up 

"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

If I check the System Monitor and look at "Processes", sure enough, what shows is "firefox-bin - Sleeping - Memor 13.1 MiB - futex_wait_queue_me"  If I kill the process, Firefox will fire up.  

I have made numerous attempts to uninstall/re-install Firefox using Synaptic and The Software Center to no avail

Has anyone come across this before.  Chrome is good by the way but I'm not ready to pull the plug yet on Firefox.

---

### Post by ajgreeny on 2011-11-26
I have no idea why this might happen, but it does it to me occasionally as well.

For some reason you will probably find that there is a process, **firefox-bin** running on the system, not just the normal **firefox** executable.  It seems to be a well known problem.

See what is running with ```
ps aux | grep firefox
``` or run ```
top
``` and if firefox-bin is running kill it with either its PID or use ```
killall firefox-bin
```

This problem appears to be caused sometimes by add-ons that misbehave, or by the firefox application freezing, being killed, but then leaving this annoying firefox-bin still running.

---

### Post by vasa1 on 2011-11-26
> **pstefanini said:**
> ...
I have made numerous attempts to uninstall/re-install Firefox using Synaptic and The Software Center to no avail

Has anyone come across this before.  Chrome is good by the way but I'm not ready to pull the plug yet on Firefox.

I have both Chrome and Firefox on 11.10 and haven't encountered this problem so far.

When you uninstall Firefox, do you delete your profile folder? If you don't, and if there's a problem due to something in your profile (corrupted files or add-ons that cause some weird conflict), you'll see the problem again and again.

Your profile resides in _.mozilla_ in your home folder.

At the cost of some functionality, you could also try running Firefox in safe mode (from the Help menu) and see if the problem occurs. If it doesn't, that would indicate an issue with your add-ons/plug-ins.

---

### Post by claracc on 2011-11-26
Here you have the mozilla help for the problem: [http://support.mozilla.com/en-US/kb/Firefox](http://support.mozilla.com/en-US/kb/Firefox) is already running but is not responding

---

### Post by vasa1 on 2011-11-26
> **claracc said:**
> Here you have the mozilla help for the problem: [http://support.mozilla.com/en-US/kb/Firefox](http://support.mozilla.com/en-US/kb/Firefox) is already running but is not responding

Hi! Could you please check the link?

---

### Post by LinuxFan999 on 2011-11-26
> **pstefanini said:**
> I run 10.04 LTS and though I like Firefox perfectly well, recently added Chrome to check it out. 
 
Firefox is now acting up. When I close Firefox and reopen it, an error message comes up 
 
"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."
 
If I check the System Monitor and look at "Processes", sure enough, what shows is "firefox-bin - Sleeping - Memor 13.1 MiB - futex_wait_queue_me" If I kill the process, Firefox will fire up. 
 
I have made numerous attempts to uninstall/re-install Firefox using Synaptic and The Software Center to no avail
 
Has anyone come across this before. Chrome is good by the way but I'm not ready to pull the plug yet on Firefox.
Why does the title say "[lubuntu]" when you are using Ubuntu (with gnome)?

---

### Post by bluexrider on 2011-11-26
> **vasa1 said:**
> Hi! Could you please check the link?


page not found.......

---

### Post by vasa1 on 2011-11-27
> **LinuxFan999 said:**
> Why does the title say "[lubuntu]" when you are using Ubuntu (with gnome)?
That's happened to me a few times too. I thought I chose Ubuntu for a new thread but found my post in lubuntu. I kept very quiet because I'm not sure that I wasn't careless.

---

### Post by claracc on 2011-11-27
I copy the link again: [http://support.mozilla.com/en-US/kb/Firefox%20is%20already%20running%20but%20is%20not%20responding](http://support.mozilla.com/en-US/kb/Firefox%20is%20already%20running%20but%20is%20not%20responding)

this time I expect it works

---

### Post by vasa1 on 2011-11-27
> **claracc said:**
> I copy the link again: [http://support.mozilla.com/en-US/kb/Firefox%20is%20already%20running%20but%20is%20not%20responding](http://support.mozilla.com/en-US/kb/Firefox%20is%20already%20running%20but%20is%20not%20responding)

this time I expect it works

Just fine!

---

### Post by pstefanini on 2011-11-27
You guys were right.  I disable all of the add-ons and it works fine again.  Re Lubuntu... I may have been careless so I apologize if I misled anyone.  One thing I noticed is that my Firefox Tools menu doesn't allow me to start in safe mode... but as noted, manually disable them and restarted. 

Again, thank you all, it was an annoying problem and Have a Happy Holiday Season!  Phil

---


---
title: "Update-notifier not working"
date: 2009-12-08
forum: General Help
---

### Post by brandon88tube on 2009-12-08
For some reason my update notifier isn't working. It never notifies me period of any update even if its a security update. Since I've installed I have yet to have it notify me. I have to manually check all of the time. It just gets slightly annoying having to manually check all of the time.

---

### Post by dcstar on 2009-12-09
> **brandon88tube said:**
> For some reason my update notifier isn't working. It never notifies me period of any update even if its a security update. Since I've installed I have yet to have it notify me. I have to manually check all of the time. It just gets slightly annoying having to manually check all of the time.

Add the notification applet back into your top panel.

---

### Post by brandon88tube on 2009-12-09
What is the exact name of the applet? I don't seem to have it in the list of panel apps.

---

### Post by john newbuntu on 2009-12-10
Open up a terminal and type
```
gconf-editor
```
Hopefully the configuration editor will pop up.  If not, install it first.

In the config editor, you will find apps/update-notifier on the left panel. Make sure that the auto-launch is checked.  Also, you can tinker with the regular-auto-launch-interval option to receive updates as soon as they are available.

---

### Post by brandon88tube on 2009-12-10
I did not seem to have gconf-editor installed, so I installed and messed with the settings. Set the interval to 0 to update me whenever there is a new update. I don't know if this works yet.

---

### Post by brandon88tube on 2009-12-11
Well that failed. Do I need to have it load on startup and if so how would I go about that?

---

### Post by john newbuntu on 2009-12-12
Try this workaround:
On a terminal, first type:
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

Go to system->preferences->startup applications->add and type the following for the command.  The name and comment can be anything of your choice:
```
/usr/bin/update-notifier --startup-delay 60
```
The startup-delay is the number of seconds for the update to kick in after you login. You can adjust it suitably.  Now logoff and login and see if you get a red icon on your top panel.

---

### Post by brandon88tube on 2009-12-18
Well, I waited for about a week for testing and it failed. It still never notified me of new updates and had to manually check. Need some help with this.

---

### Post by john newbuntu on 2009-12-18
Please run "/usr/bin/update-notifier" from the command line in a terminal and see if it shows up anything?

---

### Post by brandon88tube on 2009-12-18
It gives me a warning because its already running.

---

### Post by john newbuntu on 2009-12-18
Have you run "sudo apt-get update" at anytime in the last few days.  If yes, can you remember the last time you ran it?

---

### Post by brandon88tube on 2009-12-19
I didn't actually run it through the command line, but I did to it through the update manager. I did it a few days ago and nothing came up for updates so I waited a few more days without checking the updates until yesterday when I decided to check again. That was the reason it took me about a week to respond back to this thread.

---

### Post by Crosbie on 2009-12-20
Have you tried john newbuntu's start delay fix?  I had this problem and adjusted the startup line to read

```
update-notifier --startup-delay=120
```

And update manager autostarted correctly for me for the first time today. :)

---

### Post by brandon88tube on 2009-12-20
Yeah, but I figure I'll give it another shot just in case.

---

### Post by Sevy on 2009-12-20
I too am having this problem,tried whats been suggested but no luck yet
It seems something tries to show on the top panel-just a vertical line which goes after a few minutes

Its working for me now!!
All I did was change regular_auto_launch_interval to 0 in gconf-editor
But update manager comes up without notification or a red icon in the top bar

Forget the last bit I had update manager come up automatically.Ive unchecked that and now everything is as it should be ;)

---

### Post by brandon88tube on 2009-12-20
I believe I have it setup correctly, we shall see in a few days or so.

---

### Post by Sevy on 2009-12-22
It seems when I play with the settings it works OK shortly afterwards.
Booting up today I am no longer notified.
Like brandon88tube we seem to have everything setup correctly.
I dont know what else to try:confused:

---

### Post by brandon88tube on 2009-12-22
Well, so far 2 days have passed and no updates. When I hit the end of the week and still haven't gotten any then I know something is definitely wrong.

---

### Post by brandon88tube on 2009-12-26
Ugh, it still failed to notify me of any updates. Its like a pointless program to even have if I have to manually check all of the time anyways.

---


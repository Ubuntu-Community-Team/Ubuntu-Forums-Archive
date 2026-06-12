---
title: "No working notification area"
date: 2011-05-01
forum: General Help
---

### Post by tembares on 2011-05-01
Thank you for reading this post.

I am using Ubuntu Natty with Unity.

I was used to use the network and battery icon in the notification are (next to the sound and date/time). Now the bluetooth, battery, network, sound and envelope icon are visible, but there is no responds clicking on it.

Pressing the mute-button on the keyboard changes the icon in the notification area. Also connecting a wireless network changes the icon.

But to change network is becoming impossible by clicking the icon (and I do not know an other way to change it).

The only thing I can think of was whitelisting all programs:```
sudo gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```
This was the only change I made.

EDIT: Icons of external programs do respond.

Hope someone can help me.

Thank you in advance.

---

### Post by AndreaZ on 2011-05-02
I have the exact same problem.

I can´t first click for example WLAN or screenlets to get any action. 

But if I click on Date/time first , then I can scroll to the left and the other Icons work again. 
I want it to work like it did in Gnome2, just click it! :)

---

### Post by tembares on 2011-05-02
> **AndreaZ said:**
> But if I click on Date/time first , then I can scroll to the left and the other Icons work again. 
I want it to work like it did in Gnome2, just click it! :)

Thank you SO much for this 'solution'. Hope this will change with the next update! I will report a bug on Launchpad.

---

### Post by wgarcia on 2011-05-02
I reported a bug on this:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/767242](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/767242)

If you are experiencing the same issue you can there and click confirm for my bug.

---

### Post by AndreaZ on 2011-05-02
> **tembares said:**
> Thank you SO much for this 'solution'. Hope this will change with the next update! I will report a bug on Launchpad.

Happy to help, it is annoying as hell :)

---

### Post by AndreaZ on 2011-05-03
For some reason, it actually worked as intended yesterday evening! Then I had to restart due to Kernel-upgrade and then it was gone.... :(

---

### Post by tembares on 2011-05-03
Notification area works for me again as at was.

THANK YOU!

---

### Post by AndreaZ on 2011-05-03
How did you get it working? :)

---

### Post by tembares on 2011-05-03
Uhhhh... nothing :confused:
I think it was an update.

---

### Post by AndreaZ on 2011-05-03
ok, no change for me, and all updates are done...crap! :)

---

### Post by AndreaZ on 2011-05-04
I just found something interesting.

When I have Mullvad ([http://www.mullvad.net](http://www.mullvad.net)) active in the tray, I have to go to the date/time and them move right to get the tray menus to work. (like mentioned above)
When it is closed and not in the tray, everything works as it should.

Could it be that 3rd party applications somehow freezes the tray?

---

### Post by tembares on 2011-05-04
Well, the notification area works now, but the icons from extended parties are not visible, only empty spaces. Only Cryptkeeper shows its icon.
I whitelisted 'ALL', so that cannot be the probem, I guess.

Hope a solution will come soon!

---

### Post by 3rdalbum on 2011-05-04
Running:

```
unity --reset
```

appears to be a workaround for the problem, assuming it's the same problem that creates dead areas on the screen.

Doesn't hurt to give it a try (it just restarts Unity but keeps your programs running).

---

### Post by tembares on 2011-05-04
> **3rdalbum said:**
> Running:

```
unity --reset
```

appears to be a workaround for the problem, assuming it's the same problem that creates dead areas on the screen.

Doesn't hurt to give it a try (it just restarts Unity but keeps your programs running).

I can recommend this. It worked for me!
EDIT: It only works one time. After restart it is the same story.

---

### Post by 3rdalbum on 2011-05-04
> **tembares said:**
> I can recommend this. It worked for me!
EDIT: It only works one time. After restart it is the same story.

Yes, you might have to run it again after restart if you encounter the same problem. You could have the command in your login startup applications; it'll increase login time by a couple of seconds.

---

### Post by AndreaZ on 2011-05-05
Yes it works for me too, the icons are now clickable. I&#314;l add this to startup for now. :)
THank you!

EDITED: Well it semi-worked...my terminal froze. Will try again this evening.

---

### Post by tembares on 2011-05-05
> **3rdalbum said:**
> Yes, you might have to run it again after restart if you encounter the same problem. You could have the command in your login startup applications; it'll increase login time by a couple of seconds.

Well, I made the launcher icons smaller and does not let the launcher disappear, so everytime after startup I have to set those settings, too.
Not an option :-)

---

### Post by tembares on 2011-05-05
In addition to my previous post.

I have a HP TM2T with an Intel and ATI card.
Switched to the Intel the notification area icons are gone and switched to the ATI card it is there.

Maybe this helps :confused:

---

### Post by 3rdalbum on 2011-05-06
> **tembares said:**
> Well, I made the launcher icons smaller and does not let the launcher disappear, so everytime after startup I have to set those settings, too.
Not an option :-)

Sorry to hear that. Performing unity --reset doesn't seem to change my options at all.

Maybe something like the following might work:

```
metacity --replace
unity &
```

---

### Post by AndreaZ on 2011-05-06
> **3rdalbum said:**
> Sorry to hear that. Performing unity --reset doesn't seem to change my options at all.

Maybe something like the following might work:

```
metacity --replace
unity &
```


That didnt help me, my desktop freezes forever.....but hopefully we&#314;l have a solution soon. :)

---

### Post by tembares on 2011-05-08
To add another mystery to this problem.

The standard notification area icon works now.
The problem are the colored 3rd party icons.
The icon does not appear at start-up. But when I kill the processes of those programs and start them again, the icon appears in the notification area.

I whitelisted ['ALL'] programs by ```
sudo gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

Who can tell me how to solve this?

---

### Post by AndreaZ on 2011-05-30
After I removed the Dropbox icon, I do not have this issue anyomre (or, at the moment ;) )
It has worked normal for almost a week (I really wanted to try it before telling anyone to be sure).

Might be 3rd party issue?

---

### Post by hawthornso23 on 2011-05-30
As unity uses compiz,   "metacity --replace"   is a really really bad idea.

---

### Post by tembares on 2011-05-30
Execute ```
setsid unity
``` after the gsettings-command.

---

### Post by sitting_nem on 2011-06-07
Open dconf-editor and click on desktop -> unity -> panel
Set to Default.
The notification area will work again.

---


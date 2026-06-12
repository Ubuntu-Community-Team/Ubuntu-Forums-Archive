---
title: "Unity Disappeared (CCSM Issue)"
date: 2011-12-11
forum: General Help
---

### Post by Katla on 2011-12-11
Well, this is frustrating and makes me angry.

 I had an issue with choppy video. It seemed to tie in with my recent upgrade to 11.10. So I searched around to find a fix. I saw it mentioned that I could uncheck a box in CompizConfig Settings Manager that might help, so I installed the program and ran it. It opened, and I clicked to look at a different page. My computer froze for about a minute. When I regained control Unity had been nuked. To be clear, I selected no options in CCSM. I just opened it.

Looking around the web I see that this is a common issue. Common enough that Ubuntu needs to take it out of their Software Center, if you ask me. That sort of bug is just bush league. But I digress. I found a few pointers on how to fix it, but have thus far had no luck. I tried typing "unity --reset" in the terminal, but it didn't work. Just told me no value was set, so it set it at "0". I don't know enough to try and play around with that by adding a 1 or something. 

I also read that typing "ccsm" brings up options, but that didn't work at all. 

I've restarted (hard reboot) multiple times, no change. I cannot change user or start a session with Classic Unity as I have auto log-in with no delay (I had just changed that delay setting, and, boy, do I regret it now).

So I need Unity reactivated, after which the first thing I will do is uninstall CCSM and spit on it.  Any help with this would be appreciated (the reactivation, not the spitting. I can do that on my own). 

Thank you.

---

### Post by bluexrider on 2011-12-11
open terminal

```
sudo apt-get remove compizconfig-settings-manager
```

or

To reset Unity in CompizConfig Settings manager, open a terminal or press ALT + F2 and enter the following command.
 unity --reset 

 Similarly, to reset Unity Launcher icons, use the following command.
 unity --reset-icons

---

### Post by philinux on 2011-12-11
> **Katla said:**
> Well, this is frustrating and makes me angry.

 I had an issue with choppy video. It seemed to tie in with my recent upgrade to 11.10. So I searched around to find a fix. I saw it mentioned that I could uncheck a box in CompizConfig Settings Manager that might help, so I installed the program and ran it. It opened, and I clicked to look at a different page. My computer froze for about a minute. When I regained control Unity had been nuked. To be clear, I selected no options in CCSM. I just opened it.

Looking around the web I see that this is a common issue. Common enough that Ubuntu needs to take it out of their Software Center, if you ask me. That sort of bug is just bush league. But I digress. I found a few pointers on how to fix it, but have thus far had no luck. I tried typing "unity --reset" in the terminal, but it didn't work. Just told me no value was set, so it set it at "0". I don't know enough to try and play around with that by adding a 1 or something. 

I also read that typing "ccsm" brings up options, but that didn't work at all. 

I've restarted (hard reboot) multiple times, no change. I cannot change user or start a session with Classic Unity as I have auto log-in with no delay (I had just changed that delay setting, and, boy, do I regret it now).

So I need Unity reactivated, after which the first thing I will do is uninstall CCSM and spit on it.  Any help with this would be appreciated (the reactivation, not the spitting. I can do that on my own). 

Thank you.

I think you would be better deleting the .compiz folder in your home directory. Do it from the recovery boot option from grub.

---

### Post by Katla on 2011-12-11
I've previously tried the "unity --reset" command with no effect. 

I entered the remove CCSM command, as well. Nothing, though I've yet to reboot after that, as I suspect I might need to.

As far as deleting the compiz folder, would that be under /usr/share? I've got 3 folders there - CCSM, Compiz, and Compizconfig.

---

### Post by philinux on 2011-12-11
> **Katla said:**
> I've previously tried the "unity --reset" command with no effect. 

I entered the remove CCSM command, as well. Nothing, though I've yet to reboot after that, as I suspect I might need to.

As far as deleting the compiz folder, would that be under /usr/share? I've got 3 folders there - CCSM, Compiz, and Compizconfig.

It's in your home folder. Not at my pc at moment. On HTC android so can't be precise.

---

### Post by Katla on 2011-12-11
I was able to log in with 2D (ctrl+alt+del is good for something), so Unity works now. I uninstalled CCSM from the Software Center. I assume that should fix the issue when I log back in, but I don't know. If nothing else I can just continue using the 2D version. Not like I needed the the 3D effect to slow my system down. I don't use the Cube or anything gimmicky like that.

---

### Post by bluexrider on 2011-12-11
> **Katla said:**
> I was able to log in with 2D (ctrl+alt+del is good for something), so Unity works now. I uninstalled CCSM from the Software Center. I assume that should fix the issue when I log back in, but I don't know. If nothing else I can just continue using the 2D version. Not like I needed the the 3D effect to slow my system down. I don't use the Cube or anything gimmicky like that.
at least you have a working system. hope it works out

---

### Post by philinux on 2011-12-11
Uninstalling ccsm does not do anything. All the config files for compiz are in home. They like other apps on removal never remove home config files.

---

### Post by Katla on 2011-12-11
I've got a lot of Compiz files in home and have no idea which one(s) to burn. I think I even have more than one instance of Compizconfig.

---

### Post by Mark Phelps on 2011-12-12
The thread below details what needs to be done to reset Unity and ccsm:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---


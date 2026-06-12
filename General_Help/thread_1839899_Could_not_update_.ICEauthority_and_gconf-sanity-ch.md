---
title: "Could not update .ICEauthority and gconf-sanity-check-2 exited with status 256"
date: 2011-09-06
forum: General Help
---

### Post by rootless on 2011-09-06
Two errors:

"Could not update .ICEauthority file /home/myusername/.ICEauthority"

and

"There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"

I'm getting both of these right as I log into Gnome.

This is a well known bug, but there don't seem to be any clear solutions:

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215)

I am running Ubuntu 11.04 with an encrypted home on a System 76 Lemur. This will teach me to run unstable. Nautilus broke after an update. It became unresponsive. I believe it was this specific bug:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/749776](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/749776)

Anyway, I tried

```
dpkg --configure nautilus

package already configured (or something like that)
```

so then I went and did a

```
sudo apt-get purge nautilus nautilus-data

sudo apt-get install nautilus
```

I know, stupid, but I couldn't think of any other solution. Then I got the error message "Could not update ICEauthority file /home/myusername/.ICEauthority"

Well, no problem, I think. I've had issues like this many times before most of the solutions online involve fixing the user ownership and privs over the .ICEauthority file. I make sure that I am the owner, and that the privs are set correctly. Finally, out of desperation, I try

```
chmod 777 .ICEauthority
```

Even then, I get the same error!

I find another solution that says to delete the file altogether and allow it to be recreated, but the error continues. I go back to the file that I was using before I purged Nautilus. The error continues. Nothing. Any help would be greatly appreciated. Has anyone been able to solve this?





As a side note- I am quite angry with myself, and with Ubuntu right now. I should've thought more before moving off of stable, but honestly, it seems that Ubuntu's criteria for Unstable has gone from usable with a few tweaks to totally unusable.

You used to be able to run unstable on your main machine without too much trouble. It seems like Unstable is now being viewed as more of a testing and developing sandbox, but there hasn't been any announcement to indicate this change in philosophy, and ubuntu.com/download/ubuntu/download still redirects to the latest version by default, even if it is unstable. A lot of the software getting shipped out is half-finished. 

Well, what the hell, guys! I've spoken with a few people, and I know I'm not the only person who has noticed this trend. As I said before, I would be **very** grateful if anyone has any more info about this problem. I'll check back tonight, but honestly, the way things are going, it seems like I may have to do a clean install of stable to escape the unity development treadmill.  t(>___<)t

---

### Post by Seraph Trend on 2011-09-08
Just ran into the same problem, only that I succesfully changed my login password. Did a restart, then I couldn't log in anymore. :confused: 
Need help soon, please.

---

### Post by rdw53 on 2011-09-15
I am having the same problem. I tried reinstalling Nautilus too with no results. I attempted to change the ICEauthority permissions and my computer claimed it couldn't find the file. I got the impression ICEauthority was deleted but I am brand new to Linux and admit I could be missing something.

---

### Post by rootless on 2011-09-16
Nope, you didn't miss anything. It's still broken, I'll bet until 11.10. I had to wipe and restore. Luckily, I had just backed up my system that same day when it happened to me.

Sorry, guys. I went back to Long Term Stable (10.04.) It seems like LTS is the only release that you can count on, now. Ubuntu isn't like what it used to be.

---


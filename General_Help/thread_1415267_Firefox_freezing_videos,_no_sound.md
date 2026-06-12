---
title: "Firefox freezing videos, no sound"
date: 2010-02-24
forum: General Help
---

### Post by semisquirrel on 2010-02-24
A few days ago, with no apparent change to the system, Firefox started acting funny.

On most video sites, but not all, there would be no sound.  Along with this, some of these sites would also have the glitch that videos would play for about 3 seconds, then stop.  If I moved the slider to a different point in the video, it would again work for a few seconds, then stop.  

If I close FF and try to reopen, I get an error message that it is already running, although if I don't leave it open, I don't get that message.

I then go to the system monitor and shut down the sleeping FF process, and can then restart FF and the problem is fixed for a few hours.

I have tried to reinstall, but the issue has not gone away.  Any suggestions?

Thanks!

---

### Post by dabl on 2010-02-24
When your internet download bandwidth drops, for whatever reason, at a certain point audio/video streams get intermittent.  There are gaps (silence & video freezing) while it waits for the next packets to arrive.  Is it possible this is what is happening?

---

### Post by n0dix on 2010-02-24
Do you get any error if you run Firefox from console?

---

### Post by semisquirrel on 2010-02-24
I should have explained that; sorry.

No.  It has nothing to do with downloading speed.  It's a permanent break.  If I wait 10 minutes, it will not start moving again.

---

### Post by semisquirrel on 2010-02-24
> **n0dix said:**
> Do you get any error if you run Firefox from console?

I kinda feel silly asking this, but how would I go about testing that?  I'm kinda new to this stuff.....

---

### Post by n0dix on 2010-02-24
> **semisquirrel said:**
> I kinda feel silly asking this, but how would I go about testing that?  I'm kinda new to this stuff.....

If you are in Gnome.
1. Alt+F2, then write xterm and press Enter.
2. run firefox. 
```
firefox
```
3. Copy and paste.

---

### Post by lovinglinux on 2010-02-25
Make sure you don't have multiple plugins installed.

For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by TBABill on 2010-02-25
I think the folks at Mint 8 finally figured out how to make this process a part of their distro because Flash is flawless in Mint 8 without the end user going through removal/installation pains first. When Mint 8 first came out that was not the case, and both Ubuntu and Mint (both 64-bit) performed horribly with Flash, but a recent install of Mint 8 with updates applied now performs as well as Mandriva and OpenSUSE, whose Flash performance has been far better than Ubuntu 9.10. I recently tried Ubuntu 9.10 64-bit and Mint 8 64-bit (both Gnome) and Mint is far superior regarding Flash performance (without tweaks from the user).
 
I don't know what the Mint 8 people found and corrected within Karmic, but it may be safe to assume it's just a conflict between plugins, codecs, drivers or something similar. I am unsure what their fix was to correct the many flash complaints, but it sure worked well. Hopefully when 10.04 comes out of alpha and beta the Ubuntu devs will have whatever conflict there may be worked out.

---


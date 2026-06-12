---
title: "Can you reset Ubuntu?"
date: 2010-01-28
forum: General Help
---

### Post by douglas110500 on 2010-01-28
Hi everyone

I'm sort of an Ubuntu noob, I've currently got 9.10 and have (somehow) managed to mess the system up already! 

It's a new computer so I'm not fussed about data loss etc, but is there a way to completely reset the system which will also format the hard drive (as it was a download that has messed it up!) without losing the O/S?

Thanks in advance guys and girls, I look forward to your responses.

Doug

---

### Post by audiomick on 2010-01-28
I am not aware of any reset, other than to re-install.
Before you do that, what is messed up? Let us know, and what the download was. It might be something that can be fixed.

---

### Post by Revolutionary101 on 2010-01-28
Not that I know of. You might just want to reinstall Ubuntu.

> **audiomick said:**
> I am not aware of any reset, other than to re-install.
Before you do that, what is messed up? Let us know, and what the download was. It might be something that can be fixed.

Agreed. Ubuntu can be a learning experience. I think you should try and learn how to fix the problem and only resort to reinstallation as a last resort. We are here to help.

---

### Post by sailthesea on 2010-01-28
Well Yes...
You could burn the CD of 9.10 and install it....
Drive formatted, fresh install, all data gone
Is that what you meant?;)

---

### Post by sailthesea on 2010-01-28
Maybe something went wrong during a System Update?

---

### Post by douglas110500 on 2010-01-28
Well, I live in the middle east, which you may guess has a little bit of an unreliable internet connection at times. During a normal update my connection was severed, and has resulted in a partially downloaded package which has completely done in my computer, no programs open properly, I entered sudo and purged incomplete packages but it's done nothing! 

So I guess it may be a complete reinstall afteral eh?

---

### Post by audiomick on 2010-01-28
I expect that there are people here who could fix that, but I think I would indeed do a re-install.;) If it were an older system with lots of stuff I wanted to keep, I might try to save it.

If you re-install, I would suggest a separate /home partition, it you don't already have one. That way, if you have to re-install again, you can just re-mount it during the install. This retains your data and settings.

You have to choose the manual partitioning option during the install.
I would suggest
10 - 15 GB partition mounted at / for the system
swap partition = RAM if you want hibernate to work, otherwise it can be smaller if you have a decent amount of RAM
the rest of the space as a partition mounted at /home

---

### Post by sailthesea on 2010-01-28
He did it again!
 If an update failed and you don't really have anything to lose.
 Yes, reinstall.

On another note: I never update I will just install the latest image I want to use. Updates are, in my experience, are a big sweary NoNO;)

---

### Post by douglas110500 on 2010-01-29
thanks for your input guys, it was much appreciated. Have re-installed and have told the damn thing to only do extremely high importance updates :)

---

### Post by no2498 on 2010-01-29
lol i like this 
"You should know by now, don't drink and sudo" Starcraft.man
thats a good 1

dont you just open synapti package manager  an reload if some thing does not load it tells you its broken fix broken package ?

---


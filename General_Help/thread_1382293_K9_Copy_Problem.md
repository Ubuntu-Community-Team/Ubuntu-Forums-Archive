---
title: "K9 Copy Problem"
date: 2010-01-15
forum: General Help
---

### Post by joelandsonja on 2010-01-15
I have been having a problem with K9 Copy whenever I try to convert a DVD to MPEG files using the method without encoding, but for some reason lately it seems to be splitting each episode into about 6 or 7 pieces instead of just one. I never usually have a problem with this, but for some reason it seems to be doing this whenever I try to rip something.

Any suggestions?

* On a side note, I am running on Obuntu 9.10 and have K9Copy version 2.3.0 installed. I have tried installing several other versions, but it does the same thing with each.

---

### Post by joelandsonja on 2010-01-18
I really need a hand with this one, it seems to be doing it to every DVD I try to rip now. 

I have a collection of DVD's that I want to turn into MPEG files, but for some reason it is defaulting to splitting the files [into multiple files] and I can't find the setting to change this. I have tried reinstalling K9copy and that doesn't work. Is there a way to reset the settings completely, or completely reinstall K9copy and wipe out all of the former settings so the new copy is completely fresh?

---

### Post by joelandsonja on 2010-01-19
I was on another forum, and I was asked if I had a .k9copy folder in my home folder, but I can see that there isn't one there. 

Any thoughts?

---

### Post by mc4man on 2010-01-19
look in ~/.kde/share/config/

2 files, the one named just k9copy is the one that holds the settings

(you have reviewed your settings under Settings -> Configure k9copy -> DVD ..?

---

### Post by joelandsonja on 2010-01-19
I found the file, what do I do with it? Do I just delete the file and reinstall K9copy? 

I am a newbie folks, I would love a bit more details. :D

---

### Post by mc4man on 2010-01-19
Just delete it and restart k9, it will now be set to the new install defaults

---

### Post by joelandsonja on 2010-01-19
Thanks for the suggestion, that is what I was hoping to do, changing the settings seemed like it should have worked, but now for some reason K9copy keeps crashing ...

This program used to be such a good one, now it is giving me a headache!

---

### Post by jeffers.r on 2010-01-20
This is actually an option right within the k9copy configuration. Under the DVD section, you can turn off "one file/chapter" for the mpeg extraction (thus no enconding).

Unfortunately, however, there is a bug associated with this option in k9copy 2.3.0. So although turning it off will create a single file instead of multiple files per chapter, the file will be empty. You can see that the bug was fixed in version 2.3.2, as per the changelog [here]("http://www.kde-apps.org/content/show.php?content=23885"). The changelog suggest the bug occurs when the option is selected, but it actually happens when the option is unselected.

Interestingly, if you are running 9.10, the repositories should include k9copy 2.3.3 which would solve both your problems. If you are running 9.04 like myself, then you need to upgrade ... which is what I'm working on figuring out in this post: [http://ubuntuforums.org/showthread.php?p=8697792](http://ubuntuforums.org/showthread.php?p=8697792)

---

### Post by Sisyphus48 on 2010-02-03
> **joelandsonja said:**
> Thanks for the suggestion, that is what I was hoping to do, changing the settings seemed like it should have worked, but now for some reason K9copy keeps crashing ...

This program used to be such a good one, now it is giving me a headache!
Same here joelandsonja!  I have used k9 copy a bunch and it worked great but for the last month all it does is crash.  I updated to KK in hopes that it would fix the problem and it did not.  Also when I was using 9.04 the driver for my MSI R4550 easily installed and ran great.  Now that I have updated to 9.10 I can't get it installed for love nor money and can't use Nexuiz anymore.:confused::confused::confused:

---

### Post by joelandsonja on 2010-02-04
Sorry for leaving this for so long, but I found the solution to the problem and wanted to make sure that future users had an answer. 

You have to adjust the settings when you open K9 Copy, click on 'Configure K9copy' then click 'DVD', and make sure that 'One file/chapter (MPEG Extraction)' is unchecked. 

Sadly K9copy still crashes occasionally, but at least that problem is fixed.

---


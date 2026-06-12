---
title: "Any problems upgrading from 8.04 to 10.04?"
date: 2010-05-23
forum: General Help
---

### Post by shelbyvision on 2010-05-23
I just noticed that 10.04 is not beta any more, so now I am interested in upgrading from my 8.04. Is 10.04 a lot better? I have no real problem with 8.04, but I'm guessing that with 10.04 I can get newer versions of a lot of the software.
Here's my big question: If I use the network upgrade, hoping to keep my files intact, can I expect to have any problems. Have any of you done this? How did it go?
Thanks,
Steve

---

### Post by warfacegod on 2010-05-23
I believe you'll have to do an upgrade for each release. You'll have to upgrade to 8.10 then to 9.04 and so on. Considering that each upgrade can take several hours, you could easily spend a day or so doing this. On top of that, upgrading has its own inherent dangers (times 4) nor is it generally as stable or swift an install. Its possible your system will become useless forcing you to do a fresh install which is what I suggest anyway. Then again, I've seen a few guys that have been doing successful upgrades from as far back as 6.06. Its really up to you.

If you decide to do a fresh install you might consider this:

Create a small partition, say 10 or 15 GB, for the OS and during the Manual install mark it as /

Create a large partition for all of your files and during Manual install mark it as /home

This setup has the advantage of keeping your files *and* user settings separate from the OS. If your system ever breaks and you can't fix it, you can do a fresh install in your OS partition (being sure to remember to mark the other partition as /home again) without worrying about losing your files and your settings will all still be in place. The only thing you'd have to do is reinstall your programs and remove the ones you got rid of before.

Whatever you decide to do (upgrade or fresh install) MAKE A BACKUP!!!

---

### Post by louieb on 2010-05-23
As you have read you can go straight from 8.04 to 10.04.  There is always the potential for problems.  Did not upgrade my 8.04 to 10.04 - did a fresh install. But if I had - would have made an image backup 1st using partimage. 

Also some things can increase the chance of problems such as having software installed from outside sources.  That was one of the reasons I did a fresh install. I have Open office 3.x , Firefox 3.6, Virtual Box from the Oracle site, medibuntu + some ppa sources. 

It is recommend that repositories outside the Official Ubuntu ones be turned off and and software install from them be removed 1st. 

If your hardy install is sweet, clean, up to date, free of outside software sources  - you have a pretty good chance for a successful upgrade.

---

### Post by shelbyvision on 2010-05-23
Looks like a clean install would be best. I do have lots of "unapproved" stuff on my system.

---

### Post by warfacegod on 2010-05-23
> As you have read you can go straight from 8.04 to 10.04.

[https://help.ubuntu.com/community/LucidUpgrades]("https://help.ubuntu.com/community/LucidUpgrades")

I am mistaken. Reading the forums gives the impression that all upgrades need to be done successively. Evidently this is only the case with some of the releases such as 8.10 and 9.04.

Regardless, a fresh install is almost always preferable to an upgrade.

---

### Post by QLee on 2010-05-23
[QUOTE=shelbyvision]...Here's my big question: If I use the network upgrade, hoping to keep my files intact, can I expect to have any problems. Have any of you done this? How did it go?[/QUOTE]

I did it using the method you mentioned with no problems other than having to add back any outside repositories before upgrading that software. However, I did it on a system that did not have any of the video bugs that have been encountered by others. Make sure your 8.04 system is fully upgraded before starting the Lucid install. Always have a good backup.

Most definitely, read the release note before trying to upgrade, that is the advice that many people don't follow, generally to their regret. Don't blame you for not wanting to clean install, you probably spent some time configuring your system to be as you want it.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

---

### Post by QLee on 2010-05-23
[QUOTE=warfacegod]
I am mistaken. Reading the forums gives the impression that all upgrades need to be done successively. Evidently this is only the case with some of the releases such as 8.10 and 9.04.[/QUOTE]

Reading the forums (all forums, not just Ubuntu's) often gives misimpressions, that is because people write things that they don't understand then other people start to write the same mistakes. One should always verify the "information" they are providing.

LTS versions are designed to be upgradeable to the next LTS. Non-LTS versions are designed to be upgradeable to the "next" version (so 9.10->10.04 is supported). Edit: Actually, that is somewhat backward, it's really more like 10.04LTS is designed to be upgradeable from 8.04LTS or 9.10. It isn't easy to design "foward compatability", eh?

---

### Post by warfacegod on 2010-05-23
> It isn't easy to design "foward compatability", eh?

I feel lucky enough to design myself a cup of coffee in the morning.

---

### Post by TKleszynski on 2010-05-23
Yep I have been having problems!! Out of the blue now my Computer will just go to a flashing Black screen and it wont let me correct it!I will have to do a reboot to make it stop!! any suggestions?

---

### Post by warfacegod on 2010-05-23
> **TKleszynski said:**
> Yep I have been having problems!! Out of the blue now my Computer will just go to a flashing Black screen and it wont let me correct it!I will have to do a reboot to make it stop!! any suggestions?

Fresh install/start your own thread.:P

---

### Post by geeklove2rock on 2010-05-23
I didnt done that before but you can do it easy way:
You can easily upgrade over the network with the following procedure.

   1. Start System/Administration/Update Manager.
   2.

      Click the Check button to check for new updates.
   3.

      If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.
   4. A message will appear informing you of the availability of the new release.
   5.

      Click Upgrade.
   6. Follow the on-screen instructions.

and if you are going to do in a right way with required condition i dnt think dere is any problem in your way!!!!!!!!!
enjoy!!!!!!

---

### Post by moshuptrail on 2010-05-23
I upgraded 8.04 LTS as far as 9.10 and then got stuck.  9.10 would boot but the video would not work.  So I could not see anything.  Using an older kernel I could boot into recovery mode, but I did not know how to upgrade from the command line.  Question: Anyone know how to do an upgrade from the command line?

So I created a new partition and did a fresh install of 10.04.  Now I will need to re-add all the software I've collected.

However, because I keep /home in it's own partition, Ubuntu did a nice job retaining a lot of environment settings and things like that.

p.s.  I have a Dell 1525 laptop sold with Ubuntu 8.04 pre-installed by Dell.  Unfortunately Dell did not support the proprietary driver they packaged for the crappy i965 video module.  What a pain in the backside.  I will not do that again.

---

### Post by warfacegod on 2010-05-23
> **moshuptrail said:**
> I upgraded 8.04 LTS as far as 9.10 and then got stuck.  9.10 would boot but the video would not work.  So I could not see anything.  Using an older kernel I could boot into recovery mode, but I did not know how to upgrade from the command line.  Question: Anyone know how to do an upgrade from the command line?

So I created a new partition and did a fresh install of 10.04.  Now I will need to re-add all the software I've collected.

However, because I keep /home in it's own partition, Ubuntu did a nice job retaining a lot of environment settings and things like that.

p.s.  I have a Dell 1525 laptop sold with Ubuntu 8.04 pre-installed by Dell.  Unfortunately Dell did not support the proprietary driver they packaged for the crappy i965 video module.  What a pain in the backside.  I will not do that again.

I believe:

```
sudo apt-get update && upgrade
```

will do the trick.

I'd rather stuff a clutch of live, rabid squirrels into my mouth than use a Dell.

---


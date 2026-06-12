---
title: "why is firefox called namoroka and thunderbird called shredder"
date: 2010-05-01
forum: General Help
---

### Post by aaronp on 2010-05-01
Hi all,

It appears when I did a funny little partial upgrade thing a few days ago my Firefox became Namoroka and Thunderbird become Shredder.
I'm concerned that I'm using pre-release versions of these programs when I really want to be using the latest stable versions.

Can anyone tell me what's going on and how to fix it?

I upgraded to 10.04 today thinking this might resolve the issue but to no avail...

thanks
Aaron

---

### Post by scouser73 on 2010-05-01
As far as I know, Namoroka and Shredder are development releases for Firefox and Thunderbird meaning that you possibly do have pre-release software.

If you want to remove these and install the stable versions then please do the following.

**Instructions For Thunderbird.**

Copy & paste this into Terminal: **> sudo apt-get autoremove thunderbird**

Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3.01**[/COLOR]]("http://www.mozillamessaging.com/en-US/thunderbird/all.html")


**1** - Extract the **.tar.bz2** file

**2** - Enter **> gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

You will now have Thunderbird installed.

1 - Go to Synaptic Package Manager

2 - Enter [package name] into the search field

3 - Highlight the installed package

4 - Click on Package on the top row

5 - Select Lock Version

Done, now [package name] will no longer be updated.



**Instructions For Firefox**

Copy and paste this into Terminal: **> sudo apt-get autoremove firefox**

[[COLOR="Red"]**Download Firefox 3.6**[/COLOR]]("http://www.mozilla.com/en-US/firefox/all.html")

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **> gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

Enter these commands in Terminal

> **sudo -i**
Enter your password if asked
> **cd /opt**
> **chown -R username firefox**
[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

You will now have Firefox installed.

---

### Post by flopwich on 2010-05-25
Okay, that's twice the update to Ubuntu 10.1 has changed Firefox to Namoroka.  I deleted it once and installed Firefox, but now it's done it again.  Everything I've read says that's a pre-release version of Firefox.  Why does it keep doing this?  How do I stop it?  Uninstalling and reinstalling is enough of a pain that I'd like not to have to keep doing it.:confused:

---

### Post by dasy2k1 on 2010-05-25
Those names are nothing to do with stable and unstable versions.... they are merely the non branded fully FLOSS compatible versions

the ONLY difference is the name and icon...
you are free to use shredder and Namoroka however you want within the terms of the GPL

Firefox and Thunderbird ARE NOT free software you are not allowed to modify them and redistribute without extra conditions (you cant use the name or logo) 

Namroka and Shredder are free and fully meet the definition as given by debian
[http://www.debian.org/social_contract#guidelines](http://www.debian.org/social_contract#guidelines)

---

### Post by PerfectReign on 2010-05-26
> **dasy2k1 said:**
> 
Firefox and Thunderbird ARE NOT free software you are not allowed to modify them and redistribute without extra conditions (you cant use the name or logo) 

Namroka and Shredder are free and fully meet the definition as given by debian
[http://www.debian.org/social_contract#guidelines](http://www.debian.org/social_contract#guidelines)

Okay, that's just bizarre!

Here I am trying to figure out why the heck I have some wierded out browser. 

All because of some perceived license issue??  

Kind of reminds me of when the GNOME folks went off and screwed us all by creating GNOME because the Qt toolkit wasn't licensed "properly" enough for them.

---

### Post by flopwich on 2010-05-26
> **dasy2k1 said:**
> Those names are nothing to do with stable and unstable versions.... they are merely the non branded fully FLOSS compatible versions

the ONLY difference is the name and icon...
you are free to use shredder and Namoroka however you want within the terms of the GPL

Firefox and Thunderbird ARE NOT free software you are not allowed to modify them and redistribute without extra conditions (you cant use the name or logo) 

Namroka and Shredder are free and fully meet the definition as given by debian
[http://www.debian.org/social_contract#guidelines](http://www.debian.org/social_contract#guidelines)lo

Well, I'll look around and see if I can figure out what FLOSS is.  From this thread alone, it's a shame the folks switching Namoroka for Firefox don't, I don't know, TELL people what's going on.  You've got at least two people here who have been uninstalling and reinstalling because nobody bothered to let users know they're switching things out.  How exasperating.  I guess if you're not geek enough to know already, the folks doing it figure you have no need to know.  Ubuntu will never 'take over the world" until they understand that they have to give folks information once in a while.

Thank you for the information.  I appreciate it.  I'd spent a bunch of quality time with Google and on the Firefox site trying to answer the question.

---

### Post by PerfectReign on 2010-05-26
FLOSS == [I]free/libre/open source software.  IOTW, it is software that is OSS and free of licence issues.  Stallman likes this, and many GNU/Linux distributions like to keep things pure.

I don't mind except that:

1. No one mentioned that the mainline Firefox was being dropped.

2. Someone put "namroka" as the user agent string. That makes things FUBAR for several sites.

Wouldn't Ubuntu provide the "true" Firefox 3.x in the non OSS repository where they keep Acrobat?

(sigh)
[/I]

---

### Post by PerfectReign on 2010-05-26
By the way, here's what I spent several hours trying to figure out - [http://ubuntuforums.org/showthread.php?t=1493547](http://ubuntuforums.org/showthread.php?t=1493547)

Basically I downloaded User Agent Switcher and then the list of user agents. I set my user agent to Firefox 3.5 and sites work well again.

HTH!

---

### Post by jocko on 2010-05-26
> **PerfectReign said:**
> [I]Wouldn't Ubuntu provide the "true" Firefox 3.x in the non OSS repository where they keep Acrobat?

(sigh)
[/I]
The "true" firefox is still in the main repo, is still the default browser, and it's licence is still open enough to remain there. If you in some way have managed to replace it with the unbranded namoroka browser, it's because of something you yourself have done (intentionally or unintentionally).
Check that you have the package "firefox-branding" installed.

---

### Post by flopwich on 2010-05-29
> **jocko said:**
> The "true" firefox is still in the main repo, is still the default browser, and it's licence is still open enough to remain there. If you in some way have managed to replace it with the unbranded namoroka browser, it's because of something you yourself have done (intentionally or unintentionally).
Check that you have the package "firefox-branding" installed.

Um, I don't think so.  I'm a newbie to Linux and don't mess with anything I don't have to. I just want things to work.  Yes, I've messed with the Firefox installation now, but that's only *_after_* Namoroka appeared out of nowhere on its own as part of the installation of Ubunto 10.  All I did prior to that was to run the update manager and let it do its thing.  Namoroka appeared entirely on its own; no explanation, no warning, and it's put itself back again, similarly without telling me or explaining what's going on.

Could you help me out here and tell me where I'd find "firefox-branding" and how and what to do if it's not there?

Thanks.

---

### Post by elliotn on 2010-05-29
Check in SPM. Type firefox and all firefox related parkages will appear

---

### Post by flopwich on 2010-05-29
Thank you.  I've done that.  Firefox 3.6.3 is installed, but the firefox-branding refers to v3.5 with a number of packages referring to being "dummy" packages to ensure Firefox installs.  Maybe on the last update it reverted to Firefox again and I didn't keep up.  Sorry to have bothered all y'all.  I'll just leave quietly now, confused and mumbling to myself.

Thanks again.

---

### Post by flopwich on 2010-06-02
> **flopwich said:**
> Thank you.  I've done that.  Firefox 3.6.3 is installed, but the firefox-branding refers to v3.5 with a number of packages referring to being "dummy" packages to ensure Firefox installs.  Maybe on the last update it reverted to Firefox again and I didn't keep up.  Sorry to have bothered all y'all.  I'll just leave quietly now, confused and mumbling to myself.

Thanks again.

Only, guess what, Namoroka's back again, ..., some of the time.  Other times it comes up as Firefox.  I don't know what's going on.  I just installed Wireshark, (gods help me, I'm trying to figure out why, since the ugrade to Ubuntu v10 and Thunderbird 3.0 the latter will only work occasionally).  When I ran Wireshark the bar across the top of the screen showed the icon for Namoroka.  I don't even know where it got that, as I thought I'd hunted it down and deleted it.  Then I got on this forum, and now it shows the icon for Firefox.

At least I'm vindicated in that I didn't confuse easily:  Ubuntu, and/or Firefox or its alter ego Namoroka are playing some very strange games.

---

### Post by cryptotheslow on 2010-06-02
Can you tell us what is listed / checked in your Software Sources?

System > Administration > Software Sources....  what is checked on the Ubuntu Software tab and what is listed on the Other Software tab?

---

### Post by flopwich on 2010-06-02
> **cryptotheslow said:**
> Can you tell us what is listed / checked in your Software Sources?

System > Administration > Software Sources....  what is checked on the Ubuntu Software tab and what is listed on the Other Software tab?

Hm.  I used to have a screen-shot capture program on here, but I've apparently lost it in the upgrade to v10.

Under the Ubuntu Software tab it lists

Canonical supported open source software (main)
Community maintained open source software (universe)
Proprietary drivers for devices (restricted)
Software restricted by legal or copyright issues (multiverse)

Under the Other Software tab it lists

[http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) ubuntu partner
Medibuntu- Ubuntu 10.04 "lucid lynx" ([http://packages/medibuntu.org/](http://packages/medibuntu.org/) lucid free non-free)

That last one was the result of following advice in another forum on here in hopes of getting Thunderbird 3.0 to work again.

Do you need anything else?

Thanks.

---

### Post by cryptotheslow on 2010-06-02
No, nothing else needed... I just had a passing suspicion that you might  have a developmental / beta software repository in there that had  caused an update beyond the standard Ubuntu repositories. Seems not.

You have more patience than me... 4 weeks on I'd have given up, backed up and done a clean install :D

---

### Post by flopwich on 2010-06-02
> **cryptotheslow said:**
> No, nothing else needed... I just had a passing suspicion that you might  have a developmental / beta software repository in there that had  caused an update beyond the standard Ubuntu repositories. Seems not.

You have more patience than me... 4 weeks on I'd have given up, backed up and done a clean install :D

Well, to be honest, it hadn't occurred to me to try that.  I guess I sort of had in the back of my mind that the problems I'm having would just recur with a new install, but I think the time is here...I'm getting to the point of just giving up, so the nuclear option may be the best.

---

### Post by cryptotheslow on 2010-06-02
I was having a few niggly issues after upgrading from karmic to lucid and as I was buying a couple of new hard disks anyway I thought I'd try a clean install on one of those. I half expected the same issues to recur, but they didn't - everything just worked.

As I'd already upgraded to lucid on the old disk, it really was quite painless as I could just mount the old disk up and copy across the .whatever settings folders from my old home directory as I needed them.

Most people don't have the luxury of being able to simply unplug their old drive and plug a new one in to do a clean install - risking nothing essentially. It really is quite a nice approach to re-installing :D

The only problem I had was the old drive was IDE and the new one SATA - and with my motherboard I have no way configure ~which~ hard drive to boot from, so as soon as I reconnected the old IDE drive it would boot from that not the new install on the SATA drive. I just had to figure out how to amend the GRUB entry during bootup to make it boot the new install and all was well.

It took about half a day to do the install, get all my settings and files across and get everything looking and working how I like it. As a plus I gained a system that boots in 20 seconds not 2 minutes as the previous lucid / karmic upgrade did :D

It seems like it's going to be a lot of work before you start, but as long as you make sure you backup everything including the hidden folders in your home directory it really isn't.

---

### Post by TheDesertDragon on 2010-06-02
[https://wiki.mozilla.org/Firefox/Namoroka](https://wiki.mozilla.org/Firefox/Namoroka)

You've got the development release of 3.6. (which is basically older than the stable branch of 3.6)

No idea why this would happen, but I suppose you've got it resolved from the first post. Just do that every time you get the name of Firefox changed into a development name or even "Minefield".

---

### Post by flopwich on 2010-06-02
Silly question, I know, but I don't know how to uninstall this beast.  I have a dual-boot setup, with the hard drive partitioned to run Winders 7 and this.  I searched on the Ubuntu web site, and all it gave me was solutions for uninstalling it from Winders, but since Winders can't see the Ubuntu partition, it can't touch it.  A little help here?

---

### Post by TheDesertDragon on 2010-06-02
> **flopwich said:**
> Silly question, I know, but I don't know how to uninstall this beast.  I have a dual-boot setup, with the hard drive partitioned to run Winders 7 and this.  I searched on the Ubuntu web site, and all it gave me was solutions for uninstalling it from Winders, but since Winders can't see the Ubuntu partition, it can't touch it.  A little help here?

Your Windows can't delete the Linux partition? I would understand if it couldn't read it, but not see it? Mine could always see it. It shouldn't be in My Computer, but it should be in the partition manager.

Be careful when you delete the Linux partition though. You have to have either a Windows CD at the ready or you have to type 'mbrfix' (without the quotes) in a Windows command prompt before you remove it - otherwise you won't be able to boot again because GRUB has overwritten the Windows MBR and put it's data on the Linux partition (which is now gone).

---

### Post by cryptotheslow on 2010-06-02
What are you wanting to uninstall?

If you mean the entirety of the Ubuntu install (having backed up everything you need of course!) then grab a copy of the installer CD ISO from the ubuntu site and burn it to CD. Then boot from that and use GParted in System > Administration to delete the Ubuntu related partitions - you'll most likely have a minimum of two (/ and swap).

Careful how you go in there and be sure not to delete your windows partition!

---

### Post by flopwich on 2010-06-03
Ah, well, I thought I'd bricked it there.  It's a netbook, so I don't have a disk drive.  I have a flash drive set up to install Ubuntu v9.  I booted off that and deleted what I thought were Ubuntu partitions, but something got hosed.  I managed somehow, I'm not really sure how, to recover and can now boot to Winders 7 and Ubuntu v9.  And guess what?  I still have the problem with Evolution unable to connect to my ISP.  "No route to host".  Yet I can ping it just fine and Firefox is working fine.  The one benefit from the near-brick experience is that I do seem to have lost that Namoroka thing, at least so far.

---

### Post by flopwich on 2010-06-05
> **cryptotheslow said:**
> No, nothing else needed... I just had a passing suspicion that you might  have a developmental / beta software repository in there that had  caused an update beyond the standard Ubuntu repositories. Seems not.

You have more patience than me... 4 weeks on I'd have given up, backed up and done a clean install :D

Sure wish I'd thought of this sooner.  As I said before, I thought I'd bricked the thing for a while, but I got it working again, thanks to having a flash drive set up to boot and install Ubuntu v9.04.  After that I used update manager to update to v10.1.  This time, though, I allowed it to replace GRUB.  Last time I updated I didn't know what GRUB was or did and out of fear of the unknown I told the upgrade manager to to replace it.  This time I did and now Thunderbird and Evolution are working fine.  I suspect that somehow the v9 GRUB was not initializing the communications hardware properly for the way v10 works.

I could have saved a lot of hassle and time if only I'd done this a month ago.  Ah, well, next time I'll know better.

Thanks to all for your help.

---


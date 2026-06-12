---
title: "Upgrading to new version of Ubuntu"
date: 2012-04-29
forum: General Help
---

### Post by Wuxin on 2012-04-29
I am still using Ubuntu 10.10 and received word that there is no longer any LTS.  So I guess the thing to do is to upgrade to the latest version.  Okay...do I need to download the new version and burn it on an install disk, or can I upgrade directly through the "upgrade manager"?  I've heard some people say it's better to start with a clean install than to overlay on an earlier version(s).  What are the advantages one way or the other?  If I do a clean install--is it necessary to wipe my hard disk clean and start over?  I would be a bit reluctant to do that!  Does anyone have any suggestions?  Thanks in advance!

---

### Post by abyrne on 2012-04-29
If you're still on 10.10, then I would highly recommend a fresh install of 12.04. Distro Upgrades through Update Manager are notoriously buggy, and if your resulting system isn't broken, it will probably be slow as hell.

And yes, you will have to wipe the partition that Ubuntu is installed on in order to perform a fresh upgrade. _Backup_ is the magic word here.

The fresh upgrade process shouldn't take long, and remember you can always ask someone here at the Forums if you have any other issues.

Good Luck!

---

### Post by Wuxin on 2012-04-29
Okay this is good.  So I would download the new version--12.04--and burn that to a disk.
Then how do I uninstall my existing version of Ubuntu (10.10)?  I don't imagine I just drag
Ubuntu to the trash--there must be a more systematic way to uninstall so that the files are all wiped clean.  How do you do this?  And yes, I do have a backup drive that is up to date.  Will that play a part in the installation process?  You can perhaps understand my hesitation--I have a good system that has been performing great and I'm reluctant to dismantle it and put in something that might not work as well.

---

### Post by oboedad55 on 2012-04-29
> **Wuxin said:**
> Okay this is good.  So I would download the new version--12.04--and burn that to a disk.
Then how do I uninstall my existing version of Ubuntu (10.10)?  I don't imagine I just drag
Ubuntu to the trash--there must be a more systematic way to uninstall so that the files are all wiped clean.  How do you do this?  And yes, I do have a backup drive that is up to date.  Will that play a part in the installation process?  You can perhaps understand my hesitation--I have a good system that has been performing great and I'm reluctant to dismantle it and put in something that might not work as well.

Your new install will write over your current system. Do you have /home on a separate partition? If not, then you'll need to copy over any data you have from your external drive. I would suggest if you do a new install to make three partitions, /, /home, and swap. That way if things go wonky in the future you can reinstall and keep your data/settings.

---

### Post by pqwoerituytrueiwoq on 2012-04-29
just copy all your music/docs/pictures to a flash drive
don't forget your .mozilla folder (and .thunderbird if you use that)
then just pop in a install disk/usb and it will be really strait forward

if you are using 10.10 cause of you are one who does not like unity you may want to install xubuntu for lubuntu this time

---

### Post by Wuxin on 2012-04-29
Yes, I have been reluctant to switch from 10.10 because of Unity.  But isn't there a simple way that you can delete Unity (or at least stash it somewhere) and go to the original Ubuntu desktop?  I've heard that is an option.  Could I just take my home file and music files, etc., and drag them to my external drive until I install the new version?  Incidentally, I didn't partition my drive when I downloaded Ubuntu 10.10.  I only have Ubuntu on this computer, nothing else.  Why would I keep Windows??  My other computer, my desktop, is a Mac mini.  I will probably download the new Ubuntu program on that because it's much faster than my laptop.

---

### Post by 3rdalbum on 2012-04-30
You do NOT need to erase your hard drive to update to 12.04. The Ubuntu installer has an "Upgrade" option a couple of screens in. It does a fresh install but preserves your home directory (even if not in a different partition) and attempts to reinstall the software you had before.

So people, PLEASE stop telling others that fresh installing will cause data loss or that you need a seperate /home partition. It has not been true for years.

Also, I'd recommend giving Unity a week. Loads of people prefer Unity after giving it an honest try. It is different to Gnome 2 and not as tweakable, but very modern with some great features and thoughtful design. Many people love Unity.

---

### Post by Wuxin on 2012-04-30
Thank you, 3rdalbum for your advice on this.  I was frankly dreading the idea of a clean
install that involved erasing the hard drive.  (Of course sometimes when you renovate a home it's easier to take it "down to the bones" rather than try to do a retro around the existing structure.  Don't know if the analogy is an apt one...)  So I gather from what you say that you DON'T have to install all the successive versions of Ubuntu from 10.10 through to 12.4?
Can you be a bit more specific as to how you get to the "Upgrade" option you speak of, so that I can be certain I'm on the correct page?  Using this method, then, I take it there is no reason to DOWNLOAD the new 12.4 and then burn that to a disk as I did when I first installed Ubuntu?  If this works, I will be forever grateful!

I will give Unity a try as you suggest.  I am assuming that whatever bugs were present in its first incarnation have since been remedied.  Is that correct?  Thanks again.

---

### Post by Wuxin on 2012-04-30
Hmm.  I just went to the Ubuntu documentation page and they say there that the upgrade process does involve downloading and installing all prior versions, from 10.10 to 12.04.  Maybe I'm looking at the wrong thing.  They argue it takes considerable bandwidth and also that there's no assurance that the new version will work on my existing hardware.  (I use an IBM ThinkPad t43p which is known to be Linux friendly.)  Ubuntu seems to be pressing for downloading, burning to disk, and starting with a clean drive.  

What I gathered from 3rdalbum's entry was that a fresh install is possible--i.e., the system automatically takes out the existing version of Ubuntu and replaces it with the current one.  In other words, not the laborious process of adding one version on top of the other, in mud pie fashion!  If I'm not at the right page, if 3rdalbum could provide a link to it, that would be enormously helpful.  Thank you again!

---

### Post by forrestcupp on 2012-04-30
> **Wuxin said:**
> And yes, I do have a backup drive that is up to date.What type of backup do you have? If you just copied your important files to the external, then you're fine. But if it's a Clonezilla type backup, then you'll go through all the trouble of installing 12.04, restore your backup, and be right back to 10.10. ;)

> **3rdalbum said:**
> 
So people, PLEASE stop telling others that fresh installing will cause data loss or that you need a seperate /home partition. It has not been true for years.
It's still wise to have an up to date backup in case of human error when he chooses which method of installation to go with.

---

### Post by holycow131415 on 2012-04-30
> **3rdalbum said:**
> You do NOT need to erase your hard drive to update to 12.04. The Ubuntu installer has an "Upgrade" option a couple of screens in. It does a fresh install but preserves your home directory (even if not in a different partition) and attempts to reinstall the software you had before.

So people, PLEASE stop telling others that fresh installing will cause data loss or that you need a seperate /home partition. It has not been true for years.

Also, I'd recommend giving Unity a week. Loads of people prefer Unity after giving it an honest try. It is different to Gnome 2 and not as tweakable, but very modern with some great features and thoughtful design. Many people love Unity.

Any modification to your system may cause data loss so it is always smart to back up your stuff. Also, your home directory has more stuff than just your data. it has hidden conf files from programs and such, which might cause problems. Its always better to do a clean install period.

---

### Post by Wuxin on 2012-04-30
My backup is a total backup system that basically mirrors my internal hard drive.  But I can take my home file and drag that to the back-up drive as a separate file so that it's there intact.  So I'm still left feeling a bit confused here: My sense is that it is possible to do a system upgrade that would probably come out just fine, but there are advantages to performing a clean install.  Why is that?  

IF I decide to opt for a clean install, what has to be done in preparation?  Does 10.10 need to be uninstalled, or can I simply reformat the hard drive?  (Either prospect makes me shudder!)  The advantage to having an entire backup is that I can always get back to where I started from if worst comes to worst (which I doubt it will!).

---

### Post by forrestcupp on 2012-04-30
> **Wuxin said:**
> My backup is a total backup system that basically mirrors my internal hard drive.  But I can take my home file and drag that to the back-up drive as a separate file so that it's there intact.  So I'm still left feeling a bit confused here: My sense is that it is possible to do a system upgrade that would probably come out just fine, but there are advantages to performing a clean install.  Why is that?  Once upon a time, upgrades weren't as reliable as they are now and sometimes problems would come out of them. Even now, I've seen people have problems from upgrading that they didn't have when they did a clean install. But I definitely wouldn't want to risk upgrading from a version that old, even if it is the last LTS. What we're talking about now is doing a clean install from the LiveCD and choosing the option to save your settings. If it doesn't work like it's supposed to, you can just copy your /home folder back over from your backup. You wouldn't want to completely restore your whole cloned backup, unless 12.04 just isn't working out for you. Personally, I wouldn't even copy the whole /home folder. I'd only copy the important files I need so that all the old configuration files won't mess with the new system.

> **Wuxin said:**
> IF I decide to opt for a clean install, what has to be done in preparation?  Does 10.10 need to be uninstalled, or can I simply reformat the hard drive?  (Either prospect makes me shudder!)  The advantage to having an entire backup is that I can always get back to where I started from if worst comes to worst (which I doubt it will!).You don't have to do anything to prepare, other than backup your important stuff. The installation will automatically take care of formatting your drive and getting rid of the old version.

---

### Post by Wuxin on 2012-04-30
Great!  I appreciate your very complete answer Forrestcupp!  So all I've got to do is create the Live CD and then select the option to save my settings.  With any luck, this should do it. 
One other thing: When I install the new 12.04--do I then need to erase the clone of 10.10 that's on my back up drive?  Or the next time I do a back up, will it just transfer the new version onto the backup drive?  I appreciate all these very informed and generous answers from everyone.

---

### Post by deserthowler on 2012-05-01
I've upgraded since 9.10 with no problems.  I use a salvaged Dell 4600 desktop, a Thinkpad T60, and a Dell Inspiron 1420 N.  There have been no problems with upgrades.

Back up your data.
Burn a copy of 12.04 iso.

Do the upgrades 10.10 ==> 11.04 ==> 11.10 ==> 12.04.  If it works ... fine.  If it doesn't work do the fresh install of 12.04.  All you will have invested is some time and you will get to experience what an upgrade is about.  If an upgrede fails [COLOR="Red"]"All of your babies will be born naked"[/COLOR] but there will probably be no lasting effects.  :)

Unity works OK.  It takes some getting used to.  It's not really as terrible as many say.  I started with Ubuntu at 4.10 and had no trouble changing.

Earl

---

### Post by forrestcupp on 2012-05-01
> **Wuxin said:**
> 
One other thing: When I install the new 12.04--do I then need to erase the clone of 10.10 that's on my back up drive?  Or the next time I do a back up, will it just transfer the new version onto the backup drive?  I appreciate all these very informed and generous answers from everyone.

If you're doing a clone type backup, you need to take a little while to get everything set up and make sure *everything* is working how you need it to with no problems before you replace your backup. I wouldn't want to replace the old backup and find out something isn't going to work, and not be able to go back. As far as how you go about doing that, it all depends on what backup software you're using.

---


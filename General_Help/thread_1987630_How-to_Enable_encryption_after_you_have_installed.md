---
title: "How-to: Enable encryption after you have installed"
date: 2012-05-26
forum: General Help
---

### Post by Paddy Landau on 2012-05-26
[SIZE=4][COLOR=Red]IMPORTANT[/COLOR][/SIZE]

**This thread has been moved to the [Community Wiki]("https://help.ubuntu.com/community/PostInstallationEncryption"). I shall no longer update this thread (although you are welcome to post queries here); I shall update the Wiki instead.**

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?p=12062071#post12062071](http://ubuntuforums.org/showthread.php?p=12062071#post12062071)

Thread closed.

__________________________________________________

Normally, if you want to have encrypted data (a.k.a. an encrypted home folder), you specify this when you install or when you create a new user.

But what happens if you decide only afterwards that you want to encrypt your data?

Here is how to do so. This will encrypt a single user; if you wish to encrypt every user, you need to repeat the how-to for each one.
__________________________________________________

[SIZE=4][COLOR=Red]DISCLAIMERS & WARNINGS[/COLOR][/SIZE]

[LIST]
[*]I tested this on **Ubuntu Precise 12.04**. I do not know whether or not it will work on other distributions.
[/LIST]

[LIST]
[*]Enabling encryption will disable hibernation &#8212; but you can re-enable it afterwards by following the thread explaining [how to enable hibernation with encryption]("http://ubuntuforums.org/showthread.php?t=1986821").
[/LIST]

[LIST]
[*]You may want to [print this post]("http://ubuntuforums.org/printthread.php?t=1987630") in case it doesn't work, so you can recover ([COLOR=Red]Test your New Login; and Finalise[/COLOR], below).
[/LIST]
__________________________________________________

[SIZE=4][COLOR=Red]PREPARATION[/COLOR][/SIZE]

[LIST=1]
[*]Check your **wallpaper**. Due to [an existing bug]("https://bugs.launchpad.net/ubuntu-tweak/+bug/888186"), you will be unable to log in with encrypted folders if your wallpaper is in an encrypted area. So, either:
[LIST]
[*]Change your wallpaper to one of the standard ones; or
[*]Move your wallpaper to [FONT=Lucida Console]/usr/share/backgrounds[/FONT] and then set your wallpaper to it over there.
[/LIST]
 
[*]This procedure is safe as it creates an encrypted copy of your folder, which means **you need sufficient space** on your drive to duplicate everything you have! If you don't, you need to **back up** your big data (e.g. movies); **delete** that data; run through this how-to; and **restore** your deleted data. (Having said that, I always recommend a **full backup** anyway in case of unexpected problems.)
[*]This process uses the **Terminal** and the **Recovery Mode**. If you don't know how to use them, please find out before proceeding.
[*]Install **ecryptfs-utils**. You may use Ubuntu Software Centre or, if you  prefer, your favourite package manager, or enter the command:```
[COLOR=Blue]sudo apt-get install ecryptfs-utils[/COLOR]
```
[/LIST]
__________________________________________________

[SIZE=4][COLOR=Red]HOW TO ENCRYPT YOUR FOLDER[/COLOR][/SIZE]

In this how-to, I've used my user name *paddy*. Please replace it with your user name.

[LIST=1]
[*]Reboot into Recovery Mode.
[*]Drop to root shell prompt.
[*]Fix existing 12.04 bugs as follows:```
[COLOR=Blue]mount --options remount,rw /[/COLOR]
[COLOR=Blue]mount --all[/COLOR]
```
[*]Encrypt your folder. It prompts you for your password, runs, then gives you some warnings. I'll talk about the warnings in the next step.```
[COLOR=Blue]ecryptfs-migrate-home --user *paddy*[/COLOR]
```
[*]In the warnings, note the name of the temporary folder that is shown on your screen. It will look something like [FONT=Lucida Console]/home/paddy.ChPzzxqD[/FONT]. The last 8 characters will be random; we will call these eight characters your ***random characters***.
[*]Ignore the rest of the warnings.
[*]Reboot with the following command (it may take several seconds to get going; be patient).```
[COLOR=Blue]reboot now[/COLOR]
```
[/LIST]
__________________________________________________


[SIZE=4][COLOR=Red]TEST YOUR NEW LOGIN; AND FINALISE[/COLOR][/SIZE]

Log in normally. Check that everything seems to work properly.

Did it work?

[LIST]
[*]Yes, it worked:
[LIST=1]
[*]Open a terminal and enter the following command. Replace my random characters with yours (as noted in [COLOR=Red]How to Encrypt Your Folder[/COLOR] above, step 5).```
[COLOR=Blue]sudo rm -R /home/*paddy.ChPzzxqD*[/COLOR]
```
[*]Restore any data, if you deleted some to make space ([COLOR=Red]Preparation[/COLOR] above, step 2).
[*]Set up encrypted swap space, as follows. Note: This step needs to be done only once; if you already have an encrypted user, you can skip this step.```
[COLOR=Blue]sudo ecryptfs-setup-swap[/COLOR]
```
[*]Reboot.
[/LIST]
 
[/LIST]

[LIST]
[*]No, it didn't work:
[LIST=1]
[*]Repeat  [COLOR=Red]How to Encrypt Your Folder[/COLOR] above, steps 1-3.
[*]Check that your random-name folder really is there with the following command; you should **not** see an error:```
[COLOR=Blue]ls -l /home/*paddy.ChPzzxqD*[/COLOR]
```
[*]Type the following commands. Ensure you replace *paddy* and the random characters.```
[COLOR=Blue]cd /home
rm -R  *paddy*  .ecryptfs/*paddy*
mv  *paddy.ChPzzxqD*  *paddy*[/COLOR]
```
[*]Reboot.```
[COLOR=Blue]reboot now[/COLOR]
```
[*]Restore any data, if you deleted some to make space ([COLOR=Red]Preparation[/COLOR] above, step 2).
[/LIST]
 
[/LIST]

---

### Post by kevdog on 2012-05-26
This thread is awesome, however I dont believe it belongs in the General Help section.

---

### Post by Paddy Landau on 2012-05-26
> **kevdog said:**
> This thread is awesome, however I dont believe it belongs in the General Help section.
Thank you.

Where would the thread belong? Perhaps a moderator can move it to the right place.

---

### Post by nothingspecial on 2012-06-29
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/PostInstallationEncryption](https://help.ubuntu.com/community/PostInstallationEncryption)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?t=2012410](http://ubuntuforums.org/showthread.php?t=2012410)


Support threads regarding the wiki and it's content should be created in a suitable forum.

---


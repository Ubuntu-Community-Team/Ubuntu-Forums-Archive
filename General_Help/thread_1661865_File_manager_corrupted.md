---
title: "File manager corrupted?"
date: 2011-01-07
forum: General Help
---

### Post by Kimenyi on 2011-01-07
Hello

I'm new to Ubuntu and moved to to the OS in late October last year. I'm therefore running 10.10 and have had no experience with any other versions of the OS. I'm running all the default programs except for the mail manager (I run Thunderbird) and now, the file manager (the reason for this post).

Everything was running fine until early December 2010. Then, my file manager started acting up. Whenever my computer boots up, the file manager starts running overtime. I get an icon labelled, "Opening File Manager", and this runs repeatedly for approximately 15 mins. After this, the different instances of the "Opening File Manager" would close one-at-a-time and disappear altogether. I still hear my machine working hard in the background (fan), and it would get very hot (and the fan runs continuously). When this is happening, I can't see any of the files or folders on my desktop. Opening the file manager to access files prompts the same sequence of events ("Opening File Manager" repeatedly) to recur.

If I reboot the machine (or log-off), after the machine asks if I really want to close all programs, I get a message saying that the file manager is still running and asking if I want to wait for it to respond. I always decline this and reboot (or shut-down). When I restart, the same thing happens all over again.

I tried changing the default file manager from Nautilus to PCManFM (using Ubuntu Tweak), and when I logged in again, despite PCManFM being the default file manager) the same thing has happened. I will try to change to Thunar as the default file manager, but I have little faith at the moment.

One strange thing that happened is that over the holiday break, I didn't use my machine much. This was before I had switched from Nautilus to PCManFM. The instances of "Opening File Manager" would begin, but stop in a few minutes and I would be able to see all the files on my desktop.

If anyone has a solution to my problem, please reply to this post. Thank you in advance.

---

### Post by Bucky Ball on 2011-01-07
Try 10.04 LTS. You will get a longer support time and a smoother ride for a newcomer. ;)

Unless you want in the deep end and expect to do some tweaking. The updates for 10.10 are causing a few headaches at the moment as well. 2.6.35-24 kernel is the culprit so think twice and do some research if you are going to update your kernel to it. 

If you are using it now, could be your issue. Try booting the last kernel; 2.6.35-22 or 23. It should be there on the list at boot. Do you get the same issue?

10.04 LTS might be your best bet for now though, either way. The latest is NOT always the greatest. Back up anything you don't want to lose before installing. ;)

Welcome to the forums, Ubuntu, and the learning curve. Enjoy!

---

### Post by Kimenyi on 2011-01-07
Thanks for the quick response @BuckyBall. I have a newbie-type question...

How do I boot to a previous kernel from memory?

---

### Post by Bucky Ball on 2011-01-07
Just boot up your machine. If you are not looking at a selection of kernels and it just boots into the regular one then restart and right after it boots, start pressing escape key. That should get you to a list of Ubuntu kernels (and show any other operating systems your running). First you will have the current kernel and its recovery kernel below it.

Third on the list below that you should have the last kernel (click that one) followed by its recovery kernel. ;)

---

### Post by Kimenyi on 2011-01-07
Thanks again. I'll try that and let you know if it works.

Nano Nano

---

### Post by Kimenyi on 2011-01-07
Hi @BuckyBall

No luck. I tried hitting Esc as the machine was booting up several times, but had no luck. The problem has recurred and is happening again. Is there another way of booting up from an earlier kernel?

---

### Post by Bucky Ball on 2011-01-07
I know you're a bit green with Ubuntu, but this is fairly easy and will guarantee you get a menu at boot. Plus you'll learn how to change whether you get a grub list or not and for how long. ;)

Open a teminal (Applications->Accessories->Terminal) and type (safer to copy and paste):

```
nano /etc/default/grub
```Look in there for a line that looks like this:

```
GRUB_TIMEOUT=0
```You are going to want to change that to:

```
GRUB_TIMEOUT=10
```When you are confident you know what you are doing, hit control+x to exit the file and you will be back at the cursor in the terminal. Type or copy and paste:

```
sudo nano /etc/default/grub
```Sudo makes you root user so you can make changes to the file. Now change that line - and **NOTHING** else - to:

```
GRUB_TIMEOUT=10
```Hit control+x, then 'y' (you'll be instructed on the line at the bottom).

Reboot the machine and you should see the menu. Choose the third one down. ;)

---

### Post by Kimenyi on 2011-01-07
@BuckyBall

I'll try that fix when I get back. I have to excuse myself as the wifey needs to leave the house. I will log in again and hopefully be able to go back to a previous kernel. Thanks again and I'll keep you informed.

---

### Post by mikewhatever on 2011-01-07
Last time I checked, the Esc key for showing the menu was changed to Shift in grub2. Press and hold the Shift key after the BIOS screen, and you should see the menu in a second.

I wonder if the file manager problem is user related. Kimenyi, can you try adding another admin user to your system (System->Administration->Users and Groups), and then logging in with that user's credentials. If running as a new user fixes the problem, then something must be messed up with the initial user's settings, but it's not a system wide problem. If that's the case, you really don't need to reinstall.

Every release has its share of bugs, LTS's included.

---

### Post by Bucky Ball on 2011-01-07
> **mikewhatever said:**
> Last time I checked, the Esc key for showing the menu was changed to Shift in grub2. Press and hold the Shift key after the BIOS screen, and you should see the menu in a second.

Cheers for that info. ;)

> **mikewhatever said:**
> Every release has its share of bugs, LTS's included.

Yes, but the 2.6.35-24 kernel has known issues on some machines at the moment; eg breaking Broadcom card config, Ubiquity installer wiping Windows when attempting a dual-boot, side by side install, and numerous other oddities. Not on ALL machines (I am using it problem free) but there are numerous threads and bug reports about. 10.04 LTS has been about since April and is stabler for the most part. ;)

I was going to suggest booting from the LiveCD and seeing if you get the same issues. This probably would have proved the same point as mikewhatever's suggestion; problem with the user config/settings.

---

### Post by Kimenyi on 2011-01-08
> **mikewhatever said:**
> Last time I checked, the Esc key for showing the menu was changed to Shift in grub2. Press and hold the Shift key after the BIOS screen, and you should see the menu in a second.

I wonder if the file manager problem is user related. Kimenyi, can you try adding another admin user to your system (System->Administration->Users and Groups), and then logging in with that user's credentials. If running as a new user fixes the problem, then something must be messed up with the initial user's settings, but it's not a system wide problem. If that's the case, you really don't need to reinstall.

Every release has its share of bugs, LTS's included.
@mikewhatever

Logging in with a different profile doesn't render the same problem. From what you suggested, then it must be a problem with my specific user account.

I can use the new account, but I will need to migrate all my data to it. So here's another newbie-type question: how can I migrate all my data to the new user profile (hopefully in a non-techie type method - if there's a program that can do this, I would prefer installing and using that). I've backed up all my files (using both SpiderOak and Ubuntu One -- I originally used Spider Oak when I used to use Mr Gates' OS, and discovered that Ubuntu One is integrated so started using it...). However, I don't know how to move ALL my mail messages and folders in all my email accounts across. I'm using Thunderbird. Any suggestions? And should I continue with Thunderbird or switch to the Ubuntu default Evolution?

---

### Post by mikewhatever on 2011-01-08
Try moving your Thunderbird profile from the old home folder to the new one.
[http://email.about.com/od/mozillathunderbirdtips/qt/et_move_profile.htm](http://email.about.com/od/mozillathunderbirdtips/qt/et_move_profile.htm)

All you messages and email settings should be in the .thunderbird folder. All these .somthing folders are hidden by default, but you have make them visible in the file browser by pressing Ctrl+h.
To copy the .thunderbird folder:
login with your new user,
navigate to /home/old-username,
hit Ctrl+h to show the hidden stuff,
find the .thunderbird folder and copy it to your new home folder.

If you like Thunderbird, keep using it, I don't see why not.

---

### Post by Kimenyi on 2011-01-09
!

---

### Post by Kimenyi on 2011-01-09
> **mikewhatever said:**
> Try moving your Thunderbird profile from the old home folder to the new one.
[http://email.about.com/od/mozillathunderbirdtips/qt/et_move_profile.htm](http://email.about.com/od/mozillathunderbirdtips/qt/et_move_profile.htm)

All you messages and email settings should be in the .thunderbird folder. All these .somthing folders are hidden by default, but you have make them visible in the file browser by pressing Ctrl+h.
To copy the .thunderbird folder:
login with your new user,
navigate to /home/old-username,
hit Ctrl+h to show the hidden stuff,
find the .thunderbird folder and copy it to your new home folder.

If you like Thunderbird, keep using it, I don't see why not.
Hi @mikewhatever

Thanks for the assistance. I managed to rename the profile and even move it and change the profile location so that I could still use it in Thunderbird without any loss of data. However, I wasn't able to copy the new profile when logged in to the new account. I get a message saying that I don't have permissions to do so.

Should I copy it onto an external drive in the old profile and then copy it back into the new profile? Or is there a simpler method?

---

### Post by mikewhatever on 2011-01-09
I don't understand, if you were able to rename and move the Thunderbird profile, why copy it? What exactly are you trying to copy?

---

### Post by Kimenyi on 2011-01-10
Hi

I was trying to move it from the old profile into the new profile. I can move and copy files within folders in the old profile, but I can't move or copy files from my old profile to my new profile, or log into the new profile and copy files from my old profile to my new one.

---

### Post by mikewhatever on 2011-01-10
Right, I see. If I understand correctly, you are trying to move .thunderbird from the old profile to the new one. User profiles are isolated from each other by permissions, and the .thunderbird folder must be locked out for other users. Try the following commands when logged in with the new user:

```
sudo cp -r /home/old-user/.thunderbird ~/.thunderbird

sudo chown -R $USER:$USER .thunderbird
```

The first command will copy the .thunderbird folder. Make sure you replace 'old-user' with your old username. The second one will give the ownership to the new user.

---

### Post by Kimenyi on 2011-01-10
Thanks -- in the second line, does the $USER;$USER need to be written as is, or should I replace those with the new user-name / old user-name or some other combination?

---

### Post by Bucky Ball on 2011-01-10
As is.

---

### Post by mikewhatever on 2011-01-10
> **Kimenyi said:**
> Thanks -- in the second line, does the $USER;$USER need to be written as is, or should I replace those with the new user-name / old user-name or some other combination?

As is, just make sure you are logged in as the new user. Replacing them with the new username would also work.

---

### Post by Kimenyi on 2011-01-11
@mikewhatever and @Bucky Ball

I would like to thank you for all your assistance. I have successfully migrated to a new problem free profile that so far has been working well. This would not have been possible without you. Once again, many thanks for all your help.

---

### Post by Bucky Ball on 2011-01-11
Great news and you're welcome. I didn't do a lot, mikewhatever da man! ;)

---

### Post by mikewhatever on 2011-01-13
Most welcome.:KS

---

### Post by Sam234 on 2012-05-09
I had exactly the same issue!

I have Ubuntu 10.10 with dual monitors on a nvidia card, all was fine till I changed the nvidia configuration to 'Separate X-Screen' so I could configure each screen separately, having set to 'Separate X-Screen' and re-booted I got this issue, returning to 'TwinView' mode removed the problem.

Hopefully that will help anyone attempting to de-bug this annoying issue. :(

---

### Post by oldos2er on 2012-05-09
Old thread closed.

---


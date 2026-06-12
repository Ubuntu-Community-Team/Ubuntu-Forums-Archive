---
title: "Desktop environment freezes during load after kernel update"
date: 2011-01-27
forum: General Help
---

### Post by n125 on 2011-01-27
Hello,

This morning I noticed that there was an update to the kernel ready in the Update Manager, to version 2.6.35-25. I let Update Manager do its thing and I restarted my computer when it prompted me to.

If I select 2.6.35-25-generic in Grub, Ubuntu boots just fine, all the way to the login screen. However, after entering my password, it looks like Gnome is going to load, but it never does. All I see is the default wallpaper and nothing else; the system locks up and does not respond to any input; and the fans start spinning at full-speed. My only option at this point is to do a hard shutdown. I have no problems if I select the kernel I was using previously: 2.6.35-24-generic.

Does anybody know what could have gone wrong or how I could fix this?


Thanks for reading!

---

### Post by n125 on 2011-01-27
Just messing around with a few things..

-Selecting 2.6.35-25-generic (Recovery Mode) from Grub, and subsequently, the resume normal boot option, lets me log in and presents me with a Terminal prompt.

-I can fully load the Gnome desktop environment under 2.6.35-25-generic using Ubuntu Desktop Edition (Safe Mode).

-I tried reinstalling linux-image-2.6.35-25-generic from Synaptic by clicking on the green square next to it and selecting Mark for Reinstallation. No difference.

I'm getting the impression that this problem is somehow related to Gnome rather than today's kernel update, but I really wouldn't know for sure..

Any ideas?

---

### Post by Krytarik on 2011-01-27
It's most probably an issue with the video driver. What video card/chip is installed, what driver do you run, how did you install it?

---

### Post by n125 on 2011-01-28
> **Krytarik said:**
> It's most probably an issue with the video driver. What video card/chip is installed, what driver do you run, how did you install it?

Thanks for the reply.

lspci | grep VGA says that it's a Mobile 945GME Express Integrated Graphics Controller (rev 03) by Intel. The video driver is i915. The system is an Asus 1005HA EeePC netbook, and everything just worked when I installed Ubuntu on it over a year ago, so I never had to explicitly install a video driver.

I think I remember installing an xorg update a few days ago as well; not sure if that might have anything to do with the cause of this problem.

---

### Post by Krytarik on 2011-01-28
What version of Ubuntu do you run then, on that machine?

---

### Post by n125 on 2011-01-28
Just the standard 32-bit 10.10 desktop edition.

---

### Post by Krytarik on 2011-01-28
> **n125]I installed Ubuntu on it over a year ago[/QUOTE]
[QUOTE=n125 said:**
> Just the standard 32-bit 10.10 desktop edition.
That contradicts somehow, don't confuse me! ;-)
[http://hellboundbloggers.com/2010/10/10/ubuntu-10-10-released/](http://hellboundbloggers.com/2010/10/10/ubuntu-10-10-released/)

Anyways, if you indeed run 10.10, try upgrading to the driver package provided by Ubuntu-X-Swat:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by n125 on 2011-01-28
> **Krytarik said:**
> That contradicts somehow, don't confuse me! ;-)
[http://hellboundbloggers.com/2010/10/10/ubuntu-10-10-released/](http://hellboundbloggers.com/2010/10/10/ubuntu-10-10-released/)

Anyways, if you indeed run 10.10, try upgrading to the driver package provided by Ubuntu-X-Swat:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

Haha. :wink: I started with the 9.04 or 9.10 distro (can no longer remember which) over a year ago and upgraded my way to 10.10 as time went on.

I added the repository but I will hold off on upgrading the driver package until later today when I have time to tinker around again.

Thanks again for the suggestion.

---

### Post by n125 on 2011-01-29
I finally had the time to upgrade the drivers and unfortunately the issue still persists. :(

---

### Post by Krytarik on 2011-01-30
After the issue occured, please attach "/var/log/Xorg.0.log", "/var/log/Xorg.0.log.old" and "~/.xsession-errors".

---

### Post by n125 on 2011-01-30
Alright. I booted into 2.6.35-25 to test the drivers and then back into 2.6.35-24 so that I could continue working, so hopefully Xorg.0.log and Xorg.0.log.old captured the correct information.

Another 10.10 laptop user, albeit with different hardware, reported the same problem today as well--[http://ubuntuforums.org/showthread.php?t=1677565](http://ubuntuforums.org/showthread.php?t=1677565)

---

### Post by Krytarik on 2011-01-30
The Xorg.log's neither contain crucial error messages nor are they significant different.
But .xsession-errors contains numerous error messages regarding the "Orta" theme. If you are using that theme currently, which should not be possible, then please switch to the default "Ambiance" theme and boot again with the new kernel.

---

### Post by n125 on 2011-01-30
Unfortunately that yielded no results. :(

I have attached a new xsession-errors log created after changing to Ambiance, booting into 2.6.35-25 and freezing, and booting back into 2.6.35-24.

---

### Post by Krytarik on 2011-01-30
Unrelated: You should fix this by removing the respective directory in "~/.gconf/apps/panel/objects".
> Unable to open desktop file /usr/share/applications/openoffice.org-writer.desktop for panel launcher: No such file or directory
Please make sure that you really have the latest updates:
```
sudo apt-get update
sudo apt-get upgrade
```
Then try again.

If that fails again, try those, each at a time:
- disable "Update Notifier" in "Startup Applications", since it is mentioned in each log
- set "Visual Effects" to "None" in "Appearance", effectively disabling Compiz

---

### Post by n125 on 2011-01-30
> **Krytarik said:**
> Unrelated: You should fix this by removing the respective directory in "~/.gconf/apps/panel/objects".

Ah thanks, I was wondering how to get rid of that. Artifact from the move to LibreOffice.:)

> 
Please make sure that you really have the latest updates:
```
sudo apt-get update
sudo apt-get upgrade
```Then try again.Yeah, for sure I have the latest updates. There are none available to download.

> 
If that fails again, try those, each at a time:
- disable "Update Notifier" in "Startup Applications", since it is mentioned in each log
- set "Visual Effects" to "None" in "Appearance", effectively disabling CompizIt felt like it took a while longer for my touchpad/cursor to freeze after disabling the Update Notifier, but the outcome was the same. :(

New xsession_errors log. (This was made after disabling Update Notifier, since I tried the Visual Effects test earlier yesterday.)

---

### Post by Krytarik on 2011-01-30
It seems more and more likely that there is some kind of incompatibility between the new kernel and the intel video driver. At this point I have only two options left to offer:

- create a new user and try to log in with those
- stick with the old kernel until the next upgrade

---

### Post by n125 on 2011-01-30
Updated my BIOS (2 years out of date!) as suggested in the other thread made by the poster with the same issue--no luck. It might be me, but Ubuntu seems a bit snappier now though. 

Is there a way to completely delete a new user if I were to try that option?

I suppose I can wait for 2.6.35-26, or whatever the next kernel will be, since 2.6.35-24 works fine. I'm just worried that this issue will continue on to future kernel versions.

Is there a place I could try submitting a bug report? (Though I really wouldn't know what to write since I've never submitted one of those before. :eek: )

---

### Post by tvphil on 2011-01-30
I think there is a bigger issue with this kernel. I have the exact same problem with the ZaReason Strata 9660 laptop using an ATI Mobility HD graphics card. For this reason, I don't think it's a driver issue, but an Xorg.conf issue. I haven't found a solution either, but I'm working on it.

---

### Post by Krytarik on 2011-01-30
> **n125 said:**
> 
Is there a way to completely delete a new user if I were to try that option?

Sure, add it via "System -> Administration -> Users & Groups", and right there you can also delete it after that, it may be necessary to remove "/home/NEWUSER" manually.
> **n125 said:**
> 
I suppose I can wait for 2.6.35-26, or whatever the next kernel will be, since 2.6.35-24 works fine. I'm just worried that this issue will continue on to future kernel versions.

That is indeed possible, but I wouldn't paint it black before the next kernel is out.
> **n125 said:**
> 
Is there a place I could try submitting a bug report? (Though I really wouldn't know what to write since I've never submitted one of those before. :eek: )
"launchpad.net" is the place to file bug reports. Here is guide about how to report kernel bugs:
[https://wiki.ubuntu.com/KernelTeam/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeam/KernelTeamBugPolicies)

Here is a more comprehensive guide on how to report bugs, also applyable to the intel video driver:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

This is the launchpad site of the intel video driver:
[https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel](https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel)

If you want to try to fix this issue by setting up a "xorg.conf", follow this guide:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by n125 on 2011-01-31
> **Krytarik said:**
> Sure, add it via "System -> Administration -> Users & Groups", and right there you can also delete it after that, it may be necessary to remove "/home/NEWUSER" manually.

Success. :D I created an account with "Desktop user" privileges and managed to log in successfully under 2.6.35-25. Now the big question is "why?". I can't say I've done anything too crazy in terms of customization and tweaking under my regular account, but there has to be something that's causing the loading to trip up. If I can log in with a new account, or in Recovery Mode and Safe Mode with my regular account, then that would indicate that the video driver and new kernel are functioning correctly, wouldn't it?

I have attached the xsession-errors created by the new account.

---

### Post by Krytarik on 2011-01-31
> **n125 said:**
> If I can log in with a new account, or in Recovery Mode and Safe Mode with my regular account, then that would indicate that the video driver and new kernel are functioning correctly, wouldn't it?

Exactly.

Here is one difference between the log of your own user and the new user, I didn't notice it upon comparing with my own .xsession-errors:

the new user:
```
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
```I have exact the same line in my .xsession-errors.

your own user:
```
Start IM through /home/anthony/.xinput.d/en_CA linked to /etc/X11/xinit/xinput.d/none.
```Try renaming the directory ".xinput.d" in your home directory. I don't have such a directory.

---

### Post by n125 on 2011-01-31
Last night I renamed ".xinput.d" to "old.xinput.d", rebooted into 2.6.35-25, and it froze. After booting back into 2.6.35-24, I checked my Home directory and saw that ".xinput.d" was not recreated or anything. The directory just contains symbolic links to "en_CA" and "en_CA.backup". There are no hidden files in it.

I then checked the xsession-errors log and saw that the line you quoted changed to

```
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
```So just now I decided to change the theme back to Ambiance and the wallpaper to the default one (I had changed back to Orta after reply #17) and boot into 2.6.35-25. I first logged into Safe Mode, which loaded normally as expected. I made a backup of xsession-errors and decided to try the regular desktop session.

The desktop loaded normally. :KS

I made a backup of xsession-errors again, turned Orta back on, and relogged. Again, success. :KS Then I set my wallpaper back to what it was before, relogged, and could load the desktop as well. :KS Not that I'd expect the wallpaper to be an issue, though.

I'm still not sure if ".xinput.d" was the culprit because the computer did freeze when attempting to log into 2.6.35-25 immediately after renaming the folder, as I mentioned in the first paragraph. I haven't made any changes between logging back into 2.6.35-24 and now. So I'm not really sure what it could be.

But I guess that's case solved. Thank you for all of your help; I really appreciate it!

EDIT: Unfortunately I spoke too soon. After writing this post I put my computer into standby and resumed it a while later with no problems. When I finished, I put it back into standby again. When I resumed later, I found that it was frozen at the "input password to unlock" screen. Now I'm back at square one. Repeating the exact same procedure I used to successfully boot into 2.6.35-25 earlier yields no results. :(

---

### Post by Krytarik on 2011-01-31
However, these are some encouraging steps forward.

I want to check the result of the following steps:
- log in with the old kernel
- do nothing in that session
- reboot with the new kernel
- login again

---

### Post by n125 on 2011-02-01
No luck.

I also tried

-Log into old kernel and do nothing.
-Reboot into new kernel, log into Safe Mode, and do nothing.
-Log out and log into a normal session.

Both tests were done in Ambiance with default 10.10 wallpaper.

The above steps are essentially the same as the ones I took to successfully into a normal session under the new kernel earlier today. I was also on battery power that time, but I ruled that variable out earlier  by trying to log in under both A/C and battery.

And just now, before attempting to log in under 2.6.35-25, I hit ctrl+alt+F1 to switch everything to text to see if an error would come up, and none did. I'm guessing this is the same as Recovery Mode.

EDIT: I wonder if this wouldn't hurt to try? [http://ubuntuforums.org/showthread.php?t=381376](http://ubuntuforums.org/showthread.php?t=381376) It's perfectly safe to delete anything in /tmp, right?

---

### Post by Krytarik on 2011-02-01
> **n125 said:**
> 
EDIT: I wonder if this wouldn't hurt to try? [http://ubuntuforums.org/showthread.php?t=381376](http://ubuntuforums.org/showthread.php?t=381376) It's perfectly safe to delete anything in /tmp, right?
Yes, I would say so. But it makes no real sense.

Try instead to remove the file "~/.gconfd/saved_state". Logout and do it at the console.

---

### Post by bilallucky on 2011-02-01
I can fully load the Gnome desktop environment under 2.6.35-25-generic using Ubuntu Desktop Edition.

---

### Post by Krytarik on 2011-02-01
> **bilallucky said:**
> I can fully load the Gnome desktop environment under 2.6.35-25-generic using Ubuntu Desktop Edition.
Eh!?

---

### Post by n125 on 2011-02-01
I deleted saved_state and /tmp's contents on separate tests--no go. :( 

Maybe I'm doing it wrong? I select 2.6.35-25 from Grub, and at the credentials screen, I hit ctrl+alt+F1 to get into tty and log in from there. Then I find myself at a terminal prompt, make the changes there. I log out and and hit ctrl+alt+F7 to switch back to the GUI. Then I try logging back in again.

---

### Post by Krytarik on 2011-02-01
> **n125 said:**
> I deleted saved_state and /tmp's contents on separate tests--no go. :( 

Maybe I'm doing it wrong? I select 2.6.35-25 from Grub, and at the credentials screen, I hit ctrl+alt+F1 to get into tty and log in from there. Then I find myself at a terminal prompt, make the changes there. I log out and and hit ctrl+alt+F7 to switch back to the GUI. Then I try logging back in again.
That's perfectly right.

At this point, it could be many things stored in your user profile, since we have no hint at all by what the error may be caused. Try the following after each other to narrow it down, do all renamings like those before:

- disable all custom "Startup Applications"
- check Compiz again, rename the dirs "~/.compiz" and "~/.gconf/apps/compiz"
- rename "~/.local/share/gvfs-metadata"
- rename "~/.gconf"
- rename "~/.gnome2"
- rename "~/.local"

---

### Post by n125 on 2011-02-02
I haven't had the opportunity to see the effects of renaming those directories yet, but I have been able to boot into 2.6.35-25 just now, at around the same time as last time too. I was on battery power then, and I'm on battery power now as well.

I followed the same procedure too--switching back to default theme and wallpaper; logging into 2.6.35-25 Safe Mode first; logging out; and logging back into a normal session. I even tested going into standby and resuming, and fully rebooting. All seems to be working regardless of the theme I'm using.

But like last time I managed to load a normal session under 2.6.35-25, I eventually got a freeze at the credentials screen when trying to resume from standby, which brought me back to square one, so it's possible that the same will happen again this time.

I did apply today's round of updates, though. I wonder if those had any effect...

EDIT: As expected, resuming from standby after coming home resulted in a freeze. Last time this happened, the computer froze at the credentials screen; this time, however, my desktop actually loaded and froze a few seconds after.

---

### Post by Krytarik on 2011-02-02
Thanks for the update, try my suggestions if you have the time. You could also try to login with the fresh user again, I'm curious if it still works.

---

### Post by n125 on 2011-02-05
Sorry for the delay. I finally found the time to run a bunch of tests.

Everything was done when connected to A/C power. The two occasions I've been able to load 2.6.35-25 have been under battery, if it makes a difference.

First I just tested to see if theme and wallpaper have any effect.

> 
1) Theme: Orta; Wallpaper: custom; Session: normal; Result: Freeze.
2a) Theme: Orta; Wallpaper: custom; Session: safe mode; Result: Load.
2b) From desktop, logging out and back in under a normal session resulted in a freeze.
3) Theme: Ambiance; Wallpaper: default; Session: normal; Result: Freeze.
4a) Theme: Ambiance; Wallpaper: default; Session: safe mode; Result: Load.
4b) From desktop, logging out and back in under a normal session resulted in a freeze.
It doesn't seem that theme and wallpaper (laugh) have an effect.

Next up, I created a new user again.

> 
5a) Theme: Ambiance; Wallpaper: default: Session: normal; User: new; Result: Load.
5b) From desktop, logging out and back in again under a normal session with my normal account resulted in a freeze.
So it looks like there's something about my account that's causing the freezes.

Now I tried renaming the directories you suggested previously. I restored each directory before moving on to the next one.

> 
6) "disable all custom "Startup Applications"": I never added any custom startup applications.
7) "check Compiz again, rename the dirs "~/.compiz" and "~/.gconf/apps/compiz"": Freeze.
8) "rename "~/.local/share/gvfs-metadata"": Freeze.
**9) "rename "~/.gconf"": Load.**
**10) "rename "~/.gnome2"": Load.**
11) "rename "~/.local"": Freeze.
So I suppose we can narrow down the problem to something in "~/.gconf" and/or "~/.gnome2". Are there any files in these folders that interact together? I find it odd removing either directory allowed the desktop to successfully load.

---

### Post by Krytarik on 2011-02-05
So, following your first tests, we can safely say that you can only successfully login with your own user and the current kernel, when choosing "safe mode".

Following the "renaming" tests, we can indeed narrow it down quite a bit. What may be the culprit in those two dirs depends, of course, of what you have in them. At my system the only dir in ".gnome2" what makes sense to affect the startup in any way, and has also a counterpart in ".gconf", is "panel2.d", which is generally holding launchers for the gnome-panels. If you are using the default gnome-panels, try renaming its gconf dir: "~/.gconf/apps/panel".

---

### Post by n125 on 2011-02-05
Yeah, without making any changes, I can reliably log in with my normal account under the current kernel when choosing safe mode. There have been those two occasions where I logged into a normal desktop session with my normal account, but it eventually froze up after resuming from standby.

Renaming "~/.gconf/apps/panel" did not work.

I have attached dumps of the contents of "~/.gnome2" and "~/.gconf" just in case there may be a hint. Both directories just seem to contain mostly configuration files for various programs.

---

### Post by Krytarik on 2011-02-06
Is Sticky Notes run at startup? If so, try disabling it. The same applies to Yelp. And please try renaming "~/.gnome2/backgrounds.xml".

---

### Post by n125 on 2011-02-06
I don't think Sticky Notes and Yelp are enabled at startup. I've used Sticky Notes before, and have never heard of Yelp. Neither appear to be listed in Startup Applications.

Renaming backgrounds.xml didn't really seem to have an effect on anything.

---

### Post by Krytarik on 2011-02-06
> **n125 said:**
> I don't think Sticky Notes and Yelp are enabled at startup. I've used Sticky Notes before, and have never heard of Yelp. Neither appear to be listed in Startup Applications.
Please check in System Monitor if they are listed in Processes.

---

### Post by n125 on 2011-02-06
Yes, "stickynotes_applet" is listed there. I don't see anything related to Yelp. I then rebooted to see if "stickynotes_applet" would load, and it did.

Is there any way to dump a list of all processes to a text file? It might be helpful to see what's running after a fresh reboot.

---

### Post by Krytarik on 2011-02-06
> **n125 said:**
> Yes, "stickynotes_applet" is listed there. I don't see anything related to Yelp. I then rebooted to see if "stickynotes_applet" would load, and it did.
Did you try renaming its .gnome2 dir then?
> **n125 said:**
> Is there any way to dump a list of all processes to a text file? It might be helpful to see what's running after a fresh reboot.
```
ps -u USERNAME > processes.txt
```

---

### Post by n125 on 2011-02-06
I don't see a Sticky Notes directory in ~/.gnome2. Though, I did try deleting stickynotes_applet from that directory and was not able to boot into 2.6.35-25. Further, upon returning to the old kernel, that file was recreated in that folder.

I cut and pasted everything from ~/.gnome2 into a temporary directory and was able to boot into 2.6.35-25 as expected. I think I'm going to try adding things back into ~/.gnome2 bit by bit until I freeze up, so we can pointing the exact cause.

---

### Post by Krytarik on 2011-02-06
> **n125 said:**
> I don't see a Sticky Notes directory in ~/.gnome2. Though, I did try deleting stickynotes_applet from that directory and was not able to boot into 2.6.35-25. Further, upon returning to the old kernel, that file was recreated in that folder.
Yeah, it is a file. I forgot about it upon posting.
> **n125 said:**
> I cut and pasted everything from ~/.gnome2 into a temporary directory and was able to boot into 2.6.35-25 as expected. I think I'm going to try adding things back into ~/.gnome2 bit by bit until I freeze up, so we can pointing the exact cause.
Yes. proceed like this. My next guess would be the keyrings.

---

### Post by n125 on 2011-02-06
Bingo.

The first batch of folders I moved into .gnome2 were keyrings/, nautilus-scripts/, and panel2.d/. I tried moving various combinations of these folders back into .gnome2/ and I could load the desktop only when keyrings/ was not included. keyrings/ alone causes it to freeze.

keyrings/ contains two files, login.keyring and user.keystore. The desktop can load with only user.keystore, but will freeze with only login.keyring.

So, login.keyring is most likely the culprit.

None of the other folders that were originally in .gnome2/ cause the desktop load to freeze.

Including everything that was originally in .gnome2/, except for login.keyring, allows me to successfully load.

I wonder why renaming ~/.gconf also worked?

EDIT:

Okay, now this is interesting. The freezing appears to be related to wireless. Excluding the login.keyring that was in .gnome2 before causes Network Manager to prompt me for my WPA2 network key, which makes sense. I enter it, and as soon as it's just about to connect, everything freezes.

This also may explain why I could successfully load the desktop on those two occasions without making any changes--I was on university campus during those times, using its wireless network. Both times I ended up freezing when resuming from standby, when I came home, meaning there is something about my wireless network that is causing the freezing.

My network is WPA & WPA2 Personal. Other than a password, there are no other options under the Wireless Security tab in Network Manager.

My campus' network is WPA & WPA2 Enterprise, with Protected EAP (PEAP) authentication; Thawte_Premium_Server_CA.pem as its CA certificate; PEAP version set to Automatic; and MSCHAPv2 inner authentication.

Everything else between the settings for the two networks are the same.

 I have an AR9285 Wireless Network Adapter (PCI-Express) using the ath9k driver, driver version 2.6.35-24-generic. Wireless always worked with Ubuntu, so I never explicitly installed a network driver.

---

### Post by Krytarik on 2011-02-07
So, there is apparently some kind f incompatibility between the driver, which is subversion 24, and the current kernel subversion 25.

I did a little search for the package that includes the driver, it should be those:
[http://packages.ubuntu.com/maverick-updates/linux-backports-modules-compat-wireless-2.6.37-2.6.35-25-generic](http://packages.ubuntu.com/maverick-updates/linux-backports-modules-compat-wireless-2.6.37-2.6.35-25-generic)

Check what version of those package you have installed.

It may be this one:
[http://packages.ubuntu.com/maverick-updates/linux-backports-modules-compat-wireless-2.6.36-2.6.35-24-generic](http://packages.ubuntu.com/maverick-updates/linux-backports-modules-compat-wireless-2.6.36-2.6.35-24-generic)

If it's the case, remove the respective metapackage and install the newer one.

---

### Post by n125 on 2011-02-07
> **Krytarik said:**
> Check what version of those package you have installed.

It may be this one:
[http://packages.ubuntu.com/maverick-updates/linux-backports-modules-compat-wireless-2.6.36-2.6.35-24-generic](http://packages.ubuntu.com/maverick-updates/linux-backports-modules-compat-wireless-2.6.36-2.6.35-24-generic)

If it's the case, remove the respective metapackage and install the newer one.

Synaptic doesn't indicate that linux-backports-modules-compat-wireless-2.6.35-24-generic (or -2.5.36-) is installed. I'm not really sure how I'd go about finding the driver-containing package.

---

### Post by Krytarik on 2011-02-07
> **n125 said:**
> Synaptic doesn't indicate that linux-backports-modules-compat-wireless-2.6.35-24-generic (or -2.5.36-) is installed. I'm not really sure how I'd go about finding the driver-containing package.
Ok, it seems to be not installed by default, at my system neither.

I found ath9k.ko in the "normal" kernel modules.
[http://packages.ubuntu.com/maverick-updates/linux-image-2.6.35-25-generic](http://packages.ubuntu.com/maverick-updates/linux-image-2.6.35-25-generic)

I'm wondering about the statet old version number (24), but I'm not going to suggest to remove the old kernel packages, since you could then obviously end up with no working kernel at all.

You may try to install the mentioned backports package.

---

### Post by Krytarik on 2011-02-07
> **n125 said:**
> 
 I have an AR9285 Wireless Network Adapter (PCI-Express) using the ath9k driver, driver version 2.6.35-24-generic.
Where did you see those version number? Maybe after booting with the old kernel?

---

### Post by n125 on 2011-02-07
Would it be simple to uninstall the 2.6.35-25 backport package if it does not work?

> **Krytarik said:**
> Where did you see those version number? Maybe after booting with the old kernel?

I ran the lshw command while in 2.6.35-24. I'll give it a shot in 2.6.35-25 when I get home.

```

*-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:25:d3:1a:d7:d7
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.35-24-generic firmware=N/A ip=128.189.241.103 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:fbff0000-fbffffff

```

---

### Post by Krytarik on 2011-02-07
> **n125 said:**
> Would it be simple to uninstall the 2.6.35-25 backport package if it does not work?
 
I believe it's as simple as removing any other package.
> **n125 said:**
> 
I ran the lshw command while in 2.6.35-24. I'll give it a shot in 2.6.35-25 when I get home.

Ok, then I assume, when running kernel -25, the driver version will also read -25.

---

### Post by n125 on 2011-02-07
You are correct--lshw reports the driver subversion as -25 when in kernel 2.6.35-25.

The problem *was* definitely related to wireless, though. I could successfully connect to my university wireless network in 2.6.35-25 today, and froze when trying to boot into that kernel under my own network. I even disabled disabled my computer from connecting to my network automatically, and was able to load 2.6.35-25 normally; attempting to connect manually resulted in an immediate freeze.

Anyway, I installed the linux-backports-modules-compat-wireless-2.6.37-2.6.35-25-generic package that you suggested, under 2.6.35-24, because that's the kernel that let me connect online. I rebooted into 2.6.35-25, and was able to successfully connect to my network without any issue. :KS

So I guess that solved it! Cursory tests like rebooting and connecting to my network automatically, and resuming from standby, all seem to work. I'll monitor the computer for a few days and flag this thread as SOLVED if nothing comes up.

Thanks again for all of your help!

---

### Post by Krytarik on 2011-02-07
Great then! I guess, we may have finally solved it.:p

PS: The installed package is kernel independend.

---

### Post by n125 on 2011-02-07
> **Krytarik said:**
> PS: The installed package is kernel independend.

What does this mean when it comes to updating the kernel once a new one is distributed? Will the backport package have to be uninstalled or upgraded; will it be disabled in favor of the driver in the new kernel; or will the system just continue using it anyway?

---

### Post by Krytarik on 2011-02-07
> **n125 said:**
> What does this mean when it comes to updating the kernel once a new one is distributed? Will the backport package have to be uninstalled or upgraded; will it be disabled in favor of the driver in the new kernel; or will the system just continue using it anyway?
The latter. ;-) The backport modules somehow overrides those of the kernels (in terms of usage). They don't need to be touched at all upon a kernel upgrade. They can be updated independendly.

---


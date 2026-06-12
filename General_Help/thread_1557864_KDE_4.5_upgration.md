---
title: "KDE 4.5 upgration"
date: 2010-08-21
forum: General Help
---

### Post by ganeshmallyap on 2010-08-21
Hello,

I have upgraded my Kubuntu Lucid AMD64 desktop with KDE 4.5 using the kubuntu ppa backports.  I am impressed with the overall visual and performance improvements.  However I am facing the following issues after upgradation -

1.  When I execute any application as root user (using kdesudo <app name>) they load with a primitive GUI.  I have attached a copy of the dolphin application loaded as root user (kdesudo dolphin).  Not sure how to restore the latest GUI for them.  I tried running systemsettings as root user and tried to customize the theme little bit.  But not much has changed :(

2.  One new short cut for ExpoBlending has comeup in section Graphics. I am unable to execute it, since it has multiple missing dependencies, neither able to uninstall it. 

3.  I installed kpart-webkit and configured it using keditfiletype utility. Now while browsing certain websites such as facebook(after loading farmville application in facebook), I can see few dummy popup windows.  Attached file contains one such screenshot.

Any pointers to resolve the above issues will be highly appreciated.

Thanks in advance.

Regards
Ganesh

---

### Post by wnelson on 2010-08-21
If you have any personally install themes that are in you home directory. ".themes" As root cp -R /home/user/.themes /root

Then you have to configure root to use that theme you are using.

---

### Post by ganeshmallyap on 2010-08-21
Thank you Nelson for the reply.  I have not installed any customized themes on my desktop.

---

### Post by ankspo71 on 2010-08-23
Hi,
I just upgraded to kde4.5 in LinuxMint9 KDE and I am finding the same problem. 'kdesudo dolpin' and 'gksudo dolphin' both open up dolphin as the root user but without a theme. Strangely enough, 'sudo dolphin' works correctly. 

I used this command that fixed a similar problem with gtk apps, but I can't find anything as useful for KDE apps yet.
```
sudo cp ~/.gtkrc-2.0-kde4 /root/.gtkrc-2.0
```

If I find something that works I'll post back.

---

### Post by ganeshmallyap on 2010-08-24
Hi,

What I have seen is this issue affects kde applications equally.  My first post includes screenshot of dolphin which is a kde application.

I have see the following two additional issues today -

1.  Qt creator is taking too long time to load for the first time after boot.  It use to take not longer than 3 seconds in the past.  Now takes around one minute to load for the first time.

2.  Last logged in user name is not displayed even after configuring it in systemsettings.

---

### Post by ankspo71 on 2010-08-24
> **ankspo71 said:**
> 
I used this command that fixed a similar problem with gtk apps before, but I can't find anything as useful for KDE apps yet.
```
sudo cp ~/.gtkrc-2.0-kde4 /root/.gtkrc-2.0
```
I totally messed up what I was trying to say about being able to fix the root's gtk themes, but not kde's themes... It's corrected now.

---

### Post by ankspo71 on 2010-08-24
Hi,
Try running 'kdesudo systemsettings' then open 'application appearance'. In the style category, choose anything other than 'oxygen' for 'widget style'. Click apply. Now go back and choose 'oxygen'again  for 'widget style'. Click apply. Close systemsettings then run 'kdesudo dolphin'. Dolphin when used with kdesudo should now be themed.

The problem with doing it this way is apparently the sudo user will not use the current user's theme settings, but will instead use it's own.

---

### Post by ganeshmallyap on 2010-08-24
Thanks a ton ankspo71.  Your advise solved issue # 1 in my original post.

---


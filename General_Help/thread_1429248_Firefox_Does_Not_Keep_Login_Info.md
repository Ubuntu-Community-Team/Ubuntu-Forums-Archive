---
title: "Firefox Does Not Keep Login Info"
date: 2010-03-13
forum: General Help
---

### Post by jereece on 2010-03-13
All of a sudden, Firefox no longer remembers login information.  For example, I log into Facebook and tell it to remember me.  Then I close Firefox and come back a few hours later and I get prompted to log in again.  It's not just Facebook.  It happens with this forum, My Yahoo, and others.  In Firefox preferences, I have Remember History and Remember Passwords checked.  I have not run any kind of cleanup program or cleared my browsing history.  This just started happening within the past couple of days.

Any help is appreciated.

Jim

---

### Post by dcstar on 2010-03-13
> **jereece said:**
> All of a sudden, Firefox no longer remembers login information.  For example, I log into Facebook and tell it to remember me.  Then I close Firefox and come back a few hours later and I get prompted to log in again.  It's not just Facebook.  It happens with this forum, My Yahoo, and others.  In Firefox preferences, I have Remember History and Remember Passwords checked.  I have not run any kind of cleanup program or cleared my browsing history.  This just started happening within the past couple of days.

Any help is appreciated.

Jim

Shutdown FF and rename the existing profile in the .mozilla folder and let FF create a fresh one when it is next started.

If it now works then something in the old profile got corrupted.

---

### Post by lovinglinux on 2010-03-14
Go to "Edit >> Preferences >> Privacy" in Firefox, take a screenshot of your settings and post it here.

There is no need to rename your ~/.mozilla folder to troubleshoot Firefox profile. You can simply create a new profile from the profile manager. See the [COLOR="Sienna"]**Troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for additional info.

---

### Post by Silvertones on 2010-03-14
Same thing happened to me also. All of a sudden. The "search and form history" came unchecked.

---

### Post by jereece on 2010-03-14
dcstar - When do that, and then try to launch FF, I get the error message below....even after rebooting my computer.  

```
Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.
```

Any other suggestions?

Thanks,
Jim

---

### Post by jereece on 2010-03-14
lovinglinux - I don't see anything in the Troubleshooting section that matches my problem.  My history is working fine.  FF just does not remember my saved login info for web sites.

---

### Post by lovinglinux on 2010-03-14
> **jereece said:**
> lovinglinux - I don't see anything in the Troubleshooting section that matches my problem.  My history is working fine.  FF just does not remember my saved login info for web sites.

See quote below:

> Firefox issues are usually caused by corrupted profiles, extensions incompatibilities or sub-optimal settings. Usually, there is no need to re-install Firefox, although in some cases it does help to re-install xulrunner (Firefox 3.5 or older) or even Firefox itself.

There are some things you can do to pinpoint the culprit and solve the problem. First close Firefox, then start Firefox Profile Manager with this command:

```
firefox -P
```

Create a new profile from the Profile Manager and test it. If the problem does not persist, then you will know the problem resides in your profile. To find if it’s an extension, close Firefox and start your default profile with this command:

```
firefox -safe-mode
```

If that works, then you need to find which add-on is causing the problem. To do that, disable all extensions and enable one-by-one and test Firefox, until you can find which extension is causing the problem.

If the problem persists even when starting Firefox in safe mode, then you probably have a corrupted file on your profile or sub-optimal settings. To find out if it is some settings causing the problem, make a backup of the file prefs.js from your profile folder (see Profiles section) and replace it with the one from the clean profile. Keep in mind that this will reset all Firefox settings, including extension specific ones, hence the need for the backup.

If the problem does not persist, then you can configure Firefox settings again, including the settings for each extension installed and delete the prefs.js backup. Restore the prefs.js backup file in case the problem persists or if you don’t want the trouble of configuring all Firefox settings again and want to further investigate the problem.

If the problem persists, even after replacing the file prefs.js, then you probably have a corrupted file in your profile. This can be easily fixed by restoring a working profile backup (see Backup section), by deleting the corrupted profile folder or deleting specific files inside the profile.

To determine which file in your profile is causing the problem, check what is the function of each file [here](http://kb.mozillazine.org/Profile_folder_-_Firefox#Files).


---

### Post by Silvertones on 2010-03-15
Did you check the box I mentioned. That's the one the remembers logins.

---

### Post by jereece on 2010-03-15
"Remember History" is checked on the Privacy Tab and "Remember Passwords for Sites" is also checked on the Security Tab.

---

### Post by jereece on 2010-03-15
Although, on the Security Tab under "Remember Passwords for Sites", I clicked on Exceptions and for some odd reason the web sites I have been having a problem with were listed as exceptions.  I removed them so hopefully that was the problem.  Now the question is how did they get listed as exceptions?  These are web sites I go to every day and have always told FF to remember passwords.  That's odd but at least this most likely is the problem.

Jim

---

### Post by Silvertones on 2010-03-15
Check my post above as I edited it with a screen shot.

---

### Post by jereece on 2010-03-15
Thanks Silvertones.  Mine was set to "Remember History" but when I changed it to Custom then all were checked.  I really think the problem was that my sites got added into the exceptions for remembering passwords on the Security Tab.  I have no idea how they got added as exceptions.

Thanks for all your help.

Jim

---

### Post by Silvertones on 2010-03-15
I'm using 3.6 are you?

---

### Post by jereece on 2010-03-15
No..I am using version 3.5.8.

---


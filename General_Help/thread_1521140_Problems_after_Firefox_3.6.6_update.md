---
title: "Problems after Firefox 3.6.6 update"
date: 2010-06-30
forum: General Help
---

### Post by lykeion on 2010-06-30
**Problem**
After the update to Firefox 3.6.6 the browser freezes (totally unresponsive) when it's launched. No feedback at all on what could have been the problem.

**Info**
Ubuntu Lucid Lynx 10.04 (32-bit)
Firefox v3.6.6+nobinonly-0ubuntu0.10.04.1_i386
Xulrunner v1.9.2.3+nobinonly-0ubuntu2

**Tried this** (didn't help)
Reinstalled firefox & xulrunner
Launch firefox in safe mode
Deleted some files in profile folder (prefs.js, extensions.*, localstore.rdf, XUL.mfasl)

**Solution** (a bit unsatisfactory)
See: [http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)
Create a new profile
Reinstall extensions (I only have 4 addons)
Import bookmarks from old profile
Copy files from old profile (passwords, certificates, mimetypes)

I wonder if anyone else is having this problem and perhaps found the cause, or maybe a smoother solution than mine.

---

### Post by kamratanders on 2010-06-30
I deleted secmod.db in my firefox profile and it worked for me.

---

### Post by alkalyzer on 2010-06-30
Deleting secmod.db also worked for me (running Lucid 10.04).

PS : Thanks lykeion for posting the problem and kamratanders for the solution

---

### Post by lykeion on 2010-07-01
Thanks a lot kamratanders, your solution worked perfectly for me.

---

### Post by KennetS on 2010-07-02
+1

(it actually gave me a reason to install chromium to be able to read this forum...)

---

### Post by rajeev1204 on 2010-07-03
Same freezing after the update to 3.6.6 . Happens on  visiting flash sites .

I havent tried the fix mentioned here yet .If you wait for sometime you can see the message 'flash plugin crashed ' on some pages.

But mostly it just stays frozen.

---

### Post by rajeev1204 on 2010-07-04
*W*orst firefox update ever .Grrr.

And it wrongly says  the flash plugin has crashed, how come it wasnt crashing before for the same sites ?

Looks like a regression to me.

---

### Post by agurk on 2010-07-06
This has happened to me twice now. The first time was just after upgrading to Lucid and I since thought it was a one-time hiccup, I just bit the bullet and created a new profile. Well, it happened again today and I spent a couple of hours trying different methods to get my profile running again. Removing secmod.db worked. Very annoying and not something I have encountered since I started using Firefox years ago. Will see if I can come up with a test case.

---

### Post by ubuntwinkel on 2010-07-07
I can confirm this bug as described by lykeion.  However, HTop reveals that firefox-bin is not frozen, but just really tied up doing something (fluctuating 60-99% cpu and 99-115M memory), in my case for about 15 minutes!  When it finally opens it has deleted most of my bookmarks-toolbar, and replaced it with hundreds of duplicates of just a couple of the bookmarks that were there before.  :?

Sounds like a corrupted DB to me, and it seems to be happening frequently, suggesting a cause other than just erratic DB corruptions.  

Will delete secmod.db and report back.

UPDATE
Deleting secmod.db did not help.  Startup was faster, but firefox allowed me to watch this time as it deleted half my bookmarks-toolbar, and added duplicates as before.  I closed firefox, deleted places.db, and restarted.  Same result, but startup was 15 minutes again, as was original problem, and bookmarks-toolbar was a mess again. 

Resuming search for solutions, using chrome.

---

### Post by thmch1 on 2010-07-07
I keep getting this error:
Add-ons: [email]vd@bbmao.com:0.8.7,bindwood@ubuntu.com[/email]:1.0.4,{972ce4c6-7e08-4474-a285-3208198ce6fd}:3.6.6
BuildID: 20100625222733
CrashTime: 1278533412
EMCheckCompatibility: true
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1278533156
Not sure how I can get an addon error on a fresh install.  Anyone know whats up?

---

### Post by lovinglinux on 2010-07-07
> **thmch1 said:**
> I keep getting this error:
Add-ons: [email]vd@bbmao.com:0.8.7,bindwood@ubuntu.com[/email]:1.0.4,{972ce4c6-7e08-4474-a285-3208198ce6fd}:3.6.6
BuildID: 20100625222733
CrashTime: 1278533412
EMCheckCompatibility: true
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1278533156
Not sure how I can get an addon error on a fresh install.  Anyone know whats up?

Which add-on is failing?

---

### Post by ubuntwinkel on 2010-07-08
Fixed my particular version of this issue.  It seems the bindwood add-on was the problem.  Uninstalled it and firefox resumed fast start-up and with bookmarks-toolbar intact.

---

### Post by Neobuntu on 2010-07-15
What is the real problem? Solution?

Does removing "secmod.db" work or not?

Will removing that delete any of my stuff or cause other problems?

---

### Post by lovinglinux on 2010-07-15
> **Neobuntu said:**
> What is the real problem? Solution?

Does removing "secmod.db" work or not?

Will removing that delete any of my stuff or cause other problems?

Works for several users.

The "secmod.db" file seems to contain information about encryption, more specifically, security devices. I'm not sure exactly which info, but deleting it shouldn't cause issues to most users. The file will be recreated when you start Firefox again.

---

### Post by lykeion on 2010-07-25
Firefox problem revisited:

I tagged this thread as SOLVED, but the solution to remove secmod.db from the profile folder didn't really solve the problem for me, 
it just made it possible to start firefox again after a freeze.

What really did solve problem for me was this post by **lovinglinux**:
_[http://ubuntuforums.org/showpost.php?p=9112649&postcount=5](http://ubuntuforums.org/showpost.php?p=9112649&postcount=5)_

And I turned off flash process isolation described here by **eMJayy**:
_[http://ubuntuforums.org/showpost.php?p=9104945&postcount=19](http://ubuntuforums.org/showpost.php?p=9104945&postcount=19)_

Now I have no more freezes when visiting web pages with flash content (like youtube).
Note: I'm using firefox version 3.6.7+build2+nobinonly-0ubuntu0.10.04.1

---

### Post by lovinglinux on 2010-07-25
> **lykeion said:**
> Firefox problem revisited:

I tagged this thread as SOLVED, but the solution to remove secmod.db from the profile folder didn't really solve the problem for me, 
it just made it possible to start firefox again after a freeze.

What really did solve problem for me was this post by **lovinglinux**:
_[http://ubuntuforums.org/showpost.php?p=9112649&postcount=5](http://ubuntuforums.org/showpost.php?p=9112649&postcount=5)_

And I turned off flash process isolation described here by **eMJayy**:
_[http://ubuntuforums.org/showpost.php?p=9104945&postcount=19](http://ubuntuforums.org/showpost.php?p=9104945&postcount=19)_

Now I have no more freezes when visiting web pages with flash content (like youtube).
Note: I'm using firefox version 3.6.7+build2+nobinonly-0ubuntu0.10.04.1

Just to let you know, Mozilla released Firefox 3.6.8 only two days after 3.6.7, to fix instability issues. It should be available soon in the repositories.

---

### Post by lovinglinux on 2010-08-07
I know is not a solution, but I have created a new Firefox extension that allows to delete secmod.db and compatibility.ini automatically when exiting Firefox, so you don't need to do it manually.

[http://profilecleaner-extension.blogspot.com](http://profilecleaner-extension.blogspot.com)

After installation, the extension will start without deleting the files by default and it will prompt for selecting the files you want to delete.

I have included compatibility.ini because that is causing the same issue here, with Firefox 3.6.8.

---


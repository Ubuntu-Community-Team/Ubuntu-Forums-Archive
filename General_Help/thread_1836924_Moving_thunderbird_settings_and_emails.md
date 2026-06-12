---
title: "Moving thunderbird settings and emails"
date: 2011-08-31
forum: General Help
---

### Post by 3lud13 on 2011-08-31
So have decided to get rid of windows now as I'm not using it and go just with ubuntu the problem lies with my emails and accounts and whatnot I have in thunderbird I dont really wanna lose them. Plus I have an email account I use all the time and cant remember the password too though it is saved in thunderbird. WOndering if it is possible to copy all that data over and move it into thunderbird in ubuntu and if so how would I go about doing it

---

### Post by pqwoerituytrueiwoq on 2011-08-31
just copy thunderbirds app data you a separate drive/partition
start-> run
explorer %appdata%
if you rename the thumnderbird folder .thunderbird <-- see the dot 
and put it in your home folder on ubuntu and it *should* work be ware of windows only addons and settings in about:config

---

### Post by agillator on 2011-08-31
First, back up your Linux profile found in /home/<user>/.thunderbird (note hidden directory). It will be named xxxxxxxx.default. Then, to replace the entire profile, copy the Windows profile, I can't remember where it is, and replace the CONTENTS of the Linux profile with the CONTENTS of the Windows profile. There may be some Windows specific addons you are using that will complain and fail, you can delete those. But the program and the settings, passwords, mail, etc. should move across without problem. Be sure to back everything up first!

---

### Post by oldfred on 2011-08-31
Just to add to the good advice already given.

I use the same profile in XP & several of my Ubuntu installs. It resides in a shared NTFS partition. I boot once to create a profile.ini & the XXX.default and then edit profile.ini with the name of my working profile. I also copy same profile to my portable when traveling and copy it back. Once profile.ini is edited then I do not have to reedit, but I usually rename old one to save as backup.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---


---
title: "Firefox and Ubuntu!!!!!!!!!!!!!!!!!"
date: 2010-02-22
forum: General Help
---

### Post by bdemers on 2010-02-22
A while back I asked for help with  broken packages while updating firefox.  Got nothing in reply, so I ask again.  Seems that until this gets resolved, package manager won't install anything for me.
I have done the gui approach to removing packages, very, very confusing and dangerous with no safeguards and also apt-get install -f.  Both approaches eventually do the same thing, fail because some file contains the same thing as some other file.  I could n't care less, at this point my firefox is gone, along with bookmarks, etc, but this artifact remains, preventing, like I said, further installs of anything.  Trying to install firefox from the firefox website is a shining example why people don't go to linux, and in addition, this I believe is the root of why I got myself into this frustrating position: version conflicts. 

Thanks to Google I can still get on the net, and perhaps I will keep firefox where it currently resides, but I sure would appreciate someone taking the time to help this flaming idiot out of trouble.

---

### Post by sgosnell on 2010-02-22
What specific error message are you getting?  Your post doesn't provide a lot of information for providing specific help.  Using the GUI, Synaptic, to do installs is by far the safest way to get it done, but it's always possible to mess things up very badly if you don't think about what the program is doing, and why.

---

### Post by bdemers on 2010-02-22
Sorry,
Below is a copy from apt-get install -f:


(Reading database ... 246998 files and directories currently installed.)
Removing firefox-mozilla-build ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
  found `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg: error processing firefox-mozilla-build (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 firefox-mozilla-build
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by egalvan on 2010-02-23
> **bdemers said:**
> **Trying to install firefox from the firefox website** is a shining example why people don't go to linux,

 and in addition, this I believe is the root of why I got myself into this frustrating position: **version conflicts. **

Software should be installed with Synaptic (or Add/Remove) to allow the package manager to resolve dependencies/versions.
 This is what they were designed to do. Let them do their job.
Doing otherwise puts the onus of the work on you.

And "version conflicts" have existed in Microsoft products for decades...
they were/are called "dll hell", and they became far more prevalent with the introduction of Windows.


Linux is Not Windows.
Follow the recommended *nix procedures, and you will rarely go wrong. 
The package managers have been tweaked constantly to try to avoid dependency/version problems. Overall, they do an excellent job.
I've been using *nix heavily for three years, and have never had such problems as you describe.
 Neither have my customers who follow recommended install/un-install procedures.

Strike out on your own, or use Windows-type procedures, and you can find problems along the way.
And yes, I have experience in this area. It helps pay my bills :)

---

### Post by sgosnell on 2010-02-23
Wow.  Not sure how you got there.  You have Firefox installed very strangely, and you may have to just delete /usr/bin/firefox.ubuntu manually.  If you want to install the latest cutting-edge versions, it's best to start out by installing them without sudo, and putting them in your /home folder somewhere.  You can still run them from there, with the proper path statements, either from a .desktop or from an icon in the panel.

---

### Post by lovinglinux on 2010-02-23
To fix the problem, run these:

```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
```

This should allow you to continue with the removal of the package you wanted to remove, but before you proceed, please let me know what version of Firefox you want to keep.

It seems you have installed Ubuntuzilla and failed to remove it.






keywords: divert, firefox, ubuntuzilla, dpkg error, fix

---

### Post by bdemers on 2010-02-23
I really want to thank LovingLinux for the able assistance.  This did the job.  The rants, well, please reread the post, I did try both procedures, neither working.

---

### Post by lovinglinux on 2010-02-23
> **bdemers said:**
> I really want to thank LovingLinux for the able assistance.  This did the job.  The rants, well, please reread the post, I did try both procedures, neither working.

The Oscar goes to [Leppie](http://ubuntuforums.org/showpost.php?p=8713337&postcount=19).

---

### Post by bdemers on 2010-02-23
Below is the snippet that LovingLinus referred to. So, it seems that I am not unique.  Regardless, thanks for the help, and not some off the wall instruction to change os's


 Re: Strange Firefox 3.6 Error?
Quote:
Originally Posted by Enigmapond View Post
I hope this isn't considered a hi-jack...but I'm also having issues with FF. I had 3-4 different versions so I was deleting through synaptic and was unable to get them all out. I finally did, probably not the best thing, but I just went in and deleted all the folders in root pertaining to FF and just left my config file in my home directory. Well this still didn't do it and I still have a 3.5 version stuck..it won't install or purge...see the attached picture of the errors I'm getting.

I have since just gotten the files right from the site and threw them into /opt and then just made a link...I now have at least a working 3.6...but still unable to get rid of the errors and I won't be able to update it through the manager...

any suggestions on how to delete this mozilla-build?
try the following:
Code:

sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox

__________________
I'm not antisocial. I'm just not user friendly...

---

### Post by bdemers on 2010-02-23
BTW, I got to this forum via Firefox, since the fix.

---


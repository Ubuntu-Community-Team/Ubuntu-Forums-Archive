---
title: "Upgrading OpenOffice in Lucid to 3.2.1"
date: 2010-08-09
forum: General Help
---

### Post by inameiname on 2010-08-09
I am curious about other's opinions on their experience using the official OpenOffice from their main website, not the one Ubuntu ships with their distro. I was curious about upgrading OpenOffice 3.2.0, which is the latest that comes with Lucid, and found that if you do the following, you can have 3.2.1 on your system, which apparently is a bug fixed release:

```

To install OpenOffice 3.2.1 in Ubuntu Lucid:

- Download latest version ('OOo_3.2.1_Linux_x86_install-deb_en-US.tar.gz') from http://download.openoffice.org/other.html
- Extract and you'll see a folder called 'OOO320_m18_native_packed-1_en-US.9502'
- Remove the existing version of OpenOffice (3.2.0):
    - sudo apt-get remove openoffice*.*
- Then in the terminal direct the following to the folder 'OOO320_m18_native_packed-1_en-US.9502':
    - sudo dpkg -i ~/Temp/OOO320_m18_native_packed-1_en-US.9502/DEBS/*.deb
    - sudo dpkg -i ~/Temp/OOO320_m18_native_packed-1_en-US.9502/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9502_all.deb

```So, again, I am wondering about other's experiences doing this, as looking at it, it does look a little different, at least with how it puts itself in the Applications menu, and it seems to run much, much faster. In addition, when removing 'openoffice', it frees up 263mb, whereas the official OpenOffice installation adds barely 200mb. Might there be more the Ubuntu one installs?

Also, another way I've noticed that it might be possible to upgrade would be to install the Maverick repos temporarily and install Ubuntu's OpenOffice 3.2.1 in Lucid that way. Is that a wise alternative?

---

### Post by AlphaLexman on 2010-08-09
Generally, the standard *nix update numbering system is like this: 0.0.0-0 where '1.9.9-9' is an older version of '1.10.0-0'. Generally every other update (the even numbers) are more stable than the previous (the odd numbers).

So unless you are having major / serious issues with your system / or are using the newest hardware, it is generally best to avoid, or even skip the odd number updates.

You mentioned Maverick in your post, so if are are just testing, then go ahead, but if you are on a production machine that is critical for work revenue, I would just wait.

---

### Post by inameiname on 2010-08-09
Thanks for the info. No, I'm not having any major issues. I just read that this was a bugfix release, and after testing it out on my Lucid machine, it is noticeably quicker. And as far as what I meant by the Maverick version, I was just curious if upgrading it through Maverick's repos in my Lucid machine would be better than from the official OpenOffice website using the instructions I gave. Nonetheless, I'm always testing something or another. I can easily restore the whole thing from images if I screw something up.


Also, what I'm also inquiring about isn't just the 3.2.0 to 3.2.1 upgrade, but if the OpenOffice website's version of OpenOffice runs better for those Ubuntu users who have tried instead of the Ubuntu version of OpenOffice (which is different) that ships with the distro, even if both are, say, 3.2.0.

---

### Post by AlphaLexman on 2010-08-09
Sorry I couldn't help, I am currently on my desktop (stable) setup and I am only running ooffice-3.1.1 (I know all **odd** numbers) on karmic, my laptop maybe newer, but it doesn't have internet at the moment.

---

### Post by inameiname on 2010-08-09
No worries. I didn't know that about odd numbers being lesser stable versions and whatnot. That's good info to know.

---

### Post by Hagar Delest on 2010-08-10
Not at all for OOo!!! The numbering scheme is as follow for a X.Y.Z version:
X is for the branch version. 2.x and 3.x for example can run in parallel on the same system because they are considered as different applications, they don't use the same OOo profile BTW.
Y is the version number for a branch. Installing 3.2 will replace any 3.x previous version.
Z is now 0 or 1. A new version (with new features) is 0 and 1 is for the bug fixes only.
Therefore, an odd version of OOo (for last number) is always more stable than the even version.

As for 3.2.1, even if it should be a bug fix only, the OOo team (I've not said Oracle) has decided to implement a new identity (splash screen is rather ugly, new icons have been introduced). There are several topics about that in the OOo forums.

Almost all the GNU/Linux distros use the go-oo version from Novell. Additional features inside but also additional bugs! Personally, I only use the version from the OOo web site, installed from the debs. The version from external repos can have troubles so better install from the debs, there is just a download and then 3 command lines to type (that stay in the shell history so you don't even have to type them at each upgrade!

---

### Post by inameiname on 2010-08-10
Appreciate the info!

So you are saying Hagar de l'Est that you only use the official OpenOffice version from the official website, [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html), not the Ubuntu-shipped version? IE, you use the version I decided to install?

---

### Post by Hagar Delest on 2010-08-11
Right.

If you've a rather big document, you can try to play with it with the Ubuntu version before removing it and then compare with the Sun version. I've never tried but there are some reports saying that the Sun version is quicker.

---

### Post by inameiname on 2010-08-12
To be honest with you, using the Sun version for the past few days, I don't really see a difference at all, other than it loading faster. So far so good.

---


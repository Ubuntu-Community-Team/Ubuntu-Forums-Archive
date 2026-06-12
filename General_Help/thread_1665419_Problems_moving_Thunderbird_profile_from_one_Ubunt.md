---
title: "Problems moving Thunderbird profile from one Ubuntu pc to another"
date: 2011-01-12
forum: General Help
---

### Post by johannesbodin on 2011-01-12
Hi, 

I've recently re-installed Ubuntu 10.10 since I had some problems upgrading from 10.04. The pc is only used to read e-mail och browse the web, so I saved the profile folder from the old installation and put it in the .thunderbird folder in the new one. I also replaced the automatically generated profile name in the profiles.ini file, with the profile name from the old installation. I used this method once before, and back then I just started Thunderbird and it found all mails and contacts and so on. This time, it only shows the "Mail Account Setup" dialog box, in which you're supposed to fill in your accout information. 

There must be a way to make Thunderbird find all my profile informaton, but how? 

Thanks in advance!

---

### Post by johannesbodin on 2011-01-12
Just solved it. During the re-installation of Ubuntu, I stored all personal data on a DVD. Fortunately I saved the e-mail stuff on a USB-stick also. When I had replaced the Thunderbird profile folder with the one from the USB stick, it worked! It was probably some problem with my DVD burner (it's very old).

---

### Post by johannesbodin on 2011-01-12
Just solved it. During the re-installation of Ubuntu, I stored all personal data on a DVD. Fortunately I saved the e-mail stuff on a USB-stick also. When I had replaced the Thunderbird profile folder with the one from the USB stick, it worked! It was probably some problem with my DVD burner (it's very old).

---

### Post by johannesbodin on 2011-01-12
Just solved it. During the re-installation of Ubuntu, I stored all personal data on a DVD. Fortunately I saved the e-mail stuff on a USB-stick also. When I had replaced the Thunderbird profile folder with the one from the USB stick, it worked! It was probably some problem with my DVD burner (it's very old).

---

### Post by tentaro on 2011-02-03
So I have looked but I can not find the profile folder....where is it located?

---

### Post by oldfred on 2011-02-03
More info:
Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

It is in a hidden folder so you have to turn on see hidden files & folders.

My default one, but I edit my profile.ini and use one mounted elsewhere:
/home/fred/.thunderbird/4xwe1fuk.default

When from a different mount in fstab.
Profile.ini
[B][General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/mnt/shared/mozilla/thunderbird/profiles/lyu25irb.default[/B]

---

### Post by tentaro on 2011-02-03
I went and searched under dolphin for the jref file and then went to folder and found it that way. it took a little work but I got everything from the windows profile to my kubuntu profile. :)

---


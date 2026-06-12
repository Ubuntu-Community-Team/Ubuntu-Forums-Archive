---
title: "How to install multimedia codecs without internet connection?"
date: 2006-06-12
forum: General Help
---

### Post by maxx_730 on 2006-06-12
Does someone know which debs i need to download for this? Debs would be greatly appreciated. This is for a friend of mine who doesnt have internet on his pc but'd like to use ubuntu nonetheless.
Thanks in advance.

---

### Post by ubuntu27 on 2006-06-12
Hi Max. 

Your friend is in good Luck. Some of our comrades in UbuntuForums has created  a CD that let's you install stuff that you normally will need Internet.

It's called "UbuntuPlus" and you can find it here:

[http://ubuntuforums.org/showthread.php?t=183933](http://ubuntuforums.org/showthread.php?t=183933)

Their description:

"The main focus of the project is creating a CD for users who have slow/no internet on their Ubuntu computer, and want to install upgrades and commonly used extras, like media playback, language support, etc. Of course, users who reinstall frequently may find it useful as well."

[http://ubuntuforums.org/showthread.php?t=183933](http://ubuntuforums.org/showthread.php?t=183933)

Good Luck!

---

### Post by maxx_730 on 2006-06-13
Thanks for the tip!

---

### Post by eqisow on 2006-06-13
It says at the bottom of that post that w32codecs and libdvdcss2 are not included on the CD. They are also apparently not available at [http://packages.ubuntu.com](http://packages.ubuntu.com). I could run you through getting packages from apt-cache (and still can, if you want), but I thought it'd be easier just to upload the packages you need for you.

libdvdcss2: [http://thepiratecove.org/files/libdvdcss2.deb]("http://thepiratecove.org/files/libdvdcss2.deb")
w32codecs: [http://thepiratecove.org/files/w32codecs.deb]("http://thepiratecove.org/files/w32codecs.deb")

---

### Post by muzakman on 2006-06-13
my package installer says that the "dependency is not satisfiable" and won't install libdvdcss2.

do you know a way to install it anyway/use an alternative?


**EDIT:** worked fine. I was still mistakenly trying to install the version of libdvdcss i dl-ed earlier. yours worked! cheers


will

---

### Post by eqisow on 2006-06-13
Would you mind giving the exact error message? libdvdcss2 only has one dependancy, and that is libc6. There's no way you don't have libc6, because many essential programs such including X, OpenOffice, and gstreamer depend on it.

Edit: Perhaps you have an old version of libc6, are you running an older version of Ubuntu? (ie. not Dapper)

---


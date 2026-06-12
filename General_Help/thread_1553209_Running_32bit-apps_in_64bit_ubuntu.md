---
title: "Running 32bit-apps in 64bit ubuntu"
date: 2010-08-14
forum: General Help
---

### Post by kwbauson on 2010-08-14
I'm thinking about switching to 64-bit ubuntu, but I'd like to know if there is an easy way to make it so that all 32bit programs were available and basically I wouldn't be able to tell the difference between 64bit and 32bit except that 64bit apps would be available as well as 32bit apps.  Is this possible?  If I have to something like run a 32bit ubuntu virtual machine, then I'd rather stay with 32bit.

---

### Post by bowens44 on 2010-08-14
Which apps in particular? Most apps available in the repos are available in 64 bit versions. For those that are not, you can install the 32 bit libraries , force the 32 bit app to install and then you will see virtually no difference. You will not have to run a 32 bit version of ubuntu to run 32 bit apps.

---

### Post by kwbauson on 2010-08-14
How would I force the apps?  I read somewhere to download the actual .deb files, which I don't really want to do.  Also, would I be able to take a fresh 64bit install and install a 32bit app and get all the dependencies automatically?  I'd like it if the switch pretty much only increased performance, not the amount of work.

---

### Post by oldfred on 2010-08-14
I converted with Karmic and have noticed no issues. I used this to list & then reinstall all my apps:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

Above is just a list of apps to install, if you want to know a little more about them:
List with explanations of programs, not for reinstall
dpkg -l > ~/Desktop/installed_programs.txt

---


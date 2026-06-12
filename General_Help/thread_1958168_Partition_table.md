---
title: "Partition table"
date: 2012-04-13
forum: General Help
---

### Post by malikge on 2012-04-13
Hi,
I have two questions.

1. Is my partition table is right? 
            > 
/dev/sda2 is window7 partition
/dev/sda4 is /
/dev/dsa5 is swap space
           /dev/sda6 is /home
2. If the partition table is Ok then, when I want to update ubuntu 10.04 to 12.04 are my documents and installed applications be effected by it.

---

### Post by jjpcexpert on 2012-04-13
You will be fine if you have verified everything (i'm an Aspie Techie so I find it hard to explain things in 1st-grader English)

---

### Post by malikge on 2012-04-13
Well sir I am not an Aspie Techie, so could you explain it a little more.

---

### Post by oldfred on 2012-04-13
You seem to be showing very little data in /home, it is correctly mounted or have you just not saved much?

Whatever you do, have good backups.

You can upgrade two ways. You can upgrade in place and then it does not matter where /home is. It should save all your configurations and data.

I used upgrade in place from 6.06 thru 9.04. I had some minor & some major issues each time. But with 9.10 I wanted to change to 64bit and had to do a clean install. I now suggest clean installs just because it auto-housecleans eliminates some of the upgrade possiblities of conflicts. But it may not be totally easier either. If /home is separate you can use manual install, use existing / as new / with new format so it overwrites everything, also choose existing /home but DO NOT format it. Then your settings and data should be in the new install. Of course with any major system change, you need to have good backups.

---

### Post by malikge on 2012-04-15
> You seem to be showing very little data in /home, it is correctly mounted or have you just not saved much?Yes I have not yet saved much data on it.

> If /home is separate you can use manual install, use existing / as new / with new format so it overwrites everythingYes my /home is separate.
Can you please explain a little more, on how to use existing "/" as new "/" with new format. In other words, all my data and configuration will be saved.

---

### Post by oldfred on 2012-04-15
All user data and configuration is in /home, so if you reuse it and do not reformat it all those settings and data is still there. You use manual install or something else and manually specify partitions. Just keep track of which is which, I have many partitions and have installed to the wrong one.

But you may have made some system setting changes. Those are in /etc. I have had issues with updates where I have made changes and it asks do you want to keep old or use new. If you keep old setting it may not work with the new & if you use new, it erases the old. So anytime I edit a system wide configure file in /etc (rarely) I make a copy and save in my /home so it is part of my normal backup without backing up all of /etc.

If you have installed a lot of new programs you can simplify the reinstall by exporting a list of programs and using that to reinstall. But again that old list may have old programs you do not want or need. I found I was reinstalling python2.5 when 2.7 was the current standard. You do not need old kernels and if an older install you do not want OpenOffice as it now is LibreOffice.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---


---
title: "Transfer Files and settings"
date: 2012-03-20
forum: General Help
---

### Post by jpayne21 on 2012-03-20
I recently installed Ubuntu 11.10 32 bit on my laptop. It is a Dual boot with windows 7.  My laptop is a 64 bit system i had downloaded both .iso files and installed the wrong one. I would like to convert to the 64 bit OS But i didn't realize that i had installed the 32 bit version until after i finished setting up everything and configuring all my settings. :(  I am wondering if i could either upgrade the 32 bit version to the 64 bit version and save settings or un-install the 32 bit version and install the 64 bit version and transfer all the settings and programs. If there is a way is it worth the work?

---

### Post by Habitual on 2012-03-20
**copy your /home/$use**r directory. (control+h in nautilus to show hidden stuff) **to removable media**
Install the correct OS version creating the same user when/if prompted.
restore the copy of /home/$user (as root)
rm /home/$user/.config 
rm /home/$user/.gconf
Logout as root
Login as $user

Programs would have to be re-installed.

---

### Post by jpayne21 on 2012-03-20
Is there a way i could get a program list and then run apt-get install $PROGRAMLIST or something of that sort.

---

### Post by oldfred on 2012-03-20
I have used this on my last several upgrades, but now there are so many changes I may have to do a lot of editing to not install a lot of obsolete apps.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

I was still installing python2.5 and realized there is a lot of things you may not want. OO has changed to LO, it list kernels so you want to remove those and many other changes. It is just a text file so you can easily edit it. It using the same version of Ubuntu you should not have any of the old app issues.

---

### Post by jpayne21 on 2012-03-20
Thanks ill try it out this weekend.

---

### Post by jpayne21 on 2012-03-21
When i right click and select copy on the home folder it says i am transferring 186 some gigabytes of data. I have no files saved in that directory is that accurate?

---

### Post by oldfred on 2012-03-21
I moved Firefox & Thunderbird profiles  to a shared partition. They are hidden folders in /home but my /home is about 2GB and most of that is .wine with Picasa. 

If you are getting 186GB from an otherwise empty /home something does not seem correct.

Have you emptied trash, checked for large files/folders?

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by polki@mac.com on 2012-03-22
FWIW: If you have a remote filesystem (a fileserver maybe?) mounted in your home directory (have a look in .gvfs for example) it wants to copy all those files as well.

---


---
title: "Migrate user from old linux install"
date: 2010-06-02
forum: General Help
---

### Post by beengone on 2010-06-02
I searched around and found only limited info and mostly outdated.

I'm moving a user from an old 8.x Xubuntu install to a different machine with 10.04 installed.  I want to migrate all the user's files and settings to the new machine.  I see Ubuntu has a migration assistant, but the limited documentation I've found on it talks about using for in-place upgrades from older/other OSes.  

Ideally, something like this would work like the Apple Migration Assistant or Windows Easy Transfer.  If so, how do I access this?  Anyone have a tutorial?  If not, can someone point me to instructions to move the proper folders, create the user, assign permissions, etc.?

---

### Post by dino99 on 2010-06-02
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by beengone on 2010-06-02
> **dino99 said:**
> [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
Are you saying I should set up NFS to migrate the files? That still doesn't help with a migration except that I'd have access...  Unless I'm missing something, this isn't helpful, please remove your post to keep the thread clean.

---

### Post by oldfred on 2010-06-02
NFS would not be a bad way to copy data. I use it to rsync my settings to my portable which I have set up  with a similar structure, so when I travel I have my current firefox, thunderbird & data files. I do not copy all of /home which you would want to do. Someone recently posted that you have to pull data not push it or you lose ownership & permissions.

If not using rsync, you can copy to USB or CD. If format is not linux type you will lose ownership and permissions and have to reset them.

The /home should have all the user settings and files unless you have linked other data folders into /home like I have. Then you have to also copy those.

Generally /etc has system wide setting but if it is a different computer there should not be much if anything that you would want to copy since hardware is different. 

You can  copy all installed programs to a list and it will reinstall the new current version. When I installed Karmic clean I used this but had not housecleaned 3 years of upgrades. I went back and in synaptic I had pages & pages of totally obsolete programs (which it did not copy) and it did reinstall some stuff that I have not used & really did not want to copy. Houseclean throughly first.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

The dpkg is just a list. If you want a version showing more info you can also do this. It is not for the reinstall.
List with explanations of programs
dpkg -l > ~/Desktop/installed_programs.txt

If you use the same user name and only have one or assign in the same order the user id's should be the same.

I am sure there is more but this is what I have used to do a clean install of Lucid from Karmic or copy to my portable. I also tried to do as much as possible from a command line, listed history and am converting to a bash file so I can reinstall easily. Some settings I have yet to find a way to automate.

---


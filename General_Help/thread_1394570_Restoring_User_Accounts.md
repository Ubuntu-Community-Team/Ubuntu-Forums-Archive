---
title: "Restoring User Accounts"
date: 2010-01-30
forum: General Help
---

### Post by ebcovert3 on 2010-01-30
All,
I inadvertently deleted my wife's account using Landscape. I am now trying to restore her data (Yes, I checked the "Delete user folder" option - I know...rookie mistake). If I run "Locate <her name>" on her machine, I can still see a lot of her original data listed in her home directory. When I CD into her home directory, it is not there. 

I am open to ideas since this could seriously affect my marriage. LOL

---

### Post by dcstar on 2010-01-30
> **ebcovert3 said:**
> All,
I inadvertently deleted my wife's account using Landscape. I am now trying to restore her data (Yes, I checked the "Delete user folder" option - I know...rookie mistake). If I run "Locate <her name>" on her machine, I can still see a lot of her original data listed in her home directory. When I CD into her home directory, it is not there. 

I am open to ideas since this could seriously affect my marriage. LOL

Check the permissions or use sudo.

---

### Post by ebcovert3 on 2010-01-30
> **dcstar said:**
> Check the permissions or use sudo.
That is the problem. When I go into the directory, nothing is there. ls -la gives me no data on the files that I saw.

---

### Post by ebcovert3 on 2010-01-30
when I ls -la her home directory, I see this:
> d?????????  ? ?    ?         ?                ? .gvfs

Could her old data be in there?

---

### Post by amac777 on 2010-01-30
If you deleted the files and they are not in the trash folder, then you have a serious problem. 

My advice would be to stop using the drive and shut it off or at least remount it read-only until you know how to recover the files. I think it will involve booting from a CD and running some special tools to possibly clone the drive and then try to recover the files. The exact method will depend on what kind of a file system you have. Do some searches for "ext3 undelete" or "ext4 undelete" etc to see what you can find. 

And for the future, take a look at some of the backup programs, especially the ones that let you take a periodic snapshot of your data. (one example: rsnapshot)

EDIT: I did a google search and found this:

[http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

I've never used that though so can't say how well it works.

---

### Post by john newbuntu on 2010-01-30
Do not rely on "locate" at this point because it is a database/repository lookup based on a snapshot taken at some point.  "find" command is your friend to check for files.

I believe there is a utility called "testdisk/photorec" that can be used to recover files.  But you need to run that using a liveCD. As amac777 suggested, turn off the machine and google for the utility unless you have other plans.

---


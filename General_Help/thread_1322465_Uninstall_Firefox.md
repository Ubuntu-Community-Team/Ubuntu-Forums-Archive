---
title: "Uninstall Firefox?"
date: 2009-11-11
forum: General Help
---

### Post by ian2112 on 2009-11-11
I'd like to completely uninstall firefox 3.5.  I'm having no luck getting 64-bit flash to work and I'd like to try uninstalling ff3.5 and then reinstalling.

I've tried this through SPM but when I re-install ff3.5 my bookmarks are there, saved passwords, etc.  So is there a more thorough / complete method of removing ff?

Any help would be appreciated.

Thx,
Ian.

---

### Post by fluffman86 on 2009-11-11
How did you install flash?  I'm running 64 bit and all I did to get flash running was:
sudo apt-get install ubuntu-restricted-extras

But if you want to remove your firefox profile, where all of your passwords, bookmarks, and settings are stored, you can delete .mozilla in your home folder.  Press ctrl + H to see it.

---

### Post by lovinglinux on 2009-11-11
> **ian2112 said:**
> I've tried this through SPM but when I re-install ff3.5 my bookmarks are there, saved passwords, etc.  So is there a more thorough / complete method of removing ff?.

Firefox profiles are stored under ~/.mozilla/firefox. If you want to get rid of ALL Firefox settings, including bookmarks, then delete that folder. Nevertheless, I don't think re-installing Firefox or deleting your profile would help.

See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

For Flash 64bit, see [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

---

### Post by ian2112 on 2009-11-11
Thank-you for the tips.  Agreed, not sure removing the .mozilla folder will do much for me.

I've been following the advice in this thread [http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102).  It provides a script that seems to do the same thing as the article referenced above.  That said, while I took a peek at the script, I don't pretend to be knowledgeable enough to confirm.

I'm still not sure where my problem resides; flash was working (using the script) and now it's not.  It stopped working after blindly performing an update.

I also suspect I may have an issue / conflict with Opera, not sure.

Again - thanks for the information and assistance.  It is definitely appreciated.  And the link to FF Optimization is very interesting, too!!

Ian.

---


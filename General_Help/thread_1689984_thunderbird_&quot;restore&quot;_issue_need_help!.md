---
title: "thunderbird &quot;restore&quot; issue need help!"
date: 2011-02-17
forum: General Help
---

### Post by goosefartfan on 2011-02-17
Hi, all!

I just installed 10.04.
Before the move, I saved my files from 9.04 to DVDs.
I had save my Thunderbird files by drilling down to the mail and adress book file, zipped 'em and saved 'em to DVD.

does anyone know how and where the Thunderbird file location is that I can move the old files to?
I've already gotten some emails on the new system, and I don't want to delete those!

BTW, the Thunderbird Tools>Import wizard isn't working.

Thanks a million!):P

---

### Post by pqwoerituytrueiwoq on 2011-02-17
depends if you were using mozilla's version or ubuntu's version
/home/$USER/.mozilla-thunderbird
or
/home/$USER/.thunderbird

---

### Post by oldfred on 2011-02-17
Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

You need to start Thunderbird to create a profile. Then copy your old profile to the same location and edit profile.ini to use the old one.

Sometimes you have to correct permissions:
Correct permissions:
chmod -R 755 ~/.mozilla-thunderbird

---


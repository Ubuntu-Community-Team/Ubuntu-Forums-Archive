---
title: "dual boot with shared firefox and thunderbird profiles"
date: 2010-11-18
forum: General Help
---

### Post by confused old guy on 2010-11-18
Hi everyone.  I wonder if anyone has experience with this.  I did not find quite this problem when I searched the forums.  I dual boot 10.04 and XP.  I decided to try sharing thunderbird and firefox profiles between Ubuntu and XP.  Lots of people seem able to do it with various linux systems by simply creating new profiles in their linux system and pointing them to the profiles in the windows  operating system.  So I created them in Ubuntu and pointed them to XP's versions of the profile, just as many people suggest online. Worked fine, I thought.  

The problem is that whenever I reboot into Ubuntu and try firefox or thunderbird, I get the following error:[INDENT]Firefox is already running, but is 	not responding. To open a new window, you must first close the 	existing Firefox process, or restart your system.
[/INDENT]I check to find its PID and it is not, in fact running.  I searched the internet, and this is an error associated with profile locks in firefox and thunderbird.  So, from Ubuntu, I hunted up the locks in the XP side profiles (in my case it was called "parentlock") and deleted it.  Everything is fine until I reboot and the same happens again. It seems that some sort of lock is created everytime the profile is accessed and is not removed when it is accessed from a different operating system.  Any suggestions would be appreciated.

---

### Post by oldfred on 2010-11-18
I have my Firefox & Thunderbird profiles in a separate NTFS shared partition and never (ok rarely and not recently) had any issues. I also copy the entire profiles to my portable when we travel and back to my desktop when we return.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

Older:
More info:
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)

I though locks were released when you shutdown Firefox. Are you hibernating by any chance and not fully shutting down?

---

### Post by techunit on 2010-11-18
I have a significantly simpler approach to your problem. Install the Firefox Sync extention on both of your firefox and they will be reliably synced. As for the thunderbird accounts just use the Imap configuration of your email.

---

### Post by blomson on 2010-12-09
I experienced the same problem and I cannot find a solution. It was suggested to delete the lock files in the profile folders. I did that and it worked until I started the programs in Windows. They worked there but on the next Ubuntu boot the same problem occured. 
Next thing I did, was create a new fat-partition and store the profiles for both OS there, I then directed the windows tb and ff as well as the Ubuntu tb and ff to the profiles on that partition. The problem remains: After running the progs under windows they are supposedly still running under Ubuntu and I would have to reset the profiles.
Does anybody have a clue?
I did not try the sync-app for ff because that won't solve my problems in tb and my e-mail provider does not support imap unless I subscribe and pay...

---

### Post by ryan78 on 2010-12-09
Web Creatives … I   like it!

---

### Post by blomson on 2010-12-09
> **ryan78 said:**
> Web Creatives … I   like it!

i googled it, cause i thought it could be an add-on, or a prog but i couldn't find anything, so how exactly will "web creatives" help me?
just an addition: i run windows 7 pro and ubuntu 10.4

---

### Post by oldfred on 2010-12-09
Are you sure you are shutting down cleanly?

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

---

### Post by Krytarik on 2010-12-09
The trick is perhaps to symlink only those files/dirs to the original files/dirs which are really holding the content you want to share, in my case these are:

adblockplus
brief.sqlite
chrome
cookies.sqlite
key3.db
places.sqlite
prefbar.rdf
prefs.js
searchplugins
session.rdf
signons3.txt
signons.sqlite

Extensions are unfortunately not shareable! Never had any problems when doing it this way.

---


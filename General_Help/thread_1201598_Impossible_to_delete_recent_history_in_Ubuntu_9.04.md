---
title: "Impossible to delete recent history in Ubuntu 9.04?"
date: 2009-07-01
forum: General Help
---

### Post by viking_maniac on 2009-07-01
Every time I delete the file **/home/username/.recently-used.xbel**, that contains all recent history in most applications, it comes back again with all the previously history intact after reboot--every time. Even when using sudo while deleting.

Do you know how to delete this file permanently or at least not have it reappear with all previously history intact after each boot? I get some Microsoft Windows vibes here :(

---

### Post by philinux on 2009-07-01
[http://ubuntuforums.org/archive/index.php/t-91154.html](http://ubuntuforums.org/archive/index.php/t-91154.html)
Old but the last post is May 2009.

---

### Post by iponeverything on 2009-07-01
Yea that is a tricky one.
 
Use extended attributes.

Delete recently-used.xbel and recently-used and create an empty ones.

Then change them to immutable with:

```

sudo chattr +i .recently-used.xbel
sudo chattr +i .recently-used

```

---

### Post by viking_maniac on 2009-07-01
Actually, If I try to change the permission of this file to "read only", Ubuntu sets it back to "read and write" again without my consent.

This is just unacceptable and highly disturbing. Even in Windows XP and Vista you can actually delete history files and they do never come back again or are forced do stay there _over_ your admin/root authorization. Come on, this must be a joke or something? Please tell me that there's something wrong on my system or it's infected by some rootkit, and that Ubuntu doesn't work in this way by default? That would be just sorely and purely ridicoulus.

The only two programs that I've installed outside the Synaptic Package Manager is Creative drivers and TrueCrypt--all from their respective websites. Do they contain rootkits or any form of harmful code?

---

### Post by MechaMechanism on 2009-07-01
Oooooh...  I know the answer to this one!

Delete the 2 files and create 2 folders with the exact same name including the period in front.

$rm .recently-used.xbel
$rm .recently-used

$mkdir .recently-used.xbel
$mkdir .recently-used

---

### Post by philinux on 2009-07-01
Post #2 says all the above

---

### Post by MechaMechanism on 2009-07-01
> **philinux said:**
> Post #2 says all the aboveWell I only read the first post and that was all about permissions.  I wasn't going to read the entire thread.  Anyway hopefully you solved your problem.  :)

---

### Post by iponeverything on 2009-07-01
> **viking_maniac said:**
> Actually, If I try to change the permission of this file to "read only", Ubuntu sets it back to "read and write" again without my consent.

This is just unacceptable and highly disturbing. Even in Windows XP and Vista you can actually delete history files and they do never come back again or are forced do stay there _over_ your admin/root authorization. Come on, this must be a joke or something? Please tell me that there's something wrong on my system or it's infected by some rootkit, and that Ubuntu doesn't work in this way by default? That would be just sorely and purely ridicoulus.

The only two programs that I've installed outside the Synaptic Package Manager is Creative drivers and TrueCrypt--all from their respective websites. Do they contain rootkits or any form of harmful code?


fyi

```
chmod -w
``` is not the same as ```
chattr +i
```

---

### Post by Andrew.Z on 2009-08-12
> **viking_maniac said:**
> least not have it reappear with all previously history intact after each boot? I get some Microsoft Windows vibes here :(


To [delete recently-used.xbel temporarily](http://heuristically.wordpress.com/2009/08/12/truncate-file-command-line-bash-linux/) you must truncate it like this:

echo > ~/.recently-used.xbel

---


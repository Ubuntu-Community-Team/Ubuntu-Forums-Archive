---
title: "Flash Local Storage is Currently Disabled"
date: 2010-06-26
forum: General Help
---

### Post by JackRammer on 2010-06-26
After installing the latest updates to 10.04 (there were many, so I don't know root cause) Flash didn't work properly.  I'm running Adobe flash 10.1r53, 2.6.32-22-generic kernel, Chrome5.0.375.86, Firefox3.6.3

Pandora complained "Flash Local Storage is Currently Disabled".  When I went to Adobe Flash Player Settings Manager Global Security Settings Panel, it wouldn't allow me to click the box to "Allow third-party Flash content to store data on your computer".  It was unclickable. I also received the Google Chrome error "Your Permissions Can Not Be Read".

This thread fixed google permissions, thanks dexlavis: [http://ubuntuforums.org/showthread.php?t=1499189](http://ubuntuforums.org/showthread.php?t=1499189)

The fix to Flash isn't much different.  Perform this command & it should fix it for Google Chrome and Firefox.

sudo chown user:user/home/user/.macromedia/Flash_Player\#SharedObjects

Somehow all these directories had its ownership changed to root.

---

### Post by errold32 on 2010-09-01
Thanks for the info JackRammer, some corrections though

the above command should be 


sudo chown user: /home/user/.macromedia/Flash_Player/#SharedObjects

---

### Post by errold32 on 2010-09-01
More corrections, this time of myself.
 
The above command is not all that you need to do

The following must be done in order

sudo chown user: /home/user/.macromedia/
sudo chown user: /home/user/.macromedia/Flash_Player/
sudo chown user: /home/user/.macromedia/Flash_Player/#SharedObjects

---

### Post by arcangel96 on 2010-10-22
Thanks! that worked!... :) Also, you can,

sudo chown -R user:user ~user/.macromedia

---


---
title: "Login loop"
date: 2012-03-31
forum: General Help
---

### Post by godelski on 2012-03-31
Hey guys I've been searching to forums for quite some time and can not find a solution to my issue.  I have a login loop.  I can log into the guest session and as root, ttyl but I can't log into my account.  I've been trying some of the things on the other forums and nothing seems to be working for me.  After I logged out of root I got stuck on this screen, which looked oddly like the screen that would flash for a second when I was trying to log in to my account.  (Note, I know my password is correct, as a bad password does not work.  My root password works and everything else is fine)

```
^[[21~^[[23~^24~fsck from util-linux 2.19.1
/dev/sda1: clean, 140597/360448 files, 945082/14391040 blocks
Skipping profile in /ect/apparmor.d/disable: usr.bin.firefox
   * Starting AppArmor profiles
speech-dispatched disabled; edit /etc/default/speech-dispatcher
Checking for running unattended-upgrades:
  * Starting bluetooth

*  PulseAudio configured for per-user sessions  saned disabled; edit /etc/default/ saned     mountall: Disconnected from Plymouth

* Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

speech-dispatched; edit /etc/default/speech-dispatcher  Checking for running unattended-upgrades:    *Starting bluetooth

* PulseAudio configured for peer-user sessions     saned disabled; edit /etc/deault/saned    * Checking battery state...
``` 

It got stuck there and I had to manually restart the system.  Now when I try to log in i get a message "Could not update ICEauthority file /home/USER/.ICEauthority" and has a button that allows me to log out.  Then a text screen briefly comes up like before and has some code with Plymouth.

Now the original error message doesn't pop up at all.


Running Ubuntu 11.10 on an HP mini netbook.  This only started happening after I did a fresh install.  Immediately after the install everything worked fine.  I would like to fix this without doing a new install because I don't have a good access to a wired connection (I mostly use my phone as a hotspot).  

Also, I'm a complete noob, so I may be missing something really simple but the other forums I've found don't seem to be helping.

Thanks

---

### Post by HiImTye on 2012-03-31
try chowning the files/folders that are giving you errors, you probably messed something up by logging in as [root]("https://help.ubuntu.com/community/RootSudo")

---


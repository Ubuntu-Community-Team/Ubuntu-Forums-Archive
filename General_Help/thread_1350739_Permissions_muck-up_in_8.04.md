---
title: "Permissions muck-up in 8.04"
date: 2009-12-09
forum: General Help
---

### Post by MattP220 on 2009-12-09
I was trying to install a new program yesterday and I ended up screwing up my permissions, which had locked me out of the entire system. I accidentally chmoded the /usr/bin and /usr/lib directories to 644 (don't ask). 

I used the recovery console to fix that, but inadvertently created a new crop of errors when I adjusted the /home/username directory to chmod 777. When I logged in, I got the .dmrc [file permission error]("http://ubuntuforums.org/showthread.php?t=371052"):

"User's $HOME/.dmrc file is being ignored. This prevents the default sessin and language from being saved. File should be owne dby user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

I managed to fix that based on that thread, again using the recovery console and chown/chmod commands:

chmod 644 /home/username/.dmrc
chown username:username /home/username/.dmrc

chmod -R 700 /home/username
chown -R username:username /home/username

That fixed me up, so I thought. As it stands right now, I can log in just fine, with no errors, however I have no ability to access the system administration controls.

Networking is down, which is how I noticed it; even the icon is missing from the system tray. Everything I've tried under "administration" is giving me an access error. I know there's some little permission that I've screwed up in there somewhere that's locking me out; anybody got any ideas?

---

### Post by MattP220 on 2009-12-09
Additional info:

When I login, the sound is missing and I get an error saying that the Harware Abstraction Layer could not run. 

I've also found that trying to use sudo in the terminal gives me an error:

sudo: must be setuid root

---


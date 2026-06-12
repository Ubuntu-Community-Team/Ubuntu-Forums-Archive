---
title: "cannot log into primary user account following root login"
date: 2012-08-27
forum: General Help
---

### Post by sippyCUP on 2012-08-27
Hey all,

I recently delved into Ubuntu 12.04 for my desktop and installed Xubuntu 12.04 on my HP 5103 netbook. I moved a ton of movies to the disk of the netbook, inadvertently using up a ton of disk space. So much, actually, that Xubuntu hung on boot before reaching the login window, on "Checking battery state."

While I was troubleshooting this, I entered a console via alt-F5 and tried startx, but to no avail. I rebooted and used "sudo startx" and was able to get into xfce, but it was like the standard xfce, not the Xubuntu flavor, and it threw me a prompt for setting first-time xfce settings. Regardless, this worked for using the net for research, following which I freed up space (~7 gigs) and was able to reach an actual login window.

However, now I can only login to my guest account and not my main user account, which is pretty odd. I can only guess that I have someone buggered up something in the profile.

Two questions:

(A) What log files should I have been scanning throughout this episode to get clues as to what was failing during boot?

(B) How can I restore my main user profile short of a reinstall?

Thanks all,
Eric

---

### Post by steeldriver on 2012-08-27
A) maybe the xsession just failed to start because the filesystem (or at least your home partition) was full? You could look in /var/log/Xorg.0.log, /var/log/Xorg.1.log etc

B) using 'sudo startx' usually creates a root-owned .Xauthority file in the user's home directory - which prevents subsequent X sessions being started by the user - delete it and see if that helps

---

### Post by sippyCUP on 2012-08-29
steeldriver, I found .Xauthority and rm'ed with root, but I still couldn't login to my home account. also went through the log but didn't really see anything which would indicate what is going on with my account.

do you think I need to reinitalize xfce/xubuntu defaults with my user account?

---

### Post by Wim Sturkenboom on 2012-08-29
How did you remove the files? From gui? If so, did you empty the recycle bin / trash? If not, your files are still there occupying space and that's why you can login as a normal user.

It's just a guess.

Note:
When formatting a HD, 5% of the space is usually reserved for root so in case the hard disk is full for normal users, root can still login and fix the user's stupidities and other mistakes ;)

---

### Post by sippyCUP on 2012-08-30
> **Wim Sturkenboom said:**
> How did you remove the files? From gui? If so, did you empty the recycle bin / trash? If not, your files are still there occupying space and that's why you can login as a normal user.

It's just a guess.

Note:
When formatting a HD, 5% of the space is usually reserved for root so in case the hard disk is full for normal users, root can still login and fix the user's stupidities and other mistakes ;)

I actually logged in via the terminal to do it, so it really was deleted. Not sure what's still holding it up.

---

### Post by Toz on 2012-08-30
Do you have enough free space left on the drive (this is a common cause). Run the following command to see:
```
df -h
```

Or, have a look for an .ICEauthority file as well in your home directory and make sure that you are owner. 

Or, have a look at your ~/.xsession-errors file after an unsuccessful login attempt to see if there is anything in there to indicate what might have gone wrong. The /var/log/lightdm/lightdm.log file might also yield some useful information.

---


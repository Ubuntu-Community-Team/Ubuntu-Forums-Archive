---
title: "Questions about system configuration and backups"
date: 2009-10-06
forum: General Help
---

### Post by mullba on 2009-10-06
I'm new to Linux, but I'm considering using Ubuntu for a small business.  I have a couple of questions about system configurations and backup options.  I would like to be able to set up the systems so that each user's data and program preferences are compartmentalized for easy transfer and backup.  I would like to set things up so that if something should happen to one of the systems or if I want to update the distro, I could backup just the user's data, re-image the drive with the updated setup, then drop the user's data back on (and have it work).  Is that possible/easy?  I see that each user has their own directory, but is all of their relevant data stored there?  Is there another directory I should know about?

---

### Post by ezsit on 2009-10-06
If you install your systems and designate a separate partition for the /home directory, then it makes upgrading easy to save the user data and preserve the settings.

As for backing up the user's data and settings, I've simply tarred the /home/username folder and saved it to a network drive, restoring is a simple matter of untarring the file after a reinstall and resetting the ownership to the username and groupname previously used. I would suggest using the exact same username for each user when reinstalling or upgrading, it keeps the ownership and permissions easier to deal with.

Another option is to install, configure, then install **remastersys** and create a liveCD/DVD backup of each machine. The LiveCD/DVD can be used to restore after a crash and will maintain the user data.

---

### Post by mullba on 2009-10-06
That's just what I needed to know.  Thanks!

---


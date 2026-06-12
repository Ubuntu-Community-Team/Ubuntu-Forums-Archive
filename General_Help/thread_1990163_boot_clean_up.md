---
title: "/boot clean up"
date: 2012-05-29
forum: General Help
---

### Post by VorlonShadow on 2012-05-29
My /boot partition has been at 100% for quite some time now.  I'm running Ubuntu 10.04.3 Server.  I researched this and found that the best way to handle this was to use "apt-get remove" and remove all the old versions.  I've done this on several other Linux servers we have and it has worked great.  However, with one of my servers I get a message that says:

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-image-server: Depends: linux-image-2.6.32-38-server but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

When I do "uname -r" (to get the current version), it returns 2.6.32-36-server.  The error message above seems to be indicating 2.6.32-38, which is 2 versions later than the version I'm running right now.  I'm half afraid to do the apt-get -f install because I don't want it to disable what I'm running right now. This is a major database server and if I disable it I'm REALLY screwed.  I'm not very "Linux oriented", so I really have no idea if running this will mess me up or actually fix me so I can continue removing old versions and free up the space.  Or, is there some other way to handle this?

Can someone point me in the right direction?

Thanks,
Jesse

---

### Post by hwttdz on 2012-05-29
What's your uptime? It's possible you installed a new kernel but aren't using it because you haven't rebooted since?

---

### Post by VorlonShadow on 2012-05-29
178 days, 4 hours, 45 minutes.

Usually when I log in (I use SSH most of the time) it tells me when I need to restart.  It doesn't say that, so I have not restarted for a very long time.

Jesse

---

### Post by dino99 on 2012-05-29
maybe its time to clean the room a little bit :)

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove


install -f will try to find a workaround about the issue by finding missing package(s) that need to be installed/upgraded, so no woryy, it will not break your install nor disturb it.

if you are using a mirror archive, then switch to the main server before updating again, then try install the new kernel.

the other solution is to download the 3 kernel files into an empty folder (image + 2 headers) then run: sudo dpkg -i * (from that folder)

---

### Post by anonymous5 on 2012-05-29
> **VorlonShadow said:**
> My /boot partition has been at 100% for quite some time now.  I'm running Ubuntu 10.04.3 Server.  I researched this and found that the best way to handle this was to use "apt-get remove" and remove all the old versions.  I've done this on several other Linux servers we have and it has worked great.  However, with one of my servers I get a message that says:

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-image-server: Depends: linux-image-2.6.32-38-server but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

When I do "uname -r" (to get the current version), it returns 2.6.32-36-server.  The error message above seems to be indicating 2.6.32-38, which is 2 versions later than the version I'm running right now.  I'm half afraid to do the apt-get -f install because I don't want it to disable what I'm running right now. This is a major database server and if I disable it I'm REALLY screwed.  I'm not very "Linux oriented", so I really have no idea if running this will mess me up or actually fix me so I can continue removing old versions and free up the space.  Or, is there some other way to handle this?

Can someone point me in the right direction?

Thanks,
Jesse

You can remove some of the kernel version older than 2.6.32-36. If you're sure you're not using 2.6.32-38 you can remove it too, but I don't recommend it since it may be used in the following restart.

What are the contents of /boot and what is it's size ?
Depending on your hdd partition layout, if your /boot partition is too small you could resize it or create another one.

---

### Post by VorlonShadow on 2012-05-29
sudo apt-get clean - said nothing
sudo apt-get autoclean - did something, but I'm not sure what.
sudo apt-get autoremove - gave me the same error as I indicated in the original message.

If you're pretty that apt-get -f install won't mess me up, then I may just try that later.  I'll wait until Saturday, though since there will be little activity then.

---

### Post by VorlonShadow on 2012-05-29
df -h reports that the /boot partition is 228M in size.

Perhaps it ran out of space when installing the .38 update?

Jesse

---


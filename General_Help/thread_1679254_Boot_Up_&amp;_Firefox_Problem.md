---
title: "Boot Up &amp; Firefox Problem"
date: 2011-01-31
forum: General Help
---

### Post by Pegasuss on 2011-01-31
I just had a problem reported when I booted up My Computer (Failed to Boot, & I had to press the 'restart/reboot' button on my computer.

When I eventually got it booted up, I found the following error message:
 "An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was: 'Error: Opening the cache(e:Unable to parse package file /var/lib/apt/lists/
security.ubuntu.com_ubuntu_dists_mavarick-security_main_binary-i386_Packages )1), E: The package lists or status file could not be parsed or opened.) This usually means that your installed packages have unmet dependanvies"

On opening Update Manager I got the Following Error Message:

"Could not initialise the package information
An unresolvable problem occurred while initialising the package information.
Please report this bug for the 'update-manager' package and try to include the following error message:
'E:Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages (1), E:The package lists or status file could not be parsed or opened.'

I last used my computer Yesterday, after which I did a standard/normal 'Shutdown', I am a Novice so would like some Help understanding what all this means & How to fix it?

P.S.  Also I got an error message when opening Firefox, All My Bookmarks & History have disappeared?

---

### Post by Pegasuss on 2011-01-31
Ok, Problem Found (If not totally solved).

It was (apparently a Loose connection on My Hard drive Data Cable).

I will have to save up for a new Hard Disc (Just in Case?).

---

### Post by Krytarik on 2011-02-01
Firefox: Try restoring your bookmarks to the last saved state:

- "Bookmarks -> Organize Bookmarks... -> Import and Backup -> Restore"
- then choose the most recent date
- confirm it

Apt: Try the following:
```
sudo apt-get clean
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get upgrade
```

---


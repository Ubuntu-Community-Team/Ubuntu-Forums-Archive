---
title: "Non-US Keyboard layout gets reset to US after reboot"
date: 2010-01-09
forum: General Help
---

### Post by thomas_t on 2010-01-09
I am using a fresh Ubuntu 9.10 installation with english-only language but with a German keyboard.

So, once booted into my (only) account, I use the ***Keyboard Preferences*** app to change my Layout from US to German. Which works. I also remove the US keyboard so that the only layout left is German.

But upon a reboot, not only the US kbd is back in the layouts list, but the kbd also has defaulted back to US, so that I have to open the Kbd Prefs to again remove the US layout to get my German layout active again.

I also tried "Apply System-wide" and even logged in as root to make the same changes, but the system always goes back to US layout after a reboot.

This is also a problem when logging in after a reboot - I want the system to use German layout there, too.

So, how do I change the layout ***globally*** so that even at the login page I have my German layout already active?

---

### Post by thomas_t on 2010-01-09
After learning not to use the simple search box but use advanced search, I actually found a few other threads mentioning the same problem.

Apparently this is a new bug introduced in 9.10 (was not present in 9.04).

I guess we'll have to wait for a bugfix release.

---

### Post by mkvnmtr on 2010-01-09
I use a spanish keyboard and can switch to a english layout for when i forget where something is. Ihave no trouble in either 9.04 or 9.10. For that matter in Puppy, PCLinux or Chrome OS. I do always set it up on the install as a latin american keyboard. Maybe that is the key, do it during the install.

---

### Post by thomas_t on 2010-01-09
OK, I got it solved somehow now, too. I did two things, one of them is probably what did it:

1. I followed the suggestion of "nyarlathotep77" ([http://ubuntuforums.org/showthread.php?t=1319305](http://ubuntuforums.org/showthread.php?t=1319305) post #16), by turning off automatic login, and re-logging in as root, where I set up the kbd anew as well.

2. While logged in as root I used Webmin to set the user ID of my normal user to 1001 (someone had suggested that this problem only occurs with the first user account of ID 1000).

After a reboot, even the login screen now uses the desired German keyboard.

---


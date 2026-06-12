---
title: "ecryptfs sometimes mounts $HOME wrong"
date: 2011-07-28
forum: General Help
---

### Post by xSpidey01x on 2011-07-28
Sometimes when I log in to Natty, I am granted with a bunch of files matching the glob ECRY* and my $HOME contents are not visible. The files look like what I get if I ls my .Private directory. GDM/X then runs what appears to be a unity or gnome session with no panels, etc, just a blank desktop with a pretty useless context menu.

When this happens, I log out by logging in as root from a vtty, killing my users x-session-manager process, and removing the files auto-created from said fiasco: the XDG user dirs, .gnome, etc.

Then I reboot and login my user from a vtty: it works. I log out and log back in to the same vtty as root, and ls my users home directory and see files (symlinks) that includes a README on how to access my encrypted data. I assume that's what happens when it unmounts ^_^




To my understanding the WHOLE point of setting up encrypted $HOME when I installed this system as a Maverick, was that I would get _MY_ data on login, not garbage!



I rather like the idea of encrypted $HOME, given that this is a netbook -- but I would rather [turn it off](https://help.ubuntu.com/community/EncryptedPrivateDirectory#How to Remove an Encrypted Private Directory Setup) if this is going to keep happening!






Anyone got a clue what the bloody heck is happening, or where I should be looking for problems? There are no hand-done customizations to the base install beyond my configuration files in $HOME, and whatever installed packages have touched. It is also kept up to date. So I don't think I've broken anything :-)

---


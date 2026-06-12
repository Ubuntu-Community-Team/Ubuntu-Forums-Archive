---
title: "rc.local doesn't complete before auto-login?"
date: 2012-06-01
forum: General Help
---

### Post by alexpage on 2012-06-01
Hi,
On a kiosk-type machine I'm setting up, I have a script launched by rc.local which removes the "guest" user's home folder and then restores it from a tarball containing a "clean" state.  I have this guest user set to automatically log in without a password, so in theory the kiosk should boot up, clean up their home folder, and then log them in.  Sometimes, though, in either KDE4 on Ubuntu 12.04 or GNOME2 with 10.04, the automatic login occurs *before* the home folder is completely restored.  (The system will come up with errors related to things in the home folder when trying to log in.)  Sometimes it works fine, though, and if I manually run the script first and *then* log in as that user, there are no issues.  It definitely seems that rc.local is still being processed while the login is occurring.

I don't want to hard-wire any delays into anything; I'd like to ensure that my script completes before allowing the auto-login process to start.  Nothing in rc.local or my script is launched in the background (i.e. with &), so it should be blocking everything else until it's done.  The guts of the script are basically:
```
rm -rf $folder_to_restore
tar -xzf $tarball_to_restore_from
```where $tarball_to_restore_from is only abut 40MB and the script takes just a couple of seconds to run.

I'm having trouble figuring out what actually handles automatic logins, though.  I don't know if there's a process that initiates the auto-login somewhere in e.g. /etc/rc2.d/ that I could reorder to come after rc.local; I don't see anything obvious in there.  Or maybe there's some other place besides rc.local that I could put my script?  Maybe involve lightdm somehow?

Any tips/advice greatly appreciated.

---

### Post by alexpage on 2012-06-11
Disregard.  Since the DM is running as an upstart job, there really wasn't a good way to use a conventional init script for my task.  I just converted my script over to upstart, and set it to run on "starting gdm" (for Ubuntu Lucid, anyway).  It works fine now.  More info: [URL="http://superuser.com/questions/133595/running-a-script-on-startup-before-x-starts-in-ubuntu-9-10"]http://superuser.com/questions/133595/running-a-script-on-startup-before-x-starts-in-ubuntu-9-10
[/URL]

---


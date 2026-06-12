---
title: "Firefox path problem since 9.10 upgrade"
date: 2010-10-19
forum: General Help
---

### Post by rcbinwi on 2010-10-19
I just upgraded from 9.04 to 9.10 on a Dell e1405.  I dual boot Ubuntu and XP.  I had Firefox running off of a single profile/path for both OS's.  Since the upgrade, I have not been able to use Firefox from Ubunutu, though XP has been working fine.

For a while I was getting an error when I launched Firefox.  The error was the "Firefox is currently running."  (I don't have the exact wording of the message because I haven't been seeing it recently.)  This was typical if Ubuntu couldn't access the XP partition, such as when I had left XP in hibernate mode.

Then more recently I've been getting the message, "Could not launch application.  Failed to execute child process "/home/richard/.mozilla/firefox/profiles.ini" (Permission denied)."

From what I can tell, profiles.ini has not changed.  The XP side of things don't seem to have changed, either.

Any advice?  Thanks!

---

### Post by rcbinwi on 2010-10-19
More information: Previously, I was trying to boot Firefox from the shortcut.  I just tried booting Firefox from a terminal.  I got the error message "Firefox is already running, but is not responding.  To open a new window, you must first close the eisting Firefox process, or restart your system."

When I try to boot Firefox from root, sudo Firefox, I get, "(firefox-bin:2658): GLib-WARNING **: g_set-prgname() called multiple times."

Oddly, I get the same error message for Thunderbird, except the beginning is (thunderbird-bin:2680), when I boot it from a terminal rather than the shortcut.  But Thunderbird works.  It runs with separate profiles in the two OS's, unlike my Firefox.

---

### Post by WorMzy on 2010-10-19
I do the same thing as you -- one Fx profile for all my OS', but I've never had this problem. Still, lets see if we can figure out what's wrong.

First, can you run ```
ls -l ~/.mozilla/firefox/profiles.ini
```

make sure that it's owned by you, and has rwx for your user. If you've run firefox with sudo for whatever reason, then there's a chance that root has taken possession of this file. (You shouldn't use sudo for graphical applications for this reason; use gksu or gksudo)

If it's not owned by you, run ```
sudo chown $USER:$USER ~/.mozilla/firefox/profiles.ini
```
If the permissions aren't right, then run ```
chmod u+rwx ~/.mozilla/firefox/profiles.ini
```

Does Fx launch now?

If not, try launching it with the following arguments:

```
firefox -P /path/to/the/shared/profile/folder
```

If that works, then open profiles.ini in vim (or your favourite text editor) and make sure that the Path variable for your firefox profile is set correctly.

---

### Post by rcbinwi on 2010-10-19
Thanks!  When I run ls -l ~/.mozilla/firefox/profiles.ini, I get:
```
-rw-r--r-- 1 richard richard 256 2009-11-3 15:03 /home/richard/.mozilla/firefox/profiles.ini
```
So does this mean I have possession of the file?

In any case, I ran the other code.  

(What exactly do I put in $USER?  I'm assuming that it should be, in my case $richard:$richard.  Is that correct?)

When I run Fx from the path of the correct profile, Fx gives me an option of what profile to run (Ubuntu or XP).  I ran XP, where I have the profile.  I got the same error: "Firefox cannot use the profile "RichXP" because it is in use.  To continue, close the running instance of Firefox or choose a different profile."

Any other ideas?

---

### Post by WorMzy on 2010-10-19
$ means that the next word is going to be a variable, and that the system should use the value of that variable, $USER is just a session variable containing your username (open a terminal and run "echo $USER", you'll see what I mean). You don't need to worry about the chown command anyway, the file is already owned by you.

Your profile.ini doesn't have execute permissions, but I'm not sure whether that's a problem. Mine has execute permissions, and that's all I have to go on, so run the chmod code from my last post; even if it doesn't fix the problem, it won't do any harm.

I made a mistake with the firefox -P command, it should have been
```
firefox -profile "/path/to/the/shared/profile/folder"
```

-P expects a profile name, -profile expects the folder. Also, putting quotes around the path helps if there's spaces in the path. e.g. "/media/Windows/fx profile".


If it's still not working, try creating a new profile via the profile manager. (Alt+F2, firefox -ProfileManager, run). Make the new profile use the same folder as your current shared profile (make a copy of your profile beforehand, just in case something goes wrong - which is unlikely). It may recreate whichever files are erroneously telling firefox that it's in use.

---

### Post by lovinglinux on 2010-10-19
Nevermind

---

### Post by rcbinwi on 2010-10-19
Thanks for the advice.  Unfortunately, I got the same reaction, that Firefox was already running.

Here is the code of my profile.ini file:
```

[General]
StartWithLastProfile=1

[Profile0]
Name=RichUbuntu
IsRelative=1
Path=rz2ley2e.RichUbuntu
Default=1

[Profile1]
Name=RichXP
IsRelative=0
Path=/media/sda2/Documents and Settings/Rich/Application Data/Mozilla/Firefox/Profiles/why53lpg.Default User

[Profile2]
Name=RichUbuntu2
IsRelative=0
Path=/media/sda2/Documents and Settings/Rich/Application Data/Mozilla/Firefox/Profiles/why53lpg.Default User 
```

I just added the third one to see if it would clear up the second one, but it didn't help.

Any ideas?

---

### Post by lovinglinux on 2010-10-19
> **rcbinwi said:**
> Any ideas?

First make sure Firefox is closed by killing firefox-bin process.

```
killall firefox-bin
```

If that doesn't help, delete the files compatibility.ini and secmod.db from Firefox' profile folder.

If that doesn't help, try to disable Firefox Apparmor profile. See [this discussion]("http://ca.ubuntuforums.org/showthread.php?t=1553837&page=5") for more info.

---

### Post by rcbinwi on 2010-10-30
I took out compatibility.ini and secmod.db, and nothing changed.  I got lost in the discussion about Apparmor.

Somehow along the way, my profile.ini looks like it went back to the default.  But when I run firefox -P, I get all the profiles I had before.

Also, when I run Firefox, I get:

(firefox-bin:2607): GLib-WARNING **: g_set_prgname() called multiple times

---

### Post by rcbinwi on 2010-11-06
I've been trying various solutions, but I think I may have narrowed things down.  First, I uninstalled Fx on XP, just to be safe.  It didn't help.

Second, I noticed that Fx in Ubuntu consistently says that Fx is in use when I try to use my XP profile.  It's as if XP can't access the partition.

So I've been wondering what I can do to be sure the XP drive is mounted correctly, namely, if it's mounted so that Fx can have access to it.

Any ideas?

---


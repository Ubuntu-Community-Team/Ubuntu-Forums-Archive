---
title: "Erase Profile at Logoff"
date: 2010-08-03
forum: General Help
---

### Post by de Silentio on 2010-08-03
Sorry I didn't know where to post this (Security?).
 
I work for a public school and we are implementing a number of Ubuntu NBR 9.1 netbooks. I wanted to use Likewise Active Directory for authentication, but have problems with the software so now I'm onto another solution for our problem.
 
We are going to have one login for all users (Students, is the name). The problem with this is that Website passwords can inadvertantly be stored, potentially compromising users personal data. Additionally, I don't want to have any files left in the Students profile in case people accidentally save personal information in their files.
 
I'm thinking there are potentially two solutions:
 
1. The Students profile is deleted when the user logs off. This will erase web history and files
 
2. The Students account is always logged in with a temporary profile (or no profile, if that is possible) that deletes itself at logoff because it is temporary.
 
I'm having a hard time coming up with search terms for a solution like this, so I thought I would put the question to the experts.
 
Thanks in advance.
 
---------
Post Edit:  Perhaps I shouldn't talk about "profiles" and I should talk about "home directories"?

---

### Post by de Silentio on 2010-08-05
Thanks to everyone for the help. Here are my results.
 
It turns out there were two areas that I needed to secure: Firefox and Home Directories.
 
Firefox:
 
I locked two settings: (i) every session is started in Private Browsing mode and (ii) Firefox never stores passwords. This made it so no private data is stored.
 
This is a two step process:
 
1. create file called "loadcustom.js" in the "/usr/lib/firefox-3.5.x/defaults/preferences" folder, with the text:
 
// Tell Firefox to load cusom file
pref("general.config.obscure_value", 0);
pref("general.config.filename", "firefox.cfg");
 
2. Create a file called "firefox.js" in the "/usr/lib/firefox-3.5.x" folder with the text:
 
// Options to Lock
lockPref("browser.privatebrowsing.autostart", true);
lockPref("signon.rememberSignons", false);
lockPref("broswer.startup.page", 1);
 
Now the Firefox preferences are locked and cannot be changed. This eliminates crafty students going in and changing the settings to steel inadvertanly saved passwords.
 
 
Home Directories:
 
This one was a little more tricky. I found a script that deletes all files and folders in a directory. I then run this script at the session logout, but only for the "student" user. If it runs for every user, special files are deleted that are needed to create the profile.
 
This script deletes all non-essential files and folders just before the session closes. The result is such that all of the deleted folders, files and settings are recreated at every login.
 
Here is what I did:
 
1 Log out and log in as an admin on the machine
2. Edit the /etc/gdm/PostSessions/Default script (must be done with sudo).
3. Enter the text:
 
If [ $USER = "student" ]; then [NOTE: student is the user I want to "lock down"]
rm -Rf /home/student
fi
 
[Post Edit] 4. Edit the /etc/gdm/Init/Default script and enter the same code (This takes care of sessions that are restarted or shutdown. The PostSessions/Default is only run at Logoff) [/Post Edit]
 
 
The "Default" script is run when the Gnome session is closed. It is run as root, but the $USER variable is populated with the username that is logged into the session AND it doesn't delete the "important" files. (I had an issue where the script was run when anhyone logged out, and the "important" files must have been closed, so they were deleted)

---


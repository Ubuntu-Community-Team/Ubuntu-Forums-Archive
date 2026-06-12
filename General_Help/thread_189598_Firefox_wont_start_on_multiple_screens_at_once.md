---
title: "Firefox wont start on multiple screens at once"
date: 2006-06-05
forum: General Help
---

### Post by Intangir on 2006-06-05
I have firefox, and multiple X Screens on my nvidia card

firefox can start fine on one or the other, but not on both at the same time

if i try to start it on a 2nd X Screen it says:

"Firefox is already running, but is not responding. To open a new windows, you must first close the existing Firefox process, or restart your system."

i looked up the message and it apparently is normal for after a crash if a lock file still exists

the thing the other firefox process is running FINE on the other X Screen, i want to be able to have it on 2 screens at once not close the first..

anyone have any ideas?
id prefer not to have to create a 2nd profile either, i checked that out but couldnt figure out how to USE the 2nd profile

---

### Post by pyromithrandir on 2006-06-05
I seem to recall that it is bad to have the same user logged in to multiple X sessions. Or, at least when you try to load desktop evironments or other more complex stuff on them, it can get messy.
If you log into the second X session with a different user, though, firefox will start up fine.

---

### Post by Intangir on 2006-06-05
its the same session, just on two screens
only 1 logon for both the screens

one instance of X, using 2 screens, same mouse/keyboard

---

### Post by Lusse on 2006-11-18
I have the same problem. I must fix it. Is there any way to install 2 firefox or something.

/Lusse

---

### Post by bollix47 on 2006-11-18
Yes, you can have two instances of Firefox running at the same time.

You must use different Firefox profiles for each instance.

You must set an environment variable called MOZ_NO_REMOTE=1.

When you run Firefox you would add -P "Profile Name" to the command line.

e.g. firefox -P "Default User" for your exisiting profile and
     firefox -P "NewCreatedProfile" for the second instance.

I.E. you would create two different launchers.  Another way to use just one launcher would be to use -ProfileManager in the command line and select from there which profile to use.

---

### Post by Valacosa on 2008-04-17
Thanks for the multiple profile tip. It seems to serve my purposes for now. 

Still, if anyone figures out how to get the same profile working on both screens, I would be much obliged.

---

### Post by ryanhaigh on 2008-04-17
You won't be able to do this because you are trying to launch two sessions of firefox (the executable not just windows) which would be trying to access the same profile information, the lock file is basically a way of saying this profile is in use, so when the second instance tries to read it the profile you will get the error message. 

A couple of options:
-create a bash script that copies your primary profile then launches the second instance of firefox using that profile
-use firefox 2 and firefox 3beta in the same way as above
(note that changes to the second instance of your profile will not be reflected in your first (so no bookmarking etc.)
-stop using separate x displays and use twinview/xinerama instead

---


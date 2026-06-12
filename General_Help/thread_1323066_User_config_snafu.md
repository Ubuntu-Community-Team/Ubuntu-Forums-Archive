---
title: "User config snafu"
date: 2009-11-11
forum: General Help
---

### Post by skippergimp on 2009-11-11
I have a system with a separate partitions with for home and /.

I have had a play with fedora after problems with karmic.  I thought I had everything working then it fall apart so I can running back to karmic  but my user setup is now bjorked....and my wife its my wifes account that is really broke.....

My login works but it isn't displayed at the gdm login screen. Her details are displayed but it fails to login  "Authentication failure"  I think the problem lies in UID somewhere as Fedora wanted to set the UID to something in the 500's whereas Ubuntu seems to like 1000's.  I think I have everything looking right but it is failing.

The User and group program from System->Administration does not list me but I can login. My wife is listed with a UID of 1000.  The group display on her files was listed as 1001.  I have changed the group to her username
and this is now listed as her username.

My guess is that somewhere a setting is still Fedora'd and therefore ubuntu won't log her in.

Any ideas where this setting is?

And why i am not listed at the login screen?

Auth log entry:
Nov 11 17:25:43 antec gdm-session-worker[2755]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:1 ruser= rhost=  user=ycs

---

### Post by skippergimp on 2009-11-11
I have deleted my wifes account and removed her directory.  I have created a new account with the same login and it works okay.

If i restore the backup of her account with tar xvpfz backup.tgz -C, will I just make the problem return?

---

### Post by cariboo on 2009-11-11
You should be ok restoring your wife's data.

---

### Post by skippergimp on 2009-11-11
The restore seems to be okay, my wife has used and didn't notice anything wrong!

Why would my account be missing from gdm?  The help screen from Users and Groups talks about a key in GConf, which GConf would this be as a file search shows quite a few and I can't find one that has app/gnome-system-tools as indicated by help screen?

---


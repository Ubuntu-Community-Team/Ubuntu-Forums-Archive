---
title: "Can not login"
date: 2010-09-28
forum: General Help
---

### Post by 1maddog on 2010-09-28
Greeting,

When I try to login with my username, the one I created when I installed the OS, it seems to try to login but almost immediately kicks back to the login screen. No authentication error it just seems to just logout? The only change I made since last successful login was to add ". .alias" to the .profile file - the only entries in the .alias file are comments and "alias" commands. I have one other username but it is not in the sudo's list of users so I can not change anything in the master login. 

Any thoughts on how to rectify this other than reinstalling which I really do not want to do.

md

---

### Post by 1maddog on 2010-09-28
I was able to get into the home directory via su from another login name. The issue was that the name of the file being sourced was misspelled and when .profile was sourced at login it could not find the file and killed the login attempt. Once the file name was corrected login was successful.

Any thoughts to why a file not found would effect the login process so drastically? I can see throwing an error and having a messed up login environment but to not allow the login to proceed seems extreme. Perhaps this is unique to Ubuntu?

---

### Post by coolman98 on 2010-09-28
wow that is strange. use live cd copy files with remastersys then reinstall

---

### Post by 1maddog on 2010-09-28
Not sure what you are suggesting, possibly because I am new to linux (have some Unix experience but not linux, esp. at the adm level). 

Do I use remastersys to build "cd copy files" and reinstall the os from that. Would the "cd copy files" have all the apps as well as the os? Is this intended as a backup/recovery strategy? or I could just google :-)

---


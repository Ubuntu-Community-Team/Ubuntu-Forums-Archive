---
title: "How to run a script using GVFS-mount at login?"
date: 2010-07-01
forum: General Help
---

### Post by risbac on 2010-07-01
The situation:
-Ubuntu Lucid
-Likewise-open for AD login

The idea:
-add the network shares of each user to the favourite places in Nautilus

The problem:
-the script we have written is working if we run it manually from each session. But it's NOT working if we place is in /etc/profile.d. 

More details:
the script is contacting the AD to get the name of the .bat script which is mounting all the shares for each user. 
Then it's mounting the netlogon share using GVFS-mount, reading the .bat script to find the network shares, and finally adding them to the nautilus favourite places. 

It's working fine if we run it manually. But I suspect that we are running it too early, and the gvfs-mount is not working at all. 

If you have any idea how to make this work, that would help a lot.

Please note that as a new user may login anytime, we cannot just add the script a file in /home/whatever or to the session applications. It must be run automatically at first login, without requiring any work from the user.

Thanks !

---

### Post by toljnima on 2010-12-02
I have noticed that some things work in shell but not in a script.
I also noticed that if the script that look like this (only an example):
> #!/bin/sh

echo ${USER:5}



This produces an errormessage saying: "Bad substitution"

If, however, I change the start of the script:
> #!/bin/bash

echo ${USER:5}


...it works.
Changing the sh to bash does the trick.
Why?
So, if you want to put something in a sh-script, you might want to link to a bash-script instead.

Hope it helped :D

---


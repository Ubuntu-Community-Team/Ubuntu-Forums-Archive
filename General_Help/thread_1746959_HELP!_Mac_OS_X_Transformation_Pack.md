---
title: "HELP! Mac OS X Transformation Pack"
date: 2011-05-02
forum: General Help
---

### Post by linuxsyst on 2011-05-02
Please help, I want to uninstall a Macbuntu and I jus forgot the file I need to change the file from 11.04 to 10.10 and remove that it will read that as 10.10
I get this error:

```
Macbuntu - Mac OS X Transformation Pack 

Deinstallation script

Attention!
This script will slide back to default Ubuntu desktop
all Macbuntu-10.10 components will be removed permanently

Checking currently installed version of Macbuntu-10.10...
Failed. Currently installed version is not compatible with this uninstall
Exiting...

```

Thanks

---

### Post by matey3 on 2011-05-02
this may be unrelated (since I dont know anything about Macbuntu) but can you use -f switch to force it to Deinstall?

I had a similar problem with installing something and I got the msg "use -f to force install" so I used it, and the 2nd time it worked,(1st time I forgot to use sudo). I thought may be you could also use some sort of switch with OR Within the script (like edit the script then run uninstall)?

Just a thought!
Good Luck!

---

### Post by linuxsyst on 2011-05-02
```
petr@bingo:~/Macbuntu-10.10$ sudo ./uninstall.sh -f
[sudo] password for petr:

Macbuntu - Mac OS X Transformation Pack

Deinstallation script

Attention!
This script will slide back to default Ubuntu desktop
all Macbuntu-10.10 components will be removed permanently

Checking Ubuntu version...
Passed

Checking currently installed version of Macbuntu-10.10...
Failed. Currently installed version is not compatible with this uninstall
Exiting...
```

Didn't work but thanks for reply :)

---

### Post by Frogs Hair on 2011-05-02
Try the forum seach function because the are other thread on this topic.

---

### Post by linuxsyst on 2011-05-02
Yes but that's a bit different problem.

---

### Post by Spyderkid on 2011-05-02
Ok...
 
you'll want to go to appearance, and choose ambiance.
then change the login screen using ubuntu tweak.
remove the thing at the top panel which shows file,edit,tools, etc...
don't think there's anything else?

---

### Post by linuxsyst on 2011-05-06
It's ok but thanks for reply I tried it also (Spyderkid), I did this: ```
vi uninstall.sh
``` edited the ubuntu version, saved then ```
./uninstall.sh force
```
force because it reads other file also.

---


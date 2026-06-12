---
title: "creating folders for different users."
date: 2010-01-18
forum: General Help
---

### Post by villain222 on 2010-01-18
I want to make a script to create a videos , photos, and documents folder in all of my (or anyone's) user's home folder.  Wildcards don't seem to work if I try to put in: sudo mkdir /home/WILDCARD/videos  here is my error.

mkdir: cannot create directory `/home/*/videos1': No such file or directory

and just to clarify i want all user's to have there own seperate folders not shared.

any Ideas?

P.S.  I tried with the -p switch and no luck.  I just got a new home folder for * with the videos folder inside.

---

### Post by falconindy on 2010-01-18
A simple for loop will do the trick.

```
for user in /home/*; do mkdir -p /home/$user/{video,photos,documents}; done
```

---

### Post by warfacegod on 2010-01-18
Correct me if I'm wrong but don't those folders already exist for each user in the /home folder?

---

### Post by baddog144 on 2010-01-18
For future reference, I believe anything you put inside the /etc/skel directory will be put in every new user's home directory. I may be wrong on this though

---

### Post by villain222 on 2010-01-21
I'd heard about the etc/skel but it was empty.  I don't know it that is just how it is until somebody puts something there.  I'll try that out.  

Thanks for you help guys.  I'll give these a try and see what good it brings.

side note:  My home folder doesnt have any of those specific folders, until i created them.
CORRECTION: apparently the users setup while installing ubuntu do have those folders created.  new ones added manually don't.

---

### Post by villain222 on 2010-01-21
a quick look into /etc/skel found that it can be used to created files and directories for NEW users.  so in this case i already have the users set up and running so it won't help.  I'm going to try the loop option and see it that fixes this one.

---

### Post by villain222 on 2010-01-21
here is the error for the loop option.  is the ";" correct?  or does the "do" need to be dropped?

$ sudo for user in /home/*; do mkdir -p /home/$user/{video2,photos2,documents2}; done
bash: syntax error near unexpected token `do'

---


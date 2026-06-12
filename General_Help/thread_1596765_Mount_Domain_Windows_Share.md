---
title: "Mount Domain Windows Share"
date: 2010-10-14
forum: General Help
---

### Post by MikeyDL on 2010-10-14
I've been using the "connect to server" option when I have my laptop at work and enter the share, username, password ect. and that works okay.  However, I decided to try and manually mount the share to a share point and have been running into "Permission denied" error messages.  Here is the terminal command I've been using:

```
sudo mount-t cifs //data/masterdocs /home/michael/shares/mdocs -o user=DOMAIN\myusrname,password=mypassword
```

I've mounted cifs shares with a similar script at home but they don't have any authentication information. 

I've been googling the issue but not allot of luck finding any info.

My cifs version is 4.5

Any ideas or suggestions?

---


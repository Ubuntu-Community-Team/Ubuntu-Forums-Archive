---
title: "Folder permissions problem"
date: 2012-04-18
forum: General Help
---

### Post by LuniTux on 2012-04-18
Hello,

I seem to be having a problem with folders on my ftp server. The folders are pathed as:

```
/my_ftp
       /user1/
              fldr1/
              fldr2/
       /user2/
              fldr1/
              fldr2/
       /user3/
              fldr1/
              fldr2/
```

fldr1 allows users full access.
fldr2 allows users to download only.
All folders should have full access inside the building.

The ftp access to the folders works correctly. The problem I am having is that fldr2 for user1 and user3 do not
allow me to add files from the server end. They appear to have the same permissions as user2 but, I can add
files to user2's fldr2 folder without any problems.

```
ls -l
drwxr-xr-x [COLOR="blue"]4[/COLOR]  2001  2001 4096 2011-08-03 14:11 user1
drwxr-xr-x [COLOR="Red"]6[/COLOR]  2001  2001 4096 2012-04-18 10:45 user2
drwxr-xr-x [COLOR="blue"]4[/COLOR]  2001  2001 4096 2011-08-03 14:11 user3

ls -l user1 user2 user3
user1:
total 8
drwxrwxrwx 2  2001  2001 4096 2012-02-03 16:20 fldr1
dr-xr-xr-x 2 lunitux lunitux 4096 2012-04-10 09:47 fldr2

user2:
total 8
drwxrwxrwx 3  2001  2001 4096 2012-04-18 10:45 fldr1
drwxr-xr-x 2 lunitux lunitux 4096 2012-04-18 13:02 fldr2

user3:
total 8
drwxrwxrwx 2  2001  2001 4096 2012-04-04 11:25 fldr1
dr-xr-xr-x 2 lunitux lunitux 4096 2012-04-10 09:47 fldr2

```

The only difference between the folders that I see is that **user2** has a **[COLOR="Red"]6[/COLOR]** after the **drwxr-xr-x** where as [B]user1 and
user3[/B] have a **[COLOR="Blue"]4[/COLOR]**. Is there anything I need to change for this to work?

Thanks

---


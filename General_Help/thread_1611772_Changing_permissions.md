---
title: "Changing permissions"
date: 2010-11-02
forum: General Help
---

### Post by Markh83 on 2010-11-02
Hi Guys
 
Im a real noob to ubuntu. I have just installed ubuntu 10.10 as im fed up of microsoft. I have also installed testdisk to recover files from a corrupted harddrive. I have successfully recovered the required files to 'photos' folder on the primary drive. Some how i have managed to duplicate all of this data into a secondary folder and completely filled up my 120gb hard drive. I have tried to delete the files, but i do not have the permissions.
 
I understand that something has to be done with root, but everything that i have seen so far all looks a little confusing. Could someone spread some light on this?
 
Thanks
 
Markh83 aka the noob:(

---

### Post by Piccy on 2010-11-02
sudo chown *yourusername* *pathtofolder*

eg:
say your login is mark
sudo chown mark /media/120gbdrive/pictures

this is a change owner command giving you complete ownership of the directory
also if its an external drive it will mount to /media/*drivelabel*

---

### Post by Markh83 on 2010-11-02
thanks i will try that out:)

---

### Post by coffeecat on 2010-11-02
> **Piccy said:**
> eg:
say your login is mark
sudo chown mark /media/120gbdrive/pictures


Good advice, but I'd add to that slightly. Put a colon after the username so that the group ownership gets changed to the username's default group, otherwise it will stay with the root group. Also, without the recursive option I think that will only change the permission of the pictures folder; you need -R. So, in total:

```
sudo chown -R mark: /media/120gbdrive/pictures
```... changing '120gbdrive' to whatever the mountpoint is called and changing 'pictures' to 'photos' if that is what the folder is called.

---


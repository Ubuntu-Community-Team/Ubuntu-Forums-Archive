---
title: "Help i did somthing wrong =S (10.4)"
date: 2010-06-24
forum: General Help
---

### Post by TommyfoarRoshie on 2010-06-24
Hai i have just installed Ubuntu 10.4 and is great so far. I had a power blackout while updating the system in system update it was installing them ect.
now when i rebooted it looks like windows 95/98 xD 

[http://twitpic.com/1zkwer](http://twitpic.com/1zkwer) <--- heres a pic

Anyone know how to put it back to normal?

---

### Post by VH-BIL on 2010-06-24
First try and check for updates and then if the packages are still there you can install them.

If not, you can try uninstalling the offending packages then reinstalling them.

---

### Post by TommyfoarRoshie on 2010-06-24
im a right noob to ubuntu XD
em how and where would i find system update?

---

### Post by 3Miro on 2010-06-24
> **TommyfoarRoshie said:**
> im a right noob to ubuntu XD
em how and where would i find system update?

System -> Administration -> Update Manager (you need to be connected to the Internet)

After you install the updates (and probably reboot), go to System -> Administration -> Hardware Drivers to see if there are restricted drivers available for you.

What has gone "wrong" is that you have probably selected a different theme. Go to System -> Preferences -> Appearance and check the themes available for one that looks good to you.

---

### Post by TommyfoarRoshie on 2010-06-24
Em i went to install another software and it said to Repair? but i dont know where =S /crys

---

### Post by TommyfoarRoshie on 2010-06-24
> **3Miro said:**
> System -> Administration -> Update Manager (you need to be connected to the Internet)

After you install the updates (and probably reboot), go to System -> Administration -> Hardware Drivers to see if there are restricted drivers available for you.

What has gone "wrong" is that you have probably selected a different theme. Go to System -> Preferences -> Appearance and check the themes available for one that looks good to you.

Oh Thanks =D

---

### Post by VH-BIL on 2010-06-24
Where you updating or installing Ubuntu when you had the blackout? I am just asking this because you didn't know where the update option is.

---

### Post by TommyfoarRoshie on 2010-06-24
when i installed it and it ran fine it popped up asking to downlaod updates for the system  around 10 mins into it the power went out =P

---

### Post by 3Miro on 2010-06-24
> **TommyfoarRoshie said:**
> Em i went to install another software and it said to Repair? but i dont know where =S /crys

Go to Apps -> Accessories -> Terminal and type:
```
 sudo aptitude update 
```

It will ask you for your password and then it will repair the database. Once this is done, you should be able to update normally.

---


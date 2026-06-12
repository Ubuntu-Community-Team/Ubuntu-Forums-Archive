---
title: "User and group administration problem: Users no longer show up in GUI user admin tool"
date: 2009-07-03
forum: General Help
---

### Post by zbeekman on 2009-07-03
Please help me answer the following questions: How do i fix this problem, and, in the future, how can I safely change UIDs and GIDs without this happening?

The problem: A few weeks ago I was making the change from a RHEL derivative to ubuntu on my workstation at work.  (Our sys admin was very busy and I like Ubuntu MUCH better than any RHEL systems/derivatives I have used.)  So as I was reconfiguring my machine after my hard drive died, I was doing my best to set things up in keeping with our infrastructure here at the lab.  I did not realize, however, that in order to access the NFS shares the users would have to have the same UID and GID as they do on the server to have read-write permission, etc.  So I went ahead and changed a number of UIDs and GIDs from the command line using 'usermod' *I beleive*.  Now, while the users are still there and can still log in and are listed in /etc/passwd, etc. they don't show up in the System>Administration>Users and Groups menu.  I originally made the UID/GID changes under 8.04 but have since upgraded to Jaunty.  If any one can tell me how to: a) Get these users back into the gui admin menu and b) change UIDs and GIDs in the future without this happening that would be fantastic!

Many thanks!
-Z

---

### Post by zbeekman on 2009-07-03
One more note: I just added a user using the gui (i.e. System>Administration>Users and Groups) and he does not show up there!!!!

---

### Post by otonka on 2009-12-16
I seem to have the same kind of problem.
When using the users-admin GUI interface I only see "root" as a user.
I can still add new users, but after restarting the users-admin program these new users are not visible.
The added new users are able to log in and they are added to the file /etc/passwd.
I suspect this problem started after I had to force a system shutdown while I was using the users-admin program.

Can anyone tell me how to resolve this problem.
I'm using an Ubuntu 9.10 release.

---

### Post by zbeekman on 2009-12-17
I have a suspicion that this may have to do with UIDs and GIDs.  What are the UIDs (look in /etc/passwd) associated with the users who do not show up?  I would bet that they are below 1000.

---

### Post by otonka on 2009-12-22
> **zbeekman said:**
> I have a suspicion that this may have to do with UIDs and GIDs.  What are the UIDs (look in /etc/passwd) associated with the users who do not show up?  I would bet that they are below 1000.

I used UID's ranging from 1001 to 1005.
I also used an UID of 504. None of these show up in the users-admin GUI.
As an alternative to user-admin I tried to use KUser.
This program showed all users, however I was not able to Add/change any users. I think this is an authorisation problem. At startup of KUser the following message is displayed: 
"Error opening /etc/shadow for reading"

---

### Post by zbeekman on 2009-12-23
Have you tried launching kuser with root privileges?  (i.e. try gksudo Kuser on the command line.)  I would imagine that this would resolve this issue.  You definitely need root priveleges to read and modify /etc/shaow.

---

### Post by otonka on 2010-01-04
I tried this work-around. It seemed to work fine. 

My problem with users-admin is still unsolved.
As a beginner to Linux/Ubuntu I tried some things and played around with the system.
Have to admit however that I gave up and reinstalled Ubuntu (practicing SBackup). Now the users-admin program works fine again.

Thanks.

---


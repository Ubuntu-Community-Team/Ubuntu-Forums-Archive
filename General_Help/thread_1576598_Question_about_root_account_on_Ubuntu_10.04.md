---
title: "Question about root account on Ubuntu 10.04"
date: 2010-09-17
forum: General Help
---

### Post by davidvandoren on 2010-09-17
Hi this is my first post here. I am used to use fedora.


During the installation of Ubuntu 10.04 I was not asked for a root password. Does this mean that my first account created is the one with Root privileges?

I created a new user account and when I try to run sudo or a software installer it won't work. How can I change this? Or is it ok to log in with the first user account which I created?

Thanks.

---

### Post by lostprophetpunk on 2010-09-17
You can become the sudo root user by using this command in terminal...

sudo -i

Then when it requests you for a password, enter your account password that you use to login to your account.

---

### Post by uRock on 2010-09-17
Welcome to ubuntuforums,

The password you used for the account will work with sudo commands. By default ubuntu doesn't create a root account. Check out this link to learn more about the root account. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ubunterooster on 2010-09-17
The first is a sudo account which is not *quite* the same (the root does not ask for a password to do things)

It is fine to log in as the first user, but to change the second user so it can have root permissisions, log in with the first account and go to  System>administration>users and groups.
Right-click on the second users name and select "settings". Check "allow this user to administer the system.

---

### Post by pbrane on 2010-09-17
*I was too slow*:)

First, Ubuntu uses the **sudo** method to access root privileges. Fedora uses a root account and a user can **su** to gain root privileges. 

In using **sudo** simply type your user password to gain root privileges.

If you created a new user and that user cannot use **sudo** then they are not a member of the **adm** group. You can tell what groups a user is in by typing **groups <username>**, replacing <username> with the actual username. In a user account with **sudo** privileges you can correct this in *System->Administration->Users and Groups*.

---

### Post by davidvandoren on 2010-09-17
Thanks that cleared everything up so far.

By the way fedora does not have a root account anymore.

---

### Post by QIII on 2010-09-17
Is there a Fedora 14?

Fedora 13 requires the use of "su" and a password still...

I just updated mine last night.

---

### Post by ubunterooster on 2010-09-17
> **QIII said:**
> Is there a Fedora 14?
Yep, 
   
                       [           [IMG]https://fedoraproject.org/static/images/banners/f14alpha.png[/IMG]]("https://fedoraproject.org/get-prerelease")



You *can* enable the root account on Ubuntu or Fedora but it's pretty much against the rules to say how to do it in the open forums. See why (works for .buntu and fedora) [here]("http://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account")

---

### Post by Rocket2DMn on 2010-09-17
Just FYI, check out the [forum policy on root logins]("http://ubuntuforums.org/showthread.php?t=1486138").  Also, welcome to Ubuntu!

---

### Post by QIII on 2010-09-17
Cool.  I'm adding Fedora 14 Alpha on a vm.

---


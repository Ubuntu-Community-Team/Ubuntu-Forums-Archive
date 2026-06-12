---
title: "Locked down remote access sessions"
date: 2011-08-30
forum: General Help
---

### Post by zmchenry on 2011-08-30
I have a customer that needs to grant access to his Linux (Ubuntu 10.4 LTS) box
 
For general collaboration, we have him using NX
 
In this case, he specifically needs someone to be able to login to the machine in a very specifically limited context...able to launch an application to look at/run a few data sets, but should not be able to traverse directories or do too much else at all
 
Essentially, the remote party should login to a session that offers the application and the dataset, and that's it.
 
Asking some local experts, they began attacking the problem at the permissions level, but I have to imagine that someone out there knows of an existing 3rd party product that specifically accomplishes this.
 
Maybe one of the cloud solutions like LogMeIn can do this? Maybe there's some local client software that's easy to configure this way? All thoughts welcome.

---

### Post by zero2xiii on 2011-08-30
In my opinion,

First, I am by no means an expert. But here is my recommendation:

Setup a restriced user account, (yes, I am reffering to permissions as well, but you will see in a sec why)

Disable the things you wish (all the basics can be done under the users and group settings >> System > Administration > Users and groups)

Now setup a deffenit home directory (not the standart /home/$user)

Change the shell to /bin/false

Now you can use virtualy any program you wish for the remote access.. Unless he is some skilled hacker, he wont be able to do much on the computer (sure, maybe mess up his OWN files in the restricted home directory)..

To even restrict it further. Deny write access by him to his own home directory and keep list and read acceptable, this way even if he makes cahnges, it will not persist.

Haha hope this didn't waste TO much of your time :)

Cherz

---

### Post by bodhi.zazen on 2011-08-30
> **zmchenry said:**
> I have a customer that needs to grant access to his Linux (Ubuntu 10.4 LTS) box
 
For general collaboration, we have him using NX
 
In this case, he specifically needs someone to be able to login to the machine in a very specifically limited context...able to launch an application to look at/run a few data sets, but should not be able to traverse directories or do too much else at all
 
Essentially, the remote party should login to a session that offers the application and the dataset, and that's it.
 
Asking some local experts, they began attacking the problem at the permissions level, but I have to imagine that someone out there knows of an existing 3rd party product that specifically accomplishes this.
 
Maybe one of the cloud solutions like LogMeIn can do this? Maybe there's some local client software that's easy to configure this way? All thoughts welcome.

It is not so easy. "the application" needs libraries, you can identify them with ldd

Best solution would be to use ssh and restrict the account with a custom apparmor profile.

See : [http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

You will have to allow a shell (jailbash) + libs + database application + data.

---


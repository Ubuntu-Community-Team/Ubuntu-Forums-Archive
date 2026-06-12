---
title: "Users read rights"
date: 2009-08-05
forum: General Help
---

### Post by willemto on 2009-08-05
Maybe somebody could help me with something, maybe obvious.
I have my primary user, willem, main group willem, and then another user frank, main group frank.

I want frank to only see his home directory and nothing else. His e-mail, office, and internet browser must however work.

With current system he can see all remote drives etc and everything from /.

How do I accomplish that? Changing the rights to every file on the system is not an option. (Will not run chmod xxx -r / every again!)

---

### Post by soapBAR2 on 2009-08-05
I've never used this before, but it sounds like what you are looking for is

[http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)
[http://www.faqs.org/docs/securing/chap29sec296.html](http://www.faqs.org/docs/securing/chap29sec296.html)
[http://kegel.com/crosstool/current/doc/chroot-login-howto.html](http://kegel.com/crosstool/current/doc/chroot-login-howto.html)

---

### Post by willemto on 2009-08-05
CHROOT seems a bit like an overkill. 

What would "sudo chmod -R o-r  /" do to the system? The idea is that all the root group files should be hidden from the users.
Will it cause another painful re-installation?

---

### Post by soapBAR2 on 2009-08-05
> **willemto said:**
> CHROOT seems a bit like an overkill. 

What would "sudo chmod -R o-r  /" do to the system? The idea is that all the root group files should be hidden from the users.
Will it cause another painful re-installation?

Well, the problem with using chmod is that for the system to work, some files need to have certain permissions (eg, binaries need to be readable, log files need to be writable, etc). It would be technically possible to restrict using chmod where possible, but it would be a logistical nightmare.

Not only that, but frank will constantly need sudo permission (and unless you want to configure a custom /etc/sudoers file) you'll need to help frank a lot. A chroot jail does not have this problem, because even if you have sudo in a chroot jail, you're still in jail. I'd go with the chroot jail, not necessarily because you fear frank's hacking abilities, but because it's a system that's ready to go instead of you going to each and every file and directory and determining how hard you can lock the file down without breaking something.

---

### Post by willemto on 2009-08-05
You are probably right.  

It seems that practically all files have user = root and group = root. Then the others    	 	 	 	 	 	  Permission are used to allow users to access programs etc. Why is the groups set up like this? 



Making all files invisible to others, will stop the users from doing anything. 



A better scheme would have been to have,  for every user, a set of permissions for all files/entities in the filesystem, and not have a concept like groups at all. So every entity in the file system gets a permission file, only  	 	 	 	accessible to root or roots. And the roots get assigned by grandmaster root... But I guess this is not how unix/linux work.


Maybe making the linux system hidden is not a good idea, because then people can not learn what goes on in the system, but for older people having a very very restrictive simple system is very attractive. This is for people born before WWII.



I will now attempt the chroot way. Thanks for the help

---


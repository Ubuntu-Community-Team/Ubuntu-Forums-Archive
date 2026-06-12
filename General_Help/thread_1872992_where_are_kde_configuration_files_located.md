---
title: "where are kde configuration files located?"
date: 2011-10-31
forum: General Help
---

### Post by quickk on 2011-10-31
Hi everyone, 

    I updated from kubuntu 11.04 to kubuntu 11.10 on two separate machines, and the update was a disaster.   One machine would not even finish booting, while the other has major issues with crashes to Nepomunk and a bunch of kde applications like kile, and the software updater.  

I figured that the problem was related to some configuration files in my home directory, and so I created a new user called "test".   With this user, everything works perfectly.  So the problems have to do with my account.

I tried moving .kde to .kde_old, but this didn't fix my issues.   

Are there other places in the home directory where configuration files are stored?   

If not, what's the best way to create and use new "fresh" home directory?  I can then just manually move my data over.

Thanks!

---

### Post by mastablasta on 2011-10-31
every user has it's own home directory, so your test user has it's home already. you could move the stuff form the old home to test's home if you wish.

---

### Post by quickk on 2011-10-31
Thank you for your suggestion mastablasta.  I realize that each user had their own home directory.  Because the test user can start programs like kile without any problems, this means that something is wrong with my own home directory.   The problem is that I am not sure how create a new home directory for myself.  

For example, say that my home is /home/bob.   If I do this:

```
mv /home/bob /home/bob_old
mkdir /home/bob 
```

Then my desktop environment does not work anymore.  

If I use the configuration tool to specify a new home directory, it doesn't seem to create this new home (maybe I need to login/logout, but I am afraid this will really break things).   

If I create a new user and then use that user's home, then my permissions are messed up.

---


---
title: "Account setup overwrote encrypted home"
date: 2012-09-13
forum: General Help
---

### Post by slawekk on 2012-09-13
I was moving to a new machine after a hardware failure. The hard drive was good, so a took it out from the old box and put it in the new one. I did a clean install of Xubuntu 12.04 (the previous system was 11.04 I think) choosing not to reformat the /home partition. That way I got a new /home partition that contained old home directories of all users, in particular my encrypted home directory, say /home/slawekk. To recover that directory I renamed it to /home/slawekk_old and added (with Xubuntu graphical “System/Users and Groups” tool) a user slawekk with the same password as on the old system, checking the option to encrypt the home directory. This created an encrypted /home/slawekk. I removed that, renamed /home/slawekk_old back to /home/slawekk and did 

sudo chown -R slawekk slawekk

Then I logged in as the user slawekk. The login was successful, but to my surprise I did not get the contents of the old slawekk’s home but an new empty account with standard folders.
I now know that I should have used encrypt-recover-private or similar method. I tried to use it afterwards but it was finding only one encrypted directory and it was the one with the empty standard folders. It seems that the procedure for adding a user with encrypted home just silently overwrites the existing home directory with the new, empty one.  
My questions now are: 
1. What really happened here? Why my home directory was overwritten?
2. Can my data be recovered somehow? The disk usage from du suggests that the data are still somewhere on the disk. I do know the password and passphrase for the encrypted directory.

---

### Post by SlugSlug on 2012-09-13
just tagging in to see the outcome

---

### Post by Ang Baki on 2012-10-17
Hi, I think I'm having the same problem. I'm hoping somebody could also put me in the loop in case somebody answered on this thread.
:p

[http://askubuntu.com/questions/199641/user-account-chown](http://askubuntu.com/questions/199641/user-account-chown)

---


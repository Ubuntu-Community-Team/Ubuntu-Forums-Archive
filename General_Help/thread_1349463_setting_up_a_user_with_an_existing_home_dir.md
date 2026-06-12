---
title: "setting up a user with an existing home dir"
date: 2009-12-08
forum: General Help
---

### Post by sefs on 2009-12-08
Hi all.

In my previous installation i had a user call moxiie. with home at /home/moxiie

After a fresh install i want to put back this user I can see that he was previously uid 1002 from doing a ls -la on his dir.

But when I try to create this user it tells me that the home dir already exist to choose another.

How can I create back this user to use his existing home directory?

Thanks.

---

### Post by sedawk on 2009-12-08
I would create a new user manually by appending one line
to two system files, but that is considered
a dangerous task, so lets do it "officially":

1) Rename existing directory
sudo mv /home/moxiie /home/moxiie_old

2) Create new user "moxiie" 
Use GUI or "useradd" to add a new user moxiie.
It will get any ID - it is not important

3) give ownership of moxiee_old to new moxie user
sudo chown -R moxiie /home/moxiie_old

4) Keep a backup of new moxiie dir in case there
   are conflicting configuration files with newer Ubuntu
sudo mv /home/moxiie /home/moxiie_new

5) And activate old directory again
sudo mv /home/moxiie_old /home/moxiie

Now moxiie should be able to login ...

---

### Post by sefs on 2009-12-08
Thanks!

---


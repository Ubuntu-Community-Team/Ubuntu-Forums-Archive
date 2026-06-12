---
title: "Get access to other site NO SUDO"
date: 2010-08-13
forum: General Help
---

### Post by sarahfoxnz on 2010-08-13
hi,

I've got my username on Ubuntu (I can't remember version number, but its 6 months old aprox)..

I'm the sole user (& admin)..

I have /home/myusername/  & can edit all files (without using sudo), but if I want to edit a file in another directory - i need to use Sudo..

I'm setting up a website  /home/website/ 

(this is the same structure as the external website I'm going to edit, i want the directory structure to be the same..)

is there a way, I can allow FULL access to the /home/website/ directory - While logged in as /myusername/

(IE So I do not need sudo (or any 'admin' command), to edit the files  )

---

### Post by aeiah on 2010-08-13
you should be able to add your username to the group of users allowed to edit your 'website' user's files using the 'users and groups' menu entry in administration

---

### Post by sarahfoxnz on 2010-08-13
System >> Admin >> User & Groups. (from my admin / my username)

I click on 'website' username >> Manage groups 

scroll down to find my username >> Click properties

Group members :- my username, website - both ticked. I click OK, then my admin password 

scroll down to find my 'websites' user >> Click properties

Group members :- my username, website - both ticked. I click OK, then my admin password 


I then go into 'nautilus' & I can't even create a directory or file in the /home/website/ directory...

Do I need to reboot ?? (I doubt it)

---

### Post by Noz3001 on 2010-08-13
well, if "website" is a user then you can su to it.

```
sudo su website
nautilus &
```

Should bring you into /home/website with all access

---

### Post by sarahfoxnz on 2010-08-13
Found solution

[http://ubuntuforums.org/showthread.php?t=1009520](http://ubuntuforums.org/showthread.php?t=1009520)

sudo chmod a+w /var/www


now I can edit it from my main a/c *without* sudo :)

---

### Post by RiceMonster on 2010-08-13
> **Noz3001 said:**
> well, if "website" is a user then you can su to it.

```
sudo su website
nautilus &
```

Should bring you into /home/website with all access

I don't see why you should run su with sudo. Root privilages are not required to switch to another account, only it's password.

---

### Post by sydbat on 2010-08-13
> **sarahfoxnz said:**
> Found solution

[http://ubuntuforums.org/showthread.php?t=1009520](http://ubuntuforums.org/showthread.php?t=1009520)

sudo chmod a+w /var/www


now I can edit it from my main a/c *without* sudo :)Glad you found this solution. It was one I was going to suggest.

---

### Post by Noz3001 on 2010-08-13
> **RiceMonster said:**
> I don't see why you should run su with sudo. Root privilages are not required to switch to another account, only it's password.

Yeah. I'm just used to typing sudo su root.

---


---
title: "Changing computer &amp; user names a bad idea?"
date: 2010-04-19
forum: General Help
---

### Post by GARoss on 2010-04-19
I'm giving an old computer to my sister & would like to change the computer name to her name - Geri. I was able to change the user name from *clear-desktop* to *geri-desktop* but can't find the right method to change the computer name without issues (see screen grabs). For example, I did Alt+F2 *gksuso nautilus* & navigated to the home folder & changed it from clear to geri. Ubuntu wouldn't boot after that, of course, so I booted to root & renamed it back to clear. Boots fine now. 
I'm thinking this is a bad idea as there are lots of references throughout the computer that has the original *clear* as the computer name but is there a safe way to do this?

---

### Post by Kai Summers on 2010-04-19
The two highlighted points on your screen shots show the user you are logged in as, why not create a new user 'geri' with the same user privs as 'clear' then delete the original user.

---

### Post by neur0 on 2010-04-19
How to change Computer name:
[http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name](http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name)

As for the user name, the best way would be to create a new user.

---

### Post by sandyd on 2010-04-19
```

gksudo gedit /etc/hostname
```
change it to whatever you want.

---

### Post by GARoss on 2010-04-19
> **Kai Summers said:**
> The two highlighted points on your screen shots show the user you are logged in as, why not create a new user 'geri' with the same user privs as 'clear' then delete the original user.

Thanks, that works. But now to migrate data like family photos & music. From the new user "geri" I tried *gksudo nautilus* & failed because of root privileges. I logged back as the original "clear" & I am able to copy Pictures & Music folders to "geri" but now I'm wondering if I delete the original "clear" would I lose all root privileges?

---

### Post by GARoss on 2010-04-19
> **carlee said:**
> ```

gksudo gedit /etc/hostname
```
change it to whatever you want.

I tried this earlier. It changed the desktop name from **clear-desktop** to **geri-desktop** only (as seen in screen grabs). Not the computer name.:(

---

### Post by philinux on 2010-04-19
You need to edit/change /etc/hosts too.

---

### Post by ajgreeny on 2010-04-19
In your original screenshots, **clear-desktop** is the computer name and **clear** is the username.  I am a little confused about which you really want to change, and I think you are confusing the two.

Once you have it as you want, and before you get rid of the first admin user (ie, clear), you will need to make sure the new user has admin privileges, most easily done as the first user in System ->Administration ->Users and Groups and needing root permisssions, hence doing it as first user.  Then copy all the first users home files from clear to newname user, and then change ownership of all the files with ```
sudo chown -R newname:newname /home/newname
```

---

### Post by GARoss on 2010-04-19
> **philinux said:**
> You need to edit/change /etc/hosts too.

> **carlee said:**
> ```

gksudo gedit /etc/hostname
```
change it to whatever you want.

Thanks for the responses. I tried both of these & neither of worked. 

My computer terminology might be the problem. In the 1st post, is "clear" the computer name? Clear is what to what I'm trying to change.

---

### Post by GARoss on 2010-04-19
> **ajgreeny said:**
> In your original screenshots, **clear-desktop** is the computer name and **clear** is the username.  I am a little confused about which you really want to change, and I think you are confusing the two.

Once you have it as you want, and before you get rid of the first admin user (ie, clear), you will need to make sure the new user has admin privileges, most easily done as the first user in System ->Administration ->Users and Groups and needing root permisssions, hence doing it as first user.  Then copy all the first users home files from clear to newname user, and then change ownership of all the files with ```
sudo chown -R newname:newname /home/newname
```

Yes, quite confused!:confused: Username is what I want to change.

So, to extend privileges to the new username "geri" I would open terminal from the original "clear-desktop" & type;

```
sudo chown -R geri:geri /home/geri
```?

---

### Post by ajgreeny on 2010-04-19
Not quite as you want things yet.

Firstly as the user "clear" (that is the username, the machine name is "clear-desktop") make the new user geri by going to System Administration Users and Groups.  This needs admin privileges to change anything, hence the need to use the user clear.  Make the user geri with admin privileges so it can use sudo, then do the chown command in terminal on all the files from clear;s home that you copied to the new geri's home.  That command simply changes ownership to geri.

I'm afraid I now have to go out so can't help more at the moment.  I'll check again later.

---

### Post by GARoss on 2010-04-19
At this point it reads - **clear@geri-desktop:~$**. That's close enough.

Thanks to everyone who tried to help!

---


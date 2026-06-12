---
title: "How can you assign a user profile to another user?"
date: 2011-12-03
forum: General Help
---

### Post by geek2330 on 2011-12-03
Got Ubuntu configured the way I want it with Cairo Dock and Compiz effects.
I'd like to have these settings applied to another user in the system, Desktop theme, startup options,etc.?

---

### Post by zero2xiii on 2011-12-03
Hay,

The easiest way I can think of (if its just from one user to another on the SAME MACHINE) is using the following command (from the user you wish the setting to changed):

```
cp -R /home/<USER FROM WHICH YOU WISH SETTINGS> /home/<USER YOU WANT NEW SETTINGS> 
```

**_Please note this is NOT tested_**

You can do the same manualy by going to the home directory of the user you want the settings coppied from (loged in as the other user for permission's sake) and then hitting ctrl+h to show hidden files, and copy all the files with a dot (.) and dubble dot (..) to the home directory of the user you wish the settings to be applied to. This should work for most of the programs. Backup first!! (the entire home directory if you can spare the space) and merge+replace all the files.

Good luck, but please be careful and make a full backup first! This is not guaranteed to work.

Cherz

---

### Post by ajgreeny on 2011-12-03
The command shown by zero2xiii will also copy over all the user's files and folders, which is probably not what you want, and may need sudo to run at all.  It would also probably require that you run the command ```
sudo chown -R *user*:*user* /home/*user*
``` from a user with admin permissions, substituting the new user name for where I show *user*.

Tell us in more detail if it is just the configuration that you want, or all files and folders as well.

---

### Post by philinux on 2011-12-03
New users accounts take the defaults from /etc/skel

So use gksu nautilus and copy any .config files into the above folder.

 [http://linuxers.org/howto/how-set-default-content-new-users-home-directory-using-etcskel](http://linuxers.org/howto/how-set-default-content-new-users-home-directory-using-etcskel)

---

### Post by geek2330 on 2011-12-03
No files/folders, I just want Cairo Dock, Compiz, Desktop Wallpaper, etc to display for that user as if it was me.

I am the main Admin on the laptop, that person is not.

See attachment, I want her Desktop to look the same with all my older Gnome bar on top and Cairo Dock loaded as well.

Thanks guys.

---

### Post by Lampi on 2011-12-03
the pure copy will most likely produce bogus results once you login the new user, because many config files will still contain the previous username instead of some user substitute (like $USER)

You can run
```
egrep -rcI "/home/<previous username>|<previous username>" /home/<new username>/
```
just to get the basic idea what I'm talking about

this will list all non-binary files still containing a reference to the previous user.

You can try to run this through some perl script, to remove all traces of the previous user.

I hope kde will improve this in the future, can't say whether it's better or worse in gnome ..

---

### Post by geek2330 on 2011-12-03
Sounds like nobody is confident with this as it may bring problems.
I will just setup her profile and go through the manual configuration item by item...

---

### Post by dcstar on 2011-12-03
> **geek2330 said:**
> Sounds like nobody is confident with this as it may bring problems.
I will just setup her profile and go through the manual configuration item by item...

All of the desktop settings will be in the hidden folders in the user's home folder.

If **you** can identify each one you just copy them from the original to the new user and change the ownership credentials to suit.

---


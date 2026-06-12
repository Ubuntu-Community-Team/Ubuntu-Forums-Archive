---
title: "Sharing wine installations with other users"
date: 2010-05-12
forum: General Help
---

### Post by blueyelabs on 2010-05-12
Hi All,

I know that there are posts on here describing various methods for sharing a wine installation across the system but I haven't managed to get them to work (you'd think that this is something that would have been implemented properly a LONG time ago. Crossover has a rubbish version of it but I wanted to get it to work in Wine).

Here's what I did (it works insofar as office 2003 can be used but the menu entries don't (as of yet) appear in the different users' menus):

[LIST=1]
[*]Regular install of wine, start wine on my profile and let it build all its stuff. DO NOT INSTALL ANY PROGRAMMES YET (I did the first time and it didn't work afterwards).

[*]Create user and group "wine" with disabled password/login and no home dir.

[*]Move system.reg and drive_c to /wine and chown wine:wine, chmod 0775 (both recursively, bien sur).

[*]Add all users to the "wine" group.

[*]Make symlinks to drive_c and system.reg in my .wine directory.

[*]Copy ~/.wine to all the other users' home directories, delete user specific registration files user.reg and userdef.reg. Chown the .wine directory for each user.

[*]Install Office 2003 (for me at least) or whatever programmes you want (I've only tried this is Office 2003).

[*] chown wine:wine /wine -R because your installation will have messed things up a bit.

[*]Now cd (in Terminal, obviously) to /wine/drive_c/users.

[*]If you ls you'll see a folder called Public and a folder with your user name (mine is "gideon"). cp your home directory (recursively again) for each of your other users who you want to be able to use wine. Chown their user folders to user_name:wine (recursively - I'm going to stop writing that, just assume it).

[*]su as each user, go into their user directory and you'll see something like this (ls -al):
```

drwxr-xr-x 13 gideon wine 4096 2010-05-12 13:09 .
drwxr-xr-x  8 wine   wine 4096 2010-05-12 13:31 ..
drwxr-xr-x  3 gideon wine 4096 2010-05-12 13:10 Application Data
drwxr-xr-x  2 gideon wine 4096 2010-05-12 12:48 Cookies
lrwxrwxrwx  1 gideon wine   20 2010-05-12 13:09 Desktop -> /home/gideon/Desktop
drwxr-xr-x  2 gideon wine 4096 2010-05-12 12:48 Favorites
drwxr-xr-x  5 gideon wine 4096 2010-05-12 12:48 Local Settings
lrwxrwxrwx  1 gideon wine   12 2010-05-12 13:09 My Documents -> /home/gideon
lrwxrwxrwx  1 gideon wine   18 2010-05-12 13:09 My Music -> /home/gideon/Music
lrwxrwxrwx  1 gideon wine   21 2010-05-12 13:09 My Pictures -> /home/gideon/Pictures
lrwxrwxrwx  1 gideon wine   19 2010-05-12 13:09 My Videos -> /home/gideon/Videos
drwxr-xr-x  2 gideon wine 4096 2010-05-12 12:48 NetHood
drwxr-xr-x  2 gideon wine 4096 2010-05-12 12:48 PrintHood
drwxr-xr-x  2 gideon wine 4096 2010-05-12 12:48 Recent
drwxr-xr-x  2 gideon wine 4096 2010-05-12 12:48 SendTo
drwxr-xr-x  3 gideon wine 4096 2010-05-12 13:12 Start Menu
drwxr-xr-x  2 gideon wine 4096 2010-05-12 13:14 Temp
drwxr-xr-x  2 gideon wine 4096 2010-05-12 12:48 Templates

```

[*]Execute the following (you can copy and paste this because it is ever so tedious to write out:
```

rm Desktop; ln -s ~/Desktop/ Desktop;
rm My\ Documents; ln -s ~/Documents/ My\ Documents;
rm My\ Music; ln -s ~/Music/ My\ Music;
rm My\ Pictures; ln -s ~/Pictures/ My\ Pictures;
rm My\ Videos; ln -s ~/Videos/ My\ Videos;

```
(remember to hit enter on the last one).

[*]Finally, chmod g+rw /wine -R so that the group can use the installation.

[*]Before each user uses the wine install get them to open winecfg and go to drives and click "autodetect" just to make sure the c:/ drive is working properly).
[/LIST]

So, it's not really a guide for beginners (n00bs as I believe some would call them). If such is required, ask and I might make it clearer.

I hope this helps someone.

Anyway, what works: running programmes (as far as I can tell) and using winecfg/the wine un-installer programme. What doesn't work is winemenubuilder. I get the following errors:
```

gideon@computer:~$ wine winemenubuilder
fixme:ole:CoInitializeSecurity (0x413ea8,-1,(nil),(nil),1,3,(nil),72,(nil)) - stub!
err:ole:CoGetClassObject class {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} not registered
err:ole:CoGetClassObject no class object {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} could be created for context 0x1

```

I also (and probably as a result of the prior problem but I'm not sure) can't get wine to make menu entries for the installed programmes for each user, it's a tad annoying.
Any ideas guys?

(If I sound ratty in this post it's because I have really quite bad flu at the moment, apologies).

---

### Post by blueyelabs on 2010-05-12
The problem with winemenubuilder is that you have to user wineprefix stuff and all that e.g.:
```

export WINEPREFIX=~/.wine; find $WINEPREFIX/dosdevices/c\: -name "*.lnk" -exec wine winemenubuilder '{}' \;

```

but this does not rebuild my applications menu. I tried copying everything in ~/.config/menus to each other user (because in there are all the wine application files) and even tried copying it to /etc/xdg/menus but to no avail. Nothing I do will make the MS office programmes appear in the menu for the other users...
Anyone?

---

### Post by rajanghanshyam on 2012-04-26
> **blueyelabs said:**
> The problem with winemenubuilder is that you have to user wineprefix stuff and all that e.g.:
```

export WINEPREFIX=~/.wine; find $WINEPREFIX/dosdevices/c\: -name "*.lnk" -exec wine winemenubuilder '{}' \;

```

but this does not rebuild my applications menu. I tried copying everything in ~/.config/menus to each other user (because in there are all the wine application files) and even tried copying it to /etc/xdg/menus but to no avail. Nothing I do will make the MS office programmes appear in the menu for the other users...
Anyone?

i have done all your given steps but still i have some confusion on point number 10.
all softwares are working but menu is not comming in all users...

Also, for number 10 you worte there to copy home directory that means .wine folder only or complete home directory..

---

### Post by rajanghanshyam on 2012-04-26
i have done all your given steps but still i have some confusion on point number 10.
all softwares are working but menu is not comming in all users...

Also, for number 10 you worte there to copy home directory that means .wine folder only or complete home directory..

---

### Post by nothingspecial on 2012-04-26
Hi, please start a new thread with as much details as you can about your problem.

This one is old.

Closed.

---


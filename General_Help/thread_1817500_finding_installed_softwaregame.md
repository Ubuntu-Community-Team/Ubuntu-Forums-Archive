---
title: "finding installed software/game"
date: 2011-08-03
forum: General Help
---

### Post by rahulbest on 2011-08-03
i installed vdrift in ubuntu...but i m nt able to find from where to run it...how u can find this???i encounter this problem many times

---

### Post by smurphy_it on 2011-08-03
Good day.  I don't use the app, but here a couple of things you could try in the cli.

```
find / -name vdrift
```

To get full package name, in case it's not vdrift.
```
dpkg --get-selections | grep -i vdrift
```

To get a listing of all of the files contained within a .deb package.
```
apt-get install apt-file
```
```
apt-file list package-name-goes-here
```

---

### Post by rahulbest on 2011-08-03
hey thnks i got the path...but how to run that...i m nt getting that

---

### Post by krytorii on 2011-08-03
If using natty, open the applications by pressing win+a or clicking the icon with a magnifying glass and a plus on the sidebar. Search for vdrift.


If that doesnt throw up any results click on "all applications" at the top right. Then click on games, and show all. It should be somewhere in there.

---

### Post by smurphy_it on 2011-08-03
Sounds like the program/app installed for you fine, that's good.  I take it, there wasn't a shortcut/link created for it and in your menu's anywhere's.  If not, you'll have to create one.

Right click the "Applications" menu item and choose "Edit Menus".  Find a convenient placeholder for it (internet, accessories, etc).  Click "New Item".  Give it a friendly name, and point it to the location you of the binary you found earlier.

Change the icon if you wish.  That should do it.

In the cli, you can navigate to your desktop (cd ~/Desktop) and then create a shortcut/symbolic link to it.

example:
```
ln -s /usr/bin/vdrift vdrift
```

---


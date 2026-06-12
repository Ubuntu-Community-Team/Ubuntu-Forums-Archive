---
title: "Firefox Profile Missing"
date: 2012-03-12
forum: General Help
---

### Post by winehouse711 on 2012-03-12
Hello, I have installed xubuntu onto my acer aspire one and have had no problems but this one.

I can not get firefox to open through any way except through the terminal.
The drop down menu ones don't work neither does the one on the dock every time i open through these i get, Profile Missing. you Firefox profile can not be loaded. it may be missing or inaccessible. 
Then if i try to set chromium as my default it pops up to choose preferred  application, too which i can only pick Debian sensible browser or firefox it can't find chromium.

the only thing i've tried is unstalling firefox and downloaded it again but gives me the same errors

Thank you for your time.

---

### Post by claracc on 2012-03-12
It seems you have a corrupted firefox profile, you will have to create a new one.

This link: [http://www.webgapps.org/tutorials/firefox/troubleshooting/fixing-corrupted-profiles](http://www.webgapps.org/tutorials/firefox/troubleshooting/fixing-corrupted-profiles) can help.

---

### Post by winehouse711 on 2012-03-12
It didn't help i followed the steps. made a new profile. start firefox. still gives me the error

any other ideas?

---

### Post by polt on 2012-03-12
You should be able to find out where Firefox is looking for the profile.  There is usually a hidden folder in your home folder with the Firefox preferences.  You can look at the profiles file in that directory to see what it is looking for.  I'm not sure if this is exactly the same in xubuntu, but on my computer it is:

```

~/.mozilla/firefox/profiles.ini

```

My file looks like this:

```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=5r93s2k1.default

```

The "IsRelative=1" tells whether to look for the profile directory in the same folder as profiles.ini  If you switch it to "IsRelative=0" then you will need to put the complete address to a folder on the "Path" line, rather than just putting the name of a directory.  So you should be able to find out, in this file, what directory Firefox is looking for, and then you can look to see if that directory exists.

---

### Post by Gremlinzzz on 2012-03-12
try deleting the  .mozilla folder it will get rid of old info:popcorn:

the one in show hidden files
you can delete the .macromedia folder while your at it
its flash player old info

---

### Post by kdford on 2012-12-07
Check your permissions on the ~/.mozilla (and subfolders/files).  It should be owned by the same user launching firefox.

If it is not, you can change ownership using
chmod user:group -R ~/.mozilla  <-(changesfolder/subfolders/files)
by default your user and group are the same so if your username is brian, you'd enter
sudo chmod brian:brian -R ~/.mozilla


Common way for this to happen -- If you rsync'd/copied a home folder from a previous install to a new install without regard for the filesystem of the backup media (maybe it was a filesystem that didn't speak unix style permissions).  Or ran a backup/copy as root, without preserving permissions during the copy...

update: Gremlinzzz's fix should work, but it is using a machete instead of a scalpel.  Of course if you don't want those old files and didn't intend them, or they came from a system with different FF version/plugins/etc/etc/etc, then Gremlinzzz's method would be the right way to go...  If your intention was to keep your profiles that you brought from elsewhere, you're going to want to change the owners/permissions

---

### Post by Rebelli0us on 2012-12-07
run 

firefox -profilemanager

check location of profile, also linux has huge permissions problem so check that too. You can create a new profile in that dialog, or copy your existing one to a new location.

---

### Post by kdford on 2012-12-08
> **Rebelli0us said:**
> run 

firefox -profilemanager

check location of profile, also linux has huge permissions problem so check that too. You can create a new profile in that dialog, or copy your existing one to a new location.

Alright, I can't resist asking.. What do you mean "linux has huge permissions problem"?

Just curious as to what you see as the problem.

---

### Post by Rebelli0us on 2012-12-08
> **kdford said:**
> Alright, I can't resist asking.. What do you mean "linux has huge permissions problem"?

Just curious as to what you see as the problem.

Because too often I’m prevented form using my computer and accessing my own files.

---

### Post by vasa1 on 2012-12-08
> **Rebelli0us said:**
> Because too often I’m prevented form using my computer and accessing my own files.
Never seen that.

---


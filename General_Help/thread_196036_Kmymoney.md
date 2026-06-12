---
title: "Kmymoney"
date: 2006-06-13
forum: General Help
---

### Post by Drifter on 2006-06-13
Could someone point me to a how to for installing kmymoney I have a tar.bz2 on my desktop. Thanks

---

### Post by eqisow on 2006-06-13
Delete the tar.gz file then go to the command line and type

```
sudo apt-get install kmymoney
```

That's it. :)

---

### Post by Drifter on 2006-06-13
[QUOTE=eqisow]Delete the tar.gz file then go to the command line and type

```
sudo apt-get install kmymoney
```

That's it. :)[/QUOTE]

This is what I got:

david@david-desktop:~$ sudo apt-get install kmymoney
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kmymoney
david@david-desktop:~$

---

### Post by eqisow on 2006-06-13
Sorry, I made a mistake.
```

sudo apt-get install kmymoney2
```

---

### Post by Drifter on 2006-06-13
[QUOTE=eqisow]Sorry, I made a mistake.
```

sudo apt-get install kmymoney2
```[/QUOTE]

go this this time:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kmymoney2
david@david-desktop:~$

---

### Post by eqisow on 2006-06-13
Hmm, have you added the extra repositories?

See: [Adding Repositories Howto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by Drifter on 2006-06-13
[QUOTE=eqisow]Hmm, have you added the extra repositories?

See: [Adding Repositories Howto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")[/QUOTE]

I can't follow this how to it is too confusing to me.  It appears to be for hoary not Dapper

---

### Post by eqisow on 2006-06-13
OK, then try the following at the command line:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

Now erase replace the entire contents of that file and replace it with contents of the following link:

[sources.list]("http://thepiratecove.org/files/sources.list")

Save and close gedit, then do the following in the command line:

```
gpg --keyserver subkeys.pgp.net --recv 1135D466
gpg --export --armor 1135D466 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv DD4D5088
gpg --export --armor DD4D5088 | sudo apt-key add -
```

Now try again to install KMyMoney:

```
sudo apt-get update
sudo apt-get install kmymoney2
```

*Note: This sources.list also includes new KDE, amarok, and Wine packages as well as various multimedia codecs. You may have some new updates to install after these changes.*

---


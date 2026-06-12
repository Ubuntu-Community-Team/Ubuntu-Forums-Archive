---
title: "flash runs root only"
date: 2010-04-23
forum: General Help
---

### Post by viralmeme on 2010-04-23
Installed Firefox, Installed flashplugin-nonfree using apt-get, run FF as root and flash plays ok. Run FF as user and no flash. It prompts to download plugins and then fails.

$sudo add-apt-repository ppa:mozillateam/firefox-stable
$sudo apt-get install firefox-3.6
$sudo apt-get install flashplugin-nonfree

---

### Post by dabl on 2010-04-23
Running GUI apps as root is a pretty good way to destroy your system.  :(

---

### Post by sisco311 on 2010-04-23
> **dabl said:**
> Running GUI apps as root is a pretty good way to destroy your system.  :(

+1

@OP: Did you use sudo to run it as root?

If yes, then run:
```
sudo chown -R $USER: ~/.mozilla
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by lovinglinux on 2010-04-23
> **sisco311 said:**
> +1

@OP: Did you use sudo to run it as root?

If yes, then run:
```
sudo chown -R $USER: ~/.mozilla
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

+1

Also see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by viralmeme on 2010-04-24
> **sisco311 said:**
> @OP: Did you use sudo to run it as root?

I checked the .mozilla directory, all files are owned by ubuntu. The thing is Flash works on Opera as user, and Flash works on FF as root, but don't work on FF as user. There also don't seem to be a plugin directory in .mozilla, would that have an effect. It seems to be an issue with the location of libflashplayer.so ..

Sucess, I created a plugins dir in ./mozilla and linked to /usr/lib/flashplugin-installer/libflashplayer.so

cd /home/user/.mozilla
mkdir plugins
cd plugins
ln -s /usr/lib/flashplugin-installer/libflashplayer.so ./

---

### Post by sisco311 on 2010-04-24
Try to create a new profile:
```
firefox -ProfileManager
```

---


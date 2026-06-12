---
title: "Could not download all repository indexes"
date: 2011-09-19
forum: General Help
---

### Post by griffsterb on 2011-09-19
So I always have a little "!" icon on the panel across the top of my screen. I right click it, click "Check for Updates" and I always get this error:

"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/tuheum/equinox/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/tuheum/equinox/ubuntu/dists/natty/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/tuheum/equinox/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/tuheum/equinox/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead."

Doesn't really seem to be affecting anything but it's annoying to have this error icon on my panel all the time... I am not very good with Linux, still a relatively new user. Does anyone know of a way I can go about fixing this? Thank you very much.

---

### Post by Elfy on 2011-09-19
Go to Software Sources - Other Software - disable the ppa's causing the problem and reload when prompted.

You can get there from the update manager - settings button at the bottom left or from the software centre - Edit - software sources

---

### Post by griffsterb on 2011-09-19
> **forestpiskie said:**
> Go to Software Sources - Other Software - disable the ppa's causing the problem and reload when prompted.

You can get there from the update manager - settings button at the bottom left or from the software centre - Edit - software sources

Interesting. Both of the URLs giving me fits are not listed under "Other Software".

---

### Post by drs305 on 2011-09-19
You could try to remove them manually.

First check your sources.list file to see if they exist. We'll make a backup copy of the file first and then open it as root for editing:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
gksu gedit /etc/apt/sources.list
```

If you find them listed, either completely delete the line or place a # symbol at the start of the line. If you make changes, save the file.

If they are not specified in the file, close it and run this command to open the root file browser:
```
gksu nautilus /etc/apt/sources.list.d
```
If you see the ppa files here, either delete them or move them to the desktop.

After making either change, update the repository list in the manner you normally use and check for errors.

---


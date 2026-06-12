---
title: "Kubuntu Jaunty broken apt-get/aptitude"
date: 2009-11-20
forum: General Help
---

### Post by iceburnt on 2009-11-20
I can't run any apt-get or aptitude command or install anything due to unmet dependencies/unable to load shared library. the unmet dependency is libapt-pkg-libc6.9-6____ 

I'm a complete Newbie and have been having problems with jaunty ever since I installed.

---

### Post by Giblet5 on 2009-11-20
Open a terminal window and enter ```
sudo apt-get install -f
```

Post the output in a CODE block ('#' icon at the top of the thread comment editor).


Edit assuming OP abandoned issue.

---

### Post by iceburnt on 2009-11-20
I ran the command and here is the output-

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  apport apport-qt apt-transport-https apt-utils apt-xapian-index aptitude command-not-found gdebi-core gdebi-kde
  install-package jockey-common jockey-kde kpackagekit kubuntu-desktop language-selector-qt libept0 network-manager
  packagekit packagekit-backend-apt plasma-widget-network-manager python-apport python-apt python-launchpad-bugs
  python-software-properties software-properties-kde tasksel tasksel-data ubuntu-minimal ubuntu-standard
  unattended-upgrades update-manager-core update-manager-kde update-notifier-common update-notifier-kde
0 upgraded, 0 newly installed, 34 to remove and 0 not upgraded.
After this operation, 34.7MB disk space will be freed.

```

---

### Post by iceburnt on 2009-11-24
*bump*

---

### Post by iceburnt on 2009-11-27
*RE-BUMP*'

Somebody please read this....

---

### Post by Zorael on 2009-11-27
Is aptitude more verbose?
```
$ sudo aptitude update

# this next command should offer you solutions, try declining until
# you get a solution that doesn't involve removing a bunch of
# packages but instead installing something

$ sudo aptitude install -fvvP

$ sudo aptitude full-upgrade
```
Paste the output here if you're in doubt.

---

### Post by iceburnt on 2009-11-27
All Three commands have the same outcome.

```
aptitude: error while loading shared libraries: libapt-pkg-libc6.9-6.so.4.7: cannot open shared object file: No such file or directory

```

Basically, nothing with aptitude/apt works.

---

### Post by Zorael on 2009-11-27
> **iceburnt said:**
> Basically, nothing with aptitude/apt works.
But, how did you manage to get the output pasted earlier?
> **iceburnt said:**
> I ran the command and here is the output-

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  apport apport-qt apt-transport-https apt-utils apt-xapian-index aptitude command-not-found gdebi-core gdebi-kde
  install-package jockey-common jockey-kde kpackagekit kubuntu-desktop language-selector-qt libept0 network-manager
  packagekit packagekit-backend-apt plasma-widget-network-manager python-apport python-apt python-launchpad-bugs
  python-software-properties software-properties-kde tasksel tasksel-data ubuntu-minimal ubuntu-standard
  unattended-upgrades update-manager-core update-manager-kde update-notifier-common update-notifier-kde
0 upgraded, 0 newly installed, 34 to remove and 0 not upgraded.
After this operation, 34.7MB disk space will be freed.

```

Anyway, the file you're mentioning is part of the **apt** package. In the best case scenario, there's just a broken symlink. In the worst case, you'd just have to download the apt package and install it manually.

Paste the output of the following;
```
$ ls -l /usr/lib/libapt*
```


If you want to try to simply reinstall the package, try this in a directory you can write to (like your home directory).
```
$ wget http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.20.2ubuntu6_i386.deb
$ sudo dpkg -i apt_0.7.20.2ubuntu6*.deb
```

Replace the wget link with [http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.20.2ubuntu6_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.20.2ubuntu6_amd64.deb) if you're running a 64-bit system.

---

### Post by iceburnt on 2009-11-27
Oky so here's the output of the first command-

```
 lrwxrwxrwx 1 root root     30 2009-11-13 21:44 /usr/lib/libapt-inst-libc6.9-6.so.1.1 -> libapt-inst-libc6.9-6.so.1.1.0
-rw-r--r-- 1 root root  71484 2009-04-17 09:57 /usr/lib/libapt-inst-libc6.9-6.so.1.1.0
lrwxrwxrwx 1 root root     29 2009-11-14 22:36 /usr/lib/libapt-pkg-libc6.7-6.so.4.6 -> libapt-pkg-libc6.7-6.so.4.6.0
-rw-r--r-- 1 root root 774436 2009-04-21 01:24 /usr/lib/libapt-pkg-libc6.7-6.so.4.6.0

```

---

### Post by iceburnt on 2009-11-27
I'm running the second command right now but I don't know if the package will work. My Kpackagekit is crashing to for some reason.

---

### Post by Zorael on 2009-11-27
```
lrwxrwxrwx 1 root root     29 2009-11-14 22:36 /usr/lib/libapt-pkg-libc6.7-6.so.4.6 -> libapt-pkg-libc6.7-6.so.4.6.0
-rw-r--r-- 1 root root 774436 2009-04-21 01:24 /usr/lib/libapt-pkg-libc6.7-6.so.4.6.0

```
```
libapt-pkg-libc6.9-6.so.4.7
```
I don't know why, but the name of your symlink suggests it's of an old version. For comparison;
```
[COLOR="Lime"]libapt-pkg-libc6.9-6.so.4.7[/COLOR]      # what apt wants
[color="red"]libapt-pkg-libc6.7-6.so.4.6.0[/color]    # what apt has
[color="red"]libapt-pkg-libc6.7-6.so.4.6[/color]
```

You may want to try to just fetch and install that apt package and see if it solves things. Unless of course, that package has the old one and for some reason you have some newer package that expects a newer. You haven't mixed Jaunty and Karmic repos, I assume?

The workaround would be to manually make a new symlink, but whatwith the version mismatch it may not work. Can't really hurt, though.
```
$ sudo ln -s [COLOR="Red"]/usr/lib/libapt-pkg-libc6.7-6.so.4.6[/COLOR] [COLOR="Lime"]/usr/lib/libapt-pkg-libc6.9-6.so.4.7[/COLOR]

$ sudo aptitude update
$ sudo aptitude install -fvP   # see if you can get it to just upgrade/downgrade and not remove
$ sudo aptitude full-upgrade
```

---

### Post by iceburnt on 2009-11-27
I LOVE YOU. It's working.

---

### Post by Zorael on 2009-11-27
Cheers. :3

Might want to mark thread as solved.

---

### Post by iceburnt on 2009-11-29
Ok, It worked for a while but today while trying to install synaptic (which I had forgotten I alreadt had) Gdebi came up with a dependency error. So I ran 

```
 sudo apt-get install -f
```

and got this output 

```
 apport apport-qt apt-transport-https apt-utils apt-xapian-index aptitude command-not-found gdebi-core gdebi-kde install-package jockey-common jockey-kde kpackagekit
  kubuntu-desktop language-selector-qt libept0 network-manager packagekit-backend-apt plasma-widget-network-manager python-apport python-apt python-launchpad-bugs
  python-software-properties software-properties-gtk software-properties-kde synaptic tasksel tasksel-data ubuntu-minimal ubuntu-standard unattended-upgrades update-manager-core
  update-manager-kde update-notifier-common update-notifier-kde 
```


I'm pretty sure I'm not supposed to remove half of those so I thought I'd unsolve this thread. Reinstalling apt comes up with an all dependencies could not be satisfied or something like that. the troublesome package again is 
libapt-pkg-libc6.9-6-4.8

---

### Post by Zorael on 2009-11-29
Have you mixed repositories? Some debian ones, some weird ppas, Karmic repos?

Also;
> **iceburnt said:**
> Reinstalling apt comes up with an all dependencies could not be satisfied or something like that. the troublesome package again is 
libapt-pkg-libc6.9-6-**4.8**
```
libapt-pkg-libc6.9-6.so.**4.7**
```
Is this a typo or is it now asking for a **4.8** version? We faked/symlinked a **4.7** version earlier, so you would have to redo it as a **4.8** one.

The Jaunty apt contains;
```
/usr/lib/libapt-pkg-libc6.9-6.so.**4.7**
/usr/lib/libapt-pkg-libc6.9-6.so.**4.7**.0
```
...so if anything is asking for anything later than 4.7, it sounds like it's beyond Jaunty.

What does it say about the apt you're using?
```
$ apt-cache policy apt
```

Also, please don't use apt-get when trying to resolve this, as it will simply give up and tell you to remove stuff when it gets complicated. aptitude may instead offer downgrades, in case version inconsistencies are causing this.

---

### Post by iceburnt on 2009-11-29
You're right. That was a typo, It's 4.**_7_**

Output of command -

```

apt:
  Installed: 0.7.24
  Candidate: 0.7.24
  Version table:
 *** 0.7.24 0
        100 /var/lib/dpkg/status
     0.7.20.2ubuntu6 0
        500 http://archive.mitra.net.np jaunty/main Packages

```

---

### Post by Zorael on 2009-11-29
> **iceburnt said:**
> ```

apt:
  Installed: 0.7.24
  Candidate: 0.7.24
  Version table:
 *** 0.7.24 0
        100 **/var/lib/dpkg/status**
     0.7.20.2ubuntu6 0
        500 http://archive.mitra.net.np jaunty/main Packages

```
This suggests you have a later version of apt installed than what is available from the repos. You have 0.7.**24**, while the Jaunty repos have 0.7.**20**. 0.7.**24** isn't even in Karmic which has 0.7.**23** (as does Lucid so far).

Either you've downloaded it and installed it manually, or it was briefly in someone's PPA that you had enabled as a software source. If so it's now deleted, at least; the "*/var/lib/dpkg/status*" string suggests that apt-cache can't resolve where it came from, only that it's currently installed. It's certainly not the apt I linked to earlier, which is 0.7.**20**. So, time to install that.

Download this [i386](http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.20.2ubuntu6_i386.deb) or this [amd64](http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.20.2ubuntu6_amd64.deb) package and install with 'dpkg -i'.

```
$ cd
$ wget http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.20.2ubuntu6_i386.deb
$ dpkg -i apt_0.7.20.2ubuntu6*.deb

$ sudo aptitude update
$ sudo aptitude full-upgrade
```
As earlier, replace the URL with [http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.20.2ubuntu6_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.20.2ubuntu6_amd64.deb) if you have a 64-bit installation.

---

### Post by iceburnt on 2009-11-29
output- 

```
 --2009-11-29 21:31:47--  http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.20.2ubuntu6_i386.de
Resolving mirrors.kernel.org... 149.20.20.135, 199.6.1.174, 204.152.191.39, ...
Connecting to mirrors.kernel.org|149.20.20.135|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-11-29 21:31:49 ERROR 404: Not Found.

```

---

### Post by Zorael on 2009-11-29
```
http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.20.2ubuntu6_i386.de___
```
You're missing a **b** there.

Also see [http://packages.ubuntu.com/jaunty/i386/apt/download](http://packages.ubuntu.com/jaunty/i386/apt/download) for other mirrors.

---

### Post by iceburnt on 2009-11-30
Fixed. If I reopen this thrad again I'll PM you.

---


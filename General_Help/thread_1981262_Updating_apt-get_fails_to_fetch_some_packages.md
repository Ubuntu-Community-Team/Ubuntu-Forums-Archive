---
title: "Updating apt-get fails to fetch some packages"
date: 2012-05-16
forum: General Help
---

### Post by airspoon on 2012-05-16
Hello, 

I'm running Gnome-Shell on Ubuntu 12.04 and while trying to run 'sudo apt-get update', it's telling me that it fails to fetch some packages and that some index files failed to download.

Here is the actual C & P from the terminal (end):
```
Fetched 19.2 MB in 15s (1,250 kB/s)                                            
W: Failed to fetch http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Any and all help would be greatly appreciated. Thanks!

---

### Post by wilee-nilee on 2012-05-16
Check the ppa no precise release I can see, and last update 11/2011

[https://launchpad.net/~killeroid/+archive/ppa]("https://launchpad.net/%7Ekilleroid/+archive/ppa")

I would comment it out in software sources or remove it, it seems if you are running precise.

---

### Post by cortman on 2012-05-16
Looks like wilee-nilee is correct; the latest version offered is Mavirick (10.10). I'd remove the ppa from your sources.list.

```
gksu gedit /etc/apt/sources.list
```

Delete the lines for the killeroid repositories and save.

---

### Post by kc1di on 2012-05-16
> **airspoon said:**
> Hello, 

I'm running Gnome-Shell on Ubuntu 12.04 and while trying to run 'sudo apt-get update', it's telling me that it fails to fetch some packages and that some index files failed to download.

Here is the actual C & P from the terminal (end):
```
Fetched 19.2 MB in 15s (1,250 kB/s)                                            
W: Failed to fetch http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Any and all help would be greatly appreciated. Thanks!

It's telling you it can not find The ppa index for Killeroid.
that may mean the repository is temporarily off line or that it no longer exists at that address.

I'm not sure what that PPA was for you must have added it at some point to install something.

but you can stop the warning messages if you want by following the instructions on this page for removing the PPA.

[http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html]("http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html")

---

### Post by airspoon on 2012-05-16
Thanks for the replies! I went into the sources.list and can't find anything for killeroid. What's a little scary, is that I recently installed Ubuntu on this brand new machine only a week or two ago and don't remember adding that PPA at all. Could it have been added from a virus on my android mobile?

Following the instructions in the link posted by 'kc1di' isn't working either, so I tried to do it through the Software Center. I can actually see the killeroid in the Software Center, but it isn't allowing me to uncheck the PPA. Instead, it only crashes (and the boxes remained checked).

---

### Post by airspoon on 2012-05-16
Okay, after a quick google search, I believe that the PPA was added by me for tint2. If I find a way to remove it, will it kill my tint2? Is tint2 not yet ready for 12.04? Thanks.

---

### Post by kc1di on 2012-05-16
> **airspoon said:**
> Okay, after a quick google search, I believe that the PPA was added by me for tint2. If I find a way to remove it, will it kill my tint2? Is tint2 not yet ready for 12.04? Thanks.

Here's another page for a program called ppa-purge it may be of help.

[http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/]("http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/")

Also try this in a terminal:
```
sudo apt-get autoclean
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update 
```

---

### Post by wilee-nilee on 2012-05-16
I see tint2 0.11 in my synaptic in the development, must be in precise repos to, you have gotten no updates anyway. Should be okay without the ppa.

---

### Post by CatKiller on 2012-05-16
Removing a repository will not remove the packages installed from that repository, it just means that you won't get updates from that repository. Since you aren't getting them anyway, that's unlikely to affect you much.

---

### Post by cortman on 2012-05-16
> **airspoon said:**
> Thanks for the replies! I went into the sources.list and can't find anything for killeroid. What's a little scary, is that I recently installed Ubuntu on this brand new machine only a week or two ago and don't remember adding that PPA at all. Could it have been added from a virus on my android mobile?

Following the instructions in the link posted by 'kc1di' isn't working either, so I tried to do it through the Software Center. I can actually see the killeroid in the Software Center, but it isn't allowing me to uncheck the PPA. Instead, it only crashes (and the boxes remained checked).

Run

```
gksu nautilus
```

And go to /etc/apt/sources.list.d. There's probably a killeroid file in there. Delete it.

---

### Post by loklaan on 2012-05-16
If you prefer GUI, you can add/edit/remove repositories with Ubuntu Software Center. In the Edit menu you can find *Software Sources*. Your current ppa's etc etc are in the *Other Software* tab.

---


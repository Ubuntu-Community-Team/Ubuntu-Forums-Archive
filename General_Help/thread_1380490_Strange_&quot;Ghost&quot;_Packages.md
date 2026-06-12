---
title: "Strange &quot;Ghost&quot; Packages"
date: 2010-01-13
forum: General Help
---

### Post by Kcj1993 on 2010-01-13
I was trying to fix a problem with Openshot not starting and I foud this:
[ATTACH]143532[/ATTACH]
[ATTACH]143533[/ATTACH]

Can someone please explain this and/or help me fix it?

---

### Post by Kcj1993 on 2010-01-13
I'm running Ubuntu 9.10 32 bit

---

### Post by Mr Nemo on 2010-01-13
Can you elaborate? Try to remove/reinstall the packages through the terminal or refine your search.

---

### Post by Kcj1993 on 2010-01-13
Please look at the images. The conflicting packages are not installed and I can't even find them. They have been installed from .deb packages in the past but they were uninstalled.

---

### Post by Mr Nemo on 2010-01-13
You may want to try and purge openshot and then completely reinstall it.

---

### Post by Kcj1993 on 2010-01-13
I've done that

---

### Post by running_rabbit07 on 2010-01-13
```
sudo apt-get autoremove
``` may clean it up.

---

### Post by AlexandreP on 2010-01-13
> **Kcj1993 said:**
> I was trying to fix a problem with Openshot not starting and I foud this:
[ATTACH]143532[/ATTACH]
[ATTACH]143533[/ATTACH]

Can someone please explain this and/or help me fix it?

It just mean that, when trying to install the *openshot* package from the repos, if Synaptic finds that packages named *mlt-python*, *openshot-ffmpeg*, *openshot-frei0r*, etc. are listed as installed packages, it will uninstall them. Their contents would conflict with the ones installed by the *openshot* package and its dependancies.

Now, there is no problem: these packages are not installed. Synaptic even has no packages of these names in its list. So there should be no conflict problem when installing OpenShot.

---

### Post by Kcj1993 on 2010-01-13
> **AlexandreP said:**
> It just mean that, when trying to install the *openshot* package from the repos, if Synaptic finds that packages named *mlt-python*, *openshot-ffmpeg*, *openshot-frei0r*, etc. are listed as installed packages, it will uninstall them. Their contents would conflict with the ones installed by the *openshot* package and its dependancies.

Now, there is no problem: these packages are not installed. Synaptic even has no packages of these names in its list. So there should be no conflict problem when installing OpenShot.
So this is just a bug and is a non-issue and I can ignore it? 
BTW The pakages listed as conflicts are part of an older version of openshot that was installed using .deb packages and have been uninstalled, I am trying to get openshot v1 working and I found this while troubleshooting.

---

### Post by ev0x on 2010-01-13
[FONT=Arial][SIZE=2]Could try this..


```
rm /var/lib/dpkg/info/openshot*;* dpkg* --remove --force-remove-reinstreq* openshot;*  apt-get autoclean; apt-get clean; apt-get update; apt-get -f install
```See if that makes em go..[/SIZE][/FONT]

---

### Post by AlexandreP on 2010-01-14
> **Kcj1993 said:**
> So this is just a bug and is a non-issue and I can ignore it? 
BTW The pakages listed as conflicts are part of an older version of openshot that was installed using .deb packages and have been uninstalled, I am trying to get openshot v1 working and I found this while troubleshooting.
No, it's not a bug, but yes, this is a non-issue and you can ignore it. ;)

These *conflicts:* lines are instructions given to Synaptic to uninstall any packages of these names, if (1)Synaptic finds these packages are available in its packages list, and (2)Synaptic finds these packages are installed.

If these packages are not installed nor are even listed in Synaptic, then Synaptic won't take any special action.

These *conflicts:* instructions are actually given to uninstall previous OpenShot packages, in order to avoid conflicts with the new OpenShot version. Probably that packages names and/or dependancies changed from the previous OpenShot version, so to avoid any conflict with a previous OpenShot installation, anything related to OpenShot should be uninstalled. This is why the *conflicts:* instructions exist.

---

### Post by Kcj1993 on 2010-11-12
Wow. I forgot I started this thread. I didn't even thank you guys for the help. How rude of me.

Thanks for the help. :)

---


---
title: "About To Compile WICD, Need Help First"
date: 2009-07-31
forum: General Help
---

### Post by jlacroix on 2009-07-31
Here's the scoop. I am using Kubuntu, and the plasma widget that it comes with isn't adequate for me. I prefer wicd, even in KDE. With my laptop, the version of wicd in the Ubuntu repository is unstable (my wireless works 100% fine with Gnome's network manager) so I figured I would compile a fresh copy of wicd. Ubuntu Jaunty ships version 1.5.9 of Wicd I believe, and the latest is 1.6.2. I figured that I would try the latest version. I will compile this when I get home, but first I want to get some questions answered so I know what I'm in store for. Here are my questions.

1.) I already have all of the dependencies satisfied so that should not be an issue. However, since I'll be removing Jaunty's wicd package and compiling my own, will "apt-get autoremove" still remove the dependencies since I'm not using Ubuntu's precompiled package? I am just curious if "autoremove" can tell the difference between packages installed from source and those installed from binaries.

2.) If possible, how could I possibly use the wicd source and create my own .deb package so if I reinstall Kubuntu I can easilly reinstall wicd?

3.) The INSTALL text file in the source tree says that I would need to add the scripts to startup and there are no instructions for doing that because it's distribution independent. Does anyone know how I would compensate for this and set it up properly?

4.) Since I'm installing from source, is there anything I need to do to compile it to be a native 64-bit build when creating my .deb binary?

Thank you guys so much. I'm not very experienced with building packages, but in this case I see no other way. Kubuntu's plasmawidget-network-manager (or whatever it's called) is jank. Wicd worked fine with my other laptop with the same router so I'm hoping it works fine when I update it to run on my new laptop.

FYI: My laptop is a Dell Inspiron 15n that shipped with Ubuntu preinstalled.

---

### Post by cariboo on 2009-07-31
Use:

```
sudo apt-get purge wicd
```

To completely remove the Ubuntu version of wicd. Use:

```
sudo apt-get autoremove
```

to get rid of any unneeded dependencies, this will also clean out the archived packages in /var/cache/apt/archives.

---

### Post by SuperSonic4 on 2009-07-31
> **jlacroix said:**
> 1.) I already have all of the dependencies satisfied so that should not be an issue. However, since I'll be removing Jaunty's wicd package and compiling my own, will "apt-get autoremove" still remove the dependencies since I'm not using Ubuntu's precompiled package? I am just curious if "autoremove" can tell the difference between packages installed from source and those installed from binaries.

Don't think so, just using apt-get remove should be ok.

> 2.) If possible, how could I possibly use the wicd source and create my own .deb package so if I reinstall Kubuntu I can easilly reinstall wicd?

Yeah, it uses the checkinstall package: ```
sudo apt-get install checkinstall
``` This will make a deb and install it for easy removal via synaptic.

> 3.) The INSTALL text file in the source tree says that I would need to add the scripts to startup and there are no instructions for doing that because it's distribution independent. Does anyone know how I would compensate for this and set it up properly?

I believe it goes into /etc/init.d in kubuntu but don't quote me on it. 

[/QUOTE]

No, it ought to be fine:

---

### Post by Zorael on 2009-07-31
One way would be to completely purge wicd (with the commands listed earlier), then do **sudo build-dep wicd** to get the dependencies needed to compile it.

Then fetch the current repository source with **apt-get source wicd**, and *overwrite* files in the directory it creates with the newer source you downloaded. That way you would have the install script and all the debian bits from the Jaunty version of wicd, but the newer source.

Add an entry to the **debian/changelog** file to make it a newer version, and finally boil it down into a .deb for easy installation, using the method of choice.

---

### Post by jlacroix on 2009-07-31
> **cariboo907 said:**
> Use:

```
sudo apt-get purge wicd
```

Use:

```
sudo apt-get autoremove
```

to get rid of any unneeded dependencies, this will also clean out the archived packages in /var/cache/apt/archives.

The thing is, wicd is still going to need those packages. I want to make sure that the next time I do "sudo apt-get autoremove" it won't remove wicd's dependencies, since I installed wicd from source and not a deb package I'm wondering if autoremove will take that into consideration or would it think that those packages weren't needed?

> **SuperSonic4 said:**
> 
Yeah, it uses the checkinstall package: ```
sudo apt-get install checkinstall
``` This will make a deb and install it for easy removal via synaptic.



I believe it goes into /etc/init.d in kubuntu but don't quote me on it. 



So checkinstall is what we use to create deb packages? How do I use it?

> **Zorael said:**
> One way would be to completely purge wicd (with the commands listed earlier), then do **sudo build-dep wicd** to get the dependencies needed to compile it.

Then fetch the current repository source with **apt-get source wicd**, and *overwrite* files in the directory it creates with the newer source you downloaded. That way you would have the install script and all the debian bits from the Jaunty version of wicd, but the newer source.

Add an entry to the **debian/changelog** file to make it a newer version, and finally boil it down into a .deb for easy installation, using the method of choice.

Thank you. However, the version that ships with Jaunty is old and I fear the source would be too. Wicd is up to version 1.6.2 or so, and I think I'd better go with the newest stable source, right?

Edit: Nevermind, I misread your post.

Thank you guys for everything. :)

---

### Post by ryokea on 2009-08-07
You should be able to just purge Wicd and use the Wicd's repos to install the latest version, that is what worked for me at least. Took me a few minutes to figure out why it wasn't upgrading but it worked smoothly after purging. 1.6.2 is a nice improvement over 1.5.9

---

### Post by jlacroix on 2009-08-08
> **ryokea said:**
> You should be able to just purge Wicd and use the Wicd's repos to install the latest version, that is what worked for me at least. Took me a few minutes to figure out why it wasn't upgrading but it worked smoothly after purging. 1.6.2 is a nice improvement over 1.5.9

Thank you! Using the repository, I was able to get the latest version. It does seem to be a valid improvement. I didn't even notice that there was a repository. Thanks again.

---


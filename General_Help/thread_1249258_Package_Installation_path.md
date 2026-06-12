---
title: "Package Installation path"
date: 2009-08-25
forum: General Help
---

### Post by satish_j on 2009-08-25
Can anyone tell me the path where the files are copied/installed when we use synaptic package manager to download any package??
I suppose there must be some default path for all packages installed in this way.Like in windows,it is C:\Program files\...

---

### Post by mcduck on 2009-08-25
There is no such thing, different files go to different place based on the purpose of the file, not the package in which they belong.

For example the executable binary goes to /usr/bin, graphics and icons to /usr/share/pixmpas and /usr/share/icons, system-wide configuration to &/etc, documentation to /usr/share/docs and so on.. The rest willl usualy end in /usr/share/*programname*.

---

### Post by 3rdalbum on 2009-08-25
> **satish_j said:**
> Can anyone tell me the path where the files are copied/installed when we use synaptic package manager to download any package??
I suppose there must be some default path for all packages installed in this way.Like in windows,it is C:\Program files\...

If you need to know precisely what has been installed where, go to Synaptic and find the package. Right-click it and go to Properties. Click the "Installed Files" tab.

If you just want to make a launcher in your Applications menu, the name of the program will suffice as the "command".

---

### Post by satish_j on 2009-08-25
> **mcduck said:**
> There is no such thing, different files go to different place based on the purpose of the file, not the package in which they belong.

For example the executable binary goes to /usr/bin, graphics and icons to /usr/share/pixmpas and /usr/share/icons, system-wide configuration to &/etc, documentation to /usr/share/docs and so on.. The rest willl usualy end in /usr/share/*programname*.
Very sad...for first time,i have come across a feature of Ubuntu i think i do not like(i think this is not the proper management of files).
Anyways,do you mean that executable binary of _every package_ goes to /usr/bin.Likewise,docs of _every package_ to /usr/share/docs,etc,

---

### Post by mcduck on 2009-08-25
> **satish_j said:**
> Very sad...for first time,i have come across a feature of Ubuntu i think i do not like(i think this is not the proper management of files).
Anyways,do you mean that executable binary of _every package_ goes to /usr/bin.Likewise,docs of _every package_ to /usr/share/docs,etc,

Yes, these locations apply to all programs. It really makes sense after you get used to it, this way you never need to browse around the file system to find stuff like executable files or docs. You already know where they are, regardless of what the program is.

If you want to find out where some program's files are, you can use the "whereis"-command, although after learning the locations of most common file types that's not something you'd usually ever need to do. 

(for example "whereis firefox" will list all the directories where Firefox has installed it's files).

edit: Honestly, I think this makes a lot more sense than the Windows way. I sort all the things I use at home based on what they are for, kitchen stuff in kitchen, books in bookshelf, screwdrivers and such stuff in their own place etc. What I *don't* do is pile them all in one stack arranged by name or manufacturer. ;)

---

### Post by satish_j on 2009-08-25
Yeah,i think you are also right.Once i get used to things Ubuntu way,it will seem sensible to me as well.
BTW,what about deb packages installed manually.Does these also have any specific path or it depends how deb package was created??

---

### Post by mcduck on 2009-08-25
> **satish_j said:**
> Yeah,i think you are also right.Once i get used to things Ubuntu way,it will seem sensible to me as well.
BTW,what about deb packages installed manually.Does these also have any specific path or it depends how deb package was created??

Manually installed .deb packages are no different from the .deb packages downloaded from repositories. They are installed exactly the same way, using exactly the same tools.

---

### Post by 3rdalbum on 2009-08-25
> **satish_j said:**
> Yeah,i think you are also right.Once i get used to things Ubuntu way,it will seem sensible to me as well.
BTW,what about deb packages installed manually.Does these also have any specific path or it depends how deb package was created??

When you install things in Synaptic, you're actually just downloading .deb packages and installing them. As with Synaptic, it depends on what the maker of the package has specified, but yes it's likely that there will be files installed into lots of different places.

The system makes a lot of sense - for instance, the piece of code that manages your Applications menu doesn't have to scoot all over the disk for application launchers; they are all in one place. Programs can install libraries (reusable pieces of code) where other programs know where to find them.

In any case, you don't need to worry about this as there simply is no reason for you to touch these files.

---

### Post by satish_j on 2009-08-25
Thanks for your replies.Lastly,is there anyway i can get to show the path where application resides when i hover over any application in Applications menu.i.e Tooltip kinda thing.
@3rdalbum
your workaround to right click and select 'installed files' is also good,but honestly,i dont like to open synaptic just for knowing the path,as it keeps asking for root password(which irritates me a lot)

---

### Post by CatKiller on 2009-08-25
> **satish_j said:**
> Lastly,is there anyway i can get to show the path where application resides when i hover over any application in Applications menu.i.e Tooltip kinda thing.

Not as far as I'm aware. But you can just right-click on the menu, select Edit Menus, find your application and select Properties to see exactly what your launcher does. The location of the executable can be found with *which programname*, but that doesn't tell you what options might be passed to it by the launcher.

---

### Post by 3rdalbum on 2009-08-25
> **satish_j said:**
> 
@3rdalbum
your workaround to right click and select 'installed files' is also good,but honestly,i dont like to open synaptic just for knowing the path,as it keeps asking for root password(which irritates me a lot)

Having your computer compromised is much worse than being asked for a password. Trust me on this (and they *are* mutually exclusive).

I still have no idea why you need to know where packages have been installed to; it's so incredibly rare that you'd need to look at the Installed Files list.

---

### Post by satish_j on 2009-08-25
The reason I need to know the path is that,if in future,i remove any package using apt-get purge,i can confirm whether the files have actually been deleted from their paths..
So,before purging any package,i shall take a note of their path and after purging,again check the same path to confirm.
I also needed to know that if synaptic uses deb packages in background,does it first download the package on harddrive and then install it?
If this is the case,then after installation,the deb file is auto-deleted or kept as it is??
Or the scenario is entirely diff then i think?

---

### Post by CatKiller on 2009-08-25
> **satish_j said:**
>  I also needed to know that if synaptic uses deb packages in background,does it first download the package on harddrive and then install it?

Yes. To /var/cache/apt.

> If this is the case,then after installation,the deb file is auto-deleted or kept as it is??

It depends. If you're using Synaptic, then there's an option in the preferences that controls whether cached packages are deleted after install or not. I have no idea which is the default. If you're using apt-get then you need to run *apt-get clean* to delete the package cache. You can probably configure apt-get to automatically do it as well. I don't know which way aptitude goes by default.

---

### Post by satish_j on 2009-08-25
> **CatKiller said:**
> Yes. To /var/cache/apt.

This will be the first thing iam going to check when i go home today.If i found any deb packages there,can i move those packages to my home directory for future use so that i will not need Internet connection next time OR if i want the same package on another system without Internet connection.
Iam assuming here that there will be no dependencies issues as deb packages already handles that.(I read somewhere they are like setup files in windows that includes all dependency files required for application)

---

### Post by fanglinyong on 2009-08-25
you can use ubuntu-tweak ,this software can clear your download software after you installed them !

---

### Post by mcduck on 2009-08-25
> **satish_j said:**
> This will be the first thing iam going to check when i go home today.If i found any deb packages there,can i move those packages to my home directory for future use so that i will not need Internet connection next time OR if i want the same package on another system without Internet connection.
Iam assuming here that there will be no dependencies issues as deb packages already handles that.(I read somewhere they are like setup files in windows that includes all dependency files required for application)

Yes, you can copy the packages from there and use them if you want to install same versions of same programs on another machine.

But no, this isn't any magical way to get rid of dependencies. Of course all the required packages (and thus also the dependencies) are in the same directory. Like already said, they are *exactly* the same .deb packages downloaded from repositories. The dependencies are just other .deb packages.

Using apt-get or Synaptic automatically handles dependencies, .deb packages themselves only contain information about what other packages they need to work.

Dependencies are not some strange thing that are separated from the actual programs just to annoy users, they are exactly the same kind of packages as everything else. It's just that all the programs are broken into smaller pieces that can then be used in other programs as well. You need to install all the pieces a certain program needs to work, and these pieces come in .deb packages. Apt-get and Synaptic are able to pick up all the required pieces and download them automatically, when installing things any other way it's up to you to get the required stuff.

---

### Post by mcduck on 2009-08-25
> **fanglinyong said:**
> you can use ubuntu-tweak ,this software can clear your download software after you installed them !

Or open a temrinal and run "sudo apt-get clean", wich will do the same wthout need to install any additional software. Or use the cleaning tool found in System/Administration-menu. ;)

---

### Post by nikhilk on 2009-08-25
> **satish_j said:**
> Iam assuming here that there will be no dependencies issues as deb packages already handles that.(I read somewhere they are like setup files in windows that includes all dependency files required for application)

That is not necessarily true. The package specifies a list of dependencies but cannot "handle" that on its own. Most likely you will have a package with all of its dependent packages as well, in the apt cache but it may not be the case always.

That is what a package manager like apt-get does. When it is instructed to install a package, apt-get checks the list of dependencies of that package and downloads any additional packages that are need to satisfy the dependencies.

Installing a standalone ".deb" package with dpkg will not automatically download dependent packages. You will have to do that manually.

---

### Post by 3rdalbum on 2009-08-25
Also, the idea of "moving the packages to my home directory in case I want to install them again" isn't necessary. If Apt notices that you already have a package in /var/cache/apt that's the same version as what you want to install, then it will install from the cache rather than download it again. If the repository version is newer, Apt will download the new version.

I recommend copying rather than moving, if you absolutely must have the packages for installation on someone else's machine.

As for "checking if it has removed the contents of the package", this is not necessary. On Windows it might be, because an (un)installer will not know if a library it has installed is used by other programs. On Linux isn't not necessary because it can track dependencies. It knows from the contents of the package, what has installed - and it just goes through and does the reverse.

Linux is here to work FOR you, not to create more work by forcing you to supervise what it does. Trust the package manager. If it doesn't give you any error messages, then it knows exactly what it's doing.

---

### Post by satish_j on 2009-08-26
Thanks all for your feedbacks.I checked the path and there are deb packages there,but after reading all your inputs,i think dependencies are of first importance.As i mentioned,I was under the impression that dependencies are handled by deb packages.But,since this not being the case,and the fact that the number of dependencies may be more,i should stick to package manager.
After reading all this,i find raw tar files more better than others since one get the option to specify the paths and also many other options.
Thanks all...

---

### Post by SunnyRabbiera on 2009-08-26
> **satish_j said:**
> Very sad...for first time,i have come across a feature of Ubuntu i think i do not like(i think this is not the proper management of files).
Anyways,do you mean that executable binary of _every package_ goes to /usr/bin.Likewise,docs of _every package_ to /usr/share/docs,etc,

For me i like the way Linux organizes things, each part of the application has its own place.
Windows actually does the same thing when concerning certain applications, I mean yes most of the programs go into C:\Program files\, but not all the settings are in that directory.
Some files go into hidden directories, some files go into the C:\WINDOWS directory, etc.

---

### Post by satish_j on 2009-08-26
I have a new query.Dont know whether i should start a new thread for it..
Is there any temp folder kind of thing in Linux which has to be periodically cleaned??My Ubuntu partition is rapidly filling and i need to get some space freed up for it.

---

### Post by CatKiller on 2009-08-26
> **satish_j said:**
> I have a new query.Dont know whether i should start a new thread for it..

Yes you should. Or look for other threads on the same subject.

>  Is there any temp folder kind of thing in Linux which has to be periodically cleaned??My Ubuntu partition is rapidly filling and i need to get some space freed up for it.

No. The /tmp directory is emptied whenever you shut down the computer, on the off chance that an application hasn't removed a file that it's put there.

/var/log can get quite large if you've got some recurring error message that's causing your log files to grow out of control. Some people had that problem a while ago.

If you want to see where your space is going ```
gksudo baobab
```will tell you all. You can run "Disk Usage Analyser" from the menu (which is the same thing) but then it won't catalogue the contents of folders that your cannot read (such as root's Home folder).

---


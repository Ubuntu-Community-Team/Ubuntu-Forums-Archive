---
title: "sudo: How do you elevate a user's privileges without temporarily making them root?"
date: 2012-04-20
forum: General Help
---

### Post by aps2012 on 2012-04-20
Hi all,

I would like to be able to run privileged commands from the comfort of my own account **as me**. When *sudo* executes, it temporarily switches UID according to the password database and then runs the specified command as the designated user (default: root).

It just so happens that the password database also contains the home area for a user. However, for a nicely written program that uses [FONT=Courier New][SIZE=2]$HOME[/SIZE][/FONT] to access the home area of the current user (and any user-specific settings stored within it) everything is well. Even if HOME is included in the set of variables removed by *sudo* during the user switchover, I can go:

```

sudo HOME=${HOME} command arg arg ...

```and all is well. My command, even though it's running as root, will still reference it's user-specific files via my [FONT=Courier New][SIZE=2]$HOME[/SIZE][/FONT] and the settings in **my** home area will be referenced and updated.

However, there is a group of sloppily written tools who don't use the environment for deriving the home area, instead they use the [FONT=Courier New][SIZE=2]getpw...()[/SIZE][/FONT] set of C functions based on [FONT=Courier New][SIZE=2]geteuid()[/SIZE][/FONT] or some other similar method. And so every time I run these tools using *sudo*, the tool's preferences that I have in my home area don't get referenced. Instead, my tool gets the home area for the current user (i.e. **root**, or whichever user that *sudo* switched to when executing the command) and uses that. And when it (unsurprisingly) finds no settings, it then reverts back to its default settings and then saves these default settings in the home area of the current user (i.e, root, or whichever user that *sudo* switched to when executing the command).

Marvellous.

Currently, for all these applications, I have to create a symbolic link from the home area of the root account back to my own account (where the settings actually are) in order to be able to run the same tool under normal mode or *sudo* mode and to not have the preferences change every time I run it. However, even this is not foolproof as every file that gets updated when the tool exits ends up being "root root" ownership in my home area and I then can't access it.

If possible, I would like to be freed from the stupidity of these sloppily written tools. I would like to be able to have *sudo* run with root privileges but tell an application that it is actually me running the tool, so that programmatic queries for the current user made within the tool come up with me and not root.

Is there any way to achieve this?

Thanks in advance,

---

### Post by CatKiller on 2012-04-20
sudo has options you can specify for how it behaves. man sudo will tell you what's available. On my phone, otherwise I'd look up one that would do what you want.

---


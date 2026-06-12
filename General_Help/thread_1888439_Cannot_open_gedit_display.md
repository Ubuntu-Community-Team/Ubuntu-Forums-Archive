---
title: "Cannot open gedit display"
date: 2011-11-29
forum: General Help
---

### Post by Tommy1Kenobi on 2011-11-29
I would really appreciate help on this. 
I am new to Ubuntu and for the most part new to a command line environment. 

Computer is a Mac G4 Cube with no mods. 
I installed Ubuntu 8.04.1-Server-PowerPC (after unsuccessfully trying to install the latest version of Ubuntu) to replace OS 9 which was sucking the life out of me. My intention was to install the Gnome GUI to have a friendly desktop interface. I tried but the installation failed. Following threads around I found that I needed to enable universe and multiverse repositories in the /etc/apt/sources.list file. I tried the [I]
sudo gedit /etc/apt/sources.list[/I] 
command which prompts me for a password. After I entered my password I got back: 
[I]cannot open display:
run 'gedit --help' to see a full list of available command options[/I].
I have done a few things after that to no avail.

Oh, also... after the "last login" line it says that the the operating system is 'Linux ubuntu 2.6.24-19-powerpc #1 and then time and date it was created. I noticed that doesn't match the version I installed, which is 8.04.1-Server as previously stated. Does that matter??? :confused:

Also, I am new to all of this so please bear with me and explain barney-style. 
If you could help me upgrade to the latest version of ubuntu (desktop environment) that would be great too :)

Thanks in advance.

---

### Post by mcduck on 2011-11-29
You can't run a graphical applications like Gedit outside of the graphical desktop environment. If you need to edit files from command-line, use a CLI text editor like nano instead.

```
sudo nano /etc/apt/sources.list
```

What comes to the version in the last login line, that's the version of Linux kernel you are running, not the Ubuntu release version.

Edit: You shouldn't need universe or multiverse repositories to install Gnome. Can you give the exact errors you got when trying to install it?

---

### Post by ajgreeny on 2011-11-29
Ubuntu 8.04 is no longer supported, so you will have some problems installing anything on it now, I'm afraid.  Use 10.04 instead.

---

### Post by mcduck on 2011-11-29
> **ajgreeny said:**
> Ubuntu 8.04 is no longer supported, so you will have some problems installing anything on it now, I'm afraid.  Use 10.04 instead.

Actually it *is* still supported, although only on server use so the desktop packages won't get any updates. But the repositories are still open for 8.04.4 LTS.

...that being said, using a more recent version would of course be a good idea. Especially if the plan is to install a graphical desktop anf run other than just server applications. :)

---

### Post by Tommy1Kenobi on 2011-11-29
Ok. I ran the command:

sudo nano /etc/apt/sources.listIt says that "Major bug fix updates produced after the final release of distribution". Also "N.B software for this repository is ENTIRELY UNSUPPORTED by the Ubuntu team". It also says to "Uncomment the following two lines to add software from the 'backports' repository" and the lines are 

#deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-backports main restricted universe multiverse

and 

#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse

I take it uncomment means taking the pounds off the front, right?

Furthermore it says to uncomment a couple more lines to add software from Canonical's 'partner' repository and the lines are

#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

and

#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

I don't know if I will be able to download a supported or even unsupported GUI after doing that but I will try.

My original problem was that I could not get a Ubuntu (latest version) installation CD to boot from the computer. Doing all the tricks like holding the c key down as well as the option key and one other exotic key combination I can't remember didn't work. The Mac OS 9 installation booted fine, as well as the Ubuntu 8.04.1 which was what I was finally able to install. I don't know if later versions of Ubuntu are incompatible with my hardware, as it is a G4 Cube after all and not so generous with RAM or drive space. I have however read about people successfully installing it... but it hasn't worked for me. Any ideas or links to supported versions that are compatible with the G4 or PowerPC?
Or can I do it the back way directly from the server using the version I have?

All I want for Christmas is a free GUI for my G4. 

And I cannot access the error codes I got when trying to install gnome. All I remember is it had something to do with fonts. I don't know how to go back and check. I am really new at this and am basically learning as I go.

Thanks for the quick replies!

Hope you can help :(

---


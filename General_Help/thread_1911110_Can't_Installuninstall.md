---
title: "Can't Install/uninstall"
date: 2012-01-18
forum: General Help
---

### Post by Ciro2010 on 2012-01-18
Everytime I try to install/remove something from software center (or sudo apt-get) I get this:

```
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libgconf2-4': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I googled it, but i only find the same error with other files, so the solutions are different.

Thanks

---

### Post by dino99 on 2012-01-18
into a terminal, run one by one these commands:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
( can take a while, dont stop it before it end itself )

---

### Post by Ciro2010 on 2012-01-18
> **dino99 said:**
> into a terminal, run one by one these commands:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
( can take a while, dont stop it before it end itself )

At the end of sudo dpkg-reconfigure -phigh -a it said:

```
cron stop/waiting
dpkg-maintscript-helper: error: couldn't identify the package
```

What do i do? is it ok?

---

### Post by carranty on 2012-01-18
> **Ciro2010 said:**
> What do i do? is it ok?

Can you now install and uninstall things? If so its ok, if not let us know :)

---

### Post by Ciro2010 on 2012-01-18
> **carranty said:**
> Can you now install and uninstall things? If so its ok, if not let us know :)

It says i should reboot, but i'm afraid that it won't boot because of that error (i know it sounds stupid but it happened with other problems..)

---

### Post by Darkling1991 on 2012-01-18
> **Ciro2010 said:**
> It says i should reboot, but i'm afraid that it won't boot because of that error (i know it sounds stupid but it happened with other problems..)

You have to try it xD

---

### Post by carranty on 2012-01-18
> **Ciro2010 said:**
> It says i should reboot, but i'm afraid that it won't boot because of that error (i know it sounds stupid but it happened with other problems..)

I'm not certain what the command does, but I don't think it'll prevent you from booting. As Darkling says, you may just have to chance it......

---

### Post by Ciro2010 on 2012-01-18
Okay, sorry about that. I just restarted and the problem is still there. :/

---

### Post by bluexrider on 2012-01-18
Your cache seems corrupted. Do
     Code:
     ```
sudo dpkg --clear-avail && sudo apt-get update
```and then 
     Code:
     ```
sudo apt-get -f install
```

---

### Post by Ciro2010 on 2012-01-18
> **bluexrider said:**
> Your cache seems corrupted. Do
     Code:
     ```
sudo dpkg --clear-avail && sudo apt-get update
```and then 
     Code:
     ```
sudo apt-get -f install
```


Still giving the error..

(when i do apt-get -f install it says this:)

```

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
```

---

### Post by bluexrider on 2012-01-18
run this

```
sudo apt-get update && sudo apt-get upgrade
```

If it has any errors please post

---

### Post by Ciro2010 on 2012-01-18
> **bluexrider said:**
> run this

```
sudo apt-get update && sudo apt-get upgrade
```If it has any errors please post

BEFORE the upgrade it says

```
The following packages will be upgraded:
  language-selector-common language-selector-gnome libavcodec53 libavformat53
  libavutil51 libnautilus-extension1 libpostproc52 libswscale2 mousetweaks
  nautilus nautilus-data python-cups
12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/8,184 kB of archives. 
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y

```


After I press y It goes:
```

Do you want to continue [Y/n]? y
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libgconf2-4': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
```


So basically the exact same error i get whenever i try to install or remove anything from software center

---

### Post by bluexrider on 2012-01-18
Ok then lets do this.

Need to make a copy of the 'status' file in the /var/lib/dpkg so to do this run this:
```

sudo cp /var/lib/dpkg/status /home
```confirm the 'status' file is in your /home directory before continuing. This is a backup just in case.

Now we need to edit the 'status' file

```
sudo gedit /var/lib/dpkg/status
```Use the search tools Ctrl + F and type "libgconf2-4" without quotes

Look for this:


[COLOR=Magenta]Package: libgconf2-4
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 488
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Source: gconf
Version: 2.32.2-0ubuntu2
Depends: libc6 (>= 2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.7, libglib2.0-0 (>= 2.26.0), libldap-2.4-2 (>= 2.4.7), liborbit2 (>= 1:2.14.10), libxml2 (>= 2.7.4), gconf2-common (>= 2.32), gconf2-common (<< 2.33)
Conflicts: libbonobo2-0 (<< 2.24)
Description: GNOME configuration database system (shared libraries)
 GConf is a configuration database system for storing application
 preferences. It supports default or mandatory settings set by the
 administrator, and changes to the database are instantly applied to all
 running applications. It is written for the GNOME desktop but doesn't
 require it.
 .
 This package contains the shared libraries and the GConf daemon.
Homepage: [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/)
Original-Maintainer: Josselin Mouette <joss@debian.org>[/COLOR]


Highlight and delete the content of those lines. 

Leave a blank line between the package groups, (just 1) edit the file to reflect this. So you have a 

"Package: BLAH group"
...........space..........
"Package: BLAH group'

Save and update.
```

sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Ciro2010 on 2012-01-18
> **bluexrider said:**
> Ok then lets do this.

Need to make a copy of the 'status' file in the /var/lib/dpkg so to do this run this:
```

sudo cp /var/lib/dpkg/status /home
```confirm the 'status' file is in your /home directory before continuing. This is a backup just in case.

Now we need to edit the 'status' file

```
sudo gedit /var/lib/dpkg/status
```Use the search tools Ctrl + F and type "libgconf2-4" without quotes

Look for this:


[COLOR=Magenta]Package: libgconf2-4
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 488
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Source: gconf
Version: 2.32.2-0ubuntu2
Depends: libc6 (>= 2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.7, libglib2.0-0 (>= 2.26.0), libldap-2.4-2 (>= 2.4.7), liborbit2 (>= 1:2.14.10), libxml2 (>= 2.7.4), gconf2-common (>= 2.32), gconf2-common (<< 2.33)
Conflicts: libbonobo2-0 (<< 2.24)
Description: GNOME configuration database system (shared libraries)
 GConf is a configuration database system for storing application
 preferences. It supports default or mandatory settings set by the
 administrator, and changes to the database are instantly applied to all
 running applications. It is written for the GNOME desktop but doesn't
 require it.
 .
 This package contains the shared libraries and the GConf daemon.
Homepage: [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/)
Original-Maintainer: Josselin Mouette <joss@debian.org>[/COLOR]


Highlight and delete the content of those lines. 

Leave a blank line between the package groups, (just 1) edit the file to reflect this. So you have a 

"Package: BLAH group"
...........space..........
"Package: BLAH group'

Save and update.
```

sudo apt-get update && sudo apt-get upgrade
```


When i type the command to copy nothing shows up (i can put another command) but there's no file called "status" in /home, not even showing hidden files :/

EDIT: I went in the files and copied it on my own, but when i went to find libgconf2-4 in it i didn't find it!!! I mean, there's no PACKAGE libgconf2-4, but there are a lot of "libgconf2-4" in that text file!

---

### Post by bluexrider on 2012-01-18
you could 
```
sudo apt-get -f install libgconf2-4
```

but I think we will end up with the same result

---

### Post by Ciro2010 on 2012-01-18
> **bluexrider said:**
> you could 
```
sudo apt-get -f install libgconf2-4
```but I think we will end up with the same result


Yep, what's the point to install it to delete it, if we wanted to delete it because it was installed wrong? ...

---

### Post by bluexrider on 2012-01-18
The -f install forces the package to install overwriting the older package.

The editing of the 'status' file removes the package reference and gives the software manager or APT a cleaner installation.

---

### Post by Ciro2010 on 2012-01-18
> **bluexrider said:**
> The -f install forces the package to install overwriting the older package.

The editing of the 'status' file removes the package reference and gives the software manager or APT a cleaner installation.


I get this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgconf2-4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

```

---

### Post by bluexrider on 2012-01-18
I found 1 other reference to this type of issue:

[http://ubuntuforums.org/showthread.php?t=1410379](http://ubuntuforums.org/showthread.php?t=1410379)

Go to post #3

In this instance it would be:
```

sudo apt-get update && sudo apt-get safe-upgrade
```

```
sudo dpkg --clear-avail
```

```
sudo apt-get safe-upgrade
```

If this doesn't do it my grey matter will have exhausted itself.

---

### Post by Ciro2010 on 2012-01-18
> **bluexrider said:**
> I found 1 other reference to this type of issue:

[http://ubuntuforums.org/showthread.php?t=1410379](http://ubuntuforums.org/showthread.php?t=1410379)

Go to post #3

In this instance it would be:
```

sudo apt-get update && sudo apt-get safe-upgrade
``````
sudo dpkg --clear-avail
``````
sudo apt-get safe-upgrade
```If this doesn't do it my grey matter will have exhausted itself.

when it gets to safe-upgrade it says:

```
E: Invalid operation safe-upgrade
```

(I'm on Ubuntu 11.10)

---

### Post by bluexrider on 2012-01-18
Need some other help here.....calling all gurus.....

---

### Post by Ciro2010 on 2012-01-19
> **bluexrider said:**
> Need some other help here.....calling all gurus.....


I hope for the best..

---

### Post by Q-collective on 2012-01-19
The simplest option might be to try and reinstall?

Of course, make a backup of your data first.

---

### Post by Ciro2010 on 2012-01-19
> **Q-collective said:**
> The simplest option might be to try and reinstall?

Of course, make a backup of your data first.


Sadly, I was just about to do that, i'm backing up my stuff now... :/

---

### Post by bluexrider on 2012-01-19
**Re: Extra help here please** 			
 			 			 		   		 		 		 	Quote:
 	 	 		 			 				 					Originally Posted by **bluexrider** 					 				
 				[I]Hey there, If you have a second could you help out here:
[http://ubuntuforums.org/showthread.php?t=1911110](http://ubuntuforums.org/showthread.php?t=1911110)

Unable to solve this one and need some other help. 

Thanks[/I]
 			 		 	 	 
Hello bluexrider ,

As you may know the following command posted by Dino should have reconfigured the entire system . 	Code:
 	sudo dpkg-reconfigure -phigh -a 
 I have know idea why it didn't run and returned the following error .  	Code:
 	  cron stop/waiting dpkg-maintscript-helper: error: couldn't identify the package 
I can only speculate that the software center and / or  configuration is corrupt in some way . I don't think I can find a  package repair/ configuration command that is not already posted and  they don't appearer to be working anyway . I would probably be trying to  reinstall the software center and if nothing changed that would point  to a configuration . Problems like this happen more often with upgrades  and not clean installations with good checksum .

---


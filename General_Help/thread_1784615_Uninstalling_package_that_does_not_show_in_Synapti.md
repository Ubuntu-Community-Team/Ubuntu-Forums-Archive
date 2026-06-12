---
title: "Uninstalling package that does not show in Synaptic"
date: 2011-06-17
forum: General Help
---

### Post by ElToro on 2011-06-17
The problem below is probably related to the fact that I tried to install a 32-bit version of Teamviewer on a 64 bit system. I have now downloaded the right version, but when I try to install it I get:

teamviewer6: 6.0.9224 (Multi-Arch: no) is not co-installable with
teamviewer6:i386 6.0.9224 (Multi-Arch: no) which is currently installed

But the Synaptic Package Manager does not indicate that Teamviewer is installed, nor does it appear under installed apps in the panel. :confused: So how do I get rid of the teamviewer6:i386? 

Thanks :)

---

### Post by An Sanct on 2011-06-17
> **ElToro said:**
> The problem below is probably related to the fact that I tried to install a 32-bit version of Teamviewer on a 64 bit system. I have now downloaded the right version, but when I try to install it I get:

teamviewer6: 6.0.9224 (Multi-Arch: no) is not co-installable with
teamviewer6:i386 6.0.9224 (Multi-Arch: no) which is currently installed

But the Synaptic Package Manager does not indicate that Teamviewer is installed, nor does it appear under installed apps in the panel. :confused: So how do I get rid of the teamviewer6:i386? 

Thanks :)

How about uninstalling it in the terminal? with
```
sudo apt-get remove *sw name*
```
?

---

### Post by ElToro on 2011-06-17
> **An Sanct said:**
> How about uninstalling it in the terminal? with
```
sudo apt-get remove *sw name*
```?

Thanks for the tip, An Sanct. When I do, I get:

[I]sudo apt-get remove *teamviewer*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package teamviewer_linux.deb
E: Couldn't find any package by regex 'teamviewer_linux.deb'[/I]

After getting the message above, I downloaded the 64 bits Debian Teamviewer package again and tried to install it via the Ubuntu Software Centre. Ended up with the same error again:

[I]dpkg: error processing /home/eric/Downloads/teamviewer_linux_x64.deb (--install): 
 teamviewer6: 6.0.9224 (Multi-Arch: no) is not co-installable with teamviewer6:i386 6.0.9224 (Multi-Arch: no) which is currently installed [/I]

:confused:

---

### Post by An Sanct on 2011-06-17
> **ElToro said:**
> Thanks for the tip, An Sanct. When I do, I get:

[I]sudo apt-get remove *teamviewer*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package teamviewer_linux.deb
E: Couldn't find any package by regex 'teamviewer_linux.deb'[/I]

After getting the message above, I downloaded the 64 bits Debian Teamviewer package again and tried to install it via the Ubuntu Software Centre. Ended up with the same error again:

[I]dpkg: error processing /home/eric/Downloads/teamviewer_linux_x64.deb (--install): 
 teamviewer6: 6.0.9224 (Multi-Arch: no) is not co-installable with teamviewer6:i386 6.0.9224 (Multi-Arch: no) which is currently installed [/I]

:confused:

My answer was slightly hard to understand ... i mentioned "**sw name**" that is where the name of the package should be, without the asterisks ("*****"), for some help, tab does auto-complete in this stage too, so try
```
sudo apt-get remove team[+tab key]
```
I don't know the exact name of the package/program, so I was guessing.

Alternatively, you could also double-click/run the deb package, that you installed, which should open up a Software Center window with a description of Team Viewer, there you have the option to uninstall/remove the program.

2. Alternative is to open Software Center and either look on the left for "installed software" or browse the install "history", if you find Team Viewer there, select and uninstall it.

---

### Post by ElToro on 2011-06-17
> **An Sanct said:**
> My answer was slightly hard to understand ... i mentioned "**sw name**" that is where the name of the package should be, without the asterisks ("*****"), for some help, tab does auto-complete in this stage too, so try
```
sudo apt-get remove team[+tab key]
```I don't know the exact name of the package/program, so I was guessing.

Alternatively, you could also double-click/run the deb package, that you installed, which should open up a Software Center window with a description of Team Viewer, there you have the option to uninstall/remove the program.

2. Alternative is to open Software Center and either look on the left for "installed software" or browse the install "history", if you find Team Viewer there, select and uninstall it.
  
Thanks, An Sanct. I first tried this (using the tab-key after "team"):

```
sudo apt-get remove teamviewer6 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'teamviewer6' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Next, I tried opening the deb-package with the Software Center. I only got an error message saying "Wrong architecture 'i386'" and no option to install or uninstall. I guess that is reasonable, as it is the 32 bits package...

No installation (or any other change) of Teamviewer is shown in the Software Center's History. This is so weird... :-x

I also tried this:

```
sudo apt-get install teamviewer6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package teamviewer6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'teamviewer6' has no installation candidate

```

---

### Post by oldos2er on 2011-06-17
Have you tried ```
sudo dpkg -r teamviewer
```

---

### Post by ElToro on 2011-06-20
> **oldos2er said:**
> Have you tried ```
sudo dpkg -r teamviewer
```

Thanks for the tip, oldos2er. Doing the dpkg -r and then doing

```
sudo dpkg -i /path/to/teamviewer_linux_x64.deb
```

worked!

:popcorn:

---


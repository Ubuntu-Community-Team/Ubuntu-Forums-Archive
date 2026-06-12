---
title: "Broken Package System Please help!"
date: 2011-03-02
forum: General Help
---

### Post by idontknowleavemealone on 2011-03-02
Upgraded to 10.10 about two months ago.  I cant update or make any package changes.
I have an invalid filename in the dependencies field for the Libgail18 package.  It will not let me install or remove anything.  I have tried sudo apt-get install -f and it gives me the   following error message:

dpkg: parse error, in file '/var/lib/dpkg/status' near line 22203 package 'libgail18':
 `Depends' field, invalid package name `libp`ngo1.0-0': character ``' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)


I don't know how to change the dependencies of the libgail18 package, and the system won't take ANY action to correct it. I don't even know how this erroniously named package got on my system.  Please help!

---

### Post by houseworkshy on 2011-03-02
Just some guesswork.  First try looking at your repositories and removing those which are not as the default install.  After that you could try reloading the software lists, then running the computer janitor OR "sudo apt-get autoclean" and "sudo apt-get auto remove"  You could also try the dpkg command itself, for details type "man dpkg" in the terminal.  As the install is two months old you will have several old kernals so could try going back to a previous one via the screen you get by tapping the left shift key after the bios check.  There are some other options from that screen which may help too.  The general opinion is that clean installs behave much better than upgrades so if all that fails you could simply save your home folder somewhere and do a clean install then put what you want to keep in the new home folder, might be better off doing that anyway.

---

### Post by temman on 2011-03-02
[COLOR=black][SIZE=2]This is how I fixed my problem with broken package.
Open Terminal type " sudo apt-get update && sudo apt-get upgrade " without the quotes!
(with this you will have some idea what is happening).
Then navigate to Administration / Synaptic Manager / Select "Custom" from the tabs bottom left / Select "Broken" and right click on package and remove it.
Hope it works for you !
[/SIZE][/COLOR]

---

### Post by idontknowleavemealone on 2011-03-03
> **houseworkshy said:**
> Just some guesswork.  First try looking at your repositories and removing those which are not as the default install.  After that you could try reloading the software lists, then running the computer janitor OR "sudo apt-get autoclean" and "sudo apt-get auto remove"  You could also try the dpkg command itself, for details type "man dpkg" in the terminal.  As the install is two months old you will have several old kernals so could try going back to a previous one via the screen you get by tapping the left shift key after the bios check.  There are some other options from that screen which may help too.  The general opinion is that clean installs behave much better than upgrades so if all that fails you could simply save your home folder somewhere and do a clean install then put what you want to keep in the new home folder, might be better off doing that anyway.
I've been thinking and, my opinion is the same.  I have always done clean installs of Ubuntu.  I never really trusted the upgrade option.  This is my first time upgrading since I first insalled Ubuntu in 2005.  I considered going through the repositories, but after running a startup error manifest that literally took me an hour to get all the way through, i think I would be better off re-installing.  Thanks for the good info though.  I really needed some fresh perspective.

---

### Post by idontknowleavemealone on 2011-03-03
> **temman said:**
> [COLOR=black][SIZE=2]This is how I fixed my problem with broken package.
Open Terminal type " sudo apt-get update && sudo apt-get upgrade " without the quotes!
(with this you will have some idea what is happening).
Then navigate to Administration / Synaptic Manager / Select "Custom" from the tabs bottom left / Select "Broken" and right click on package and remove it.
Hope it works for you !
[/SIZE][/COLOR]
Not only is the package system broken but "apt" is broken as well.  Aptitude wont work at all.  Synaptic relies on "apt" if I'm not mistaken doesn't it?  Thus, when I go into synaptic, I can locate broken packages, but it will not remove them, update them or overwrite them.  And sudo apt-get install updates fails as well. Thank you for your input though, any help is greatly appreciated!  I think I'm gonna wipe the disk and do a clean install.

---


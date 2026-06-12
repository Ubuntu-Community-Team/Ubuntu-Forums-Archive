---
title: "ubuntu still runs after its been uninstalled!!"
date: 2011-08-14
forum: General Help
---

### Post by goodbye-windows(tm) on 2011-08-14
Hi all,

I have an unusual problem in my desktop running a dual boot system.

I wanted to change the desktop unit over to xubuntu (it runs ubuntu without problems).

So, I uninstalled ubuntu from the windows control panel and deleted the wubi folder manually. There were no errors indicated, and the hard drive reclaimed the space from the uninstallation just fine and I thought I could now install xubuntu.

I was wrong::>

After the ubuntu install, I discovered that the system still gives me the option to boot into either XP or into ubuntu.._**.and, ubuntu runs just as though I had not uninstalled it!!!!  **_

I searched the windows system for 'ubuntu' and 'wubi', no hits. I looked in the root directory, and there were no wubi or ubuntu folders there.

But, somehow, ubuntu still runs...and it runs well. 

I'd like to track down the problems cause and completely take out ubuntu. But, I do not know how or why ubuntu continues to run!!!

I did have a power fail during an early installation of ubuntu, maybe the problem is related to the line voltage dropping out?

hhhhhhheeeelllpppppp.

TIA

Art

---

### Post by dandnsmith on 2011-08-14
A possibility which occurs to me is:
when you remove the wubi folder, the data will still be there until the space is recovered, so the grub bootstrap can still find a usable filesystem to boot. It's possible that the wubi file is still in the recycle bin, and if you deleted it (recycle bin empty manually), then you might lose the ability to boot ubuntu.

Just a guess, with no way to try it.

---

### Post by bcbc on 2011-08-14
Please boot Ubuntu and post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

PS there is no Wubi folder that I am aware of (Wubi installs into and *ubuntu* folder. Is this something you created yourself? There are some wubildr* files.

---

### Post by Duncan Williams on 2011-08-14
There is no chance that your ubuntu is really xubuntu?
They are similar.
( - delete this - I thought you had tried to install xubuntu - )

---

### Post by goodbye-windows(tm) on 2011-08-14
[B]
_There is no chance that your ubuntu is really xubuntu?_[/B]

There is no chance-I have never installed or attempted to install xubuntu on my desktop. I have installed and ran ubuntu several times, including the aborted attempt to install ubuntu (aborted by a power failure that shut down the computer abruptly and unexpectedly).

-------------------------------

[U][B]Please boot Ubuntu and post the results of the bootinfoscript

PS there is no Wubi folder that I am aware of....[/B][/U]

Yes, the deletion of the wubi folder was indeed the deletion of the wubidr* files...sorry for the confusion.

Regarding the results of the bootinfoscript....is bootinfoscript a program or a command that I can run in the terminal mode. I am not at the site where the desktop computer is located, it will be about a week before I can post the results.

-------------------------------

_[COLOR=black]**Duncan,**[/COLOR]_ there is no chance that there are any files in the trash can, I delete them manually and very often. It's definitely empty now and has been for about a week or so.

-------------------------------

Regards,

Art

---

### Post by bcbc on 2011-08-14
You should have removed the Ubuntu install either by reinstalling with Wubi (it automatically uninstalls first) or going to the Control Panel and removing the "Ubuntu" entry. Manually removing pieces can cause problems when you try to install again.

In this case, you need to manually uninstall and remove all the leftover bits. Refer to the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F") for instructions. 

Hope that helps

---


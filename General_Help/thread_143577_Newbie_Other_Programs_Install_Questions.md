---
title: "Newbie Other Programs Install Questions"
date: 2006-03-12
forum: General Help
---

### Post by phil64 on 2006-03-12
OK, I am completely new to Linux, I had no problem installing and getting Kubunto Breezey Badger installed and dual booted on my Pentium 1ghz machine with Windows ME.  Everything installed beutifully and I am up and functioning, here are some of the problems I need to resolve, (more like learn how to do in Linux).

I have tried using Adept and it installs most programs, but they do not appear in the K Menu.  I found some of the programs in the "usr/games" directory and was able to run them.  But I still can't locate some of the other programs I downloaded.  

Is there a way to have the K Menu automaticle populated or how can I find programs that were successfully installed using adept?

2nd problem is trying to update Nvdia Drivers from the website I downloaded a file called "file:///home/phil/NVIDIA-Linux-x86-1.0-8178-pkg1.run".  Itried runing the program using a terminal window with the following command  
"sh NVIDIA-Linux-x86-1.0-8178-pkg1.run"  Error message tells me I need to be Root, I tried opening a "New Root Shell" but it does not accept my password (only 1 user) so Root password should be same as my user password, it just closes this terminal.

What am I doing wrong?

Any help would really be appreciated to get me pointed in the right direction.

Thanks,

Phil

---

### Post by Jucato on 2006-03-12
1. Some programs, especially KDE programs are automatically updated in the K Menu. Some don't. One way I usually do to upgrade the K Menu is to run the KDE Menu Editor, kmenuedit (press Alt+F2 to get the Run command dialog box). When I'm in, I just his Save, and the K Menu is updated. Usually works. There might be an easier way, I just don't know how. :D

2. NVIDIA drivers: see this thread
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=HOWTO+latest+nvidia]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=HOWTO+latest+nvidia")

---

### Post by Parkotron on 2006-03-12
The majority of applications should be automatically added to the KMenu. But, if for some reason they don't, try kappfinder. It tries to find programs that are installed by not in the KMenu.

---

### Post by phil64 on 2006-03-13
My K Menu still does not show the programs installed with Adept.  I ran Kappfinder and it found a bunch of programs and gave me the option to add them to the K Menu, which I did.  But this seems to only find non-adept installed programs.  For example I downloaded "Ace of Penguins" using Adept, it saved the program in my "usr/games" directory, but gave me no way of running it other than doing a file search for the program, which is how I found it, why would it not show up in the KMenu?

Also there appear to be additional tabs when I used KMenu edit which does not show up on the actual displayed KMenu.  One such tab is a submenu for "Card Games" under the games tab.  But even in edit mode the Ace of Penguins game does not show up.

Is it possible I accidently changed some settings and need to go back to a Default state.  Maybe I'll just try reinstalling and see if this changes anything.  If anybody has any other suggestions I'd love to hear them.  Thanks again for the help, the link for the Nvdia driver looks great and I'll try it tonight thanks Fenyx.

Phil

---

### Post by Jucato on 2006-03-13
[QUOTE=phil64]Is it possible I accidently changed some settings and need to go back to a Default state.  Maybe I'll just try reinstalling and see if this changes anything.  If anybody has any other suggestions I'd love to hear them.  Thanks again for the help, the link for the Nvdia driver looks great and I'll try it tonight thanks Fenyx.[/QUOTE]

Nope. AFAIK, that's a common problem with the K Menu. It usually doesn't update itself immediately when non-KDE apps are installed. I don't know if it's a bug or just normal behavior.

Those "extra tabs" you are saying, are just folders for possible items that might be installed. They won't show up in the K Menu unless they actually contain something, so no worries.

Upon opening kmenuedit, did you hit "Save" like I told you? When you first open kmenuedit after installing a new program, it might not include the newly installed program immediately (unless it's a KDE app). Clicking on "Save" will refresh it.

There might be another way to refresh the K Menu, but I'm not sure if it's effective (this is only in theory). Open up a Run command dialog box (Alt+F2) and type this:
```
dcop kicker kicker restart
```
This will restart kicker (the panel) and hopefully restart and refresh K Menu with it.

---

### Post by feathers on 2006-03-14
There are so many applications on a linux system, it is good they do not all show up in the menu. What you could do: 
-Install menu. This adds a Submenu called "Debian" with some more programmes, though not all. 
- You can add the programme manually with the kmenueditor. This is, of course only practical with few programmes. 
- You can start any programme on a console by typing its startfile name. OpenOffice, f. ex. can be started by typing oowriter. This is usually faster than using the menu.

---

### Post by SeanTater on 2006-03-16
I tried the dcop method -- Nothing special.. The expected entries did not appear. However, kmenuedit, as expected, worked well.

---


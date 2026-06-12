---
title: "Ubuntu/Linux Newbie Needs Help ...."
date: 2010-03-25
forum: General Help
---

### Post by mrwizard93 on 2010-03-25
I performed a fresh install on my computer and everything seemed to install just fine. I then rebooted the machine and the first thing the comp asked for was a username and password in a command prompt. I entered my info and then the comp just sat there showing my username@ubuntu. What command do i need to enter to get to the installed desktop.

I tried startx and x -configure. And nothing. The text reads like this after I log in :

----
To run a command as ... (a bunch of text).

'username'@ubuntu:~$
----

If i type 'startx' after the $ sign, i get this:

----

-bash: startx: command not found

----

I have no clue!

I actually wanted to install Ubuntu Studio but the computer i was on had an old DVD drive that was not working well and would not allow itself to be detected. Then I tried loading the ISO data on a USB but that did not fly either. I ended up using unetbootin to load the data my usb but then the install wanted to download data from the web rather than my thumbdrive ... AAAGGGGHHHHH. What a night.

Any advice on how to get in to my Ubuntu desktop?


Thanks a ton and sorry for the newbie type questions.

---

### Post by Serpher on 2010-03-25
By default you should just see a login screen with GUI and everything. The command you're trying to type in is for Fedora, and Fedora based linux distro's. The equivalent to startx in Ubuntu is:

```
$sudo /etc/init.d/gdm start
```

The reason for this might be your video adapter just simply isn't at all compatible. If you can, could you post the output of the command 'lspci', or if you don't feel like copying it all out since you can't use a browser on that machine, 'lspci | grep VGA' or look in the 'lspci's output for what your video card is?

As for Ubuntu studio, unpack the ISO image so you're left with a bunch of files (do this in an empty directory), and drag all those files into the USB. Winrar is capable of this in Windows, and Ubuntu can do it by right clicking it and selecting mount and it'll act like a storage device (USB/Hardrive).

EDIT: Don't actually type the '$' in the command line.

---

### Post by spiderbatdad on 2010-03-25
You may have installed a server edition or minimal edition with no GUI. This command after the username@ubuntu$ should tell you:
```
$ uname -r
``` Also this:
```
$ dpkg -l | grep ubuntu-desktop
```
If you do have server or alternate installation, all is not lost. You can retrieve the ubuntu desktop and gnome desktop manager from the repositories with the following command:
```
$ sudo apt-get install ubuntu-desktop gdm
``` 
Ubuntu studio has its own host of packages and I don't whether ubuntu-desktop is a dependency...if it is, apt should handle this for you. Try, instead of the above (if you dare) ```
$ sudo apt-get install ubuntustudio-desktop ubuntustudio-gdm-theme
```

---

### Post by mrwizard93 on 2010-03-26
I think i am going to try a reinstall instead of trying to fix it.  

I know that when i tried to do the install, instead of reading data off the USB stick, the install package downloaded from the web instead.  I may have messed up some option at the start and it just snowballed from there.

This may be the fastest way.  I will let you guys know how it goes. 

Thanks to all that responded!  I really appreciate the help.

Cesar

---

### Post by mrwizard93 on 2010-03-26
OK, i tried to reinstall but the darn computer did not want to recognize the USB drive so BACK TO THE FORUMS!!!

The bottom line is this - THE FOLLOWING WORKED!!! - 

$ sudo apt-get install ubuntustudio-desktop ubuntustudio-gdm-theme

Apparently it seems that because i had a hard time installing off the USB and then allowed the install to continue off the web, that I must have not installed all the components.  

As, the end of the story is, that i am now posting off of my old computer, using ubuntu studio, and as happy as a dung beetle in, well, you know.

THANK YOU ALL FOR THE HELP AND INSIGHT!

Cesar

---


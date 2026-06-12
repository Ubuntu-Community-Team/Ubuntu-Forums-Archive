---
title: "somehow deleted almost everything... panels, firefox, shells, etc."
date: 2011-05-13
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-05-13
i am running ubuntu 10.10 on an aspire 5734z laptop, as 11.04 has a backlight issue, and i am dual booting with win7, which i am currently on. i have/had KDE, xfce, desktop edition ubuntu, and gnome 3 sessions installed. 

i had noticed recently that startup is taking longer than usual, 2x the time as win7, ubuntu and windows are both 32 bit bytheway. after grub, it would be a black screen with only '_' displayed, followed by a screen that says something about sql stuff. i figured this could be the reason my startups were long, and as i dont use sql (that i know of) i decided to just remove it and hope that would fix the problem... yeah, im a linux-noob. i went to software center, searched for it and removed the first entry, and it said it would remove some other stuff, mostly sql named things, plus shotwell and evolution, which i also dont use. after it went thru applying changes, i selected the next one on the list for removal, and the software center froze. i logged out of the gnome3 part, and logged into ubuntu desktop edition. i then only saw a wallpaper, both of the default panels were gone. 

at this point i decided a reset was in order. i logged back into the default ubuntu desktop edition part, and the panels were still missing. i figured i would login to gnome3 or kde and see if i could get something figured out from there, but they are missing from the drop down box. the only ones remaining are ubuntu (desktop, recovery and safemode) and xcfe. i logged into xcfe only to find out firefox is gone. i am not familiar with xcfe, i only added it to maybe use sometime when i need to extend battery time, and with no click here to get online - icon in the panel, i figured my best bet was to return to windows and plead for help, before i tried to 'fix' something else, and made an even bigger mess.

i dont know what i couldve done to basically render my ubuntu useless to me, to get rid of my panels, firefox, and i dont even know what else.. but the only thing i did at all was to remove the top sql entry, which was something like sql3_lib or something like that. anyone that can help me would be greatly appreciated. thanks in advance.

---

### Post by ToFue on 2011-05-13
Hey there - SQL is important to a lot of different programs for function and is considered a dependency to other critical applications as well..  When 'disabling' something, it's always wiser to start with a configuration option over an uninstall/remove if you're not yet sure how intertwined a program is with other subsystems..  *ALWAYS* check to see the 'fine print' to see what packages would be Removed or Replaced when installing or removing packages.. We've all done it at some point!


  That said, you can try a few recovery methods. I'll provide two. :p

1.) Check your 'apt' logs which should be in /var/log/apt and open the history.log file (the one with the most recent timestamp) to view what got removed.  Then comes the somewhat tedious process of reinstalling everything that was removed.

From the terminal:
```

## view what logs exist:
$ ls -la /var/log/apt

## Show the history of what got deleted/removed:
$ cat /var/log/apt/history.log

```
```

## The last entry should be the most recent, and look something like:

...

Start-Date: 2011-05-07  15:12:18
Upgrade: ubuntuone-client:i386 (1.4.6-0ubuntu2, 1.4.6-0ubuntu3), ubuntuone-client-gnome:i386 (1.4.6-0ubuntu2, 1.4.6-0ubuntu3), libsyncdaemon-1.0-1:i386 (1.4.6-0ubuntu2, 1.4.6-0ubuntu3), xdg-utils:i386 (1.0.2+cvs20100307-1ubuntu0.2, 1.0.2+cvs20100307-1ubuntu0.3), python-ubuntuone-client:i386 (1.4.6-0ubuntu2, 1.4.6-0ubuntu3), php5-cli:i386 (5.3.3-1ubuntu9.4, 5.3.3-1ubuntu9.5), php5-common:i386 (5.3.3-1ubuntu9.4, 5.3.3-1ubuntu9.5)
End-Date: 2011-05-07  15:14:28

Start-Date: 2011-05-09  21:32:38
Install: earth3d:i386 (1.0.5-1.1ubuntu1)
End-Date: 2011-05-09  21:33:06

Start-Date: 2011-05-09  22:07:36
**Remove**: earth3d:i386 (1.0.5-1.1ubuntu1)
End-Date: 2011-05-09  22:07:51

Start-Date: 2011-05-11  09:02:27
Upgrade: postfix:i386 (2.7.1-1ubuntu0.1, 2.7.1-1ubuntu0.2), ubuntu-sso-client:i386 (1.0.8-0ubuntu1, 1.0.9-0ubuntu1)
End-Date: 2011-05-11  09:03:31
tofue@Ectonut:/var/log/apt$ 


```

The entries that say "Remove" are what you want to look at, and you can even filter them in your results by using grep: 
```
 $ cat /var/log/apt/history.log | grep remove 
``` but you may not get all of the data you need -  grep shows the first line of what you're filtering.. You may have to pen & paper it, and pipe through 'less' instead if you're in cli mode (Command Line Interface; non desktop mode) so you can scroll through the results.
```
 
## you can invoke 'less' directly:
$ less /var/log/apt/history.log

## or you can pipe data stream results into less:
$ cat /var/log/apt/history.log | less

```
## FYI: the end result is the same, but you can manipulate complex scripts by piping, having independent operations perform before results are 'simply' shown or routed to other programs.. cool stuff! 

The name of the package is going to be to the left of the architecture type.. so for > Start-Date: 2011-05-09  22:07:36
Remove: earth3d:i386 (1.0.5-1.1ubuntu1)
End-Date: 2011-05-09  22:07:51 
the entry "earth3d:i386" has the format <PACKAGE_NAME>**:**<ARCH_TYPE>, so the package in **earth3d**:i386 is "earth3d".

Go ahead and reinstall the missing packages that were previously and accidentally removed using:
```

$ sudo apt-get update
$ sudo apt-get install <PACKAGE-1 PACKAGE-2 PACKAGE-3 ... ...>
## And so on, but without the greater than or less than.. you get it! :p
```

If you run into errors, you can clean the package cache using 
```

$ sudo apt-get check
$ sudo apt-get clean
$ sudo apt-get autoclean

```

Unless you removed the SQL package using the 'purge' option, your user settings for the programs should remain in your $HOME folder (type " ls -la $HOME " without quotes) to verify what data you've generated for what program if you're curious ;)

When everything is finished installing you can type ```
 $ sudo gdm 
``` to start the gnome desktop manager, but it would probably be better to simply reboot with ```
 $ shutdown -r 0 
```

If you haven't missed a package, you should be up and running to your previous state, and then can tackle the original issue you had..


2.) If by chance this all seems too confusing, or it gets beyond the point that you can manage what's installed, what's where, and what's involved, you can always reinstall Ubuntu over your old installation, replacing it.. That would be easy if you made a separate /home partition when you installed the first time, and can refer to this thread for those steps: [[COLOR="Teal"]> Click Here < [/COLOR]](http://ubuntuforums.org/showthread.php?t=1637402)

I hope this all helps you, let us know how it goes and if you need additional thoughts!
~Cheers!

---

### Post by jerrrys on 2011-05-13
forget it

---

### Post by ToFue on 2011-05-13
> **jerrrys said:**
> forget it

What do you mean?  Am I in error?

---

### Post by jerrrys on 2011-05-14
nope, my idea was suddenly not making sense.  thats when i realized that the beer had kicked in and it was time for me to go find mindless things to do.

one thing i noticed that you removed evolution.  your desktop has dependencies to this package and it cannot just be removed without breaking things. do you have access to Terminal ?

---

### Post by SE7EN-LOCSTA on 2011-05-14
thanks a bunch for the help.. after pulling up the list of stuff i had uninstalled, and seeing close to 100 items, i just did a fresh install of ubuntu. i could swear when i chose to uninstall the sql item, only about 20 items said they were on the list of removal, and gnome items definitely must have somehow been accidentally scrolled past.. or i wouldnt have pushed apply. i dont know, but i will not start deleting things i dont know for sure what they are anymore. anyways, your help made me quickly realise that the task opf 'fixing' was not worth it, and you saved me hours of frustration in trying to reinstall all the programs i deleted.

---

### Post by jerrrys on 2011-05-14
you had the option to reinstall.  really thats a good choice vs the pain of fixing.  SQL may of said 20 items, but there is the dependency of the dependency thing.  same thing happens when you install, the package can end up much bigger.

don't know if you ever used it, but **synaptic-package-manager** is a very go tool for adding and removing packages.  its in the software center.

[ATTACH]192182[/ATTACH]

i also highlighted the only package for evolution that you should 'mark for removal'  in SPM.  that will remove it from your desktop without killing your desktop.  enjoy

---


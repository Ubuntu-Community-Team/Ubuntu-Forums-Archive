---
title: "Some way to reinstall packages installed from a date and after?"
date: 2010-10-18
forum: General Help
---

### Post by Lynx Phoenix on 2010-10-18
i was installing a truckload of packages this morning, to try out, so while i had synaptic doing its job i was typing on another workspace. a box popped up and before i could react to it, it went away like a button got pushed to confirm, cause i was typing. later through the installations another two popped up asking me which users to install the package for, which i'm assuming where the same kind of box as the first one. i checked my user (the only user, the box was unchecked by default so i dont understand the purpose of this dialog box - install the package for noone by default?) and clicked on "forward". i think the first one was the same, but i didnt even get a glance at it. i didnt even press enter or escape when it popped up, it just reacted to some character key (so annoying).

anyway, i'm kinda worried something got installed but i wont actually be able to use it cause i didnt check my user on that first dialogbox. and naturally i didnt have the chance to see the package's name either. i dont know if there's a way to actually check if a package is installed but for no users (which is an oxymoron in itself) so i decided to uninstall all the packages i installed and re-download and install them (cause i tried reinstalling another one of those that popped up a box but it didnt ask me that time).

i tried reading up on grep and other commands but i cant really make out how i can read dpkg.log and extract only the names of the packages i installed last and produce a file to pipe to apt-get in order to uninstall and reinstall them (since what i want to do isnt really possible through synaptic - it cant export history to a file or categorize installed packages by date so its useless for this). i tried what i read on[ this post (post #9)]("http://ubuntuforums.org/showthread.php?t=1497530") and tried piping it to apt-get and exporting a file, but its output isnt helpful cause it has version numbers and random 2's and "1:"s in it (which i tried fixing with emacs but i dont trust that this output is going to work anyway and i dont want to risk making a gigantic mess).

sorry if i sound whiny, but i cant really do this by hand cause its about 2,5GB worth of packages (yeah i'm an idiot) and i dont want to just shrug and forget about it cause i dont even know which package it is so i can get rid of it and at least save myself the space - i actually had a markings file saved and tried to replace "install" with "deinstall" everywhere, which worked; but it had EVERY single package of the system marked, so naturally i couldnt apply the change (i didnt have save state checked when i saved the file, so i assumed it only saves changes and NOT every single installed package as well, including stuff like apt...).

i hope you can at least help me identify the elusive package

---

### Post by sendblink23 on 2010-10-18
just wondering... why  were you installing a "truckload of packages" ?? ;)

Also personal note... when installing stuff Don't do anything else - stay watching it - so you don't ever encounter the issue/concern/hassle you are in right now =P

I wish I could offer any solution.. but I have none

---

### Post by Lynx Phoenix on 2010-10-18
well in windows i had a lot of engineering and science software that i used so i decided since i moved to ubuntu i'd rather use free and/or open source software for those things as well as much as i can - so i went nuts and marked a bunch of packages related to circuits and microcontrollers and random science packages to try them out and decide which ones i like and want to keep

should've known not to bite more than i can chew i guess

---

### Post by matt_symes on 2010-10-18
Hi

dpkg --get-selections 

will list your installed software.

But this link might be more useful to you

[http://www.watchingthenet.com/show-list-of-recently-installed-packages-by-date-on-ubuntu.html](http://www.watchingthenet.com/show-list-of-recently-installed-packages-by-date-on-ubuntu.html)

Kind regards

---

### Post by Lynx Phoenix on 2010-10-18
thanks but i can already get a list of all my packages, what i need is a list of specifically those i installed the last time, that big chunk. not that i need the list necessarily, just a way to specifically target those for uninstallation.

i already found and checked that page while looking around this afternoon trying to find a solution on my own. i'm just not good enough with grep and the other commands in order to make a file with just the specific package names so that it will be useful to apt-get, but thanks anyway.

---

### Post by todak on 2010-10-18
Start synaptic and click on *File> History*. You will be presented with a dialog that will have dates on the left. Click on one of the dates and it will show what packages you upgraded, installed or removed on that particular day. You can do the same with Software Center.

---

### Post by Barriehie on 2010-10-19
Synaptic log files are located in /root/.synaptic/log/ if you ever need a file to mess with.

---

### Post by Lynx Phoenix on 2010-10-19
> **Barriehie said:**
> Synaptic log files are located in /root/.synaptic/log/ if you ever need a file to mess with.

tried to go there with ```
sudo cd /root/.synaptic/log
``` but it tells me there's no "cd" command... wth

i knew about the history by date feature synaptic has, but i'm an idiot and i didnt just think of copying the names :P i suck. i was looking for an export thingy. i guess i'll just remove the parenthesis with emacs and i'll refeed the package list to synaptic with deinstall tags

sorry for wasting your time

---

### Post by Barriehie on 2010-10-19
> **Lynx Phoenix said:**
> tried to go there with ```
sudo cd /root/.synaptic/log
``` but it tells me there's no "cd" command... wth

i knew about the history by date feature synaptic has, but i'm an idiot and i didnt just think of copying the names :P i suck. i was looking for an export thingy. i guess i'll just remove the parenthesis with emacs and i'll refeed the package list to synaptic with deinstall tags

sorry for wasting your time

If you're learning something it's not a waste of time! :)

---

### Post by SeijiSensei on 2010-10-19
Try "sudo ls -ltr /var/cache/apt/archives" to see a list of all installed packages by date.

---

### Post by Lynx Phoenix on 2010-10-19
> **SeijiSensei said:**
> Try "sudo ls -ltr /var/cache/apt/archives" to see a list of all installed packages by date.

i ran this and exported a file. it seems it lists the package version's date rather than the date it was installed. i installed that bunch yesterday which was the 18th (its like 00:15 now so i guess its technically not yesterday but whatever) and there isnt a single package dated like that. the last ones are one on the 19th, two on the 16th and the rest are from the 12th and back.

thanks though

---

### Post by praveenthivari on 2010-10-19
Ubuntu 10.10 software centre keeps all those records( stuff u installed, date, time). May b tht helps u. :-)

---

### Post by ianc1 on 2010-10-19
Sorry to but in on this one, but this is an issue I have suffered from  in the past.  I find it a pain when I do a fresh install to write down  all the packages I have installed and then reapply in the new  installation.

If the output of ```
dpkg --get-selections
``` (as suggested by matt_symes) is reinstalled on a  fresh install (next release for example) will this reinstall all the  packages correctly or does it end up back-dated files as some may be  relevant to the earlier release?

Also how do you simply list the installed packages doesn't the code above list all the dependencies as well?

Thanks

Ian

---

### Post by Lynx Phoenix on 2010-10-19
> **praveenthivari said:**
> Ubuntu 10.10 software centre keeps all those records( stuff u installed, date, time). May b tht helps u. :-)

i checked that out (and i had no idea that existed!) and it actually does keep a history detailed enough that i found exactly which packages i want to reinstall (it lists 1704 changes... which makes the level of my noobness apparent as much as the need for a proper solution :P). however there isnt any option to export that list so i cant use it anywhere else and it doesnt let me remove/reinstall packages from there. so i guess this helps with doublechecking which packages i want to fix, but i still need to do it by hand.

> **ianc1 said:**
> 
If the output of ```
dpkg --get-selections
``` (as suggested by  matt_symes) is reinstalled on a  fresh install (next release for  example) will this reinstall all the  packages correctly or does it end  up back-dated files as some may be  relevant to the earlier release?

Also how do you simply list the installed packages doesn't the code  above list all the dependencies as well?


well from synaptic you can go file->save markings as... - i dont know if actually saving state or not helps in your case. when i did this it saved every single package i had installed including system packages, so i guess its half a solution since you dont want to overwrite system packages that have been updated. also, since there are some packages like wine that include their version and have older versions available too, i'd say that for those who dont specify their version in their name (generally) it should install the latest, while for others the specific version's package that you had when you saved the markings. and i dont think there is a distinction between packages and dependencies as far as the system is concerned - at least not for all dependencies (but i'm really not sure at all). sorry if this isnt much help

---

### Post by ianc1 on 2010-10-20
I had a search at lunch today regarding the issue of simply locating packages installed by the user.  I came up with the following code which I will attempt when I get home to see how it works.

```
aptitude search ~i | grep -v "i A" 
```I beleive the -v option on grep is looking for thinkings that don't start "i A" but I could be wrong.

The info came from [http://brainstorm.ubuntu.com/idea/8595/](http://brainstorm.ubuntu.com/idea/8595/)

---

### Post by Barriehie on 2010-10-20
> **ianc1 said:**
> I had a search at lunch today regarding the issue of simply locating packages installed by the user.  I came up with the following code which I will attempt when I get home to see how it works.

```
aptitude search ~i | grep -v "i A" 
```I beleive the -v option on grep is looking for thinkings that don't start "i A" but I could be wrong.

The info came from [http://brainstorm.ubuntu.com/idea/8595/](http://brainstorm.ubuntu.com/idea/8595/)

Yes, -v inverts the match.  It worked on this end.

---

### Post by Lynx Phoenix on 2010-10-20
works for me as well. only problem is, i ran it without grep to see what was left out and i noticed a lot of packages that were linked as dependencies and/or necessary for the things i did install deliberately, were marked as automatically installed. while dependencies are easy to clean up i guess, wouldnt packages that can be installed on their own and are not dependecies be left behind even if you do clean up?

this would be great if it could search by install date too but that can be done differently so i guess its good for some jobs.

---

### Post by Barriehie on 2010-10-20
> **Lynx Phoenix said:**
> works for me as well. only problem is, i ran it without grep to see what was left out and i noticed a lot of packages that were linked as dependencies and/or necessary for the things i did install deliberately, were marked as automatically installed. while dependencies are easy to clean up i guess, wouldnt packages that can be installed on their own and are not dependecies be left behind even if you do clean up?

this would be great if it could search by install date too but that can be done differently so i guess its good for some jobs.

Perhaps the dependencies were marked as automatic because they are automatically installed with the selected package.

Edit: I know when I do my daily backup I use this to get the current state of installed packages.
```

dpkg --get-selections | gawk '{ if( $0 !~ /.*deinstall$/) { print $0 }}' > $BUP/packages-$(date +%m%d%y)

```

---

### Post by Lynx Phoenix on 2010-10-20
yeah that is what happened as some of them i remember could be installed alone (like an interpreted language some package needs, but which you can install alone as well). i'm just saying it doesnt help with some situations (though perhaps with others - it would be good to have a distinction)

edit - just saw your code; unfortunately its beyond my capacity to understand (homework for later :P)

---

### Post by ianc1 on 2010-10-20
When I got home I ran the code ```
aptitude search ~i | grep -v "i A"
``` and sent the output to file.  This file contains 1373 lines which is huge.  Since I installed 10.10 (a clean install) I have kept a log of installed packages in a text file, which is a awkward way of keeping a log, but anyway I have only installed 38 packages.

Are the remaining 1335 items really dependences?  For example I can't think what I have installed that would have had x11-common (Window System (X.Org) infrastructure) as a dependency.  Isn't this installed when the distro is installed?

---

### Post by drs305 on 2010-10-20
You mentioned the dpkg logs in your first post. I didn't figure out if you wanted *only* packages you manually installed or if you just didn't like the format.

Here is the dpkg command that might prove useful because it includes the dates:
```
grep "status installed" /var/log/dpkg.log
```
Returns in raw format (example):
> 2010-10-20 16:19:20 status installed 2vcard 0.5-3

```
grep "status installed" /var/log/dpkg.log | cut -d " " -f 5
```
Returns:
> 2vcard

You can look at the dpkg log via System, Admin, Log File Viewer.

Depending on how far back you want to go, look at log.1, log.2, etc.

---

### Post by Barriehie on 2010-10-20
> **Lynx Phoenix said:**
> ...muted...
edit - just saw your code; unfortunately its beyond my capacity to understand (homework for later :P)
...muted...

It says that if the line returned by dpkg does not end in deinstall then print that line to a file in the backup directory and the filename ends in MMDDYY format.  Gawk is a cool thing!```

dpkg --get-selections | gawk '{ if( $0 !~ /.*deinstall$/) { print $0 }}' > $BUP/packages-$(date +%m%d%y)
```

---


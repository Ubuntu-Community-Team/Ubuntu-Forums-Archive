---
title: "Reinstalling a broken program/package"
date: 2010-03-06
forum: General Help
---

### Post by acalora on 2010-03-06
Hello, I've been working on this problem for a while now, and no one is able to help me so far. I've installed the game GGZBoard, in synaptic it's called "ggz-python-games", and now, for some reason, it's not working. I do remember running apt-get autoremove to fix another program, and the person who told me to do that said it could cause undesirable side-effects. And so, after running the command, GGZBoard never opened up when I launched it from the applications menu, it didn't give me any errors or messages, it did absolutely nothing. And now, when I click on it I get the message:

```
Could not launch 'GGZBoard'

Failed to execute child process "/usr/games/ggzboard" (No such file or directory)
```I've tried to reinstall it from the "Ubuntu Software Center" and "Synaptic Package Manager" and using dpkg or apt-get in the terminal; but all of them bring up errors. 

Ubuntu Software Center says:

```
Package operation failed

The installation or removal of a software package failed.

installArchives() failed: dpkg: error processing ggz-python-games (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ggz-python-games
```Synaptic says:

Upon trying to remove
```
An error occurred

The following details are provided:

E: ggz-python-games: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.
```In the details menu
[IMG]http://img704.imageshack.us/img704/6207/removeoutput.jpg[/IMG]



Upon trying to reinstall
```
An error occurred

The following details are provided:

E: /var/cache/apt/archives/ggz-python-games_0.0.14.1-1ubuntu2_all.deb: subprocess new pre-removal script returned error exit status 255

```In the details menu
[IMG]http://img684.imageshack.us/img684/1536/reinstalloutput.jpg[/IMG]


If there is any way to fix this problem I would greatly appreciate any help. Thank you.

---

### Post by wojox on 2010-03-06
Try:

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

---

### Post by drdob on 2010-03-06
i had the same problem with stellairum i had no success but i re loaded 9.10 and down loaded stellairum again same problem, i was just coming on to the forum to warn people that the may be a problem with the program in the repository. i did remove it the second time with 

" sudo aptitude purge (the program ) 
so does any one know how we alert the repository they have a problem
Dr Dob

---

### Post by wojox on 2010-03-06
```
sudo aptitude purge <application>
```

Is how your suppose to remove an app from the command line. How did you do it before?

---

### Post by acalora on 2010-03-06
I ran 

```
sudo aptitude purge ggz-python-gamese 
```and the return was
```
thomas@thomas-desktop:~$ sudo aptitude purge ggz-python-games
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  ggz-python-games{p} gnugo{u} libblas3gf{u} liblapack3gf{u} python-ggz{u} 
  python-numpy{u} python-pygame{u} 
0 packages upgraded, 0 newly installed, 7 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 29.8MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing ggz-python-games (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ggz-python-games
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

```

---

### Post by wojox on 2010-03-06
Try:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Install that package that failed to install.

---

### Post by acalora on 2010-03-06
sudo apt-get dist-upgrade returns 

```
thomas@thomas-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  adobe-flashplugin
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/609kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package ggz-python-games.
(Reading database ... 278104 files and directories currently installed.)
Preparing to replace ggz-python-games 0.0.14.1-1ubuntu2 (using .../ggz-python-games_0.0.14.1-1ubuntu2_all.deb) ...
Using auxiliary directory to proceed...
Could not open auxiliary directory
dpkg: warning: old pre-removal script returned error exit status 255
dpkg - trying script from the new package instead ...
Using auxiliary directory to proceed...
Could not open auxiliary directory
dpkg: error processing /var/cache/apt/archives/ggz-python-games_0.0.14.1-1ubuntu2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 255
Using auxiliary directory to proceed...
Could not open auxiliary directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 /var/cache/apt/archives/ggz-python-games_0.0.14.1-1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by wojox on 2010-03-06
After you get that error, try **sudo apt-get -f install** to force an install of the files that didn't get loaded because of the error. Then try **sudo apt-get upgrade** again, **apt-get -f install** back and forth until only the package that has the error is left.

---

### Post by acalora on 2010-03-06
It isn't doing anything, I've ran it 20 times and it still has the same output each time.

---

### Post by wojox on 2010-03-06
You ran the clean and autoclean from above and still nothing?

---

### Post by acalora on 2010-03-06
Yes

---

### Post by wojox on 2010-03-06
Running out of options here. What about:

```
sudo dpkg --configure -a
```

```
sudo dpkg --P
```

---

### Post by drdob on 2010-03-07
this is exactly the problem i had,i used all the remove /delete/purge/Etc that the good folk of the forum had suggested but had no success.in the end i reloaded 9.10and tried again. that is downloaded the problem program, and it did the same thing.. but this time i removed it with "sudo aptitude purge <application>" if any body has answer to this i would like to know, yours DrDob

---

### Post by chris.arena on 2010-03-07
I'm having exactly the same problem -- I'm following the suggested steps and can't clear the "Package is in a very bad inconsistent state - you should reinstall it before attempting a removal" message.

Was a procedure ultimately worked out offline that succeeded in clearing this?

Thanks,

Chris
Portsmouth, RI

---

### Post by acalora on 2010-03-07
Sorry, but none of these operations are working. Is there a way to reinstall using apt-get?

---

### Post by acalora on 2010-03-07
No, not yet, we're still working on it.

---

### Post by acalora on 2010-03-08
bump

---

### Post by Dscottmc7 on 2010-03-08
I don't know if this will help, since I'm a multi-year pre-newby!!! But I had an openoffice (karmic) update (emailmerge and binfilter) update that caused a Broken Package.

I had an OpenOffice.org document open at the first attempt to update.

That put a "pre-installation" code in and no matter what I did after that, work arounds, code, removal, the above, you name it, same thing:  Exit status error 1.
 It continued to tell me I had an open OpenOffice.org program running and I didn't!

Finally I used Synaptic to "Mark for complete removal" anything 'openoffice." (i.e. EVERYTHING after backing up)
That removed the packages according to the time-line going backwards (I would assume...e.g. the first package(s) installed was removed last, and then the next.

It took seven (7) times for Complete Removal to get down to the last remaining 2 packages that were causing the problem for not only OpenOffice but several other packages as well.

I reloaded OpenOffice...Bingo!  A few restarts, cleaned a few things out...
FINALLY this "bug" is gone! (re: launchpad bug: 450569)

POINT:  I couldn't remove the two package updates any other way.

---

### Post by Dscottmc7 on 2010-03-08
I don't know if this will help, since I'm a multi-year pre-newby!!! But I had an openoffice (karmic) update (emailmerge and binfilter) update that caused a Broken Package.
I know I'm glossing over, but I everything I could find, everything above, other posts, research, and finally I used Synaptic to "Mark for complete removal" anything 'openoffice." (i.e. EVERYTHING after backing up)
OK, but still a lot of packages.
It took seven (7) times for Complete Removal to get down to the last remaining 2 packages that were causing the problem for not only Openoffice but several other packages as well.
I reloaded OpenOffice...Bingo!  A few restarts, cleaned a few things out...
FINALLY this "bug" is gone!
POINT:  I couldn't remove the two package updates any other way.

---

### Post by Dscottmc7 on 2010-03-09
Maybe this will help...someone...I'm a multi-year newby, but I had an OpenOffice doc open during a Karmic update.

Although I closed it during update and "Forward" the update, I got a broken package Error status 1 message.

It was OpenOffice.org emailmerge and binfilter packages...Broken...
No matter what I did, work around, purge, remove, whatever I couldn't get rid of them nor fix them.  It had a "pre-installation" code installed and told me every time that I "Had OpenOffice running." (I didn't).

Finally I used Synaptic and 'Removed Completely' OpenOffice.
That left about 80%.  I kept "Removing Completely" and after about 7 complete removals I got to the last two "emailmerge and binfilter" packages and removed them!  I think the system removes them in the chronological order they were installed, i.e. first installed, first removed and so on backwards.

I then used Synaptic and did a fresh install of OpenOffice one basic package at a time.  Restarted, cleaned up anything lying around...Bingo!
No problem.  I'm old, senile and not a techie...so after three weeks of wandering, searching hell, the 20 minute process worked for me.

Hope it helps.

---

### Post by acalora on 2010-03-09
Thank you, your remedy helped me get closer to a solution. Unfortunately the only 2 packages left for me are the very ones I need to have removed.

---

### Post by acalora on 2010-03-09
I finally got it to work, after completely removing all of the ggz entries in synaptic, although some did not remove completely, I search my file system for files containing ggz and deleted them. Then I fixed the broken packages in synaptic, reinstalled ggz, and now it works.

---


---
title: "Can't upgrade or manage packages"
date: 2010-01-16
forum: General Help
---

### Post by kismul on 2010-01-16
On the bar along the top of the screen, I've got a n icon like a road "Stop" sign.  When I hover my icon over it, a box opens with the follwing error message:

"An error occurred, please run Package Manager from the right click menu or apt-get in a terminal to see what is wrong. 
The error message was: 'Error opening the cache (E:Encountered a section with no Package: header, E: problem with Mergelist /var/lib/apt/lists
im.archive.ubuntu.com_ubuntu_dists_jaunty-
updates_restricted_binary-i386_Packages, E:The package lists
or status file could not be parsed or opened.)' This usually 
means that your installed packages have unmet dependencies".

When I try to run Package Manager, I get 

Could not initialize the package information

[B]An unresolvable problem occurred while initalizing the 
package information.[/B]

"Please report this bug against the 'update manager' package
 and include the following error message:
“E:Encountered a section with no Package: header, E: problem 
with Mergelist /var/lib/apt/lists
im.archive.ubuntu.com_ubuntu_dists_jaunty-
updates_restricted_binary-i386_Packages, E:The package 
lists or status file could not be parsed or opened.”

As a beginner, I have no idea what any of this means or what to do.  Can anyone help?  Words of comfort would be much appreciated.  :D

---

### Post by fancypiper on 2010-01-16
Open an x terminal and copy/paste the command below and try again.

# Remove package manager lock
sudo rm /var/lib/dpkg/lock

---

### Post by kismul on 2010-01-16
> **fancypiper said:**
> Open an x terminal and copy/paste the command below and try again.

# Remove package manager lock
sudo rm /var/lib/dpkg/lock


Should this command line be entered as two separate lines i.e. 

"# Remove package manager lock" (enter)

then 

"sudo rm /var/lib/dpkg/lock" (enter)

That's what I did but still getting the same Package Manager error.

---

### Post by fancypiper on 2010-01-16
Anything preceeded by # is a comment and will be ignored. Did you get any error message for the rm command?

It looks as if you may have added a source that can't be found, i.e.:

im.archive.ubuntu.com_ubuntu_dists_jaunty-
updates_restricted_binary-i386_Packages

You could try:
sudo nano /etc/apt/sources.list

Comment out that source, save the file and exit and then try again.

If that isn't successful, what error do you get if you paste this command in a terminal?

sudo apt-get update && sudo apt-get dist-upgrade

The && means if the first is successfull, continue on with the second command, otherwise output error and quit.

---

### Post by kismul on 2010-01-16
> **fancypiper said:**
> Anything preceeded by # is a comment and will be ignored.

What errors do you get if you paste this command in a terminal?

sudo apt-get update && sudo apt-get dist-upgrade

The && means if the first is successfull, continue on with the second command, otherwise output error and quit.

It looks as if you may have added a source that can't be found, i.e. im.archive.ubuntu.com_ubuntu_dists_jaunty-
updates_restricted_binary-i386_Packages

I pasted in, hit enter and it started to proceed, at some speed, through line after line of code, far too quickly for me to see exactly what's happening.  But there's lots of ".... jaunty-updates...." in there.  And the stop sign has disappeared from the top bar on the screen.

Still running - about 6+ minutes, according to the counter in the terminal.

Once it's finished, I'll try again and post the outcome.  Many thanks for helping.

---

### Post by fancypiper on 2010-01-16
Now you are upgrading your system via apt-get rather than the gui app, (Synaptic?)!  I think you have fixed it. Perhaps you would want to post a synopsis of the exact steps you took to fix it.

[Mark Your Thread as [SOLVED] After Getting Your Answer](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

### Post by kismul on 2010-01-16
> **fancypiper said:**
> Now you are upgrading your system via apt-get rather than the gui app, (Synaptic?)!  I think you have fixed it. Perhaps you would want to post a synopsis of the exact steps you took to fix it.

[Mark Your Thread as [SOLVED] After Getting Your Answer](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

It looks like that worked!  I can now run Synaptic Package Manger and Selecting "Add/Remove..." works too.  

What I did:

The first suggestion by fancypiper (post #2) didn't have any effect.  In his second suggested fix (post #4), I tried the command:

sudo apt-get update && sudo apt-get dist-upgrade

This did the trick, running a whole load of update code, over a period of several minutes.  After which, I needed to reboot, to complete the changes.  And now it's all hunky dory.  Thanks, fancypiper.

So now I can upgrade to the new karmic koala, as I wanted to.  But maybe I'll wait a bit.... :D

---

### Post by fancypiper on 2010-01-16
FYI: If you get no error message with the command **sudo rm /var/lib/dpkg/lock**, then the command removed that file and the command succeeded, so I suspect that was the cure. The apt-get commands proved that the lock file was the problem.

---

### Post by Mikepfive on 2010-01-24
Hi,

Hi,

I had a similar problem - now solved with help from here......

Could not update my system - runing Karmic/9.10

When I launched Update Manager, I got:

"Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, Eroblem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_karmic_main_i18 n_Translation-en%5fGB, E:The package lists or status file could not be parsed or opened.' "

So I found this thread and in a command window pasted:

sudo apt-get update && sudo apt-get dist-upgrade

It ran for a short time, but when offered the option to update I declined and instead went back to the Package Manager which then worked just fine.

Many thanks to fancypiper  


Mike

PS 
Ever thought of trying (proper) Northumbian Pipes ;) ?

---

### Post by fancypiper on 2010-01-24
> **Mikepfive said:**
> Hi,

PS 
Ever thought of trying (proper) Northumbian Pipes ;) ?If I only had the money!

A friend of mine just got a set last year.:-({|=

---


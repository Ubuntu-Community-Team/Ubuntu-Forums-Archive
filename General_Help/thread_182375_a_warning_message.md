---
title: "a warning message"
date: 2006-05-25
forum: General Help
---

### Post by tomslopez on 2006-05-25
I'm getting two messages, first one I get when I go into the Update Manager and clik the 'Check' botton, and the second one I get it after I close the first one and if I open the Synaptic Package Manager. Here is the snapshot of the messages. So what do the messages mean and what can I do to get rid of them?

---

### Post by Iandefor on 2006-05-25
[quote=tomslopez]I'm getting two messages, first one I get when I go into the Update Manager and clik the 'Check' botton, and the second one I get it after I close the first one and if I open the Synaptic Package Manager. Here is the snapshot of the messages. So what do the messages mean and what can I do to get rid of them?[/quote] For one, it's showing that you have some odd-looking repositores enabled. I might be inclined to think they're mirrors for non-US users, but you're in Texas. Show me the output of: > cat /etc/apt/sources.list

---

### Post by johnc4510 on 2006-05-25
Those are repositories that were added for downloads that weren't in any of the Ubuntu repositories. They are now outdated. The 404 Error message says that that web site no longer exists. Go into your repository list and edit them out and the error messages will go away.

---

### Post by tomslopez on 2006-05-25
Here is the output of:
```
cat /etc/apt/sources.list
```

```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
deb http://wine.lowvoice.nl/apt breezy main
deb-src http://wine.lowvoice.nl/apt breezy main

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

deb http://theli.free.fr/packages/breezy/ ./
## created by arniewinechanged
```

---

### Post by tomslopez on 2006-05-25
Where do I find my repositories? and how do I edit them?

---

### Post by aysiu on 2006-05-25
[QUOTE=tomslopez]Where do I find my repositories? and how do I edit them?[/QUOTE] Go to System > Administration > Synaptic Package Manager > Settings > Repositories and uncheck the boxes for those repositories. Then click Reload.

---

### Post by johnc4510 on 2006-05-25
Applications>Accessories>Terminal
Copy and paste the following:
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
The same list as above will come up in a window that you can edit
you can do one of two things to edit:
1. Put a ## in front of the last 3 repostories. (The ones with koti and theli in the line.
2. You can just back space them out.
Finally, save the file and close the window
Now rerun your package managers and they should give no error messages.

---

### Post by Iandefor on 2006-05-26
[quote=tomslopez]Where do I find my repositories? and how do I edit them?[/quote] Hit Alt-F2. A window will pop up. Enter ```
gksudo gedit /etc/apt/sources.list
``` It will ask you for your password- it's ok to enter it. Now, the text editor should pop up with the file that contains all of your repositories. Remove the two lines that say

```

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/
``` Save the file, and close the text editor. Now, open up a terminal and enter the command ```
sudo apt-get update
``` It should work now.

EDIT: ah well... a little late

---

### Post by tomslopez on 2006-05-26
Ok I got it working now, I fixed it, thanks.

---

### Post by johnc4510 on 2006-05-26
Using which set of instructions?

---

### Post by Harold P on 2006-05-26
[quote=johnc4510]Using which set of instructions?[/quote]
Both ways will work. ;)

---


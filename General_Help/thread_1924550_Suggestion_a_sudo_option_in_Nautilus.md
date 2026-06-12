---
title: "Suggestion: a sudo option in Nautilus"
date: 2012-02-12
forum: General Help
---

### Post by ladasky on 2012-02-12
Hi, folks,

I don't know if there is an official "suggestion box" for future revisions of Linux.  But after several rounds of making sysadmin-level backups for multiple users on my machine, I've had some thoughts.

I'm current, by the way, I'm running 11.10.  Lately, I'm always on the cutting edge.

So, my first problem is that the feedback from a "sudo cp" command at the terminal prompt is lacking.  Example: I just got an error while a long backup is running:

cp: cannot stat 'john/.gvfs': Permission denied

And I cannot really tell whether my long backup is proceeding.  My hard-disk light is still blinking, that's all I know.  I am transferring over 100 GB.  I expect it to take a while.  (Aside: I did look up .gvfs and I somewhat understand why it wouldn't be a good idea for root to copy it.  I also believe that its absence from my backups is unimportant.  I just hope that the rest of my copying is proceeding as intended.)

Now, GNOME Nautilus is more verbose.  You get a progress indicator, for example.  It would really help me to see that progress indicator right now.

Occasionally, I have thought to open a terminal, type "sudo nautilus", and do some file transfer work that way.  Some strange things happen when you run Nautilus under sudo.  For example, your ability to navigate is compromised.  You no longer have a place to type in your path, apparently you have to navigate entirely by point-and-click.  As much of a hassle as that is, I think that the bigger hassle is remembering that you have to open a terminal and execute it under sudo in the first place.

So, my suggestion would be that there should be a sudo option within the Nautilus File menu.  Select it, type the administrator password, and up pops a Nautilus window with admin privileges.  Preferably, with proper file navigation tools, too.  Does this sound practical to anyone?  Does anyone know where such a suggestion would best be sent?

Thanks.

---

### Post by yetiman64 on 2012-02-12
From "man cp" use the verbose switch (-v) to have more details output.
> -v, --verbose
              explain what is being doneThere is a package in the repos **nautilus-gksu **that allows opening a folder or file as Administrator (as root) from the file/folders right click menu, it may be of some use to you (does exactly as you describe towards the end of your post). Used on file or folder it will use the default application for it as root, including using nautilus for folders.

A further tip is to always use gksudo or gksu with nautilus when opening from terminal as it is a graphical application. See the Rootsudo link in my sig for further info on it. Look down the page a bit under "Graphical sudo". Some potential problems can be avoided by doing so, problems that on occasion can stop your desktop loading on boot/restarting.

---

### Post by ladasky on 2012-02-13
Thank you, yetiman64. The nautilus-gksu extension is indeed exactly what I was looking for!  \\:D/

---

### Post by catlover2 on 2012-02-13
> **ladasky said:**
> 
...And I cannot really tell whether my long backup is proceeding.  My hard-disk light is still blinking, that's all I know.... 


Perhaps not entirely relevant, but if you want a command-line copying tool, [rsync]("http://ss64.com/bash/rsync.html") works fine for local copying while showing what files are being copied. (and I assume any errors, too)

---

### Post by dcstar on 2012-02-13
> **ladasky said:**
> Thank you, yetiman64. The **nautilus-gksu** extension is indeed exactly what I was looking for!  \\:D/

Pity it has been dropped in 12.04.

Create a Launcher with this in it and it should do the job:

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

---

### Post by Quarkrad on 2012-02-13
dcstar - I use gksudo a bit (although a newbie). Can I confirm - are you saying your code will work in 12.04 or is this just a gksudo launcher for 10.xx and 11.xx?

---

### Post by mc4man on 2012-02-13
There is a replacement for the dropped nautilus-gksu in this ppa along with others that may be of interest, currently builds for 11.10 & 12.04 
(the 'nautilus-open-as-root' one

extensions can be installed individually or as a collection, these are python-nautilus extensions, the ones i've tried work well & the doctor is good about any bugs & updates, ect.

[https://launchpad.net/~nae-team/+archive/ppa](https://launchpad.net/~nae-team/+archive/ppa)=

---

### Post by Quarkrad on 2012-02-13
Apologies for my ignorance but (as a newbie) - how in 11.xx or 12.xx do you action this?  In 10.xx I would enter gksudo nautilus in terminal - do you enter some sort of code in 11/12.xx?  (And presumably get nautilus(?)).

---

### Post by ladasky on 2012-02-15
Followup: 

Getting nautilus-gksu to work, at least, in Ubuntu 11.10 (x64), is a little tricky.  You can download a package through Synaptic, but nothing happens when you do.  In order to make it work, you have to manually copy a file, and then reboot.

I found instructions in _[this discussion]("http://ubuntuforums.org/showthread.php?t=1861721")_.

---


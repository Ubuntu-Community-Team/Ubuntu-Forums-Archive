---
title: "Upgrade has failed 15 times!!"
date: 2012-04-30
forum: General Help
---

### Post by typos1 on 2012-04-30
I start the upgrade, download the upgrade tool, enter password, download the software, then it stops half way through the next item on the list and says it cant complete the upgrade because possible network probs (there is no problem with the internet and my "network" is one pc). It then lists 6 (they are all backports), when I hit ok, its cancels the entire upgrade and reverts to normal. I have tried 15 times and I m getting really frustrated ! Have looked through the bugs thread but cant find anything.

---

### Post by Dans564 on 2012-04-30
With that many failed updates I'm sure there is breakage.  I would just backup your /home and do a fresh install.

---

### Post by QIII on 2012-04-30
Don't use the "Blast off and nuke 'em from orbit" solution yet.  There may be no need for a re-install.

Can you copy and paste the exact error messages, please?

---

### Post by uylug on 2012-04-30
Run this command:

```
sudo apt-get update && sudo apt-get upgrade -y
```

Once it's done, do a:

```
sudo dist-upgrade
```

---

### Post by QIII on 2012-04-30
That's all well and good, of course, but let's have a look at the error the OP is getting before we suggest things that may not work because of that error.

---

### Post by uylug on 2012-04-30
> **QIII said:**
> That's all well and good, of course, but let's have a look at the error the OP is getting before we suggest things that may not work because of that error.

I got your point, but I see it might be easier for the OP to post their errors if it comes from a terminal. I've posted how to accomplish the same task, without a GUI.

---

### Post by QIII on 2012-04-30
Do we know if the OP is upgrading packages on his current version or uprading to the next version?

---

### Post by uylug on 2012-04-30
> **typos1 said:**
> I start the upgrade, **download the upgrade tool**, enter password, download the software, then it stops half way through the **next item on the list** and says it **cant complete the upgrade** because possible network probs (there is no problem with the internet and my "network" is one pc). It then lists 6 (they are all backports), when I hit ok, its** cancels the entire upgrade** and **reverts to normal**. I have tried 15 times and I m getting really frustrated ! Have looked through the bugs thread but cant find anything.

I assume he is trying to do a distribution upgrade.

---

### Post by Paqman on 2012-04-30
It's not unusual to have trouble with the servers around release day. Try scanning for a faster server and trying again.

---

### Post by typos1 on 2012-04-30
Yes, upgrading to 12.04.

I know its common to get failures like this when upgrading, for instance, it took 5 attempts to start the upgrade process, I kept getting network error messages, even though my internet connection was working fine. Now it starts but get the errors I mentioned above. 

Its hard to take screenshots as the messages are too long for the message window and you cant maximise it, so will try in terminal . . .

---

### Post by typos1 on 2012-04-30
I guess as I m upgrading in a terminal now I can type the second command you gave and it will finish the upgrade as the backports listed are old and it says those updates have been ignored and old ones used instead (I m sure it usually says this anyway when I upgrade and everything usually goes ok). But wont do that until I get replies . . .

Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-backports/universe Translation-en      
Fetched 32.9 MB in 6min 46s (80.8 kB/s)                                        
W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-amd64/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-amd64/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-amd64/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-amd64/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used

---

### Post by Cheesemill on 2012-04-30
The top 3 errors are for PPA's, they probably don't have repos for Precise yet.

The rest are all for Jaunty repositories, you should have been getting these errors for a long time as 9.04 reached end of life in Oct 2010 and the repositories were taken off-line.

Can you post the output of:
```
cat /etc/apt/sources.list
```
and we can let you know where to go from there.

---

### Post by typos1 on 2012-04-30
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
# deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) maverick main # disabled on upgrade to karmic disabled on upgrade to lucid disabled on upgrade to maverick
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) oneiric universe #Added by software-properties
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) karmic main # disabled on upgrade to karmic



# deb [http://ppa.launchpad.net/paul-climbing/ppa/ubuntu](http://ppa.launchpad.net/paul-climbing/ppa/ubuntu) karmic main # disabled on upgrade to karmic
# deb-src [http://ppa.launchpad.net/paul-climbing/ppa/ubuntu](http://ppa.launchpad.net/paul-climbing/ppa/ubuntu) karmic main # disabled on upgrade to karmic
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-backports restricted main multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-backports restricted main multiverse universe #Added by software-properties
# deb [http://ppa.launchpad.net/rvm/mplayer/ubuntu](http://ppa.launchpad.net/rvm/mplayer/ubuntu) jaunty main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) jaunty main # disabled on upgrade to lucid
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main #Third party developers repository
deb [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/tualatrix/next/ubuntu](http://ppa.launchpad.net/tualatrix/next/ubuntu) oneiric main

I do remember re-enabling some software sources after I last upgraded, I think I may have re-enabled some old ones.

Update manager has come up now with some upgrades for 11.10. shall I ignore them or do them first then go to 12.04 ?

I think when I type the upgrade command in a terminal it will do it.

---

### Post by QIII on 2012-04-30
> **uylug said:**
> I assume he is trying to do a distribution upgrade.

In which case the instructions would not have accomplished his goal.  dist-upgrade does not upgrade to a new version, despite the misconception.

---

### Post by QIII on 2012-04-30
Typos1 --

Your Oneiric should be completely updated before you attempt the upgrade to Precise.

So you'll have to make sure your sources.list is clean.  Also, I'd deactivate any ppas and non-standard repos until you are upgraded.

Unless you are very comfortable making the changes manually, I would suggest using Synaptic or the package manager of your choice to edit your sources.

---

### Post by typos1 on 2012-04-30
I have updated 11.10.

Does dist-upgrade upgrade me ?

---

### Post by NadirPoint on 2012-04-30
I'm liking the "backup /home, fresh install idea."

Use Bitorrent to get the CD 1st, and take network out of the equation entirely - even better.

---

### Post by QIII on 2012-04-30
No.  dist-upgrade does not upgrade you to Precise.  That's do-release-upgrade (but don't rush off and use it, please)

The dist-upgrade command is like the upgrade command in that it upgrades the current packages in your current version, but it also attempts to resolve dependency issues.

As advised above -- first back up your data.  Although I usually do full installs, getting even that done just right takes some prior planning.  I'd love to say it's as easy as just putting your /home back in place when you are done, but it's not.  For instance, with Firefox and Thunderbird you usually have to make sure your profiles are properly arranged afterwards. You also have to use a technique to create a list of your apt installed packages and reinstall them on the other side (get and set selections commands).  Simple enough if you know what you are doing.

If you want to do this through the GUI (which, in all honesty, might be less frustrating for you right now), try the update manager.

If you are completely updated, you should see a button that says "12.04 LTS is available" or something to that effect.

Click it.

If you want to do it via command line, you can use do-release-upgrade (you can find tutorials on the forum).

---

### Post by LonelyAspie on 2012-04-30
> **typos1 said:**
> I start the upgrade, download the upgrade tool, enter password, download the software, then it stops half way through the next item on the list and says it cant complete the upgrade because possible network probs (there is no problem with the internet and my "network" is one pc). It then lists 6 (they are all backports), when I hit ok, its cancels the entire upgrade and reverts to normal. I have tried 15 times and I m getting really frustrated ! Have looked through the bugs thread but cant find anything.

I tried to upgrade on two computer, unfortunately, there is a bug which will not make it successful, unless it is down from a fresh install. :(

---

### Post by typos1 on 2012-04-30
QIII, I have always upgraded my pc using upgrade manager. I used to back up but dont usually bother now as I ve never had a problem involving loss of data and I dont think the upgrade tool is likely to totally wipe data and do a fresh install.

I am familiar with upgrading and installing from cd though, as I ve done that on other pcs and obviously mine when I first used ubuntu. In my experience it is as simple as copying home, firefox and thunderbird folders then adding bookmarks and emails to the new set up. I dont really think that is necessary in this case though.

But the problem I am getting is whilst upgrading through update manager so it clearly ISNT going to be "less frustrating" its the CAUSE of the problem -  upgrade manage jsut quits the whole process after telling me its used old ppas instead, at least with the terminal I can tell it to upgrade myself.

What is wrong with using do-release-upgrade? - surely the GUI is doing exactly the same thing ?

LonelyAspie might be right, there may well be a bug somewhere. I have stuff to do online tomorrow, but after I will disable those ppas and attempt upgrading again and see what happens.

---

### Post by typos1 on 2012-05-07
Tried this again, still get the errors, so tried to disable the sources that are the problem, thing is they might appear when I type 
cat /etc/apt/sources.list[COLOR=#000][FONT=arial] 

[/FONT][/COLOR]in a terminal, but they dont appear in my software sources list, so how do I remove them ?

---

### Post by typos1 on 2012-05-08
Anyone?

---

### Post by typos1 on 2012-05-16
Everytime I try and upgrade (tried 15+ times now!)  I get to the point where it tells me about 5 repositories cant be found and that old ones are going to be used instead, when I click ok it aborts the upgrade and restores the system to its original state. 

They are old jaunty repositories, I m not sure what for, but I cant find them in software sources to remove them and I dont know what difference it makes anyway as theyve clearly been on my system since jaunty and werent a problem for upgrades to 9.10 all the way to 11.10.

Can anyone help ?

Thanks

---

### Post by jadtech on 2012-05-16
change servers and don't use any  jaunty repositories all the info I can find shows they are no longer working :)

do the apt-get update and do-release-upgrade from the terminal 

seems you really just need to do a rebuild of repositories either way

---

### Post by typos1 on 2012-05-17
But they do not appear in my software sources , list, so I cant remove them.

---

### Post by typos1 on 2012-05-17
dist-upgrade does nothing, it says command not found.

do-release-upgrade results in the same errors as doing it through the GUI.

---

### Post by jadtech on 2012-05-17
did you have an way older version of ubuntu install  before 11.04 ?? 
that you may still have programs installed from  that can no longer be updated ..

if so go to software updater, settings ,other software tab and uncheck the ppa for all of them , in fact it wont hurt to uncheck all the ppa's on other software  for the upgrade :) 

change your server and  try the update upgrade commands again ..

---

### Post by wilee-nilee on 2012-05-17
The next post is a better answer.

---

### Post by drs305 on 2012-05-17
You can search your /etc/apt folder to see if it can located a jaunty source list. It might even be in the /etc/apt/sources.list.d folder.
```
sudo find /etc/apt -iname *jaunty*
```

If that doesn't find a jaunty list (which it mightn't since a normal sources.list doesn't contain the release name), you could install 'gnome-search-tool', open as root, and search for the text 'jaunty' in the same folders (/etc/apt and subfolders).

As to why the list worked for so long, the jaunty repositories would have been available until at least Apr 2011. If you happened to install a very early version of 11.10 they could have been available at the outset, and would certainly have been available through 11.04. At some point after Apr 2011 the jaunty repository would have been moved, at which time the error messages would have started. 

If you have done any reinstalls or copying of backups, perhaps the jaunty repository entry made its way back into your system.

---

### Post by oldos2er on 2012-05-17
Threads merged.

---

### Post by typos1 on 2012-05-18
Right, thanks. 

Sudo find does nothing.

I thought it was all supposed to be managed through softwares source app/GUI ?

  I just looked in the file system.

Found nothing in /etc/apt/sources.list.d (which is a folder) but found jaunty backports in /etc/apt/sources.list (which is a file, basically it seems to be the same as the output of what I was told to type in a terminal last week).

How do I remove them ?

---

### Post by drs305 on 2012-05-19
> **typos1 said:**
> Right, thanks. 

Sudo find does nothing.

I thought it was all supposed to be managed through softwares source app/GUI ?

  I just looked in the file system.

Found nothing in /etc/apt/sources.list.d (which is a folder) but found jaunty backports in /etc/apt/sources.list (which is a file, basically it seems to be the same as the output of what I was told to type in a terminal last week).

How do I remove them ?

You can do it via Software Sources (Ubuntu Software Center: Edit, Software Sources; Update-Manager: Settings lower left; Synaptic: Edit, Repositories). 

Go to the Other Software tab and look for the jaunty entry/entries. Deselect/untick any that you find.

Otherwise, you can edit the file directly. Once you have edited the file, save it and run the second command:
```
gksu gedit /etc/apt/sources.list &
sudo apt-get update
```

---

### Post by typos1 on 2012-05-20
I removed all mention of jaunty from the list. I got his at the end :

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
[1]+  Done                    gksu gedit /etc/apt/sources.list

Update manager hung when I tried to upgrade using it, so I did it in a terminal.

Whilst it was upgrading I noticed in the terminal that it was un-installing amsn, then the icon disappeared from unity. Why did it do this ?

After a few hours I got this:

Setting up libmono-sqlite4.0-cil (2.10.8.1-1ubuntu2) ...
Setting up libmono-system-web-applicationservices4.0-cil (2.10.8.1-1ubuntu2) ...
Setting up libmono-system-web4.0-cil (2.10.8.1-1ubuntu2) ...
Setting up mono-2.0-gac (2.10.8.1-1ubuntu2) ...
Setting up libmono-system-web-services4.0-cil (2.10.8.1-1ubuntu2) ...
Setting up libmono-web4.0-cil (2.10.8.1-1ubuntu2) ...
Processing triggers for libreoffice-common ...
Setting up libreoffice-emailmerge (1:3.5.3-0ubuntu1) ...
Setting up openoffice.org-emailmerge (1:3.3.0-7ubuntu7) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for libgdk-pixbuf2.0-0 ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for resolvconf ...
Processing triggers for libgdk-pixbuf2.0-0:i386 ...
Processing triggers for python-support ...
Processing triggers for python-central ...
Errors were encountered while processing:
 whoopsie
Error in function:


A fatal error occurred

Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in
your report. The upgrade has aborted.
Your original sources.list was saved in
/etc/apt/sources.list.distUpgrade.

SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)


ERROR: hook /usr/share/apport/general-hooks/ubuntu.py crashed:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 718, in add_hooks_info
    symb['add_info'](self, ui)
  File "/usr/share/apport/general-hooks/ubuntu.py", line 49, in add_info
    check_attachment_for_errors(report, log)
  File "/usr/share/apport/general-hooks/ubuntu.py", line 149, in check_attachment_for_errors
    if attachment in report and re.search(grub_error, report[attachment], re.MULTILINE):
  File "/usr/lib/python2.7/re.py", line 142, in search
    return _compile(pattern, flags).search(string)
TypeError: expected string or buffer


What shall I do now ?

Bug reporting opened a launchpad entry, but the bug dates back 2 years and is listed as for i386 architecture, 32 bit. I m using an amd64 processor and 64 bit version of ubuntu, though.

Gone back to the terminal and it says that the upgrade has finished ! ? I m confused now, I ve also checked "system" in system monitor and it says precise. 

I havent rebooted or anything and despite the error I ve been upgraded. 

I got the message press x to terminate window or r to resurrect. 

I pressed r, thinking it would keep the terminal open, but it seemingly ran the process again and tried to  upgrade whoopsie, ( which failed again).

This is the terminal:

Errors were encountered while processing:
 whoopsie
Error in function:


A fatal error occurred

Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in
your report. The upgrade has aborted.
Your original sources.list was saved in
/etc/apt/sources.list.distUpgrade.

SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)



Could not install the upgrades

The upgrade has aborted. Your system could be in an unusable state. A
recovery will run now (dpkg --configure -a).

Setting up whoopsie (0.1.32) ...
Error: API mismatch: the NVIDIA kernel module has version 280.13,
but this NVIDIA driver component has version 295.40.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
groupadd: cannot lock /etc/gshadow; try again later.
adduser: `/usr/sbin/groupadd -g 132 whoopsie' returned error code 10. Exiting.
dpkg: error processing whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 whoopsie

Upgrade complete

The upgrade has completed but there were errors during the upgrade
process.

To continue please press [ENTER]


From that I assume its talking about the GPU, not the CPU ?

I dont appear to have nautilus - if I plug in a hard drive, it mounts but no nautilus window opens and if I try and access any files, again, nautilus doesnt open.

Wondering whether I should reboot or not ? . . .

Took the chance and did.

All is fine in Precise, I get nautilus now.

No sound and the "scale" icon has disppeared from unity, plus it doesnt work or appear in unity, even when you click on it. :(

---

### Post by drs305 on 2012-05-21
Are you still getting the 'sevenmachine' error? It's possible the ppa was offline for a while. If the error message still appears you can disable that ppa via the "Other Software" tab of Software Sources or by using one of the options in Ubuntu Tweak (if installed).

As for upgrade problems, they can be really hard to identify. I'm not sure what the system status is now, based on the last several lines of your last post.

---

### Post by typos1 on 2012-05-21
As per my l;ast few sentences really - ie fully updated (acheived without restarting, although had to restart to get nautilus to work), with two bugs :

 the "scale" window swithcer icon has disappeared from unity (its still in apps but a) doesnt work properly and b) the icon doesnt even appear in unity when its running) 

internal audio doesnt work.

"whoopsie" (!) didnt install properly and everytime I install something it gives an error message because of this

---

### Post by drs305 on 2012-05-21
Regarding 'whoopsie', have you tried to fix broken packages or uninstall it. You can do the former via Synaptic (if installed, using the Custom filter to find the broken listings) or possibly via:
```
sudo apt-get install --fix-broken whoopsie
or
sudo apt-get remove --fix-broken whoopsie

```

---

### Post by typos1 on 2012-05-21
Coding those 2 things in a terminal results in:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
whoopsie is already the newest version.
The following packages were automatically installed and are no longer required:
  libkworkspace4 libaccess-bridge-java libatlas3gf-base libx264-116 hplip-cups
  anthy awn-applet-weather libtextcat-data python-mutagen libpolkit-gtk-1-0
  libgupnp-1.0-3 libtracker-extract-0.10-0 python-indicate libcvaux2.1
  libdns69 libgps19 libiso9660-7 libboost-date-time1.46.1 libindicator3-6
  libkwineffects1abi2 caribou lib32ffi6 python-mpd libindicator6
  libaccess-bridge-java-jni liblwres60 libhighgui2.1 libept1 libgtkglext1
  libmatroska4 python-telepathy libgdata1.7-cil libminiupnpc5 libbind9-60
  libpoppler-glib6 ttf-kacst-one libcv2.1 libtextcat0 dockmanager
  unity-2d-places libjpeg62:i386 libquvi0 lib32ncursesw5 libexiv2-10
  libtracker-miner-0.10-0 libgupnp-igd-1.0-3 libisccfg62 libnl3 libgtkspell3-0
  libattica0 libanthy0 anthy-common libgfortran3 gir1.2-dee-0.5 python-wnck
  libtracker-sparql-0.10-0 libgmime2.4-cil libnatpmp1 libpoppler13
  unity-2d-launcher libgssdp-1.0-2 icc-profiles-free libllvm2.9
  libllvm2.9:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up whoopsie (0.1.32) ...
groupadd: cannot lock /etc/gshadow; try again later.
adduser: `/usr/sbin/groupadd -g 132 whoopsie' returned error code 10. Exiting.
dpkg: error processing whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 whoopsie
E: Sub-process /usr/bin/dpkg returned an error code (1)
username@username-desktop:~$ sudo apt-get remove --fix-broken whoopsie
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


The first one, ironically enough, is the same error I get when i try to install anything else. 

Its also a known bug from 2 years ago (the lock/etc/gshadow thing). 

I have added a comment on the launchpad page but no-one has replied yet.

I tried re typing the second command, was successful the second time, I think it just removed whoopsie ?

Is this a problem ? What does it do ?

---

### Post by drs305 on 2012-05-21
> **typos1 said:**
> 
I tried re typing the second command, was successful the second time, I think it just removed whoopsie ?

Is this a problem ? What does it do ?

Whoopsie: This program submits crash reports back to an Ubuntu server.

You can get a short description of many packages with:
```
dpkg -l <packagename>
dpkg -l whoopsie
```
You can reinstall it if you wish. I checked and don't currently have it installed on my system, although it is on my default install in VirtualBox. I may have removed it but it doesn't affect my normal system ops.

---

### Post by typos1 on 2012-05-21
Tried re-installing it, still failed, so removed it again. I like errors and bugs to be reported, but Ic an live without it.

---

### Post by tumutanzi.com on 2012-05-21
I have also encountered a strange problem after a "successful" upgrade, but I failed to log into the new 12.04, I tried many methods to get rid of the problem, finally I made a complete re-install, now everything is OK.
So my experience and suggestion is upgrade of Ubuntu can have lots of problems and you may never know how to fix it.

---

### Post by typos1 on 2012-05-21
Not like my experience then - I ve upgraded 6 times, only had problems on the 6th time and I sorted the problems in the end. The problems werent that bad - I could alsways use my system. Maybe you were too quick to do a fresh install ?

---


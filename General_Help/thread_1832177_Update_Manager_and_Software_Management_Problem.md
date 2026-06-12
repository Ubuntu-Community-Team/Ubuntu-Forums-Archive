---
title: "Update Manager and Software Management Problem"
date: 2011-08-24
forum: General Help
---

### Post by TurtleKing on 2011-08-24
I keep getting this pop-up to install FlightGear 2.0 base files for the flight simulator flightgear. The thing is that every time I try to install I get an error that says, "subprocess new pre-removal script returned error exit status 1". I also, cannot install the program's newer version (2.4.0)) since I get the same failed error.

Edit: Confirmed! I can't install anything or get updates for Ubuntu.

Operating System: Kubuntu 11.04 64bit
What did you do before problem occurred:
I found the FlightGear 2.4 available on Playdeb, so I decided to get it. Before I did that, I wanted to make sure the previous version (2.0) was removed, so it would not by accident write something in the old directory.I uninstalled the program via Software Management, but for some reason it left the folder with files still in usr>share>games. I went ahead into root and deleted it, and all files related in the home folder. Finally, I went ahead with the download and installation, but now I got the above error after it was about to install and from update manager.

Any help is appreciated...

---

### Post by TurtleKing on 2011-08-25
bump

---

### Post by TurtleKing on 2011-08-25
I tried running this command suggested in another thread which I think might be helpful.
```
username@computer:~$ sudo deborphan | xargs sudo apt-get -y remove --purge
[sudo] password for hades: 
sudo: deborphan: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 fgfs-models-base : Breaks: fgfs-base (< 2.4.0) but 2.0.0-1 is installed
 flightgear : Depends: fgfs-base (>= 2.4.0) but 2.0.0-1 is installed
E: Unmet dependencies. Try using -f.
username@computer:~$
```

I hope this helps someone help me fix this problem. It is starting to become very annoying (I cannot update Kubuntu files cause of it).

---

### Post by dino99 on 2011-08-25
[http://www.unitedfreeworld.com/ubuntu_debian_fgfs_installation.html](http://www.unitedfreeworld.com/ubuntu_debian_fgfs_installation.html)

---

### Post by TurtleKing on 2011-08-25
> **dino99 said:**
> [http://www.unitedfreeworld.com/ubuntu_debian_fgfs_installation.html](http://www.unitedfreeworld.com/ubuntu_debian_fgfs_installation.html)

Can you be a little more specific? It doesn't say in that link that by downloading the game again it will fix the software management and update manager.

---

### Post by ankspo71 on 2011-08-25
Hi,
I also found out that Flightgear packages can't be mix matched, eg 2.0 packages will not work with 2.4 packages. 

It sounds like flightgear 2.0's base packages didn't get uninstalled when you uninstalled flightgear, and even you manually deleted the base files, the system still thinks you have the base packages installed. 

So I recommend starting over and pasting the following commands in the terminal. The commands will fix dependency problems, remove all packages related to flightgear, and remove unwanted dependencies.

```
sudo apt-get -f install
sudo apt-get remove flightgear
sudo apt-get remove fgfs*
sudo apt-get autoremove

```
The first command will try to fix dependency conflicts and will let you update your system again. This is the command that was recommended to use by your system.

> username@computer:~$ sudo deborphan | xargs sudo apt-get -y remove --purge
[sudo] password for hades: 
sudo: deborphan: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run [COLOR="Red"]'apt-get -f install'[/COLOR] to correct these.
The following packages have unmet dependencies:
 fgfs-models-base : Breaks: fgfs-base (< 2.4.0) but 2.0.0-1 is installed
 flightgear : Depends: fgfs-base (>= 2.4.0) but 2.0.0-1 is installed
E: Unmet dependencies. Try using -f.
username@computer:~$

The second command will remove the main package called flightgear.

The third command will remove all flightgear base packages 

The fourth command will remove all unwanted dependencies on your system, and some of which will be related packages for flightgear (such as simgear and libopenscenegraph).

Now you should be able to update your system and install flightgear again. I recommend making sure the directory /usr/share/games/FlightGear/ is empty before installing flighgear again.

Hope this helps.

---

### Post by TurtleKing on 2011-08-25
Hey, I tried commands 1-4, and 1, 3, and 4 returned the same error:
```
Errors were encountered while processing:
fgfs-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Also, 4 did remove the unnecessary packages, but I still cannot install anything. I tried installing solitaire, but it just downloaded and went into error.
> One of the selected packages failed to install correctly.
More information is available in the detailed report.
Details:
subprocess new pre-removal script returned error exit status 1


---

### Post by ankspo71 on 2011-08-25
Hi,
The first command should have fixed the problem under normal circumstances (as they did for me), but here is another command that you can try:
```

sudo dpkg --configure -a
sudo apt-get install -f
```

Now see if you can update your system.
```

sudo apt-get update
sudo apt-get dist-upgrade
```

You might want to try disabling the playdeb repository first if you are using it.

If you still can't install or update, then you might have a dpkg bug in 11.04 that I have been hearing about. The following link offers some commands to try, and if all else fails, towards the end it shows a way to trick the system into thinking fgfs-base is no longer installed.
[http://journalxtra.com/2010/03/fixing-the-dreaded-errors-were-encountered-while-processing-errors/](http://journalxtra.com/2010/03/fixing-the-dreaded-errors-were-encountered-while-processing-errors/)

Hope this helps.

---

### Post by TurtleKing on 2011-08-25
If that last solution doesn't work I am just going to reinstall Kubuntu 11.04. Hopefully I will not have a problem till 11.10 is released.

---


---
title: "Hanging on graphical boot, command line boot perfect"
date: 2012-02-19
forum: General Help
---

### Post by kylewison on 2012-02-19
Hi I'm a bit new to the forums but I'm having a troubling error which I can't seem to find the correct information to get started.

I'm running Ubuntu 11.10
With kernel 3.0.0-12-generic-pae i686


A couple days ago I attempted to turn on my computer and boot into "kubuntu" I selected the option in GRUB (not GRUB 2) and it continued on to a graphical loading screen (blue with kubuntu and the small dots beneath). The dots simulate a loading bar for a while and then all of the sudden go dim and it seems to hang, I left it sitting for about an hour to make sure I wasn't just being impatient. 

First thing I tried: 
I selected the recovery mode option in GRUB and dropped to command line as root, everything works fine, I can browse the file system, use certain commands. (of course it's read-only though)

Next:
I recognized that if I select recovery mode and hit cancel it boots into a command line and allows me to log in, it allows me to do everything, connect to the internet, update packages, edit files.

Lastly:
I attempted to view the boot.log file in /var/log/ however it is very incomplete and was all of about 20 lines. I then found out that by taking out "quiet" from /etc/default/grub file in attempt to get a "verbose" boot which would hopefully give me a starting point, I didn't notice any change to the boot log nor booting through any of the methods I mentioned.


As you can tell, I'm a bit new to this and I'm not asking for someone to hold my hand step by step, but I would really appreciate a point in the right direction because at this point I'm a bit clueless as to where to start.


Cheers,

Kyle Wilson

---

### Post by oldfred on 2012-02-20
Was it booting ok before?

From command line have you tried updating to see if some update did not complete.

I often suggest these after a chroot, but you can run with sudo from recovery command line:
#if not chroot use: 
sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by kylewison on 2012-02-21
Thanks for the reply oldfred!

Just to clarify, it was booting fine before, I've been using it for just around 3 months with no problems until this. I tried to think if the last time I was successfully using it I made any major changes and none came to mind. I recall installing a program but it was from one of the main repositories, however I cant for the life of me remember what it was.

I followed your suggestions in the order you suggested as well. There wasn't much when I did the regular update/upgrade but there was like 344MB when I did the dist-upgrade(i need to keep up with that).

The whole process went fine with no errors, all successful. However, it still seems to hang on the boot. Perhaps what I don't understand, is if the system seems fine and it only seems to have trouble when using any sort of graphical mode could it perhaps be some sort of graphics drivers?

As I was typing this I thought maybe I'll hunt down what I recently installed and try and remove it, I found this command in ubuntu help

zcat -f /var/log/dpkg.log* | grep "\ install\ " | sort

I'll  report back if I have any luck, I really appreciate your suggestions and if you have any other ideas I'm open for them!

---

### Post by oldfred on 2012-02-21
I do not know what may have changed. This is mostly for new installs where users have issues:
Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

#Start gdm
sudo service gdm start

#To see video:
sudo lshw | grep -A 11 display

#If able to boot to recovery mode & netroot
#list of recommended drivers:
jockey-text -l
#Install a driver:
sudo jockey-text -e <driver>

For Kubuntu it is not gdm but I do not know for sure what it is? kdm? If so use kdm not gdm in commands below:
#Reconfigure graphics
sudo dpkg-reconfigure -phigh xserver-xorg
startx
#or now preferred to restart gdm, I have seen all of these as preferred but do not know if one is better or not.
sudo service gdm start
sudo /etc/init.d/gdm restart
sudo start gdm

---

### Post by kylewison on 2012-03-10
Just as an update, I attempted to find all recommended drivers and it was an empty list. I found some other guides on "reinstalling" the graphics drivers none of which solved the problem.

I eventually just gave up on solving this problem. I moved all my data to an external drive and wiped the whole thing and reinstalled windows and kubuntu. 

This obviously worked but probably isn't the best solution to this problem, I just wanted to say this so it wasn't one of those "unanswered" threads. If anyone else gets stuck with this problem in the future I'd love to hear how they fixed it. Good luck! :D

Kyle Wilson

---


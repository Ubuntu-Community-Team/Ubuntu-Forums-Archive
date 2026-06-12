---
title: "Accidentally uninstalled nautilus"
date: 2010-01-19
forum: General Help
---

### Post by Bender59 on 2010-01-19
Something happened, and Nautilus was uninstalled, along with gnome-session and some other thing. As I remember that was uninstalled, and didn't know nautilus had been uninstalled, I tried re-installing it in recovery mode. However, now GRUB has a Debian-style background, is cut off outside the boundaries of 800x600 (from the topleft corner) and booting into anything but Windows will result in some sort of error where something freezes and I can't do anything, including get into the command line.
When I boot normally, I get an error about not having the module "i810", and from here I can choose to edit my config files or exit to console login. First choice does nothing, and returns to the choice box, and console login makes my screen black, with nothing happening.

Does anyone know how I can solve this problem, either by getting into the command line in recovery mode (it freezes at "Starting init crypt disk") or to login. For the time being, I can settle for just being able to access my home folder on my Ubuntu partition, since I've got something important I need for tomorrow on there.

I've also tried running from a live USB (don't have discs). I can get into my Ubuntu partition to edit stuff (or replace with things from live USB), but still can't access files in my home folder, even with "chmod +r" on it.

Thanks in advance to anyone who can help with this.

PS: If I install Ubuntu again on top of that, it'll delete everything including my home folder, correct?

---

### Post by victor.zamanian on 2010-01-19
I don't know about a solution to the missing nautilus, but what steps have you taken to mount your home folder when in the LiveCD environment?

You should give the `mount' program a try if you haven't. If you can, find out on which device (in the /dev directory) your home folder is mounted, then use the mount program to mount it under a folder. A very general case might be the following:

Say your /home folder is on the same partition as your / (root dir), which is the 3rd partition (which is ext4) on the first hard disk (and you have an SATA disk):

# mkdir ~/mountpoint
# mount -t ext4 /dev/sda3 ~/mountpoint

"#" means the current user is the super user.

I hope I made this somewhat comprehensible. :|

PS: Yes it will definitely destroy your data if you install Ubuntu again on top of any disk partition on which you already have data.

---

### Post by michy99 on 2010-01-19
As for accessing your files from a live USB, open nautilus as root with```
gksudo nautilus
```Then you should be able to access files and copy them. As to the rest of your problem, maybe someone else can help.

---

### Post by Bender59 on 2010-01-19
I'm in the home folder, but the only things there are "Access Your Private Data" and "README.txt".

Upon running "ecryptfs-mount-private" as I'm told to in README.txt, it says the private directory is not setup properly.

EDIT: If I were to login as root in live USB mode, could I copy-paste everything from there to my Ubuntu partition?

---

### Post by michy99 on 2010-01-19
I didn't realize it was encrypted. I don't know anything about that.

---

### Post by KinKiac on 2010-01-19
Well, you should be able to view the files as long as you have sudo rights to those files.  You could try opening a terminal from the live cd and then type su - <username>, replacing <username> with your actual username on your installation, and then type sudo nautilus, using the same password as you would on your full installation.  That might trick it into giving you access.  I havent tried anything like this with a livecd but I know it works with a full installation(see below)

 Ive had success in a similar situation with Hardy server edition that was password protected and totally locked down, root and all(or supposed to be).  I have a full installation of Jaunty on a thumb drive and booted to that instaed of the HDD that the server edition is installed in.  Then I first mounted the root partition of the server OS by simply clicking on it in the Places menu.  After it was mounted I then ran "sudo nautilus" from a terminal and entered in MY sudo password and was able to get into the other filesystem as if I had root privileges on it, and was able to edit the server.conf file and well as any other file I wanted to, thus being able to un-do anything our network guy had done to it.  (no im not a hacker i work in IT and was testing one of our terminals to see how locked down our network guy had it, in the process I found an interesting way to hack an ubuntu box, as long as you have physical access to it anyway AND the BIOS is not locked down and set to not boot to anything other than the HDD)

P.S sorry i cant help with the nautilus issue at all, way beyond my ability.  If it were me id do my best to recover any valuable files and then re-install the whole thing.

---

### Post by Bender59 on 2010-01-19
Still unable to access it. I just finished copying all the stuff from my live USB boot to the partition, gonna try booting now. Wish me luck.

EDIT: I'm in, but I can only access the command line, even though I've installed Nautilus and rebooted. What else might I need to reinstall/configure to get to the proper login screen?

---

### Post by todak on 2010-01-19
```
sudo apt-get install ubuntu-desktop
``` should do it.

---

### Post by Bender59 on 2010-01-19
It's already installed, still getting command line. Would I need to configure anything for it, or perhaps something else needs be installed?

By the way, should /sys have anything in it? I don't recall there being anything there before, but there was some stuff when I copied from USB, and now there is.

---

### Post by Ordes on 2010-01-19
reinstalling will not delete your old data, if u know how to reinstall..

1. Do u have a separate partition for /home ?

2. If not than you have can 

>> 2.1.0 if u have enough free space on a second par to copy home
2.1.1 load up ubu live, gparted create second par, i call it sdaNEW, check which sdXY your "/" is on, i call it sda1
2.1.2 Copy your /home to sdNEW, rename "old-home"
2.1.3 might want to shrink sda1, as it will be "/" only; 10-15gb should be enough
2.1.4 install ubu, choose manual partitioning, sda1 > "/" format, sdNEW > "/home" (DO NOT FORMAT), finish install.. Username etc u should use the same as before...
2.1.5 load up ubu. terminal
$ sudo rm -r /home/username [replace username with new username, will delete new username directory]
>> check path before moving, your old-home should be in /home/old-home/username
$ sudo mv /home/old-home/username /home/username [username 1 is old one, username 2 is the one u used on the new install]
2.1.6 after moving your /home check your permissions
$ ls -l /home [thats a small L, should be username:username)
if not
$ sudo chown -R username:username /home/username
2.1.7 log in and out... your old home is back

>> 2.2.0 if u dont have enough space to create a second par for home, but enough to create a second par for "/"
2.2.1 load up ubu live, make a small partition for "/" >> sdNEW, check where your current "/home" is ....probably sda1
2.2.2 rename /home to /old-home
2.2.3 install ubu.. manual partitoner, sda1 "/home" (DO NOT FORMAT), sdNEW "/" (format)
2.2.3 finish like written above..
2.2.4 after 2.1.7 remove all "old-sys-folders" from sda1 (e.g. bin, boot, etc....)
>> difference your "/" will be on a following partition sda2, whereas "/home" is on sda1

>> 2.3.0 if u dont have enough space to create a second par at all
2.3.1 load up ubu live, rename /home to /old-home
2.3.2 install ubu.. manual partitoner, put everything on sda1 (DO NOT FORMAT)
2.3.3 finish like written above..
2.3.4 terminal, paths should be
$ sudo rm -r /home/username
$ sudo mv /old-home/username /home/username
2.3.5 back to 2.1.6

>>2.4.0 In case your "/home" already is on a second partition
2.4.1 load up live, check gparted for "/" and "/home", eg. sda1 "/", sda2 "/home"; rename "username" to "old-username"
2.4.2 load up installer, manual partitioning, sda1 > "/" format, sda2 "/home" (DO NOT FORMAT).... keep on like in 2.1.4.. 
2.4.3 after install, check paths.. but it should be 
$ sudo rm -r /home/username
$ sudo mv /home/old-username /home/username

-------

>> better to always have /home on a seperate partition than your sys

---


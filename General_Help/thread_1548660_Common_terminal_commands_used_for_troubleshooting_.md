---
title: "Common terminal commands used for troubleshooting in the forums"
date: 2010-08-08
forum: General Help
---

### Post by slooksterpsv on 2010-08-08
Hey All,

I need to know what commands we have people run in the terminal in order to help them troubleshoot their issue. The reason being, is I was reading a thread where someone was stating about how they had to do all this and all that from a terminal and what not and that there should be a GUI Tool.

Well I'm going to make a GUI tool that allows them to obtain all the necessary information (and fixes are possible too) to help with their issue that they're currently having. For example: I know we run lsmod for sound issues, but what other commands do you have them run to check sound, video, network, etc.

It will be made in wxPython so that it can be easily sent to others. If it becomes quite useful, then maybe we could get it in the repos.

Thanks All!

EDIT:

Adding a screenshot to illustrate what I'm doing.

---

### Post by ajgreeny on 2010-08-08
Sorry, but I think you are trying to do something that would be better served with a link to a command line index, but perhaps that is simply because I use the terminal quite a bit, and am not scared to use it for simple things.

Perhaps I misunderstood exactly what you meant, but I'm afraid your screenshot did not help me at all.

Anyway, here's a few that I have often found useful.

**sudo fdisk -l**                                                     to show all partitions and their format types in computer.
**sudo lshw -C display**                               to show graphic card make etc.
**lspci**                                                                           to show all of the pci cards (graphics, sound etc etc) in machine.
**sudo blkid**                                                           to list UUIDs of all partitions.
**ps aux | grep <searchterm>**                    to find any process running with name containing <searchterm>

There are masses of others, but I will try to add them as I think of them.  Where do we stop?

---

### Post by slooksterpsv on 2010-08-08
Pretty much any command where we tell them to type it into terminal and paste the results back to us.

I'll even put one in to print out the xorg.conf file. So this tool will be used for people who don't want to use the terminal or have trouble with copying data from the terminal, and even those who are just new to Linux.

So pretty much anything's fair game, even gksudo apt-get update (gksudo so they don't have to run anything in the terminal).

Yeah the screenshot is very vague, I admit that, but I'll have tabs across the top or side that say:
Graphics
Audio
Hard Drive
etc.
Run All Diagnostics

And have it output to a txt file for individual ones, or to a tar.gz if multiple are ran. That way we can tell them, go to the graphics tab and click on Get xorg.conf or what not.

---

### Post by diesch on 2010-08-08
[https://wiki.ubuntu.com/DebuggingProcedures](https://wiki.ubuntu.com/DebuggingProcedures) should be a good starting point.

---

### Post by Iowan on 2010-08-08
A couple of primary commands for networking:
**sudo lshw -C network**
**ifconfig -a**

---

### Post by linux18 on 2010-08-08
```

sudo killall synaptic && sudo killall aptitude && sudo killall mintinstall && sudo killall software-center
 sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade 

```my kitchen sink command for fixing synaptic's failed/partial downloads, broken dependencies, broken packages,  updates, upgrades, and cleaning synaptic caches.

BTW, love the idea! an all in one program for fixing the most common errors and suppling output to copy/paste into forums is a great idea!

---

### Post by slooksterpsv on 2010-08-08
Here's a better screenshot of what I'm trying to do, now the only thing is, this may not be the final look of it all so its still under work (and quickly working on it thx to wxglade).

---

### Post by slooksterpsv on 2010-08-09
In case anyone wants to give it a preliminary try, I'll call this version 0.0.1 - it only outputs and isn't fully ready, but try it out Let me know what I should fix/change/etc.

Extract, go into the Debug folder and run pydiag (its a simple sh script)

---

### Post by stinkeye on 2010-08-09
> **slooksterpsv said:**
> In case anyone wants to give it a preliminary try, I'll call this version 0.0.1 - it only outputs and isn't fully ready, but try it out Let me know what I should fix/change/etc.

Extract, go into the Debug folder and run pydiag (its a simple sh script)

I had to install wxGlade for it to work.
Works ok with an error output...
```
./pydiag.py:97: DeprecationWarning: os.popen4 is deprecated.  Use the subprocess module.
```
Good idea though. =D>

---

### Post by AlphaLexman on 2010-08-09
I understand your motivation for this project, but I don't understand why some people are SO afraid of the command line, that they need to click a menu, a tab, and then a button... all to avoid five keystrokes. But anyway here's my input for your project:


[LIST]
[*]lscpu
[*]lsdev
[*]lsdvd
[*]lshal
[*]lshw
[*]lsmod
[*]lsof
[*]lspci
[*]lspcmcia
[*]lsusb
[*]uname
[/LIST]

---

### Post by ajgreeny on 2010-08-09
> **AlphaLexman said:**
> I understand your motivation for this project, but I don't understand why some people are SO afraid of the command line, that they need to click a menu, a tab, and then a button... all to avoid five keystrokes. 

+1
But I've already said my bit, and others have added some of the common commands that I know and use, so I'll say no more.

---

### Post by cmcanulty on 2010-08-09
Sounds like a great idea to me for people that are beginners, good luck.

---

### Post by slooksterpsv on 2010-10-07
Hey thanks for all your input, I'm still working on the program, slowly, but surely.

Here's the latest version, it fixes a few bug, as well as I changed from popen4 to subprocess. Also it may take a bit of time to run some of the commands, and it may make the window turn grey. I'm going to work on threading the application to make it run better, but for now here's the latest version. Not sure if gksudo works on KDE or XFCE - if it doesn't let me know and I can have it try to detect what you're running then run it as either ksudo (or whatever KDE uses) and whatever xfce uses.

[ATTACHED]

---

### Post by linux18 on 2010-10-14
this is similar to a shell script I wrote over the weekend, if you need any further inspiration for the project feel free to take any part from my shell script below 
```
 #!/bin/bash
#
#
#       ubuntu emergency script
#
#       Copyright 2010 seth <seth@seth-laptop>
#
#       This program is free software; you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation; either version 2 of the License, or
#       (at your option) any later version.
#
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#
#       You should have received a copy of the GNU General Public License
#       along with this program; if not, write to the Free Software
#       Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
#       MA 02110-1301, USA.



#------INTRO------#
NOW=$(date +"%b-%d-%y")
clear
cd /home/$USER/
echo "_____________Ubuntu Emergency Script________________"
echo
echo "So, you broke Ubuntu? No worries it's just software."
echo
echo "Even if it looks bad now, It can always be fixed!"
echo
echo
echo "Lets get started..."
echo
echo "        1 - Fix synaptic issues"
echo "        2 - Free disk space"
echo "        3 - Purge orphaned libraries"
echo "        4 - Purge unused locales"
echo "        5 - Backup home directory"
echo "        6 - Nuke all config files"
echo "        7 - Restore Desktop"
echo "        8 - Get output for forums"
echo
read -p "Enter a number: " MAIN_CHOICE
#------/INTRO-----#



#------OPTION 1------#
if [ $MAIN_CHOICE = "1" ]
    then
    clear
    echo "Syaptic can be a hassle, but we do need to use it."
    echo "Here are my commands for repairing synaptic:"
    echo
    echo "sudo killall synaptic; sudo killall aptitude; "
    echo "sudo killall software-center; sudo rm /var/lib/dpkg/lock; "
    echo "sudo rm /var/cache/apt/archives/lock; "
    echo "sudo rm /var/lib/apt/lists/partial/*; "
    echo "sudo rm /var/cache/apt/*.bin; sudo chmod 755 /usr/bin/dpkg; "
    echo "sudo dpkg --purge \$(dpkg -l |grep  ^rc |awk '{print $2}' | "
    echo "tr '\012' ' '); sudo aptitude clean; sudo apt-get autoclean; "
    echo "sudo apt-get update; sudo apt-get upgrade dpkg synaptic; "
    echo "sudo apt-get autoremove; sudo apt-get -f install; sudo "
    echo "aptitude -f install; sudo apt-get --fix-broken upgrade"
    echo
    read -p "Accept this solution(y/n)? " Y_N_DIALOGUE_A
    if [ $Y_N_DIALOGUE_A = "y" ]
        then
        sudo killall synaptic; sudo killall aptitude; sudo killall software-center; sudo rm /var/lib/dpkg/lock; \
        sudo rm /var/cache/apt/archives/lock; sudo rm /var/lib/apt/lists/partial/*; sudo rm /var/cache/apt/*.bin; \
        sudo chmod 755 /usr/bin/dpkg; sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' '); \
        sudo aptitude clean; sudo apt-get autoclean; sudo apt-get update; sudo sudo apt-get upgrade dpkg synaptic; \
        sudo apt-get autoremove; sudo apt-get -f install; sudo aptitude -f install; sudo apt-get --fix-broken upgrade
    fi
fi
#-------OPTION 1-----#



#------OPTION 2------#
if [ $MAIN_CHOICE = "2" ]
    then
    clear
    echo "Sometimes the disks get low on space, that's unfortunate."
    echo "Here are my commands for freeing up disk space:"
    echo
    echo "sudo rm -rf /usr/src/*; sudo rm /var/log/*.gz; "
    echo "sudo rm /var/log/*/*.gz; sudo rm \$(sudo du /var/log/* -h | "
    echo "grep "M"); sudo rm \$(sudo du /var/log/* -h | grep "G"); "
    echo "sudo aptitude clean; sudo apt-get autoremove; sudo apt-get "
    echo "autoclean; sudo rm -rf /root/.cache; sudo rm -rf /root\ "
    echo "/.thumbnails; sudo rm -rf /root/.local/share; sudo rm -rf "
    echo ".local/share; sudo rm -f .cache; sudo rm -rf .thumbnails "
    echo
    read -p "Accept this solution(y/n)? " Y_N_DIALOGUE_B
    if [ $Y_N_DIALOGUE_B = "y" ]
        then
        sudo rm -rf /usr/src/*; sudo rm /var/log/*.gz; sudo rm /var/log/*/*.gz; \
        sudo rm $(sudo du /var/log/* -h | grep "M"); sudo rm $(sudo du /var/log/* -h | grep "G"); \
        sudo aptitude clean; sudo apt-get autoremove; sudo apt-get autoclean; sudo rm -rf /root/.cache; \
        sudo rm -rf /root/.thumbnails; sudo rm -rf /root/.local/share; sudo rm -rf .local/share; \
        sudo rm -rf .cache; sudo rm -rf .thumbnails
    fi
fi
#-------OPTION 2-----#



#------OPTION 3------#
if [ $MAIN_CHOICE = "3" ]
    then
    clear
    echo "Orphaned libraries take up space for nothing,"
    echo "and removing them is easy. Here are my commands"
    echo "for dealing with orphaned packages: "
    echo
    echo "sudo apt-get update; sudo apt-get install deborphan && "
    echo "for i in {1..5}; do sudo apt-get purge \$(deborphan); done"
    echo
    read -p "Accept this solution(y/n)? " Y_N_DIALOGUE_C
    if [ $Y_N_DIALOGUE_C = "y" ]
        then
        sudo apt-get update; sudo apt-get install deborphan; for i in {1..5}; do \
        sudo apt-get purge $(deborphan); done
    fi
fi
#-------OPTION 3-----#



#------OPTION 4------#
if [ $MAIN_CHOICE = "4" ]
    then
    clear
    echo "Purging unused locales can save a lot of disk space."
    echo "Here are my commands for purging locales"
    echo
    echo "sudo apt-get update; sudo apt-get install localepurge; "
    echo "sudo localepurge; locale-gen"
    echo
    read -p "Accept this solution(y/n)? " Y_N_DIALOGUE_D
    if [ $Y_N_DIALOGUE_D = "y" ]
        then
        sudo apt-get update; sudo apt-get install localepurge; sudo localepurge; sudo locale-gen
    fi
fi
#-------OPTION 4-----#



#------OPTION 5------#
if [ $MAIN_CHOICE = "5" ]
    then
    clear
    echo "Just can't seem to fix your installation? Oh well,"
    echo "reinstallation is easy enough. Here are your choices"
    echo "for backing up the system:"
    echo
    echo "        1 - Tarball     (.tar.bz2)"
    echo "        2 - lzma        (.tar.lzma)"
    echo "        3 - zip         (.zip)"
    echo "        4 - squashfs    (.squashfs)"
    echo
    read -p "Which method do you prefer: " COMPRESSION_METHOD
    if [ $COMPRESSION_METHOD = "1" ]
        then
        clear
        echo "A tarball is the most common way to store compressed"
        echo "data in *nix operating systems and is always a good"Part 2. Basics
        echo "choice. Almost every distro supports the format"
        echo
        read -p "Tarball your home directory(y/n)? " Y_N_DIALOGUE_E
        if [ $Y_N_DIALOGUE_E = "y" ]
            then
            BACKUP_TITLE_A="BACKUP-$NOW-Tarball"
            mkdir $BACKUP_TITLE_A
            tar --bzip2 -c -p -S -v -f $BACKUP_TITLE_A.tar.bz2 /home/$USER/*
        fi
    fi
    if [ $COMPRESSION_METHOD = "2" ]
        then
        clear
        echo "lzma is for faster computers, it has great compression"
        echo "and great suppport and it's available by default in most"
        echo "distributions."
        echo
        read -p "lzma compress your home directory(y/n)? " Y_N_DIALOGUE_F
        if [ $Y_N_DIALOGUE_F = "y" ]
            then
            BACKUP_TITLE_B="BACKUP-$NOW-lzma"
            tar --lzma -c -p -S -v -f $BACKUP_TITLE_B.tar.lzma /home/$USER/*
        fi
    fi
    if [ $COMPRESSION_METHOD = "3" ]
        then
        clear
        echo "zip is a cross-platform solution for file backup and is"
        echo "supported by most linux distributions, windows and mac by"
        echo "default."
        echo
        read -p "zip your home directory(y/n)? " Y_N_DIALOGUE_G
        if [ $Y_N_DIALOGUE_G = "y" ]
            then
            BACKUP_TITLE_C="BACKUP-$NOW-zip"
            zip -v -X -r -T $BACKUP_TITLE_C /home/$USER/*
        fi
    fi
    if [ $COMPRESSION_METHOD = "4" ]
        then
        clear
        echo "Squashfs is a fast compression method for large directories"
        echo "its not a default utility, but is available in the repositories"
        echo "Squashfs may require an apt-get operation"
        echo
        read -p "squashfs your home directory(y/n)? " Y_N_DIALOGUE_H
        if [ $Y_N_DIALOGUE_H = "y" ]
            then
            sudo aptitude install squashfs-tools
            BACKUP_TITLE_D="BACKUP-$NOW-zip"
            mksquashfs /home/$USER/* $BACKUP_TITLE_D.squashfs -info
        fi
    fi
fi
#------OPTION 5------#



#------OPTION 6------#
if [ $MAIN_CHOICE = "6" ]
    then
    clear
    echo "When something is wrong with a file or program deleting the"
    echo "configuration file is a good idea. When many things fail at"
    echo "the same time, purging the current configuration may be a"
    echo "good idea, but it's more like using a nuke on one person."
    echo "this will delete your browser bookmarks, theme, locale"
    echo "settings, hidden files and more!"
    echo
    read -p "Purge all configuration files(y/n)? " Y_N_DIALOGUE_I
    if [ $Y_N_DIALOGUE_I = "y" ]
        then
        cd /home/$USER/
        sudo rm -vrf .*
    fi
fi
#------OPTION 6------#



#------OPTION 7------#
if [ $MAIN_CHOICE = "7" ]
    then
    clear
    echo "Maybe purging configuration files isn't enough to fix the"
    echo "problem and your stuck without a GUI. If you tried purging the"
    echo "config files and fixing broken dependancies, this is one last"
    echo "thing that you can do before backing up and reinstalling."
    echo "Restoring the desktop takes time, and may require several"
    echo "hundred megabytes of packages to be downloaded. This will also"
    echo "delete your theme, hidden files, most settings, bookmarks and"
    echo "more! If you still want to, here are your desktop choices:"
    echo
    echo "            1 - Lubuntu"
    echo "            2 - Xubuntu"
    echo "            3 - Ubuntu"
    echo "            4 - Kubuntu"
    echo
    read -p "Which Desktop Environment do you have: " DESKTOP_ENVIRONMENT
    if [ $DESKTOP_ENVIRONMENT = "1" ]
        then
        cd /home/$USER/
        sudo apt-get purge openbox pcmanfm lxpanel leafpad lxappearance lxinput lxsession-edit lxshortcut gpicview \
                           lxterminal lxmusic lxsession xscreensaver xfce4-taskmanager lxdm lxde*
        sudo dpkg-reconfigure -a
        sudo rm -vrf .config
        sudo rm -vrf /root/*
        sudo apt-get install lubuntu-desktop
        sudo aptitude -f install
        sudo reboot
    fi
    if [ $DESKTOP_ENVIRONMENT = "2" ]
        then
        cd /home/$USER/
        sudo apt-get purge xfrun4 xfterm4 xflock4 xfmountdev4 xfbrowser4 startxfce4 xfhelp4 xfdesktop thunar mousepad \
                           xfwm4 xfce* xubuntu*
        sudo dpkg-reconfigure -a
        sudo rm -vrf .config
        sudo rm -vrf /root/*
        sudo apt-get install xubuntu-desktop
        sudo aptitude -f install
        sudo reboot
    fi
    if [ $DESKTOP_ENVIRONMENT = "3" ]
        then
        cd /
        sudo apt-get purge ubuntu*
        cd /home/$USER/
        sudo dpkg-reconfigure -a
        sudo rm -vrf .config
        sudo rm -vrf /root/*
        sudo apt-get install ubuntu-desktop
        sudo aptitude -f install
        sudo reboot
    fi
    if    [ $DESKTOP_ENVIRONMENT = "4" ]
        then
        cd /home/$USER/
        sudo apt-get purge kwin kicker kscreensaver kubuntu*
        sudo dpkg-reconfigure -a
        sudo rm -vrf .config
        sudo rm -vrf /root/*
        sudo apt-get install kbuntu-desktop
        sudo aptitude -f install
        sudo reboot
    fi
fi
#------OPTION 7------#



#------OPTION 8------#
if [ $MAIN_CHOICE = "8" ]
    then
    clear
    echo "Need to post your problem in the Ubuntu Forums? You should be"
    echo "prepared! Posting relevent information will solve your problem"
    echo "faster and this script has a few options:"
    echo
    echo "            1 - video problem"
    echo "            2 - partition problem"
    echo "            3 - boot problem"
    echo
    read -p "What's your problem? " YOUR_PROBLEM
    if [ $YOUR_PROBLEM = "1" ]
        then
        OUTPUT_A="VIDEO-$NOW-Problem"
        touch $OUTPUT_A
        echo "Linux18's GPL'd UbuntuEmergencyScript video problem debugger Version 1" | tee $OUTPUT_A
        echo >> $OUTPUT_A
        echo "Gathering Data..."
        echo "uname -a:" >> $OUTPUT_A
        uname -a >> $OUTPUT_A
        echo >> $OUTPUT_A
        echo "lspci | grep 'VGA':" >> $OUTPUT_A
        lspci | grep "VGA" >> $OUTPUT_A
        echo >> $OUTPUT_A
        echo "cat xorg.conf:" >> $OUTPUT_A
        cat /etc/X11/xorg.conf >> $OUTPUT_A
        echo >> $OUTPUT_A
        echo "the rest of lspci:" >> $OUTPUT_A
        lspci >> $OUTPUT_A
        echo "DONE! your diagnostic information is in the file " $OUTPUT_A
        read -p "Press any key to continue..." DUMMY_VALUE
    fi
    if [ $YOUR_PROBLEM = "2" ]
        then
        OUTPUT_B="PARTITION-$NOW-Problem"
        echo "Linux18's GPL'd UbuntuEmergencyScript partition problem debugger Version 1" | tee $OUTPUT_B
        echo >> $OUTPUT_B
        echo "Gathering Data..."
        echo "uname -a:" >> $OUTPUT_B
        uname -a >> $OUTPUT_B
        echo >> $OUTPUT_B
        echo "sudo parted -l:" >> $OUTPUT_B
        sudo parted -l | tee -a $OUTPUT_B
        echo >> $OUTPUT_B
        echo "df: " >> $OUTPUT_B
        df >> $OUTPUT_B
        echo "DONE! your diagnostic information is in the file " $OUTPUT_B
        read -p "Press any key to continue..." DUMMY_VALUE
    fi
    if [ $YOUR_PROBLEM = "3" ]
        then
        OUTPUT_C="BOOT-$NOW-Problem"
        echo "Linux18's GPL'd UbuntuEmergencyScript boot problem debugger Version 1" | tee $OUTPUT_C
        echo >> $OUTPUT_C
        echo "Gathering Data..."
        echo "uname -a:" >> $OUTPUT_C
        uname -a >> $OUTPUT_C
        echo >> $OUTPUT_C
        echo "sudo parted -l:" >> $OUTPUT_C
        sudo parted -l | tee -a $OUTPUT_C
        echo >> $OUTPUT_C
        echo "cat /boot/grub/grub.cfg:" >> $OUTPUT_C
        cat /boot/grub/grub.cfg >> $OUTPUT_C
        echo "DONE! your diagnostic information is in the file " $OUTPUT_C
        read -p "Press any key to continue..." DUMMY_VALUE
    fi
fi
#------OPTION 8------#



#------THE END------#
clear
echo "I hope you enjoyed the script!"
echo
read -p "Press any key to close this terminal" DUMMY_VALUE
exit
#------THE END------#

 
```

---


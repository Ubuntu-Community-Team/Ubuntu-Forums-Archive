---
title: "slimming libraries"
date: 2010-08-03
forum: General Help
---

### Post by JohnnyC35 on 2010-08-03
I am trying to remove programs, config files, libraries, etc and I think I have gone thru all of it except the libraries. I have apt-get clean, autoclean, autoremove, purge $(deborphan), found a command on the[ Mint forums ]("http://forums.linuxmint.com/viewtopic.php?f=90&t=52687")that helped me find over 400mb of old config folders. The only thing I think I have left is to go thru the libraries. I have looked thru it in Synaptic and I am a little hesitant o just start removing libraries heh. Does anyone know of a program that could find out of libraries are in use, or are needed for what I have installed right now. I suppose the other way could be to purge all program files, deborphan, and then reinstal with --no-install-recommends but that sounds like a horrible idea. anyways, I'll stop rambling and if anyone has suggestions that would be great :)

---

### Post by philinux on 2010-08-03
Remove any old kernels.
```

Don't follow this process unless you're sure you don't need to boot into the older kernels. If you're not sure, just leave things alone. Also, it is possible to remove all of the kernels from your system and make it unbootable. I suggest leaving the latest kernel and one version previous to that. You can find out the kernel version that you're currently running with
uname -r
Find and remove old kernels

The first step is to figure out what kernels are installed. The following command will do the job.
ls /boot | grep vmlinuz | cut -d'-' -f2,3

Your result should look something like this.
2.6.28-15
2.6.28-16
2.6.28-17

This is the list of kernels installed on your system. Now you want to find out which packages are installed relative to the kernel you want to remove. For my example I'm going to remove the oldest one, 2.6.28-15.
dpkg -l | grep ^ii | grep 2.6.28-15 | awk -F' ' '{ print $2 }'

On my system, (Jaunty) the resulting list is:
linux-headers-2.6.28-15
linux-headers-2.6.28-15-generic
linux-image-2.6.28-15-generic
linux-restricted-modules-2.6.28-15-generic

Now that we know what packages to remove we can remove them with dpkg, apt-get or aptitude.
sudo aptitude remove linux-headers-2.6.28-15 linux-headers-2.6.28-15-generic linux-image-2.6.28-15-generic linux-restricted-modules-2.6.28-15-generic

That's it. You've removed an old kernel and related packages. Now you can keep your system as clean as it is right after you install Ubuntu. The commands are a bit complex, so maybe I'll write up a bash script when I have some time. Proceed with caution!


```

---

### Post by JohnnyC35 on 2010-08-03
thanks for that bit of info phil. I only had 2 kernels but 2.6.32-24 is what I was using so I removed the other, and then ran sudo update-grub after as it said that there were some errrors, or something was broken in grub, it's fixed now tho.
I went thru and removed a few libraries and such, accidently removed gnome-network, and then reinstalled it after. Guess I need to reboot for the notification area to stop complaining. It still says networking is disabled (but I'm on the internet :P )
So far brought down my / 's used about to 2.1 down from 2.3Gb, got var and home on my 1.5 drive.

---

### Post by linux18 on 2010-08-03
my semi-experimental shell script for cleaning drives:
```
  #!/bin/sh




# start -------------------------------------------------------------------------------------------
echo
echo "welcome to the ultimate ubuntu disk cleaning tool"
echo 
sleep .5
echo "this program is designed specifically to free up disk space in ubuntu"
echo 
sleep .5
echo "version 0.01.1    revision 2"
echo 
sleep .5
echo "time to start cleaning disk space"
echo
echo
echo
 



# package removal part 1 --------------------------------------------------------------------------
echo "remove rarely used packages (dont worry I'll list the packages + descriptions) (y/n)"
read a   
if [ $a = "y" ] ; then
  echo
  echo
  echo
  echo "Package: mono-common"
  echo
  echo "description/programs:  F-spot, tomboy, banshee "
  echo
  echo "remove mono-common (y/n)?"
  read b
  if [ $b = "y" ] ; then 
    sudo apt-get remove mono-common
  fi
  echo
  echo
  echo
  echo "package: ttf-arabeyes ttf-arphic-uming ttf-indic-fonts-core"
  echo "ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts"
  echo "ttf-thai-tlwg ttf-unfonts-core"
  echo
  echo "description: various Asian/Arabic fonts"              
  echo
  echo "remove selected fonts (y/n)?"
  read b
  if [ $b = "y" ] ; then
    sudo apt-get remove ttf-arabeyes ttf-arphic-uming ttf-indic-fonts-core ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-thai-tlwg ttf-unfonts-core
  fi
  echo
  echo
  echo
  echo "package: bluez-audio bluez-cups bluez-gnome bluez-utils"
  echo 
  echo "description: Bluetooth support"
  echo
  echo "remove Bluetooth support (y/n)?"
  read b
  if [ $b = "y" ] ; then
    sudo apt-get remove bluez-audio bluez-cups bluez-gnome bluez-utils
  fi
  echo
  echo
  echo
  echo "package: gnome-orca brltty brltty-x11 gnome-accessibility-themes"
  echo "gnome-mag libgnome-mag2"
  echo 
  echo "description: braile display and magnified screen"
  echo 
  echo "remove braile display and screen magnifier (y/n)?" 
  read b
  if [ $b = "y" ] ; then
    sudo apt-get remove gnome-orca brltty brltty-x11 gnome-accessibility-themes gnome-mag libgnome-mag2
  fi
  echo
  echo
  echo
  echo "package: espeak espeak-data libespeak1 libgnome-speech7"
  echo 
  echo "description: text to speech synthesizer"
  echo 
  echo "remove speech synthesizer (y/n)?" 
  read b
  if [ $b = "y" ] ; then
    sudo apt-get remove espeak espeak-data libespeak1 libgnome-speech7
  fi
  echo
  echo
  echo
  echo "package: evolution-common evolution-data-server evolution-exchange"
  echo "evolution-plugins evolution-webcal"
  echo 
  echo "description: evolution mail and Ekiga voip"
  echo 
  echo "remove evolution mail and Ekiga voip (y/n)?" 
  read b
  if [ $b = "y" ] ; then
    sudo apt-get remove evolution-common evolution-data-server evolution-exchange evolution-plugins evolution-webcal
  fi
fi




# package removal part two ------------------------------------------------------------------------
echo
echo
echo
echo "okay were halfway finished with package removal and the next 400 mb"
echo "will be in three questions"
echo
echo "question 1: will you need to use a printer (y/n)?"
read c 
if [ $c = "n" ] ; then 
  sudo apt-get remove cups python-cupshelpers python-cups hplip foomatic-filters hpijs system-config-printer-common
fi
echo
echo
echo
echo "question 2: will you need to use openoffice (y/n)?"
read c 
if [ $c = "n" ] ; then
  sudo apt-get remove uno-libs3 openoffice-* openoffice.org
fi
echo
echo
echo
echo "question 3: will you need to use any help files excluding man pages(y/n)?"
read c
if [ $c = "n" ] ; then
  sudo apt-get remove *buntu-docs
fi
   



# remove all .deb and dependancy caches -----------------------------------------------------------
echo "clean .deb caches (y/n) ?"
read a
if [ $a = "y" ] ; then
  echo "cleaning caches"
  mkdir ~/Documents/Cleaner
  sudo apt-get clean 
  sudo apt-get autoclean 
  sudo apt-get autoremove 
  sudo rm /var/cache/apt/*.bin 
  echo
  echo
  echo
fi




# remove all of the logs --------------------------------------------------------------------------
echo "clean all '/var/log/' log files (y/n) ?"
read a
if [ $a = "y" ] ; then
  echo "cleaning logs, directory errors are normal"
  echo "error ''something' is a directory' is normal ouput..." 
  sudo rm /var/log/* 
  sudo rm /var/log/*/* 
  echo
  echo
  echo
fi




# remove lost+found files -------------------------------------------------------------------------
echo "list corrupted files (y/n) ?"
read a
if [ $a = "y" ] ; then 
  echo "finding lost+found files you should delete, output is in the log file" 
  sudo find / -name "lost+found" 
  echo
  echo
  echo
fi




# install orphaned package remover-----------------------------------------------------------------
echo "install and run deborphan, an orphaned package remover (y/n) ?"
read a
if [ $a = "y" ] ; then 
  echo "installing/running orphaned package remover"
    sudo apt-get install deborphan 
  sudo deborphan | xargs sudo apt-get -y remove --purge 
  echo
  echo
  echo
fi




# install localpurge ------------------------------------------------------------------------------
echo "install and run localpurge, a package to remove files "
echo "not in your language (y/n) ?"
read a
if [ $a = "y" ] ; then 
  echo "installing/running localpurge, answer 'your language' on first run" 
  sudo apt-get install localepurge 
  localepurge 
  echo
  echo
  echo
fi




# remove document/man files -----------------------------------------------------------------------
echo "remove help and man files  (y/n) ?"
read a
if [ $a = "y" ] ; then
  echo "removing help and man files from /usr/share/doc/"
  echo "error ''something' is a directory' is normal ouput..." 
  sleep 3 
  sudo rm /usr/share/doc/a*/*
  sudo rm /usr/share/doc/b*/*
  sudo rm /usr/share/doc/c*/*
  sudo rm /usr/share/doc/d*/*
  sudo rm /usr/share/doc/e*/*
  sudo rm /usr/share/doc/f*/*
  sudo rm /usr/share/doc/g*/*
  sudo rm /usr/share/doc/h*/*
  sudo rm /usr/share/doc/i*/*
  sudo rm /usr/share/doc/j*/*
  sudo rm /usr/share/doc/k*/*
  sudo rm /usr/share/doc/l*/*
  sudo rm /usr/share/doc/m*/*
  sudo rm /usr/share/doc/n*/*
  sudo rm /usr/share/doc/o*/*
  sudo rm /usr/share/doc/p*/*
  sudo rm /usr/share/doc/p*/*
  sudo rm /usr/share/doc/q*/*
  sudo rm /usr/share/doc/r*/*
  sudo rm /usr/share/doc/s*/*
  sudo rm /usr/share/doc/t*/*
  sudo rm /usr/share/doc/u*/*
  sudo rm /usr/share/doc/v*/*
  sudo rm /usr/share/doc/w*/*
  sudo rm /usr/share/doc/x*/*
  sudo rm /usr/share/doc/y*/*
  sudo rm /usr/share/doc/z*/*
  echo
  echo
  echo "directory errors are normal"
  echo
  echo
  echo
fi



 
# status update -----------------------------------------------------------------------------------
echo "run a disk usage diagnostic? " 
read a
if [ $a = "y" ] ; then 
  sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort 
  echo
  echo
  echo
  sudo du -h /var/cache/apt/ 
  echo
  echo
  echo
  sudo du -h /var/log 
  echo
  echo
  echo
  echo "usage of all filesystems"
  sudo df -Th | grep -v "fs" | sort 
  echo
  echo
  echo
  echo "total filesystem disk usage"
  sudo du -hs / | grep -v "read" | grep -v "cannot" 
  echo  
  echo
  echo
  echo
fi





# done --------------------------------------------------------------------------------------------
echo "DONE"





# recommendations ---------------------------------------------------------------------------------
echo
echo
echo "        ==============RECOMMENDATIONS:================="
echo
echo "start synaptic package manager, goto status, click (residual config), delete all of those"
echo
echo "clear all browser history/cache/cookies/etc."
echo 
echo "unmout devices 'sudo umount -a'"
echo
```

---

### Post by JohnnyC35 on 2010-08-03
> **linux18 said:**
> my semi-experimental shell script for cleaning drives:


I ran thru the commands that I needed bit by bit and it looks like most had been removed previous, but still a good script to have, especially the trash, log, man files, etc :)

I got an error with *buntu-docs tho:

```

john@mediabuntu ~ $ sudo apt-get remove *buntu-docs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Regex compilation error - Invalid preceding regular expression

```

---

### Post by linux18 on 2010-08-03
> **JohnnyC35 said:**
> I ran thru the commands that I needed bit by bit and it looks like most had been removed previous, but still a good script to have, especially the trash, log, man files, etc :)

I got an error with *buntu-docs tho:

```

john@mediabuntu ~ $ sudo apt-get remove *buntu-docs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Regex compilation error - Invalid preceding regular expression

```
I was running lubuntu when I wrote that part of the script so I couldn't confirm if that part was going to work, I'll make the necessary tweaks later. I'm always happy to improve the script, I just don't have as much time anymore ( the script uses "echo" instead of "read -p" because those parts were made before I knew about read -p, but I haven't had the time to fix it.)

---


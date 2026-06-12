---
title: "Some simple cleanup utilities?"
date: 2010-08-04
forum: General Help
---

### Post by Replicon on 2010-08-04
Hello,

I'm finding that my main installation directory, which is about 7GB, is starting to bump up against the full mark. I figure this must be due to accumulation of random installed stuff that I don't even use nowadays.

I'm wondering whether there is a tool that would easily show me some low-hanging fruits... i.e. some leaf-level packages that, if I remove them, will also remove large amounts of dependent libraries that are otherwise unused.

I hope this makes sense. :)

Thanks!

---

### Post by Replicon on 2010-08-04
Hmmm, I'm finding there are lots of artifacts from old kernels:

```

:/lib/modules$ du -h --max-depth=1  
131M	./2.6.22-14-generic
89M	./2.6.24-16-generic
89M	./2.6.24-17-generic
91M	./2.6.24-18-generic
89M	./2.6.24-19-generic
94M	./2.6.24-21-generic
92M	./2.6.24-22-generic
95M	./2.6.24-23-generic
96M	./2.6.24-24-generic
96M	./2.6.24-25-generic
96M	./2.6.24-26-generic
96M	./2.6.24-27-generic
137M	./2.6.24-28-generic
1.3G	.

```

This would be a good start to clean up... is it safe to just sudo rm -rf anything that isn't the current kernel (maybe minus 1 or 2 revisions for safety)?

---

### Post by linux18 on 2010-08-04
> **Replicon said:**
> Hmmm, I'm finding there are lots of artifacts from old kernels:

```

:/lib/modules$ du -h --max-depth=1  
131M    ./2.6.22-14-generic
89M    ./2.6.24-16-generic
89M    ./2.6.24-17-generic
91M    ./2.6.24-18-generic
89M    ./2.6.24-19-generic
94M    ./2.6.24-21-generic
92M    ./2.6.24-22-generic
95M    ./2.6.24-23-generic
96M    ./2.6.24-24-generic
96M    ./2.6.24-25-generic
96M    ./2.6.24-26-generic
96M    ./2.6.24-27-generic
137M    ./2.6.24-28-generic
1.3G    .

```This would be a good start to clean up... is it safe to just sudo rm -rf anything that isn't the current kernel (maybe minus 1 or 2 revisions for safety)?
you should remove the kernels through synaptic so that grub is updated as well and remember to keep the newest 2 kernels. I'll post back later with my ultimate cleanup script.

EDIT: and here is the script:

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

### Post by Replicon on 2010-08-04
Very nice script, thanks!

---

### Post by linux18 on 2010-08-05
> **Replicon said:**
> Very nice script, thanks!
your welcome, it's an old script but it still does the job. I just wish I had the time to improve it.

---

### Post by jimmers on 2010-08-05
You could always try this tutorial by some-one who's name I forget :-

                                        HOWTO: Cleaning up all those unnecessary junk files... 
    
   
       []("http://ubuntuforums.org/#annotation-0")[]("http://ubuntuforums.org/#annotation-1")**Hello everyone! So, do you ever get the feeling that your system is being flooded with a bunch of junk files that you can't get rid of? I know I do. Well, I'm going to show you a few ways to get rid of most, if not all, of those annoying junk files.**  

[COLOR=#FF0000]**Please note**[/COLOR] : If doing any of this messes up your system, don't blame me. Everything worked flawlessly on my machine. Everthing should be beer 'n skittles for you if you follow this HOWTO step-by-step. Good luck! 

================================================== ================================================== ====================

**_Tip #1 - Getting rid of Residual Config packages_** - In Synaptic Package Manger, there is a built-in feature that gets rid of old Residual Config packages. Residual Config packages are usually dependency packages that are left behind after you uninstall a package from your machine. To use this feature, go to **System > Administration > Synaptic Package Manager**. On the bottom left hand corner of the window, click the **Status** button. In the list above the **Sections**, **Status**, **Search**, and **Custom **buttons, you should see the following text:
    Quote:
                                              Installed
Installed (local or obsolete)
Not installed
Residual config 
                          Click on the "Residual config" text. (If the "Residual config dialogue does not appear, that means you do not have any Residual Config packages on your machine and you can skip down to Tip #2.) Do you see the packages that popped up in the window on the right? Those are the Residual Config packages. To get rid of these pests, click on the box to the left of the package name and select "Mark for Complete Removal". After you have done that for all of the Residual Config packages, look at the top of the Synaptic Package Manger window. Do you see the green check mark with the text "Apply" right under it? Click that button, and you'll flush all those Residual Config packages down the toilet! 

================================================== ================================================== ====================

**_Tip #2 - Getting rid of partial packages_** - This is yet another built-in feature, but this time it is not used in Synaptic Package Manager. It is used in the Terminal. To access the Terminal, go to **Applications > Accessories > Terminal**. Now, in the Terminal, key in the following command (or you can just copy and paste from here):
    Code:
    [LEFT]sudo apt-get autoclean[/LEFT]
    Enter your password when prompted and press **Enter**. See the package names that appeared in the Terminal? Those were partial packages that have just been deleted. Say goodbye! That's it! This command deletes the not-so-fully-downloaded packages that you acquire when a package that is being downloaded is suddenly cancelled. This is my favorite little trick when it comes to getting rid of junk files.  

================================================== ================================================== ====================

**_Tip #3 - Getting rid of unnecessary locale data_** - For this tip, you need to download the "localepurge" package found in Synaptic Package Manager. "localepurge" is just a simple script to recover diskspace wasted for unneeded locale files and localized man pages. It will automagically be invoked upon completion of any apt installation run.

To open Synaptic Package Manager, follow the instructions in Tip #1. After opening up Synaptic Package Manager, click the **Sections** button on the bottom left hand corner of the window, if it is not already clicked. Next, at the top of the Synaptic Package Manager window, click the **Search** button. In the search window, key in the following text :
    Quote:
                                              localepurge 
                          Did the "localepurge" package popup in the package window? It probably did, unless you do not have the correct Repositories. Now, click on the box next to the "localepurge" package name. Click on **Mark for Installation**. Now click the **Apply** button at the top of the window and wait for the downloading and installing of the "localepurge" package to finish. Once it is done, a new window should popup that has a bunch of abbreviations on it. for example: 
    Quote:
                                              en
fr
po
sp
ka
etc... 
                          You want to select the abbreviation of the language that you speak, or use with Ubuntu, ignoring the capitalized ones. For example, I speak english, so I would select the "en" abbreviation. A french speaker would select the "fr" abbreviation. So on and so forth... Then click next. All done! 

================================================== ================================================== ====================

**_Tip #4 - Getting rid of "orphaned" packages_** - For this tip, you need to download the "deborphan" package found in Synaptic Package Manager. "deborphan" finds "orphaned" packages on your system. It determines which packages have no other packages depending on their installation, and shows you a list of these packages. It is most useful when finding libraries, but it can be used on packages in all sections...

To open Synaptic Package Manager, follow the instructions in Tip #1. After opening up Synaptic Package Manager, click the **Sections** button on the bottom left hand corner of the window, if it is not already clicked. Next, at the top of the Synaptic Package Manager window, click the **Search** button. In the search window, key in the following text :
    Quote:
                                              deborphan 
                          Did the "deborphan" package popup in the package window? It probably did, unless you do not have the correct Repositories. Now, click on the box next to the "deborphan" package name. Click on **Mark for Installation**. Now click the **Apply** button at the top of the window and wait for the downloading and installing of the "deborphan" package to finish. Once that is done, open up the Terminal. Instructions for doing that are located in Tip #2. After you have gotten the Terminal open, key in the following command (or copy and paste from here):
    Code:
    [LEFT]sudo deborphan | xargs sudo apt-get -y remove --purge[/LEFT]
    Enter your password when prompted and press **Enter**. See the package names that appeared in the Terminal? Those were orphaned packages that have just been deleted. Say goodbye! This is my second favorite way of dealing with junk files. 

================================================== ================================================== ====================

**_Tip #5 - Adding a "Find orphaned packages" to Synaptic Package Manager_** - This is not really much of a tip on how to get rid of junk files. It's more like adding a "deborphan" shortcut to Synaptic Package Manager so that you don't have to use the Terminal to find "orphaned" packages.

[COLOR=#FF0000]**Please note:**[/COLOR] You must have the "deborphan" package installed or else this will not work.

To start this out, open up Synaptic Package Manager with the instructions from Tip #1. Now, at the top of the Synaptic Package Manager window, click the **Settings** button, followed by the **Filters** button. In the Filters window, on the bottom left hand corner, push the **New** button. You can name the new Filter if you like, but it is not necessary. I named mine "Orphaned". With your new Filter selected, in the "Status" tab on the right, click the **Deselect All** button. Next, check the "Orphaned" option under the "Other" category. Then click the **OK** button.

To use this new filter, click the **Custom** button on the bottom left hand corner of the Synaptic Package Manager window. You should see the following text, or something similiar :
    Quote:
                                              Broken
Marked Changes
(Whatever you named your "deborphan" Filter)
Package with Debconf
Search Filter 
                          Click on the "(Whatever you named your "deborphan Filter)" text. Do you see the packages that popped up in the window on the right? Those are the "orphaned" packages. To get rid of these buggers, click on the box to the left of the package name and select "Mark for Complete Removal". After you have done that for all of the "orphaned" packages, look at the top of the Synaptic Package Manger window. Do you see the green check mark with the text "Apply" right under it? Click that button, and you'll get rid of all the "orphaned" packages forever (Probably)!

---

### Post by owiknowi on 2010-12-04
BleachBit (install through synaptic or ubuntu software center) does a lot of good work.

---


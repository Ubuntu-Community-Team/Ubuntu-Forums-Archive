---
title: "liveCD mod script"
date: 2011-08-05
forum: General Help
---

### Post by OldManRiver on 2011-08-05
All,

I have litterally had to logon via, or for other reasons, run the liveCD about 50 times this month.

The live CD is so different from what my default desktop is that I decided to write a quick script to customize the environment after booting up.

I don't have all the parts done, Don't know how to do it all from cmdline or script, but here is what I have

```
#! /bin/bash

# Define the default needed apps
apt-get purge empathy
apt-get purge evolution
apt-get install thunderbird
apt-get install pidgin
apt-get install dpkg
apt-get install dselect

# Set the desktop to Clearlooks theme
gconftool-2 --type=string -s /desktop/gnome/interface/gtk_theme Clearlooks
gconftool-2 --type=string -s /apps/metacity/general/theme Clearlooks
gconftool-2 --type=string -s /desktop/gnome/interface/icon_theme gnome
#gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/usr/share/backgrounds/gnome.png"

# Set apps panel to the bottom
# ?

# Set file browser (Places) to 1. List View, 2. Show hidden files, 3. Icons 50%, 4. Compact 50%, 5. List 33%
# ?

# Add launchers to panel for 1. Gedit, 2. Terminal, 3. Pidgin, 4. Calculator
# ?

# Set the desktop icons to 33% and arrange my name
# ?

# Copy the pidgin .xml config files to current config location.
mkdir /media/pconf
mount /dev/sdg1 /media/pconf
mkdir "/home/ubuntu/.purple"
cp /media/pconf/Pidgin-Config/*.xml "/home/ubuntu/.purple/"

```

As you can see I need some help on this, so please share any commands you know that will fill in what is needed.

Thanks!

OMR

---

### Post by OldManRiver on 2011-08-05
All,

Oh hey just had to add the "mkdir" line.

---

### Post by Matt__ on 2011-08-05
or you could use [remastersys](http://www.geekconnection.org/remastersys/repository/) and create a modified live disc

---

### Post by OldManRiver on 2011-08-09
All,

My script currently reads:```
#! /bin/bash
# Bash Script set-liveCD.sh to set liveCD session to default settings and views

# Get flash drive designator and mount the drive
mntp=$1;
  if [ $mntp=="" ] ; then
     mntp="sdf1"
  fi
mount "/dev/$mntp" /mnt;

# Select Install of Thunderbird
echo "DO YOU WANT TO INSTALL THUNDERBIRD"
echo "SCRIPT BY NYLE DAVIS"
echo "1. Yes"
echo "2. No"
echo -n "Choose! [1 or 2]"

while [ $PICK -eq 3 ]; do
read PICK
  if [ $PICK -eq 1 ] ; then
     echo "Installing Thunderbird!"
     apt-get install thunderbird;
  fi
done

# Clear unwanted/uneeded apps
apt-get purge empathy;
apt-get purge evolution;

# Define the default needed apps
apt-get install dpkg;
apt-get install dselect;
apt-get install grub;
apt-get install pidgin;

# Copy the pidgin .xml config files to current config location.
mkdir /home/ubuntu/.purple;
cp /mnt/Pidgin-Config/*.xml "/home/ubuntu/.purple/"

# Set the desktop to Clearlooks theme
gconftool-2 --type=string -s /desktop/gnome/interface/gtk_theme Clearlooks;
gconftool-2 --type=string -s /apps/metacity/general/theme Clearlooks;
gconftool-2 --type=string -s /desktop/gnome/interface/icon_theme gnome;
#gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/usr/share/backgrounds/gnome.png";

# Set apps panel to the bottom
# ?

# Set file browser (Places) to 1. List View, 2. Show hidden files, 3. Icons 50%, 4. Compact 50%, 5. List 33%
# ?

# Add launchers to panel for 1. Gedit, 2. Terminal, 3. Pidgin, 4. Calculator
# ?

# Set the desktop icons to 33% and arrange my name
# ?

```
I'm not very good at scripting yet so the loop that is supposed to stop and get screen input is not working right and blows right through.  Yeah been on U-Boxes for 11 years, but most of the time banging out PHP, so don't fight with admin issues as much as some, but now running a lot of boxes and supporting even more, so gotta get smarter at this.

Also my flash drive is always seen in /dev/disk/by-uuid as "E44-2317" so want to create a function to check for this uuid as sometimes it shows in fdisk -l as sdf1 and other times as sdg1, so do not want to have to run fdisk -l to find the mount point.

I also noticed that the "gconftool-2" commands do not always work, even if they do not send errors, so trying to debug these to make sure there is a "force" method to always make them execute.

I'm still looking up the other stuff, but thought this script might be something the community at large could use and appreciate, so I would be appreciative of all inputs to finish this out right.

I did get some kudos on other scripts I built and put out there, so hoping we get the same reaction here.  I love the interaction I get here on the forums with others. Make it fun when you can learn from each other.

Thanks!

OMR

---

### Post by OldManRiver on 2011-09-15
All,

Lastest code now is:
```
#! /bin/bash

# Mount the External Drives
hvar="$(awk '/4d96b783-cce4-46fd-9a7a-ae71cfc54ad7/{print $1; exit}' /etc/mtab)"
if [[ "$hvar" ]]; then
    mkdir /homhd;
    mount "$hvar" /homhd;
fi
fvar="$(awk '/E441-2317/{print $1; exit}' /etc/mtab)"
if [[ "$fvar" ]]; then
    mkdir /flash;
    mount "$fvar" /flash;
fi

# Clear unwanted/uneeded apps
echo "Purging unwanted Apps!";
apt-get purge empathy;
apt-get purge evolution;

# Define the default needed apps
echo "Installing needed Apps!";
apt-get install dpkg;
apt-get install dselect;
apt-get install grub;
apt-get install pidgin;
apt-get install thunderbird;

# Copy the pidgin .xml config files to current config location.
mkdir /home/ubuntu/.purple;
chown ubuntu:users /home -R;
chmod 775 /home -R;
cp /flash/Pidgin-Config/*.xml "/home/ubuntu/.purple/"

# Struggling with this part
# Select Install of Thunderbird
echo "DO YOU WANT TO INSTALL THUNDERBIRD";
echo "SCRIPT BY NYLE DAVIS";
echo "1. Yes";
echo "2. No";
echo -n "Choose! [1 or 2]";

#while [ $PICK -eq 3 ]; do
#read PICK
#  if [ $PICK -eq 1 ] ; then
#     echo "Installing Thunderbird!";
#     apt-get install thunderbird;
#  fi
#done

# Can not get this part to work consistantly
# Set the desktop to Clearlooks theme
gconftool-2 --type=string -s /desktop/gnome/interface/gtk_theme Clearlooks;
gconftool-2 --type=string -s /apps/metacity/general/theme Clearlooks;
gconftool-2 --type=string -s /desktop/gnome/interface/icon_theme gnome;
#gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/usr/share/backgrounds/gnome.png";

# Set apps panel to the bottom
# ?

# Set file browser (Places) to 1. List View, 2. Show hidden files, 3. Icons 50%, 4. Compact 50%, 5. List 33%
# ?

# Add launchers to panel for 1. Gedit, 2. Terminal, 3. Pidgin, 4. Calculator
# ?

# Set the desktop icons to 33% and arrange my name
# ?


```

---

### Post by OldManRiver on 2011-09-28
All,

The "gconftool-2" commands do not seem to run, at least not right, so do I also need an "apt-get install" on this to?

Not seeing any errors, but code also not working.

Any suggestions?

OMR

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #21 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---


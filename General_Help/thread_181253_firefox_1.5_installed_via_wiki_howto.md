---
title: "firefox 1.5 installed via wiki howto"
date: 2006-05-23
forum: General Help
---

### Post by dmizer on 2006-05-23
i have installed firefox 1.5 via the directions given in the wiki, and it's basically been a nightmare to manage that way with plugins/extensions.  when i update to dapper, i am not going to want to do that again.

but that's another matter.  when i update to dapper ... what will become of my custom firefox (and less so, my thunderbird 1.5) installation?

obviously i will make a backup of my profile folders before i do my update, but will i completely loose this, or will it still be there and usable?

---

### Post by aysiu on 2006-05-23
If you followed the Wiki instructions, there are now two Firefoxes on your computer--the Ubuntu one and the Mozilla one.

If you choose to use the Ubuntu one after you upgrade to Dapper, just follow the instructions on the bottom of the Wiki page for removing the Mozilla one.

Otherwise, the Ubuntu-updated one won't disturb your Mozilla Firefox.

The profile in /home/dmizer/.mozilla is used by both Ubuntu Firefox and Mozilla Firefox (whichever one you have open--though, you can't use both at once).

For the future, you might want to know that I've created a script that automates the Wiki instructions:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by adamkane on 2006-05-23
!

---

### Post by dmizer on 2006-05-23
[QUOTE=aysiu]For the future, you might want to know that I've created a script that automates the Wiki instructions:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)[/QUOTE]
actually, i installed 1.5 before you created that script.  otherwise i would have used it, it's pretty sweet.

i don't need an upgrade ... i just want to make sure that upon moving to dapper:
1) i don't have two firefoxes on my system anymore.
2) that i am able to retain my settings.  some of the plugins that i've installed in firefox really didn't want to go and i don't want to have to go through it again.

---

### Post by dmizer on 2006-05-23
aysiu, you don't happen to have a sweet "remove firefox via wiki instructions" script do you? ;)

---

### Post by aysiu on 2006-05-23
[QUOTE=dmizer]actually, i installed 1.5 before you created that script.  otherwise i would have used it, it's pretty sweet.[/quote] Yeah, it came a little late in the game. I didn't know about shell scripts for a while...

> 
i don't need an upgrade ... i just want to make sure that upon moving to dapper:
1) i don't have two firefoxes on my system anymore. If you don't want two, you should get rid of the Mozilla one, then. Just paste these commands into the terminal after you upgrade to Dapper: ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
``` > 2) that i am able to retain my settings.  some of the plugins that i've installed in firefox really didn't want to go and i don't want to have to go through it again. Your settings are completely independent of your Firefox installations, and they live in your /home/dmizer/.mozilla folder--which should be compatible with both Ubuntu and Mozilla versions of Firefox.

The plugins live in /usr/lib/mozilla-firefox/plugins, which the Ubuntu Firefox draws on and which the Mozilla Firefox links to and draws on.

I hope that makes sense. Let me know if you need further clarification.

---

### Post by aysiu on 2006-05-23
[QUOTE=dmizer]aysiu, you don't happen to have a sweet "remove firefox via wiki instructions" script do you? ;)[/QUOTE] Sure. ```
#!/bin/bash
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
cd
mv .mozilla .mozilla-1.5
mv .mozilla.ubuntu .mozilla
sudo rm -r /opt/firefox
``` Save that code as a text file called *removefirefox.sh* and save that to your desktop. Then ```
cd ~/Desktop
chmod +x removefirefox.sh
./removefirefox.sh
```

---

### Post by dmizer on 2006-05-23
[QUOTE=aysiu]```
mv .mozilla .mozilla-1.5
mv .mozilla.ubuntu .mozilla
```[/QUOTE]
wouldn't those two lines remove my settings?  as currently my settings appear in /home/dmizer/.mozilla

i mean, obviously, my settings would still exist, but in .mozilla-1.5 rather than in .mozilla where they need to be?

---

### Post by aysiu on 2006-05-23
[QUOTE=dmizer]wouldn't those two lines remove my settings?  as currently my settings appear in /home/dmizer/.mozilla

i mean, obviously, my settings would still exist, but in .mozilla-1.5 rather than in .mozilla where they need to be?[/QUOTE] Good point. If you've modified your profile since, you probably don't want your old profile back. Just take out those two lines.

---

### Post by dmizer on 2006-05-25
now THAT is what i call support.  far more than i expected out of this thread ... lol.

---

### Post by nanotube on 2006-05-25
[QUOTE=dmizer]now THAT is what i call support.  far more than i expected out of this thread ... lol.[/QUOTE]
hehe

---

### Post by nanotube on 2006-05-30
[QUOTE=aysiu]Nanotube, thanks for the explanation. That makes sense.[/QUOTE]
no prob. 
so if you have any other interesting scripts you want to make, let me know, i'd be glad to take a crack at them. ;)

---

### Post by aysiu on 2006-05-30
> **nanotube]no prob. 
so if you have any other interesting scripts you want to make, let me know, i'd be glad to take a crack at them.  said:**
>  Well, now that you mention it...

There's [a script on the Wiki](https://wiki.ubuntu.com/AutomaticallyMountPartitions) that automatically mounts Windows partitions. It does give this little warning, though: [quote]Script assumptions

    */media/ is an acceptable location for the partitions to be mounted
    *there are no entries in your /etc/fstab for windows drives already
    *the windows drives are currently not mounted.

NOTE:- I've added the last two script assumptions after dealing with a number of problems in IRC with regards to running this script successfully. The problems were invariably caused by entries being in the /etc/fstab file that were already referring to a windows partition/s and often the drive/s were mounted already (usually without the correct permissions for them to be accessible by the user). If you find you are experiencing problems with the script then, backup your current copy of fstab (this step should always be done when editing system files), remove the entries for window drives in your fstab file, then umount the windows drives, then run the script again.  Given that Breezy (and I believe Dapper, too) defaults (you can override this, of course) to adding Windows partitions at /media/hda1, /media/hda5, etc, the last two assumptions are bad ones.

I've also noticed that sometimes, particularly with FAT32 partitions, people get weird permissions issues (locked out of some folders but not others) when the partition is mounted in the /media folder.

Ideally, I would imagine a script that does something like this:

1. Polls the partition table to see what partitions exist and what type they are.
2. Compares that to the /etc/fstab file and sees which partitions are mounted with the wrong permissions and which partitions aren't mounted at all
3. Asks the user which partitions to mount (with the default answer being "all partitions and drives").
4. Asks the users what mount points (folder names) she wants for those partitions and creates those folders.
5. Unmounts the drives to be modified.
6. Backs up the /etc/fstab file and proceeds to add or modify the appropriate /etc/fstab files.
7. Remounts the partitions.
8. For Linux partitions or drives, asks who should own the partitions and with what permissions (defaulting the current user as owner and with 755 permissions).

Right now, I have instructions for people to do this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

It'd be great if people could know their Windows partitions or Linux partitions could be added with the correct permissions.

The only warning would be to make sure that no USB drives (iPods, thumb drives, external hard drives, etc.) were plugged in when you run the script.

Would that be an extremely massive undertaking?

---

### Post by nanotube on 2006-05-30
shouldn't be too massive, especially since we can build on the first script.

you are incorrect about the last two assumptions you added, though. i read the script, and it does check whether the drive is already listed in fstab, in which case it doesn't do anything with that drive. (that explains why people were still having problems after running the script if they already had stuff in fstab - it saw that the drive was listed in fstab, and didn't do anything about it. so if it was listed incorrectly, it remained that way).

it also makes no assumption that the drive is or is not already mounted. it just issues a mount -a at the end, after it is done editing fstab. no problems with that.

the first assumption is right, though - it mounts everything in /media. which i think is not a bad choice, since everything in /media automatically gets a shortcut placed on the desktop, so people are not left wondering "where is that drive i just mounted".

so the script could use some modification, along the lines you mentioned, and could use some additional error checking and being more user friendly. but that would not be that difficult to implement, i'd venture to say as my first impression.

another thought - since knoppix does such a great job of automounting all the partitions, i wonder if that piece of knoppix code couldn't just be ripped out and used as an independent script...

---

### Post by aysiu on 2006-05-30
[QUOTE=nanotube]
another thought - since knoppix does such a great job of automounting all the partitions, i wonder if that piece of knoppix code couldn't just be ripped out and used as an independent script...[/QUOTE] I've always wondering this, too.

Knoppix has had this functionality at least since spring of last year (if not longer), and I can't imagine they'd keep the code for it closed source (especially since Mepis used it, too--as it was based on Knoppix).

I always liked that the partitions appeared on the desktop unmounted and that when you wanted to mount them, you could just click on them and they'd automount and open--regardless of what type they were (FAT32, NTFS, Ext3)--with the proper read/write permissions.

This is all gobbledygook to me, but maybe it'll make sense to you:
[http://debian-knoppix.alioth.debian.org/sources/](http://debian-knoppix.alioth.debian.org/sources/)

---

### Post by nanotube on 2006-05-30
whoa, that's a nice link :)
well, i did find some promising leads.
[http://debian-knoppix.alioth.debian.org/sources/scanpartitions-knoppix_0.5-9.tar.gz](http://debian-knoppix.alioth.debian.org/sources/scanpartitions-knoppix_0.5-9.tar.gz)
scans all the partitions and determines their filesystem, and creates fstab entries for them. 

[http://debian-knoppix.alioth.debian.org/sources/mkdesktophdicons-knoppix_0.5-11.tar.gz](http://debian-knoppix.alioth.debian.org/sources/mkdesktophdicons-knoppix_0.5-11.tar.gz)
makes desktop icons for partitions (but in the comments says it only works for kde - but at any rate, nautilus automatically makes partition links to anything in /media, so we don't really need this)

[http://debian-knoppix.alioth.debian.org/sources/knoppix-remountrw_0.5-4.tar.gz](http://debian-knoppix.alioth.debian.org/sources/knoppix-remountrw_0.5-4.tar.gz)
remounts a partition rw, presumably when you rightclick an icon on your desktop...

hm, so i suppose picking through those we can come up with a nice automount script. :)

---

### Post by aysiu on 2006-05-31
You know, before this whole Knoppix undertaking... it might be pretty easy for you to adapt the new Thunderbird script in the same way as the Firefox script...?

[http://www.psychocats.net/ubuntu/thunderbird](http://www.psychocats.net/ubuntu/thunderbird)

I stole your little if/then code, but it's still not nearly as refined as the Firefox one.

---

### Post by nanotube on 2006-05-31
[QUOTE=aysiu]You know, before this whole Knoppix undertaking... it might be pretty easy for you to adapt the new Thunderbird script in the same way as the Firefox script...?

[http://www.psychocats.net/ubuntu/thunderbird](http://www.psychocats.net/ubuntu/thunderbird)

I stole your little if/then code, but it's still not nearly as refined as the Firefox one.[/QUOTE]
heh hmm, yea, looking at that script, it looks like all we have to do is take the firefox script, and do a search/replace with firefox/thunderbird :) 
well, and remove the linking plugins part, and a few minor details.
i wanted to leave it for tomorrow, but just decided to finish it off now. here is the thunderbird script:

```

#!/bin/bash
#
# installnewthunderbird.sh
#               Script to automatically download and install the newest thunderbird version for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installnewthunderbird.sh  1.6  29-May-2006  nanotube@users.sf.net
# 
#
#######

check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully. Exiting."
    exit 1
  fi
}

## Set version-specific variables
#~ if grep -q "5.10" /etc/issue ; then
  #~ PLUGINPATH=/usr/lib/mozilla-thunderbird/plugins
#~ elif grep -q "6.06" /etc/issue ; then
  #~ PLUGINPATH=/usr/lib/thunderbird/plugins
#~ else
  #~ echo "This script only works on Breezy or Dapper."
  #~ exit 1
#~ fi

## Get the newest thunderbird release version from mozilla website
VERSION=`wget -q -O - http://www.mozilla.com/thunderbird/ |grep "product=" -m 1 |sed -e 's/.*<li>.*thunderbird-//' -e 's/&amp.*//'`

echo -e -n "The most recent release of thunderbird is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.com/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; exit ;;
  [Nn][Oo]) echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Get available localizations
LOCALIZATIONS=( `wget -q -O - http://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/$VERSION/linux-i686/ | grep 'img src="/icons/folder.gif"' | grep -v "xpi" | sed -e 's/<img.*href="//' | sed -e 's@/">.*@@'` )

LIMIT=${#LOCALIZATIONS[*]}

## Get user choice of localization

echo "Please choose the localization (language) for thunderbird. Enter the number of your choice from the list below."
for ((i=0; i < LIMIT ; i++))
do
  echo "$i: ${LOCALIZATIONS[$i]}"
done

CHOICE=$(($LIMIT + 1))

echo -n "Enter your choice of localization: "
while [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]
do
  read CHOICE
  if echo -n "$CHOICE" | grep -q "[^0-9]"; then
    echo -n "Your input contains non-numeric characters. Please try again: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ -z "$CHOICE" ]; then
    echo -n "Please enter the number of your choice from the list: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]; then
    echo -n "Your input is not in the range of available localizations. Please try again: "
  fi
done

echo -n "You have chosen localization \"${LOCALIZATIONS[$CHOICE]}\". Is that correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "In that case, start over by running this script again."; exit ;;
  [Nn][Oo]) echo "In that case, start over by running this script again."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Proceed to download and install thunderbird.

echo -e "\nUpdating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old thunderbird are installed\n"
sudo apt-get -y install mozilla-thunderbird libstdc++5
check_exit_status

if [ -d ~/.mozilla-thunderbird ]; then
  echo -e "\nBacking up old thunderbird preferences\n"
  cp -R ~/.mozilla-thunderbird ~/.mozilla-thunderbird-backup
  check_exit_status
else
  echo -e "\nOld thunderbird preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading thunderbird from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/thunderbird-$VERSION.tar.gz
check_exit_status

echo -e "\nDownloading thunderbird signature from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/thunderbird-$VERSION.tar.gz.asc
check_exit_status

echo -e "\nImporting Mozilla Software Releases public key\n"
echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there will be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"
gpg --keyserver subkeys.pgp.net --recv 1AF32821
check_exit_status

echo -e "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys.\n"
gpg --verify thunderbird-$VERSION.tar.gz.asc thunderbird-$VERSION.tar.gz
check_exit_status

### for debug purposes:
#~ echo "ok, that's enough"
#~ exit

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -z -v -f thunderbird-$VERSION.tar.gz
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f thunderbird-$VERSION.tar.gz thunderbird-$VERSION.tar.gz.asc
check_exit_status

#~ echo -e "\nLinking plugins\n"
#~ cd /opt/thunderbird/plugins/
#~ sudo ln -s $PLUGINPATH/* .
#~ check_exit_status

echo -e "\nLinking launcher to new thunderbird\n"
#~ sudo dpkg-divert --divert /usr/bin/thunderbird.ubuntu --rename /usr/bin/thunderbird
#~ check_exit_status
#~ sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird
#~ check_exit_status
#~ sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird
#~ check_exit_status
#~ sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
#~ check_exit_status
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird
check_exit_status
sudo mv /usr/bin/mozilla-thunderbird /usr/bin/mozilla-thunderbird-old
check_exit_status
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
check_exit_status

echo -e "\nThe new thunderbird version $VERSION has been installed successfully."

exit

```

i tested it up to the point where it is supposed to start un-taring things into /opt. 
have at it, see if it does everything untoward. :)

---

### Post by aysiu on 2006-05-31
I'll test it and let you know.

By the way, I'm making one small modification: ```
if [ -d ~/.mozilla-thunderbird ]; then
  echo -e "\nBacking up old thunderbird preferences\n"
  cp -R ~/.mozilla-thunderbird ~/.mozilla-thunderbird-backup
  check_exit_status
else
  echo -e "\nOld thunderbird preferences not found. Nothing to back up. Proceeding with installation.\n"
fi
``` This should become ```
if [ -d ~/.mozilla-thunderbird ]; then
  echo -e "\nBacking up old thunderbird preferences\n"
  cp -R ~/.mozilla-thunderbird ~/.thunderbird
  check_exit_status
else
  echo -e "\nOld thunderbird preferences not found. Nothing to back up. Proceeding with installation.\n"
fi
``` The old Ubuntu Thunderbird calls its config directory .mozilla-thunderbird. The Mozilla Thunderbird calls its config .thunderbird. So, by copying the old config to .thunderbird, you're automatically making a backup.

---

### Post by nanotube on 2006-05-31
> **aysiu]I'll test it and let you know.

By the way, I'm making one small modification: ```
if [ -d ~/.mozilla-thunderbird ] said:**
> ; then
  echo -e "\nBacking up old thunderbird preferences\n"
  cp -R ~/.mozilla-thunderbird ~/.thunderbird
  check_exit_status
else
  echo -e "\nOld thunderbird preferences not found. Nothing to back up. Proceeding with installation.\n"
fi
``` The old Ubuntu Thunderbird calls its config directory .mozilla-thunderbird. The Mozilla Thunderbird calls its config .thunderbird. So, by copying the old config to .thunderbird, you're automatically making a backup.
aha ok cool. :)

---

### Post by aysiu on 2006-05-31
It seems to work fine with *thunderbird*.

I get this error message when I try to launch *mozilla-thunderbird*: ```
run-mozilla.sh: Cannot execute /opt/thunderbird/mozilla-thunderbird-bin
```

---

### Post by nanotube on 2006-05-31
[QUOTE=aysiu]It seems to work fine with *thunderbird*.

I get this error message when I try to launch *mozilla-thunderbird*: ```
run-mozilla.sh: Cannot execute /opt/thunderbird/mozilla-thunderbird-bin
```[/QUOTE]
ah, well, that seems to be the fault of thunderbird itself. i looked at the source of the thunderbird startup script (the one in /opt/thunderbird/thunderbird), and basically what it does (as far as we are concerned) is check what name it was called by, then pass it (+-bin) to run-mozilla.sh. Then run-mozilla.sh does some other stuff, and then tries to start thunderbird by using that name_it_was_started_with-bin that was passed to it from /opt/thunderbird/thunderbird.
so... basically, it doesn't like to be called anything but "thunderbird". :)
there is a workaround though that i will try. i will have our script make a link from thunderbird-bin to mozilla-thunderbird-bin
and you try it and see if that works. seems like a really strange thing to do, though (with multiple startup scripts etc, i mean).

here is the freshest script for thunderbird:

```

#!/bin/bash
#
# installnewthunderbird.sh
#               Script to automatically download and install the newest thunderbird version for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installnewthunderbird.sh  1.6  31-May-2006  nanotube@users.sf.net
# 
#
#######

check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully. Exiting."
    exit 1
  fi
}

## Set version-specific variables
#~ if grep -q "5.10" /etc/issue ; then
  #~ PLUGINPATH=/usr/lib/mozilla-thunderbird/plugins
#~ elif grep -q "6.06" /etc/issue ; then
  #~ PLUGINPATH=/usr/lib/thunderbird/plugins
#~ else
  #~ echo "This script only works on Breezy or Dapper."
  #~ exit 1
#~ fi

## Get the newest thunderbird release version from mozilla website
VERSION=`wget -q -O - http://www.mozilla.com/thunderbird/ |grep "product=" -m 1 |sed -e 's/.*<li>.*thunderbird-//' -e 's/&amp.*//'`

echo -e -n "The most recent release of thunderbird is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.com/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; exit ;;
  [Nn][Oo]) echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Get available localizations
LOCALIZATIONS=( `wget -q -O - http://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/$VERSION/linux-i686/ | grep 'img src="/icons/folder.gif"' | grep -v "xpi" | sed -e 's/<img.*href="//' | sed -e 's@/">.*@@'` )

LIMIT=${#LOCALIZATIONS[*]}

## Get user choice of localization

echo "Please choose the localization (language) for thunderbird. Enter the number of your choice from the list below."
for ((i=0; i < LIMIT ; i++))
do
  echo "$i: ${LOCALIZATIONS[$i]}"
done

CHOICE=$(($LIMIT + 1))

echo -n "Enter your choice of localization: "
while [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]
do
  read CHOICE
  if echo -n "$CHOICE" | grep -q "[^0-9]"; then
    echo -n "Your input contains non-numeric characters. Please try again: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ -z "$CHOICE" ]; then
    echo -n "Please enter the number of your choice from the list: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]; then
    echo -n "Your input is not in the range of available localizations. Please try again: "
  fi
done

echo -n "You have chosen localization \"${LOCALIZATIONS[$CHOICE]}\". Is that correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "In that case, start over by running this script again."; exit ;;
  [Nn][Oo]) echo "In that case, start over by running this script again."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Proceed to download and install thunderbird.

echo -e "\nUpdating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old thunderbird are installed\n"
sudo apt-get -y install mozilla-thunderbird libstdc++5
check_exit_status

if [ -d ~/.mozilla-thunderbird ]; then
  echo -e "\nBacking up old thunderbird preferences\n"
  cp -R ~/.mozilla-thunderbird ~/.thunderbird
  check_exit_status
else
  echo -e "\nOld thunderbird preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading thunderbird from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/thunderbird-$VERSION.tar.gz
check_exit_status

echo -e "\nDownloading thunderbird signature from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/thunderbird-$VERSION.tar.gz.asc
check_exit_status

echo -e "\nImporting Mozilla Software Releases public key\n"
echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there will be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"
gpg --keyserver subkeys.pgp.net --recv 1AF32821
check_exit_status

echo -e "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys.\n"
gpg --verify thunderbird-$VERSION.tar.gz.asc thunderbird-$VERSION.tar.gz
check_exit_status

### for debug purposes:
#~ echo "ok, that's enough"
#~ exit

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -z -v -f thunderbird-$VERSION.tar.gz
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f thunderbird-$VERSION.tar.gz thunderbird-$VERSION.tar.gz.asc
check_exit_status

#~ echo -e "\nLinking plugins\n"
#~ cd /opt/thunderbird/plugins/
#~ sudo ln -s $PLUGINPATH/* .
#~ check_exit_status

echo -e "\nLinking launcher to new thunderbird\n"
#~ sudo dpkg-divert --divert /usr/bin/thunderbird.ubuntu --rename /usr/bin/thunderbird
#~ check_exit_status
#~ sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird
#~ check_exit_status
#~ sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird
#~ check_exit_status
#~ sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
#~ check_exit_status
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird
check_exit_status
sudo mv /usr/bin/mozilla-thunderbird /usr/bin/mozilla-thunderbird-old
check_exit_status
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
check_exit_status
sudo ln -s /opt/thunderbird/thunderbird-bin /opt/thunderbird/mozilla-thunderbird-bin
check_exit_status

echo -e "\nThe new thunderbird version $VERSION has been installed successfully."

exit

```

---

### Post by aysiu on 2006-05-31
It took me a while to getting around to testing this, but I did, and it works flawlessly. Thanks for that. Will you post that up on your *keylogger* site and let me know what the link is?

---

### Post by nanotube on 2006-05-31
[QUOTE=aysiu]It took me a while to getting around to testing this, but I did, and it works flawlessly. Thanks for that. Will you post that up on your *keylogger* site and let me know what the link is?[/QUOTE]

great to know it worked. it's always about the clever workarounds, isn't it? or at least i like to think it was clever. :)

sure, i will post an "install thunderbird" section on pykeylogger, and make a post here with a link.

---

### Post by aysiu on 2006-05-31
*nanotube*, thanks for all your hard work.

---

### Post by nanotube on 2006-05-31
ok, here is a link to the new section:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Thunderbird_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Thunderbird_1.5)

---

### Post by nanotube on 2006-05-31
[QUOTE=aysiu]*nanotube*, thanks for all your hard work.[/QUOTE]
my pleasure :)

---

### Post by aysiu on 2006-06-04
[Someone just mentioned a script that automounts partitions](http://www.ubuntuforums.org/showpost.php?p=1090085&postcount=6).

[This is the script](http://www.ubuntulinux.nl/files/diskmounter). Does it look legit? Could it be improved?

---

### Post by nanotube on 2006-06-04
[QUOTE=aysiu][Someone just mentioned a script that automounts partitions](http://www.ubuntuforums.org/showpost.php?p=1090085&postcount=6).

[This is the script](http://www.ubuntulinux.nl/files/diskmounter). Does it look legit? Could it be improved?[/QUOTE]
hey aysiu,
you have already mentioned this very same script in your post #70 ([http://ubuntuforums.org/showpost.php?p=1068758&postcount=70](http://ubuntuforums.org/showpost.php?p=1068758&postcount=70) ) here (it is the script being discussed on the wiki page you linked to).
so yes, it looks legit, and it does what it claims.

sure, it could be improved, i suppose (most glaringly, it should make a backup of the old fstab before tacking on entries to it, but could probably also use some more user interaction.)

but i saw some post recently, some guy said he installed ubuntu dapper, and it placed icons for his various drives on his desktop. so maybe this is obsolete, now that we have dapper doing knoppix-like stuff? i haven't tried dapper myself, though, so maybe that's not the case...?

---

### Post by aysiu on 2006-06-04
Oh, I didn't realize it was the same script...

Whoops.

---

### Post by nanotube on 2006-06-04
[QUOTE=aysiu]Oh, I didn't realize it was the same script...

Whoops.[/QUOTE]

no prob. :)
and btw, i got my first script support email today. guy said he installed firefox 1.5.0.4 (wow, it's out, and autodetected! :)), and the flash plugin is "gone". we will try to fix it, but i wonder if the dapper firefox plugins are where you said they were. :) if you still have that dapper box, could you check one more time?

edit: never mind. he found the problem. the dapper upgrade hosed his flash plugin somehow. he reinstalled flash and relinked to /opt, and it's all good. 

p.s. what firefox version comes with dapper? 1.5.0.3, i'd guess? hmm, maybe the official firefox install script still has some life in it. :)

---

### Post by nanotube on 2006-06-09
by the way... today i actually used my thunderbird install script to install tbird 1.5 on my breezy box. worked like a charm! how nice it is to use the fruits of our own labor! ;)

---

### Post by dmizer on 2007-01-24
sorry to revive this, but i thought it was best to include the background.

still have a dapper machine with a 1.8 something firefox install.  it's been behaving TERRIBLY with segmentation faults when attempting to log in with some forms, and completely crashes with no debugging detail.  just a little note about "segmentation fault" and that's it.

so i figured i'd try the script to install the new firefox.  it detected the 2.0.0.1 current version of firefox and indicated that it was successfully installed.  but when i try to run firefox now i get this:
```
/opt/firefox/run-mozilla.sh: line 131:  6098 Segmentation fault      "$prog" ${1+"$@"}
```

---


---
title: "Installed Firefox 1.5 manually before upgrade, updates don't affect it anymore"
date: 2006-06-10
forum: General Help
---

### Post by Michael%S on 2006-06-10
So back in Breezy I installed firefox 1.5 manually according to that guide in the wiki (FirefoxNewVersion, I believe). It worked fine and still does, but now that I've upgraded to Dapper the system comes with an ff1.5 that it updates itself, which is even better. Problem is, I can't even get to that ff, I only have access to the one I manually installed. And now the system upgraded to 1.5.0.4 and my copy is still on 1.5.0.1. What can I do to merge the two so I basically have my own settings and everything on the system's copy of ff?

---

### Post by Jucato on 2006-06-10
That's one of the drawbacks of manually installing FF 1.5 in Breezy. I think the wiki page gives that warning clearly. You can still update your copy of FF 1.5 (the one you manually installed). I'm not sure if this is the "official" way to do it, but this is what I did. I ran that Firefox as root (gksudo or kdesu firefox), then used the Update feature on Firefox. Once it updates itself, I close it, then I run Firefox again, this time as a normal user, and it's updated to 1.5.0.4.

---

### Post by Michael%S on 2006-06-10
But is there any way to get rid of my manually installed copy and switch to the copy that comes with dapper, while keeping my settings, extensions, bookmarks, etc?

---

### Post by dallas7 on 2006-06-10
I followed the same procedure:  Ubuntu 5.10, manual FF 1.5 install, then used Update Manager to Ubuntu 6.06.

I did yesterday's Ubuntu FF 1.5.0.4 upgrade and FF is stuck at 1.5.0.3.
Also the Help > Check for Upgrades is greyed out.  So, I can't even use the residient tool to upgrade.

I posted a separate thread on this.  Sorry for the duplication,but I wanted to add my experience to this one as I consider it a serious issue that I'd like to fix without having to wipe and re-install Ubuntu.

Thank you.

---

### Post by Ramses de Norre on 2006-06-10
The guide tells you how to remove the version you installed, look [here]("https://wiki.ubuntu.com/FirefoxNewVersion#head-51054869b8a40ea50859b0163c806e76f882499c").
You will be using the dapper version when you did that.

---

### Post by Michael%S on 2006-06-10
Thank you. I did just the first thing (restoring symbolic links) because I got confused after that but that seems to have done the trick. The only downside is ff doesn't use the icon with the fox anymore, just the earth. :'(

---

### Post by Ramses de Norre on 2006-06-10
This script takes care of the icons: ```
#! /bin/sh

#
# Restore the original Firefox and/or Thunderbird icons.
#

#
# If you're using Dapper, comment the next line and uncomment the second.
#
# TODO: Automatic detection of Ubuntu version
#
#FIREFOX_LIB="/usr/lib/mozilla-firefox/" #Hoary, Breezy
FIREFOX_LIB="/usr/lib/firefox/" #Dapper

FIREFOX_BIN="/usr/bin/mozilla-firefox"
THUNDERBIRD_BIN="/usr/bin/mozilla-thunderbird"

ICON_PACK_URL="http://ubuntu.globalvision.ch/mozilla_icons.tar.bz2"
ICON_PACK_FILENAME="mozilla_icons.tar.bz2"
TMP_DIR="/tmp/moz-icons"$$"/"


#Ctrl-C trapping
trap ctrlc INT
ctrlc()
{
        echo -e "\nAborted by user."
        rm -rf $TMP_DIR
        exit 2
}


#Check if run as root
if [ "$UID" -ne 0 ] ; then
        echo "You must be root to do that!"
        exit 1
fi


#Ask which icons to replace
replace_ff="0"
replace_ff_doc="0"
replace_tb="0"
replace_tb_pm="0"

if [ -x "$FIREFOX_BIN" ] ; then
        #Firefox
        echo -n "Replace the Mozilla Firefox program icon (y/n)? [y] "
        read input
        if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
                replace_ff="1"
        fi

        #Firefox document
        echo -n "Replace the Mozilla Firefox document icon (y/n)? [y] "
        read input
        if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
                replace_ff_doc="1"
        fi
fi

if [ -x "$THUNDERBIRD_BIN" ] ; then
        #Thunderbird
        echo -n "Replace the Mozilla Thunderbird program icon (y/n)? [y] "
        read input
        if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
                replace_tb="1"
        fi

        #Thunderbird profile manager
        echo -n "Replace the Mozilla Thunderbird profile manager icon (y/n)? [y] "
        read input
        if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
                replace_tb_pm="1"
        fi
fi

if [ "$replace_ff" -eq "0" ] && [ "$replace_ff_doc" -eq "0" ] && [ "$replace_tb" -eq "0" ] && [ "$replace_tb_pm" -eq "0" ] ; then
        echo "Nothing to do here."
        exit 0
fi


#Ask for divert the original packaged files to alternate locations
divert="0"

echo -e "\nDo you want to divert the original packaged files to alternate locations"
echo -n "(make the changes permanent) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
        divert="1"
fi


#Downloading
echo -en "\nDownloading and replacing icons. Please wait..."

mkdir $TMP_DIR
wget $ICON_PACK_URL -O $TMP_DIR$ICON_PACK_FILENAME >/dev/null 2>&1
if [ ! -f $TMP_DIR$ICON_PACK_FILENAME ] ; then
        echo -e "\nCannot download icons. Please check your internet connection."
        rm -rf $TMP_DIR
        exit 1
fi
tar xjf $TMP_DIR$ICON_PACK_FILENAME -C $TMP_DIR


#Replace Firefox icon
if [ "$replace_ff" -gt "0" ] ; then
        if [ ! -f $TMP_DIR"mozilla-firefox.png" ] || [ ! -f $TMP_DIR"mozilla-firefox.xpm" ] ; then
                echo "Cannot continue (unavailable Firefox icon file)"
                rm -rf $TMP_DIR
                exit 1
        fi

        #Backup
        cp -f /usr/share/pixmaps/mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.old.png
        cp -f /usr/share/pixmaps/mozilla-firefox.xpm /usr/share/pixmaps/mozilla-firefox.old.xpm
        cp -f $FIREFOX_LIB"icons/default.xpm" $FIREFOX_LIB"icons/default.old.xpm"
        cp -f $FIREFOX_LIB"chrome/icons/default/default.xpm" $FIREFOX_LIB"chrome/icons/default/default.old.xpm"

        #Divert
        if [ "$divert" -gt "0" ] ; then
                dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.png >/dev/null
                dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm >/dev/null
                dpkg-divert --rename $FIREFOX_LIB"icons/default.xpm" >/dev/null
                dpkg-divert --rename $FIREFOX_LIB"chrome/icons/default/default.xpm" >/dev/null
        fi

        #Replace icons
        cp $TMP_DIR"mozilla-firefox.png" /usr/share/pixmaps/mozilla-firefox.png
        cp $TMP_DIR"mozilla-firefox.xpm" /usr/share/pixmaps/mozilla-firefox.xpm
        cp $TMP_DIR"mozilla-firefox.xpm" $FIREFOX_LIB"icons/default.xpm"
        cp $TMP_DIR"mozilla-firefox.xpm" $FIREFOX_LIB"chrome/icons/default/default.xpm"
        echo -n "."
fi


#Replace Firefox document icon
if [ "$replace_ff_doc" -gt "0" ] ; then
        if [ ! -f $TMP_DIR"mozilla-firefox-doc.png" ] ; then
                echo "Cannot continue (unavailable Firefox document icon file)"
                rm -rf $TMP_DIR
                exit 1
        fi

        #Backup
        cp -f $FIREFOX_LIB"icons/document.png" $FIREFOX_LIB"icons/document.old.png"

        #Divert
        if [ "$divert" -gt "0" ] ; then
                dpkg-divert --rename $FIREFOX_LIB"icons/document.png" >/dev/null
        fi

        #Replace icons
        cp $TMP_DIR"mozilla-firefox-doc.png" $FIREFOX_LIB"icons/document.png"
        echo -n "."
fi


#Replace Thunderbird icon
if [ "$replace_tb" -gt "0" ] ; then
        if [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
                echo "Cannot continue (unavailable Thunderbird icon file)"
                rm -rf $TMP_DIR
                exit 1
        fi

        #Backup
        cp -f /usr/share/pixmaps/mozilla-thunderbird.xpm /usr/share/pixmaps/mozilla-thunderbird.old.xpm
        cp -f /usr/share/pixmaps/mozilla-thunderbird-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-menu.old.xpm
        cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.old.xpm
        cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.old.xpm
        cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.old.xpm

        #Divert
        if [ "$divert" -gt "0" ] ; then
                dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.xpm >/dev/null
                dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.xpm >/dev/null
                dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm >/dev/null
                dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm >/dev/null
                dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm >/dev/null
        fi

        #Replace icons
        cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird.xpm
        cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-menu.xpm
        cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm
        cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm
        cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm
        echo -n "."
fi


#Replace Thunderbird profile manager icon
if [ "$replace_tb_pm" -gt "0" ] ; then
        if [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
                echo "Cannot continue (unavailable Thunderbird icon file)"
                rm -rf $TMP_DIR
                exit 1
        fi

        #Backup
        cp -f /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.xpm
        cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/default.old.xpm

        #Divert
        if [ "$divert" -gt "0" ] ; then
                dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm >/dev/null
                dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm >/dev/null
        fi

        #Replace icons
        cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm
        cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm
        echo -n "."
fi


echo " done !"


#Reload gnome-panel
echo -en "\nShall I reload gnome-panel to apply the changes (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
        killall gnome-panel
fi


rm -rf $TMP_DIR
exit 0

```

---

### Post by Michael%S on 2006-06-10
Thanks, works like a charm. :)

---

### Post by dallas7 on 2006-06-11
Well, I tried "everything" to no avail.

I decided to back up my user folder to a USB stick, wipe the hard drive and install a clean 6.06 and start from scratch.

I'm a happy camper now and will never again stray from the Ubuntu Way.
It's "Add/Remove Applications" or nothing!

Thanks to all for the help.

---

### Post by GadgetsGuy on 2006-06-14
[QUOTE=Michael%S]But is there any way to get rid of my manually installed copy and switch to the copy that comes with dapper, while keeping my settings, extensions, bookmarks, etc?[/QUOTE]
it is well documented that Mozilla's Firefox for Linux is MUCH faster than Ubuntu's Firefox ..... and having used the Mozilla released Firefox for Linux for several weeks now, the difference is very noticable.

$ gksudo firefox

>> then update firefox using the SEARCH FOR UPDATES (no longer greyed out as root user)

close terminal and firefox when update is finished and reboot firefox.

VOILA!

---

### Post by Michael%S on 2006-06-14
The difference in speed is not significant to me (I didn't really notice it, though now that I think about it...) and it's more convenient for me to stay uptodate through update-manager so I'll just stick to Ubuntu ff for now.
By the way, would I have to gksudo firefox to update extensions and themes?

---

### Post by GadgetsGuy on 2006-06-15
short answer = nope

:)  just the application
GG

---

### Post by Ramses de Norre on 2006-06-15
[QUOTE=Michael%S]By the way, would I have to gksudo firefox to update extensions and themes?[/QUOTE]
Those are stored in a folder in your home folder -> full write access and no gksudo required ;)

---


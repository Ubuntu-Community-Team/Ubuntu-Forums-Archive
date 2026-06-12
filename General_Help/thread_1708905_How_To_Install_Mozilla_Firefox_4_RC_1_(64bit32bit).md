---
title: "How To: Install Mozilla Firefox 4 RC 1 (64bit/32bit)"
date: 2011-03-17
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-03-17
If you want to compile it your self go [here]("https://developer.mozilla.org/En/Simple_Firefox_build") (you will need to download around 100MB of files total)
If you want a ppa go [here]("http://www.webupd8.org/2011/03/install-firefox-4-in-ubuntu-1004-1010.html") ([about dialog screenshot]("http://i51.tinypic.com/vf8gm.png"))
If you want Mozilla's unmodified version this is for you with no risk to your installation this is for you

I went and made a sh script for it
This installs Mozilla's un-modified version 
I have attached it if you prefer download to copy/paste
This does NOT need root access
It will auto detect 32bit /64 bit and your language
It is installed in your normal user account this will allow it to auto-update
It is meant to be run from a terminal
It expects zenity, awk, and wget to be installed
*:arrow: **sudo apt-get install zenity awk wget*
Those are probably installed by default
Download or save this to install *[install_Latest_Stable_Firefox.sh]("http://ubuntuforums.org/attachment.php?attachmentid=186829&d=1300820376")*
Then run it with sh (I assume you saved it to your Downloads folder)
*:arrow: sh Downloads/*install_Latest_Stable_Firefox.sh

If you want to uninstall it just delete *.firefox* from your user folder and the icon it puts on your desktop

In simple terms all this does in download the correct firefox for your install from mozilla's ftp servers extract it and give you an icon
This script is comparable with any i686/x86_64 linux distro  others are comparable via manual download
```
#!/bin/sh
LOCAL=$(echo $LANG | awk '{ print substr( $0, 0, index($0,".")-1 ) }')
LOCAL=$(echo $LOCAL | awk '{ sub( /\_/, "-", $0); print }')
VER="10.0"
cd $HOME
if [ ! `ls firefox-$VER.tar.bz2` ]; then # allows manual download
    wget "http://releases.mozilla.org/pub/mozilla.org/firefox/releases/$VER/linux-`uname -m`/$LOCAL/firefox-$VER.tar.bz2"
fi
if [ ! `ls firefox-$VER.tar.bz2` ]; then # make sure firefox if there to install
    echo "Failed to download firefox"
    echo "This is probally due to mozilla not offering firefox in $LOCAL"
    echo "Please download firefox $VER to your $HOME folder then run this script again"
    echo "http://releases.mozilla.org/pub/mozilla.org/firefox/releases/$VER/linux-`uname -m`/"
    exit 1
fi
tar -jxvf firefox-$VER.tar.bz2
mv firefox .firefox
rm firefox-$VER.tar.bz2
chmod +x .firefox/firefox
echo "[Desktop Entry]" > Desktop/Firefox.desktop
echo "Categories=;" >> Desktop/Firefox.desktop
echo "Comment=Browse the World Wide Web" >> Desktop/Firefox.desktop
echo "Comment[en_US]=Browse the World Wide Web" >> Desktop/Firefox.desktop
echo "Exec=$HOME/.firefox/firefox %u" >> Desktop/Firefox.desktop
echo "Hidden=false" >> Desktop/Firefox.desktop
echo "Icon=firefox" >> Desktop/Firefox.desktop
echo "Name=Mozilla Firefox $VER" >> Desktop/Firefox.desktop
echo "Terminal=false" >> Desktop/Firefox.desktop
echo "Type=Application" >> Desktop/Firefox.desktop
echo "Version=1.0" >> Desktop/Firefox.desktop
chmod +x Desktop/Firefox.desktop
zenity --info --text "Please update Firefox icons to point to:\n$HOME/.firefox/firefox"
if [ $(zenity --question --title="Open Firefox?" --text "Would you like to start using Firefox $VER now\nThis will close Firefox first by killing it's process"; echo $?) = "0" ]; then
    killall firefox-bin
    .firefox/firefox
fi
exit 0
```[IMG]http://i52.tinypic.com/2qvuykg.png[/IMG]
Firefox has theses requirements:
[QUOTE="www.mozilla.com"]Please note that Linux distributors may provide packages for your distribution which have different requirements.   
[LIST]
[*]Firefox will not run at all without the following libraries or packages:
[LIST]
[*]GTK+ 2.10 or higher
[*]GLib 2.12 or higher
[*]Pango 1.14 or higher
[*]X.Org 1.0 or higher (1.7 or higher is recommended)
[*]libstdc++ 4.3 or higher
[/LIST]
 
[*]For optimal functionality, we recommend the following libraries or packages:
[LIST]
[*]NetworkManager 0.7 or higher
[*]DBus 1.0 or higher
[*]HAL 0.5.8 or higher
[*]GNOME 2.16 or higher
[/LIST]
     
[/LIST]
[/QUOTE]
attached file is a plan text file not a archive
I will update this when Firefox 4 final comes out
[installFirefox4.sh]("http://ubuntuforums.org/attachment.php?attachmentid=186374&d=1300378066") is for RC1
[installFirefox4_RC2.sh]("http://ubuntuforums.org/attachment.php?attachmentid=186490&d=1300497488") is for RC2
[installFirefox4_FINAL.sh]("http://ubuntuforums.org/attachment.php?attachmentid=186814&d=1300804059") is for the final release of Firefox 4
[install_Latest_Stable_Firefox.sh]("http://ubuntuforums.org/attachment.php?attachmentid=186829&d=1300820376") is for the latest stable firefox
if you installed using that one just go to help->about in firefox it will update automatically
**USE THE FORTH FILE LISTED (install_Latest_Stable_Firefox.sh)**

---

### Post by wewa on 2011-03-17
Thank you.

Seems to have worked on my 10.04.

But at the end of the script I got:

[GLX] your GL driver is currently blocked. If you would like to bypass this, define the MOZ_GLX_IGNORE_BLACKLIST environment variable.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

So I looked it up and found:

[https://wiki.mozilla.org/Blocklisting/Blocked_Graphics_Drivers](https://wiki.mozilla.org/Blocklisting/Blocked_Graphics_Drivers)

But really still don't know what to do.
Am I losing out on the performance aspects of Firefox 4?
I have a Compaq Presario notebook with a Intel GM965/GL960.

---

### Post by pqwoerituytrueiwoq on 2011-03-18
just means your video card and firefox will not get along for hardware acceleration
you can go to about config and over ride this
about:config (URL bar)
filter to 
force-enable
set them to true to and restart firefox

if it goes crazy (firefox will not finish opening) open prefs.js in firefox's profile folder and locate the options you set and change them (and only thoes)
i also have a Compaq Presario notebook but it has a GeForce 8200m

the real question is why is firefox looking for nvidia stuff for a Intel video card

---

### Post by pqwoerituytrueiwoq on 2011-03-18
Looks like they are releasing another candidate
updated 1st post
if you installed RC1 and want the updates now go to help -> about in firefox or wait for the auto-updater to do its thing

---

### Post by opodaniel on 2011-03-19
It is strange , mine doesn't want to auto-update it gives me a link to firefox.com for the update.

---

### Post by pqwoerituytrueiwoq on 2011-03-19
> **opodaniel said:**
> It is strange , mine doesn't want to auto-update it gives me a link to firefox.com for the update.
did you run the script as root?
cause that cause it

---

### Post by herophuong on 2011-03-20
I can't get firefox installed via this method to have anti-aliasing. Anyone can help me?

---

### Post by pqwoerituytrueiwoq on 2011-03-20
> **herophuong said:**
> I can't get firefox installed via this method to have anti-aliasing. Anyone can help me?
i just googled "anti-aliasing firefox"
i found this [https://addons.mozilla.org/en-us/firefox/addon/anti-aliasing-tuner/](https://addons.mozilla.org/en-us/firefox/addon/anti-aliasing-tuner/) if it is of any use to you
edit looks like that is windows only

---

### Post by Script Warlock on 2011-03-20
is minefield also the firefox 4?

---

### Post by Frogs Hair on 2011-03-20
> **Script Warlock said:**
> is minefield also the firefox 4?

Yes

---

### Post by Script Warlock on 2011-03-20
yeah i got minefiled installed a couple of days.

---

### Post by sports fan Matt on 2011-03-20
Where again do I need to point in edit menus the path and command for FF4?

---

### Post by sports fan Matt on 2011-03-20
Figured it out =)

---

### Post by taavi on 2011-03-22
> **herophuong said:**
> I can't get firefox installed via this method to have anti-aliasing. Anyone can help me?

Anti-aliasing is disabled because FX official binaries are not linked against needed libraries (for example Ubuntu packaged font rendering libraries). So you must get: a) precompiled package from Ubuntu-side (some ppa) b) compile yourself. 

That's the hard truth of it. I don't like the state of this and I think Ubuntu should provide firefox4, firefox5 etc themselves in their official repos along with current stable Firefox, which is defined by Ubuntu release.

---

### Post by vikramk.ibs on 2011-04-27
> **pqwoerituytrueiwoq said:**
> If you want to compile it your self go [here]("https://developer.mozilla.org/En/Simple_Firefox_build") (you will need to download around 100MB of files total)
If you want a ppa go [here]("http://www.webupd8.org/2011/03/install-firefox-4-in-ubuntu-1004-1010.html") ([about dialog screenshot]("http://i51.tinypic.com/vf8gm.png"))
If you want Mozilla's unmodified version this is for you with no risk to your installation this is for you

I went and made a sh script for it
This installs Mozilla's un-modified version 
I have attached it if you prefer download to copy/paste
This does NOT need root access
It will auto detect 32bit /64 bit and your language
It is installed in your normal user account this will allow it to auto-update
It is meant to be run from a terminal
It expects zenity, awk, and wget to be installed
*:arrow: **sudo apt-get install zenity awk wget*
Those are probably installed by default
Download or save this to install *[install_Latest_Stable_Firefox.sh]("http://ubuntuforums.org/attachment.php?attachmentid=186829&d=1300820376")*
Then run it with sh (I assume you saved it to your Downloads folder)
*:arrow: sh Downloads/*install_Latest_Stable_Firefox.sh

If you want to uninstall it just delete *.firefox* from your user folder and the icon it puts on your desktop

In simple terms all this does in download the correct firefox for your install from mozilla's ftp servers extract it and give you an icon
This script is comparable with any i686/x86_64 linux distro  others are comparable via manual download
```
#!/bin/sh
LOCAL=$(echo $LANG | awk '{ print substr( $0, 0, index($0,".")-1 ) }')
LOCAL=$(echo $LOCAL | awk '{ sub( /\_/, "-", $0); print }')
VER="latest"
cd $HOME
if [ ! `ls firefox-$VER.tar.bz2` ]; then # allows manual download
    wget "http://releases.mozilla.org/pub/mozilla.org/firefox/releases/$VER/linux-`uname -m`/$LOCAL/firefox-$VER.tar.bz2"
fi
if [ ! `ls firefox-$VER.tar.bz2` ]; then # make sure firefox if there to install
    echo "Failed to download firefox"
    echo "This is probally due to mozilla not offering firefox in $LOCAL"
    echo "Please download firefox $VER to your $HOME folder then run this script again"
    echo "http://releases.mozilla.org/pub/mozilla.org/firefox/releases/$VER/linux-`uname -m`/"
    exit 1
fi
tar -jxvf firefox-$VER.tar.bz2
mv firefox .firefox
rm firefox-$VER.tar.bz2
chmod +x .firefox/firefox
echo "[Desktop Entry]" > Desktop/Firefox4.desktop
echo "Categories=;" >> Desktop/Firefox4.desktop
echo "Comment=Browse the World Wide Web" >> Desktop/Firefox4.desktop
echo "Comment[en_US]=Browse the World Wide Web" >> Desktop/Firefox4.desktop
echo "Exec=$HOME/.firefox/firefox %u" >> Desktop/Firefox4.desktop
echo "Hidden=false" >> Desktop/Firefox4.desktop
echo "Icon=firefox" >> Desktop/Firefox4.desktop
echo "Name=Firefox 4" >> Desktop/Firefox4.desktop
echo "Terminal=false" >> Desktop/Firefox4.desktop
echo "Type=Application" >> Desktop/Firefox4.desktop
echo "Version=1.0" >> Desktop/Firefox4.desktop
chmod +x Desktop/Firefox4.desktop
zenity --info --text "Please update Firefox icons to point to:\n$HOME/.firefox/firefox"
if [ $(zenity --question --title="Open Firefox?" --text "Would you like to start using Firefox 4 now\nThis will close Firefox first by killing it's process"; echo $?) = "0" ]; then
    killall firefox-bin
    .firefox/firefox
fi
exit 0
```[IMG]http://i52.tinypic.com/2qvuykg.png[/IMG]
Firefox has theses requirements:

attached file is a plan text file not a archive
I will update this when Firefox 4 final comes out
[installFirefox4.sh]("http://ubuntuforums.org/attachment.php?attachmentid=186374&d=1300378066") is for RC1
[installFirefox4_RC2.sh]("http://ubuntuforums.org/attachment.php?attachmentid=186490&d=1300497488") is for RC2
[installFirefox4_FINAL.sh]("http://ubuntuforums.org/attachment.php?attachmentid=186814&d=1300804059") is for the final release of Firefox 4
[install_Latest_Stable_Firefox.sh]("http://ubuntuforums.org/attachment.php?attachmentid=186829&d=1300820376") is for the latest stable firefox
if you installed using that one just go to help->about in firefox it will update automatically
**USE THE FORTH FILE LISTED (install_Latest_Stable_Firefox.sh)**

Thanks, it works great with Firefox 4.0 final, except few changes in command

---


---
title: "Downgrade from Firefox 10 to 9"
date: 2012-02-06
forum: General Help
---

### Post by rusljam on 2012-02-06
Well. As always I’ve upgraded Firefox from 9 to 10. But in past it was from PPA of mozilla stable and now from main repository of ubuntu. And instead of working I had to see crash by crash of my preferred browser. This was when I decided to downgrade to 9. But in PPA from mozilla  there wasn‘t  already any version and in ubuntu repository only - 10, in others repositories from mozilla - only newest versions and no hint in Google about deb of firefox 9 for ubuntu. Here the how I’ve downgraded my Firefox.

There are two ways to do it (I suppose there are much but I’ll describe only two).
First (pretty simple): Download tar of Firefox 9 from [here]("http://mirrors.linux.edu.lv/mozilla.org/firefox/releases/9.0.1/")  for your system and language. Then extract it to any place of your home folder and you’ll be able to work with Firefox from folder where you’ve extracted it.
Second: (for integrate Firefox 9 into system).
1. Install Firefox 10 (if it wasn’t installed or was deleted)
2. Download tar of Firefox 9 from [here]("http://mirrors.linux.edu.lv/mozilla.org/firefox/releases/9.0.1/")  for your system and language.
3. Extract it to any place of your home folder.
4. Copy all files from Firefox 9 folder to /usr/lib/firefox-10.0 (you need to be superuser)

It’s done. Synaptic will think that Firefox installed in system is 10 (be careful with upgrades). Firefox will show you that it is 9 and ask you for an upgrade :-)

---

### Post by lovinglinux on 2012-02-07
I do not advise to follow the method described above. If you are experiencing such issues with Firefox 10, you should exhaust the possible solutions, like creating a clean profile, before deciding to downgrade.

With the new Mozilla release model, each new major version of Firefox (8, 9 , 10...) replaces the previous one completely and contain all security patches, which means it could be a security risk to use an old version.

If you really need to downgrade, download the binaries from Mozilla, as described, but extract the files to your home folder and launch Firefox from there until the problem with the version from the repositories is solved. There is no need to mess with Firefox system files.

---

### Post by pqwoerituytrueiwoq on 2012-02-07
i have had lots of crashes from the copy on the update servers but not from mozilla's copy 
here is a sh script to try that one DO NOT RUN AS ROOT
```
#!/bin/sh
VER="10.0"
LOCAL=$(echo $LANG | awk '{ print substr( $0, 0, index($0,".")-1 ) }')
LOCAL=$(echo $LOCAL | awk '{ sub( /\_/, "-", $0); print }')
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
```
save it to a file and open it with sh (or make it executable and run it)

---


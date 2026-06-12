---
title: "Reverting to Thunderbird v5: where and how?"
date: 2011-08-21
forum: General Help
---

### Post by Splat_NJ on 2011-08-21
I'd like to revert back to TBird v5. I've uninstalled v6, downloaded the thunderbird-5.0.tar.bz2 file but I've never installed using a tar.bz2 file.  All the directions I've read online are getting me nowhere. Is there some way I could retrieve a v5 .deb file from the repositories or can someone please tell me how to install from the tar.bz2 file? Thank you.

---

### Post by pqwoerituytrueiwoq on 2011-08-21
mozilla's .tar.bz2 are already compiled in there
just extract to a desir4ed location and run the thunderbird file inside

---

### Post by Splat_NJ on 2011-08-21
> **pqwoerituytrueiwoq said:**
> mozilla's .tar.bz2 are already compiled in there
just extract to a desir4ed location and run the thunderbird file inside

Thanks. I know I tried that and got something about executables.... I'll try it again.

---

### Post by Splat_NJ on 2011-08-21
OK, I extracted and placed the Thunderbird folder into my home folder.  Here's what I get when double-clicking on the "Thunderbird-bin" file "Could not display "/home/splat/thunderbird/thunderbird-bin. There is no application installed for executable files" . I can select an application or just hit "ok".  I right-clicked on the Thunderbird-bin file (I believe that's the Tbird main executable) and under Properties/Permissions I checked the "Allow executing file as program" but then double clicking on the tbird-bin file resulted in nothing happening at all.

---

### Post by pqwoerituytrueiwoq on 2011-08-21
there is a script called thunderbird that runs thunderbird-bin at least that is how it is with firefox

---

### Post by Splat_NJ on 2011-08-21
> **pqwoerituytrueiwoq said:**
> there is a script called thunderbird that runs thunderbird-bin at least that is how it is with firefox

I already tried running the "run-mozilla.sh" file but nothing happens. I tried it in terminal as well. I guess I'm just doing it wrong. I've tried everything I know and still can't get Tbird to run. The hell with this, I'll restore my whole Ubuntu OS from the beginning of this month. Thanks anyway.

---

### Post by pqwoerituytrueiwoq on 2011-08-26
wrong file see attachment
here is a install script (no root needed) will work with any version just edit line 4
```
#!/bin/sh
LOCAL=$(echo $LANG | awk '{ print substr( $0, 0, index($0,".")-1 ) }')
LOCAL=$(echo $LOCAL | awk '{ sub( /\_/, "-", $0); print }')
VER="5.0"
cd $HOME
if [ ! `ls thunderbird-$VER.tar.bz2` ]; then # allows manual download
    wget "http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/$VER/linux-`uname -m`/$LOCAL/thunderbird-$VER.tar.bz2"
fi
if [ ! `ls thunderbird-$VER.tar.bz2` ]; then # make sure thunderbird if there to install
    echo "Failed to download thunderbird"
    echo "This is probally due to mozilla not offering thunderbird in $LOCAL"
    echo "Please download thunderbird $VER to your $HOME folder then run this script again"
    echo "http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/$VER/linux-`uname -m`/"
    exit 1
fi
tar -jxvf thunderbird-$VER.tar.bz2
mv thunderbird .thunderbird
rm thunderbird-$VER.tar.bz2
chmod +x .thunderbird/thunderbird
echo "[Desktop Entry]" > Desktop/Thunderbird.desktop
echo "Categories=;" >> Desktop/Thunderbird.desktop
echo "Comment=Browse the World Wide Web" >> Desktop/Thunderbird.desktop
echo "Comment[en_US]=Browse the World Wide Web" >> Desktop/Thunderbird.desktop
echo "Exec=$HOME/.thunderbird/thunderbird/thunderbird %u" >> Desktop/Thunderbird.desktop
echo "Hidden=false" >> Desktop/Thunderbird.desktop
echo "Icon=thunderbird" >> Desktop/Thunderbird.desktop
echo "Name=Thunderbird" >> Desktop/Thunderbird.desktop
echo "Terminal=false" >> Desktop/Thunderbird.desktop
echo "Type=Application" >> Desktop/Thunderbird.desktop
echo "Version=1.0" >> Desktop/Thunderbird.desktop
chmod +x Desktop/Thunderbird.desktop
zenity --info --text "Please update Thunderbird icons to point to:\n$HOME/.thunderbird/thunderbird/thunderbird"
if [ $(zenity --question --title="Open Firefox?" --text "Would you like to start using Thunderbird now\nThis will close Thunderbird first by killing it's process"; echo $?) = "0" ]; then
    killall thunderbird-bin
    .thunderbird/thunderbird/thunderbird
fi
exit 0

```

---

### Post by Splat_NJ on 2011-08-27
> **pqwoerituytrueiwoq said:**
> wrong file
 see attachment here is a install script (no root needed) will work with any version just edit line 4

Thank you for this! I'm keeping it for future reference. FWIW, I restored a recent Remastersys backup and brought everything else back up to current except Tbird. Now all my Tbird extensions are working again. Thanks again.

---


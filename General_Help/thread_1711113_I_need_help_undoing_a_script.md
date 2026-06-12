---
title: "I need help undoing a script"
date: 2011-03-20
forum: General Help
---

### Post by TBruff15 on 2011-03-20
I installed a runescape thing with a script and I dont know how to undo the script. If you can help me please do so thank you 

The script is:export TMP="$(mktemp -d --tmpdir runescape.XXXXXXXXXXXXXX)" DEST="/usr/local/share/runescape" BIN="/usr/local/bin" RUN=$'/usr/bin/java -Djava.class.path=jagexappletviewer.jar -Dcom.jagex.config=\x68\x74\x74\x70://\x77\x77\x77.runescape.\x63\x6f\x6d/k=3/l=en/jav_config\x2e\x77\x73 jagexappletviewer /runescape/images'
echo "Using $TMP as temp dir, $DEST as destination and $BIN as binary dir"
sudo wget $'\x68\x74\x74\x70\x3a\x2f\x2f\x77\x77\x77\x2e\x72\x75\x6e\x65\x73\x63\x61\x70\x65\x2e\x63\x6f\x6d\x2f\x64\x6f\x77\x6e\x6c\x6f\x61\x64\x73\x2f\x72\x75\x6e\x65\x73\x63\x61\x70\x65\x2e\x6d\x73\x69\x3f\x32\x31\x30\x36\x30\x34' -O "$TMP/runescape.msi"
sudo 7z e -o"$TMP/rs_client" "$TMP/runescape.msi"
sudo 7z e -o"$TMP/rs_client" "$TMP/rs_client/rslauncher.cab"
sudo mkdir -p "$DEST" "$BIN"
sudo chmod 777 -R "$TMP/rs_client"
sudo mv "$TMP/rs_client/JagexAppletViewerJarFile."* "$DEST/jagexappletviewer.jar"
sudo mkdir "$DEST/images"
sudo mv "$TMP/rs_client/JagexAppletViewerPngFile" "$DEST/images/jagexappletviewer.png"
echo -e "#\!/bin/sh\ncd \"$DEST\" && $RUN " > "$TMP/runescape"
sudo mv "$TMP/runescape" "$BIN/runescape"
echo -e "[Desktop Entry]\nName=RuneScape\nComment=Start RuneScape\nType=Application\nExec=$RUN\nStartupNotify=true\nTerminal=false\nCategories=Game;\nPath=$DEST\nIcon=$DEST/images/jagexappletviewer.png" > "$TMP/runescape.desktop"
sudo mv "$TMP/runescape.desktop" /usr/share/applications/runescape.desktop
sudo chmod 755 "$BIN/runescape"
sudo chmod 755 /usr/share/applications/runescape.desktop
sudo rm "$TMP" -r 
exit

Thank you if i cant undo it I will have to reinstall ubuntu, and I really would rather not do that

---

### Post by Crusty Old Fart on 2011-03-23
> **TBruff15 said:**
> I installed a runescape thing with a script and I dont know how to undo the script. If you can help me please do so thank you 

Oh Man...this looks like one helluva charlie-foxtrot. But, after studying it for a while, it doesn't look like there's too much to undo it. I don't think it's as bad as it looks.

So...let's try this:
```

#!/bin/bash
sudo rm -rf /usr/local/share/runescape
sudo rm -rf /usr/local/bin/runescape
sudo rm -f /usr/share/applications/runescape.desktop
exit 0

```Hopefully, that will blow it all away unless I missed something.

By the way, what did this thing do, anyway?

Good luck,

Crusty

---


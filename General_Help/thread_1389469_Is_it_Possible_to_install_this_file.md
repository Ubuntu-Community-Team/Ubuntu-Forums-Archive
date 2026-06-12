---
title: "Is it Possible to install this file?"
date: 2010-01-24
forum: General Help
---

### Post by Linuxman. on 2010-01-24
I have download win2-7 theme pack from here ;
[http://gnome-look.org/content/show.php/Win2-7+Pack?content=113264](http://gnome-look.org/content/show.php/Win2-7+Pack?content=113264)

Archive containing two shell script. 1) install.sh 2)theme-apply.sh

I think,I can install this files directly.(with scripts)But somebody says that is not possible you must install singly.

Now I'm asking you,can I install theme directly?

---

### Post by jamesisin on 2010-01-24
Assuming you trust gnome-look.org (and I don't know who they are), they give instructions for installing the theme:

> just decompress this file and run "install.sh" to install this theme

If you post the contents of the shell script (install.sh) we can give you some idea what it's doing.  Copy this:

[NOPARSE]```
and past the script here
```[/NOPARSE]

(Also, when including large images such as in your original post, use the attach function (paper clip button) so the image doesn't break the page formatting.  You can change your original post into an attached image, but you have to click Go Advanced to get the paper clip button.)

---

### Post by Linuxman. on 2010-01-24
```
#!/bin/bash

cd "`dirname \"$0\"`"

echo "===================   INFORMATION   =============================="
echo "This script will install Win2-7 Pack."
echo "It will REWRITE other appications' icons, be sure to"
echo "know what you are doing..."
echo ""
echo "if you want to know what this script is going to do to your system"
echo "just open this file with your text editor and you'll find"
echo "commented every instruction, I hope you like it"
echo
echo "=================================================================="

sleep 5
echo
echo "Please insert root password or abort this operation by pressing Ctrl+C:"
echo ""
echo "Installing terminal server icons and theme..."
sudo cp -r tsclient  /usr/share/pixmaps/ 			#Copying to Terminal Server Directory
sleep 2
#echo "terminal server icon theme installed successfully!!"
echo ""

echo "Please choose the proper architecture for installing the correct Libia_ora-engine (necesary for gtk-theme)"
select OPCION in 32 64
  do
  if [ $OPCION ]; then
      echo "Chosen option: $OPCION Bits"
      sudo cp gtk2-engines/$OPCION/libia_ora.so /usr/lib/gtk-2.0/2.10.0/engines
      break
  else
      clear
      echo "Invalid option just select:"
      echo "- 1 for 32 Bits"
      echo "- 2 for 64 Bits"
  fi
done

sleep 2
#echo "libia-ora engines installed successfully!!"
echo ""
echo "installing icon theme"
rm -r ~/.icons/Win2-7  						#Removing older versions
tar jvxf icon-theme/Win2-7.tar.bz2				#Decompressing file
mv Win2-7 ~/.icons/Win2-7					#Moving folder to icon themes directory
sleep 2
#echo "win2-7 icons installed successfully!!.."
echo ""
echo "installing wallpaper..."
sudo cp -r backgrounds /usr/share/				#Copying to Wallpapers Folder
sudo chmod 777 /usr/share/backgrounds/Win2-7.jpg
sleep 2
#echo "Wallpaper installed successfully!!"
echo ""
echo "installing cursor theme..."
sudo cp -r cursor/aero-drop /usr/share/icons			#Copying to cursor's folder
sudo chmod -R 777 /usr/share/icons/aero-drop
sleep 2
#echo "cursor theme installed successfully!!.."
echo ""
echo "installing gtk-theme..."
sudo rm -r /usr/share/themes/Win2-7				#Removing older versions
sudo rm -r '/usr/share/themes/Win2-7 Original'
sudo rm -r /usr/share/themes/Win2-7Basic

sudo cp -r gtk-theme/Win2-7 /usr/share/themes			#Copying to Gtk folder themes
sudo cp -r 'gtk-theme/Win2-7 Original' /usr/share/themes
sudo cp -r gtk-theme/Win2-7Basic /usr/share/themes

sudo chmod -R 777 /usr/share/themes/Win2-7
sudo chmod -R 777 '/usr/share/themes/Win2-7 Original'
sudo chmod -R 777 /usr/share/themes/Win2-7Basic
sleep 2
#echo "gtk theme installed successfully!!.."
echo ""
echo "installing gnome-panel theme..."
sudo cp -r gnome-panel  /usr/share/
##sudo chmod 777 /usr/share/pixmaps/clock-calendar-icon.png
##sudo chmod 777 /usr/share/pixmaps/clock-map-location-current.png
##sudo chmod 777 /usr/share/pixmaps/clock-map-location-hilight.png
##sudo chmod 777 /usr/share/pixmaps/clock-map-location-marker.png
sleep 2
#echo "gnome-panel theme installed successfully!!"
echo ""
echo "installing gnome-center theme..."
sudo cp -r gnome-control-center  /usr/share/
sleep 2
#echo "gnome-control-center theme installed successfully!!"
echo ""
echo "installing sound theme..."
sudo cp -r sounds/Win2-7 /usr/share/sounds			#Copying theme sound
sudo chmod 777 /usr/share/sounds/Win2-7				#Applying permissions
sleep 2
#echo "gnome-control-center theme installed successfully!!"
echo ""

echo "installing emesene theme..."
sudo rm -r /usr/share/emesene/smilies/default			#Removing older version of smilies (that one contains .PNG files and this one .GIF)
sudo cp -r emesene  /usr/share/					#Installing all emesene theme
sudo chmod -R 777 /usr/share/emesene/smilies/default
sudo chmod -R 777 /usr/share/emesene/themes/default
sudo chmod -R 777 /usr/share/emesene/sound_themes/default
sleep 2
#echo "emesene theme installed successfully!!"
echo ""
echo "installing themes for emerald"
rm -r ~/.emerald/themes/Win2-7					#Removing older versions
rm -r "~/.emerald/themes/Win2-7 Original"
rm -r ~/.emerald/themes/Win2-7Basic
cp -r emerald-decoration/* ~/.emerald/				#Installing Newer version
sleep 2
#echo "emerald decoration theme installed successfully!!..."
echo ""
echo "installing nautilus patterns..."
sudo cp -r nautilus  /usr/share/
sleep 2
#echo "nautilus pattenrs installed successfully!!"
echo ""
echo "installing x-splash theme..."
sudo mv /usr/share/images/xsplash /usr/share/images/xsplash.old
sudo cp -r xsplash /usr/share/images
sudo chmod -R 777 /usr/share/images/xsplash
sleep 2 
#echo "xsplash theme installed successfully!!"
echo ""
echo "installing openoffice splash..."
sudo cp -r Openoffice/program /usr/lib/openoffice/
sleep 2 
#echo "xsplash openoffice installed successfully!!"

echo "setting new theme..."
./Theme-Apply.sh
echo ""
sleep 2
echo "enjoy this theme!! ;)"
sleep 3
```

---

### Post by Linuxman. on 2010-01-24
Any idea?

---

### Post by jamesisin on 2010-01-24
This script appears to install a theme.  It refers to another script:

echo "setting new theme..."
./Theme-Apply.sh

I don't know what that one does, but presumably it sets your current theme to the one you just installed.  You could remove those two lines and set your theme manually of course.

As to vouching for the site, you may want to do a little research on the Web to assure yourself thet they are legitimate and non-nefarious.

---

### Post by Linuxman. on 2010-01-24
Just extract file and install :D It's true.
Thanks.

---

### Post by jamesisin on 2010-01-24
Glad to be of service.

(Be sure to mark this thread as SOLVED under Thread Tools above.)

---


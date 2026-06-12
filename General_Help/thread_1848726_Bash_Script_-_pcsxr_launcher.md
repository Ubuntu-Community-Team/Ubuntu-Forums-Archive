---
title: "Bash Script - pcsxr launcher"
date: 2011-09-23
forum: General Help
---

### Post by inukaze on 2011-09-23
You must create a "folder"/"directory" or simbolyc link inside "/home/my_user/.pcsxr/" called "config" , and you must put the same name of file of "CD IMAGEN" , for example

if you game its : "Final Fantasy VII CD1.iso" , the must create a new sub-folder inside the "config" folder , called "Final Fantasy VII CD1" , and put there the files

"dfcdrom.cfg" , "dfinput.cfg" , "dfsound.cfg" .

For 2D Games you should use : 1 - "dfxvideo.cfg" or 2 - "gxvideo.cfg"
For 3D Games you should use : 3 - "PeopsMesaGL.cfg"

Copy to the "Config"/"Game Name" , the file called "pcsxr.cfg" and rename it to "Gamename" for example "Final Fantasy VII CD1.cfg" . and now , you can run games with my mini script :


Mini-Script - pcsxr-launcher :

```

[B]#!/bin/bash
filename="${1%.*}"
gamename="${filename##*/}"
basename="${filename##*/}"
gamedir="${basename%.*}"

# Copy the Config File for Emulator :
cd "$HOME/.pcsxr/config/$gamedir"
cp "$gamename.cfg" "$HOME/.pcsxr/"
cd "$HOME/.pcsxr"
mv "pcsxr.cfg" "pcsxr.cfg.bak"
mv "$gamename.cfg" "pcsxr.cfg"
echo " STEP 01 - Backup Original File & Replace it "

# Backup current cfgs plugins files
cd "$HOME/.pcsxr/plugins"
mv dfcdrom.cfg dfcdrom.cfg.bak
mv dfinput.cfg dfinput.cfg.bak
mv dfsound.cfg dfsound.cfg.bak
mv dfxvideo.cfg dfxvideo.cfg.bak
mv gpuPeopsMesaGL.cfg gpuPeopsMesaGL.cfg.bak
mv gxvideo.cfg gxvideo.cfg.bak
echo " STEP 02 - Backup current config files of plugins "

# Remove current cfgs plufins files
cd "$HOME/.pcsxr/plugins"
rm -rf dfcdrom.cfg
rm -rf dfinput.cfg
rm -rf dfsound.cfg
rm -rf gxvideo.cfg
rm -rf dfxvideo.cfg
rm -rf gpuPeopsMesaGL.cfg
echo " STEP 03 - Cleaned current config files of plugins "

# Using the Config Files for Plugins :
cd "$HOME/.pcsxr/config/$gamedir"

	if [ -e dfcdrom.cfg ] || [ -e dfinput.cfg ] || [ -e dfsound.cfg ]
	then
		cp -rf dfcdrom.cfg  "$HOME/.pcsxr/plugins"
		cp -rf dfinput.cfg  "$HOME/.pcsxr/plugins"
		cp -rf dfsound.cfg  "$HOME/.pcsxr/plugins"
	fi

	if  [ -e dfxvideo.cfg ]
	then
		cp -rf dfxvideo.cfg "$HOME/.pcsxr/plugins"
	fi
	if [ -e gxvideo.cfg ]
	then
		cp -rf gxvideo.cfg  "$HOME/.pcsxr/plugins"
	fi
	if [ -e gpuPeopsMesaGL.cfg ]
	then
		cp -rf gpuPeopsMesaGL.cfg "$HOME/.pcsxr/plugins"
	fi

echo " STEP 04 - Using config files for $gamedir "

# Begin Emulator & wait emulator exit :
echo " STEP 05 - Begin emulation of $gamedir "
pcsxr -slowboot -nogui -cdfile "$@"
wait $pid
# Finish Emulation

# Restore Files :
cd "$HOME/.pcsxr"
rm -rf pcsxr.cfg
mv pcsxr.cfg.bak pcsxr.cfg
echo " STEP 05 - Emulation of $gamedir finished "

# Remove current cfgs plufins files
cd "$HOME/.pcsxr/plugins"
rm -rf dfcdrom.cfg
rm -rf dfinput.cfg
rm -rf dfsound.cfg
rm -rf gxvideo.cfg
rm -rf dfxvideo.cfg
rm -rf gpuPeopsMesaGL.cfg


# Restore originals cfgs
mv dfcdrom.cfg.bak dfcdrom.cfg
mv dfinput.cfg.bak dfinput.cfg
mv dfsound.cfg.bak dfsound.cfg
mv gxvideo.cfg.bak gxvideo.cfg
mv dfxvideo.cfg.bak dfxvideo.cfg
mv gpuPeopsMesaGL.cfg.bak gpuPeopsMesaGL.cfg
echo " STEP 06 - Restoring original config files "[/B]

```

I Hope this , works , not only for me how "PS1 Game Launcher".

---

### Post by inukaze on 2011-10-19
I have made my own pre-configurations for Each Game , using "PCSX-R" SVN lastest version .

i put the "Folders" / "Directories" , inside /home/my_username/.pcsxr/config/

For Example Alien Resurrection must be located in

/home/my_username/.pcsxr/config/Alien Resurrection

And the ISO File , must be the same name of Folder "Alien Resurrection.iso" or ".bin" or some extension , i ever rename the extension to ".ps1"

You can download the files from : [**[CENTER]My Dropbox[/CENTER]**]("http://dl.dropbox.com/u/3164499/Linux/Emuladores/pcsxr-configs/index.html")

I Hope this help you with PCSXR

---


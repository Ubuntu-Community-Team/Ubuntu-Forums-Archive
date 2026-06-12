---
title: "gksu and  gksudo won't work correctly in my bash script"
date: 2011-06-20
forum: General Help
---

### Post by tux-world on 2011-06-20
whats problem in my script? gksu and  gksudo won't work correctly in my bash script !!
#!/bin/bash
# --------------------------------------------------
# Author: Mahdi Pishguy
# Homepage: [http://www.debian-ir.com/](http://www.debian-ir.com/)
#
#
# gutil is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
# --------------------------------------------------
#gconftool -s --type bool /apps/update-notifier/auto_launch false

while true; do
	MainMenu=$(zenity --list --width 550 --height 400 --title "Alachiq os administration utilities" --text "Please Enter Your Choice..."  --column "Choice" "Install VGA Driver" "Update XORG configuration for ouput video separator" "Force reload & reconfigure xorg(requires X restart OR System Reboot)" "Force reconfigure BootUp Alachiq(requires System Reboot)" "Automatically mark all known bad sectors" "Install Graphical boot of Alachiq os" "Update Boot loader Resolution" "Add Windows bootUp menu on GRUB/BURG" "Install PHP-GTK" "Enable/Disable Update notifier" "visit ONLINE alachiqOS support" "Quit Alachiq os administration utilities" );

	case $MainMenu in
	"Install VGA Driver")
		Vga=$(zenity --list --width 550 --height 400 --text "Which VGA Driver must be installing?" --column "VGA Driver" "nVidia" "Ati" "Unknow (such as Onboard or etc)");
		case $Vga in
		"nVidia")
			zenity --width=400 --height=100 \
				--info --title="Alachiq OS Proprietary Graphics Driver Offline Installer" \
				--text="This utility is meant for computers with poor or no internet connection AND you don't NEED running/useing apt-get update" \

			gksu -m 'Please enter your own password' cp /opt/restricted-drivers/nvidia*.deb /var/cache/apt/archives
				(
				echo "20" ; sleep 1
					sudo dpkg -i /var/cache/apt/archives/nvidia*.deb /var/cache/apt/archives
				echo "40" ; sleep 1
					sudo nvidia-xconfig
				) |
				zenity --progress \
				  --title="Installing nVidia video Driver" \
				  --text="Please wait for complete install and reconfigure xorg.conf (requires X restart)..." \
				  --percentage=0
		;;
		"Ati")
			zenity --width=400 --height=100 \
				--info --title="Alachiq OS Proprietary Graphics Driver Offline Installer" \
				--text="This utility is meant for computers with poor or no internet connection AND you don't NEED running/useing apt-get update" \


				(
				echo "10" ; sleep 1
					gksu cp /opt/restricted-drivers/bcmwl*.deb /var/cache/apt/archives
				echo "20" ; sleep 1
					sudo cp /opt/restricted-drivers/fglrx*.deb /var/cache/apt/archives
				echo "40" ; sleep 1
					sudo dpkg -i /var/cache/apt/archives/bcmwl*.deb 
				echo "60" ; sleep 1
					sudo dpkg -i /var/cache/apt/archives/fglrx*.deb 
				) |
				zenity --progress \
				  --title="Installing ATI video Driver" \
				  --text="Please wait for complete install (requires X restart)..." \
				  --percentage=0
		;;
		"Unknow (identifier Your Vga Driver)")
				(
				echo "20" ; sleep 1
					sh /usr/bin/video_info
				) |
				zenity --progress \
				  --title="Installing ATI video Driver" \
				  --text="Please wait for complete install (requires X restart)..." \
				  --percentage=0
		;;
		esac
	;;

	"Update XORG configuration for oouput video separator")
		exec gksu  sep_video
	;;

	"Force reconfigure BootUp Alachiq(requires System Reboot)")
		boot=$(zenity --list --width 550 --height 400 --text "Which Boot Loader Alachiq is installed?" --column "Boot Loader" "Grub" "Burg-Graphical Alachiq OS");
		case $boot in
			"Grub")
				(
				echo "20" ; sleep 1
					gksu update-grub
				) |
				zenity --progress \
				  --title="Reconfigure GRUB for Alachiq os" \
				  --text="Please reboot your system after configured..." \
				  --percentage=0
				
			;;
			"Burg-Graphical Alachiq OS")
				(
				echo "20" ; sleep 1
					gksu update-burg
				) |
				zenity --progress \
				  --title="Reconfigure Burg-Graphical of Alachiq os" \
				  --text="Please reboot your system after configured..." \
				  --percentage=0
				
			;;
		esac

	;;
	"visit ONLINE alachiq OS support")
		firefox [http://www.alachiq.debian-ir.com](http://www.alachiq.debian-ir.com)
	;;
	"Add Windows bootUp menu on GRUB/BURG")

		addwinpart=$(zenity --list --width 550 --height 400 --text "Which Boot Loader must be adding?" --column "Boot Loader" "Grub" "Burg-Graphical Alachiq OS");
		case $addwinpart in
			"Grub")
				(
				echo "20" ; sleep 1
					gksu echo "menuentry 'Microsoft Windows' --class os { insmod ntfs set root='(hd0,msdos0)' chainloader +1} " >> /boot/grub/grub.cfg
				) |
				zenity --progress \
				  --title="Reconfigure GRUB for Alachiq os" \
				  --text="Please reboot your system after configured..." \
				  --percentage=0
				
			;;
			"Burg-Graphical Alachiq OS")
				(
				echo "20" ; sleep 1
					gksudo -m 'passoed???' echo "menuentry 'Microsoft Windows' --class os { insmod ntfs set root='(hd0,msdos0)' chainloader +1} " >> /boot/burg/burg.cfg
				) |
				zenity --progress \
				  --title="Reconfigure Burg-Graphical of Alachiq os" \
				  --text="Please reboot your system after configured..." \
				  --percentage=0
				
			;;
		esac

	;;

	"Quit Alachiq os administration utilities")
	exit
	;;
	esac

done

---


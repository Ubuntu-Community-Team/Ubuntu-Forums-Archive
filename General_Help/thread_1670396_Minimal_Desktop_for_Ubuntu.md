---
title: "Minimal Desktop for Ubuntu"
date: 2011-01-18
forum: General Help
---

### Post by Chesamo on 2011-01-18
[SIZE="6"]This information is important. Read it and do not skip to the last post before you do.[/SIZE]

Some of you may have seen [this thread](http://ubuntuforums.org/showthread.php?t=1350592) from yesteryear (hard to believe I've been working on this for nearly two years!) and may have wondered why Karmic Koala is still relevant. Well, it's not. So I'm starting a new, generically-named thread for me to post the updates to my script.

Information on how to use this script can be found on my [project blog](http://minimal-desktop.blogspot.com/). A step-by-step guide can be found [here](http://minimal-desktop.blogspot.com/p/guide.html), or right below in this post.

[LIST=1][*]Download and burn a copy of the [Ubuntu Alternate Install CD](http://mirrors.xmission.com/ubuntu-cd/10.10/). (Note that you do not want the Desktop CD.) If you do not know how to burn an ISO file, click [here](https://help.ubuntu.com/community/BurningIsoHowto) for a guide.
[*]Once you have burned the CD, boot to it to begin the installation. For help booting to a CD, click here.
[*]Select the language for the boot CD. At the prompt, hit F4 to open up the installation modes. Select [FONT="Courier New"]Install a command-line system[/FONT]. Select [FONT="Courier New"]Install Ubuntu[/FONT].
[*]Select the default install language. This will be the language used on the final system.
[*]Select your location.
[*]Select No to disallow the installer from detecting your keyboard layout. Then, select the origin and layout of your keyboard.
[*]Ubuntu will now load a few modules. Let this run.
[*]Select a name for your computer.
[*]Ubuntu will try to guess your location based on your IP address. If this is correct, hit [FONT="Courier New"]Yes[/FONT]. Otherwise, hit [FONT="Courier New"]No[/FONT] and select your time zone.
[*]"Partitioning" is taking a hard drive and making it useable by an operating system. If you do not have anything on the drive, select [FONT="Courier New"]Guided - use entire disk[/FONT]. If you wish to install Ubuntu alongside Windows, select [FONT="Courier New"]Guided - resize...[/FONT]
[*]Confirm the partition changes. ***This is the point of no return. Be sure all of your settings are correct.***
[*]The base system will now be installed. This will take some time.
[*]Select a username. It cannot be [FONT="Courier New"]root[/FONT].
[*]Choose a password.
[*]Decide if you wish to encrypt your home directory. This is not necessary, but good for security. I generally leave this off.
[*]Enter your proxy information, or leave it blank for "no proxy".
[*]Ubuntu will now perform the majority of the base install. This could take some time.
[*]If you opted to wipe the disc earlier, you will be asked if you wish to install GRUB to the Master Boot Record (MBR). This is safe for clean installs.
[*]Ubuntu will ask if your system clock is set to UTC. If Linux is your only OS (as in, you performed a clean install), select [FONT="Courier New"]Yes[/FONT]. Otherwise, select [FONT="Courier New"]No[/FONT].
[*]Installation of the base Ubuntu system is complete. Press Enter to reboot, making sure to eject the CD.
[*]Log in at the command prompt. Note that on *NIX systems, your password will not show up as asterisks.
[*]Use the following command to download my script: [FONT="Courier New"]wget [http://minimal-desktop.sublevel21.com/latest-stable.sh](http://minimal-desktop.sublevel21.com/latest-stable.sh)[/FONT]
[*]Use the following command to make the script "executable" (that is, able to be run): [FONT="Courier New"]chmod +x latest-stable.sh[/FONT]
[*]Run the script by running the following command: [FONT="Courier New"]./latest-stable.sh[/FONT] ***(NOTE the period-slash in front of the script name. The script will not run without this.)***
[*]The installation is fairly straightforward. During the installation, the screen may go blank. This is normal. Hit the Space Bar to wake the screen back up.
[*]Once the install has completed, you should reboot your computer. Press [FONT="Courier New"]Y[/FONT] at the end of the script to do this.
[*]Congratulations! You now have a fully functional, minimal Ubuntu Desktop system.[/LIST]

---

### Post by Chesamo on 2011-01-19
Today's release, 10.10.2 "Attobuntu Update 2", sees many changes:
[LIST][*]Added support for Openbox and Blackbox
[*]Improved choice tree for *box segment: Now has all of the choices of the other sections (minus CUPS)
[*]Fixed the bug for rare moments when the script didn't terminate with a reboot
[*]Fixed the k/ubuntu-restricted-extras lockup bug[/LIST]
Here's the code:
```
#!/bin/bash
## Minimal Desktop for Ubuntu 10.10.2 "Attobuntu Update 2" by the Minimal Desktop Team
## Version 10.10.2-2011.01.18
## This script is licensed under GPL 3 (http://www.gnu.org/licenses/gpl-3.0.txt)
## http://ubuntu-minimal-desktop.blogspot.com/

if [ $UID -ne 0 ]; then
	sudo $0
	exit 0
else

	echo -e "Welcome to the Minimal Desktop for Ubuntu install script.\nI will now ask you some questions, to determine what software I should install.\nItems marked with an asterisk (*) are the default options.\nPress ENTER to continue."
	read dummy

	echo -e "Which desktop environment would you like to install? If you do not know what\nthis means just hit Enter.\n1. GNOME*\n2. KDE\n3. Flux/Black/Openbox"
	read de

	if [ "$de" = '2' ]; then

		echo -e "Which browser would you like to install?\n1. Rekonq*\n2. Firefox\n3. Chromium\n4. Opera"
		read browser

		echo -e "Which Instant Messaging client would you like to install?\n1. Kopete*\n2. Konversation\n3. None"
		read im

		echo -e "Which productivity suite would you like to install?\n1. K Office Suite*\n2. OpenOffice.org\n3. None"
		read office

		echo -e "Which e-mail client would you like to install?\n1. KMail*\n2. Thunderbird\n3. None"
		read email

		echo -e "Which media player would you like to install?\n1. Kaffeine*\n2. Amarok\n3. KPlayer\n4. VLC Media Player\n5. None"
		read player

		echo -e "Do you want to install restricted software, including Flash player\nand Java? [y*|n]"
		read restrict
		if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
			true
		elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
			echo "Do you want to enable DVD playback support? [y*|n]"
			read dvd
			if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
				true
			elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
				echo -e "WARNING: This format is restricted in some countries. Are you sure you wish\nto continue? [y*|n]"
				read dvd
			fi
		fi

		echo -e "Do you want to install printing support? [y*|n]"
		read printing

		echo -e "Installation will now begin. Please do not interrupt installation by powering\noff the machine, pressing Ctrl+C, or otherwise killing this process. Press ENTER\nto continue."
		read dummy

		echo -e "The following software was installed:\nX.org\nKDE\nLinux Sound base system\nk3b" > README

		echo "* Preparing the installation..."

		if [ "$browser" = '4' ]; then
			echo "deb http://deb.opera.com/opera/ stable non-free" >> /etc/apt/sources.list
			wget -o /dev/null -O - http://deb.opera.com/archive.key | apt-key add -
			echo -e "sleep 5m\nwget -O - http://deb.opera.com/archive.key | apt-key add -\nexit 0" > /etc/rc.local
		fi

		sed -i -e '/deb cdrom:/d' /etc/apt/sources.list
		sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
		apt-key adv --keyserver keyserver.ubuntu.com --recv 3E5C1192 > /dev/null
		aptitude update > /dev/null

		echo "* Updating the system..."
		aptitude -y safe-upgrade > /dev/null

		echo "* Installing X.org and the Linux Sound base system..."
		aptitude -y install alsa-utils xinit > /dev/null

		echo "* Installing KDE and other essentials..."
		sudo aptitude -y install kdm kdebase > /dev/null

		echo "* Installing some important software..."
		sudo aptitude -y install k3b kpackagekit kdeartwork kterm jockey-kde okular > /dev/null
		sudo aptitude -yR install kdeutils udev > /dev/null

		if [ "$browser" = '2' ]; then
			echo "* Installing Firefox..." && echo "Firefox" >> README
			aptitude -y install firefox > /dev/null
		elif [ "$browser" = '3' ]; then
			echo "* Installing Chromium..." && echo "Chromium" >> README
			aptitude -y install chromium-browser > /dev/null
		elif [ "$browser" = '4' ]; then
			echo "* Installing Opera..." && echo "Opera" >> README
			aptitude -y install opera > /dev/null
		elif [ -z "$browser" ] || [ "$browser" = '1' ]; then
			aptitude -y install rekonq > /dev/null
		fi
		

		if [ "$im" = '2' ]; then
			echo "* Installing Konversation..." && echo "Konversation" >> README
			aptitude -y install konversation > /dev/null
		elif [ "$im" = '3' ]; then
			true
		elif [ -z "$im" ] || [ "$im" = '1' ]; then
			echo "* Installing Kopete..." && echo "Kopete" >> README
			aptitude -y install kopete > /dev/null
		fi
		

		if [ "$office" = '2' ]; then
			echo "* Installing OpenOffice.org..." && echo -e "OpenOffice.org Suite:\n  Writer\n  Calc\n  Impress\n  Draw\n  Base" >> README
			aptitude -y install openoffice.org-writer openoffice.org-impress openoffice.org-calc openoffice.org-kde openoffice.org-style-oxygen > /dev/null
		elif [ "$office" = '3' ]; then
			true
		elif [ -z "$office" ] || [ "$office" = '1' ]; then
			echo "* Installing K Office Suite..." && echo -e "K Office suite:\n  KWord\n  KSpread\n  KPresenter" >> README
			aptitude -y install kword kspread kpresenter > /dev/null
		fi

		if [ "$email" = '2' ]; then
			echo "* Installing Thunderbird..." && echo "Thunderbird" >> README
			aptitude -y install thunderbird > /dev/null
		elif [ "$email" = '3' ]; then
			true
		elif [ -z "$email" ] || [ "$email" = '1' ]; then
			echo "* Installing KMail..." && echo "KMail" >> README
			aptitude -y install kmail > /dev/null
		fi

		if [ "$player" = '2' ]; then
			echo "* Installing Amarok..." && echo "Amarok" >> README
			aptitude -y install amarok > /dev/null
		elif [ "$player" = '3' ]; then
			echo "* Installing KPlayer..." && echo "KPlayer" >> README
			aptitude -y install kplayer > /dev/null
		elif [ "$player" = '4' ]; then
			echo "* Installing VLC Media Player..." && echo "VLC Media Player" >> README
			aptitude -y install vlc > /dev/null
		elif [ "$player" = '5' ]; then
			true
		elif [ -z "$player" ] || [ "$player" = '1' ]; then
			echo "* Installing Kaffeine..." && echo "Kaffeine" >> README
			aptitude -y install kaffeine > /dev/null
		fi

		if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
			true
		elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
			echo "* Installing restricted extras..." && echo "Kubuntu restricted extras" >> README
			aptitude -y install kbuntu-restricted-addons lame libavcodec-extra-52 libmp3lame0 unrar > /dev/null
			if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
					true
				elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
					echo "  DVD playback support" >> README
					ARCH="$(uname -m |grep 64)"
					if [ -z "$ARCH" ]; then
						wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
					else
						wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
					fi
				dpkg -i libdvdcss2.deb > /dev/null
				rm libdvdcss2.deb
			fi
		fi

		if [ "$printing" = 'n' ] || [ "$printing" = 'N' ]; then
			true
		elif [ -z "$printing" ] || [ "$printing" = 'y' ] || [ "$printing" = 'Y' ]; then
			echo "* Instlling the printing subsystem..." && echo "CUPS subsystem" >> README
			aptitude -y install cups system-config-printer-kde > /dev/null
		fi

		echo "* Performing some clean-up..."
		aptitude -yf install > /dev/null
		aptitude clean > /dev/null

	elif [ "$de" = '3' ]; then

		echo -e "Minimal Desktop for Ubuntu using *box is recommended for experienced Linux users\nonly. Are you sure you wish to continue? [y*|n]"
		read cont
		
		if [ "$cont" = 'n' ] || [ "$cont" = 'N' ]; then
			$0
			exit 0
		fi

		echo -e "Which *box environment would you like to install?\n1. Fluxbox*\n2. Openbox\n3. Blackbox"
		read boxenv

		echo -e "Which browser would you like to install?\n1. Midori*\n2. Arora\n3. Chromium"
		read browser

		echo -e "Which Instant Messaging client would you like to install?\n1. Ayttm*\n2. Instantbird\n3. None"
		read im

		echo -e "Which e-mail client would you like to install?\n1. Sylpheed*\n2. Claws\n3. None"
		read email

		echo -e "Which media player would you like to install?\n1. VLC*\n2. Audacious\n3. MPlayer\n4. Quod Libet\n5. None"
		read player

		echo -e "Do you want to install restricted software, including Flash player\nand Java? [y*|n]"
		read restrict
		if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
			true
		elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
			echo "Do you want to enable DVD playback support? [y*|n]"
			read dvd
			if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
				true
			elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
				echo -e "WARNING: This format is restricted in some countries. Are you sure you wish\nto continue? [y*|n]"
				read dvd
			fi
		fi

		echo -e "Installation will now begin. Please do not interrupt installation by powering\noff the machine, pressing Ctrl+C, or otherwise killing this process. Press ENTER\nto continue."
		read dummy

		echo -e "The following software was installed:\nX.org\nLinux Sound base system\nNedit" > README

		echo "* Preparing the installation..."

		sed -i -e '/deb cdrom:/d' /etc/apt/sources.list
		sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
		apt-key adv --keyserver keyserver.ubuntu.com --recv 3E5C1192 > /dev/null
		aptitude update > /dev/null

		echo "* Updating the system..."
		aptitude -y safe-upgrade > /dev/null
		
		echo "* Installing X.org and the Linux Sound base system..."
		aptitude -y install alsa-utils xinit > /dev/null

		if [ "$boxenv" = '2' ]; then
			echo "* Installing Openbox and other essentials..." && echo "Openbox" >> README
			aptitude -y install xdm openbox nedit > /dev/null
		elif [ "$boxenv" = '3' ]; then
			echo "* Installing Blackbox and other essentials..." && echo "Blackbox" >> README
			aptitude -y install xdm blackbox nedit > /dev/null
		elif [ -z "$boxenv" ] || [ "$boxenv" = '1' ]; then
			echo "* Installing Fluxbox and other essentials..." && echo "Fluxbox" >> README
			aptitude -y install xdm fluxbox eterm nedit > /dev/null
		fi

		if [ "$browser" = '2' ]; then
			echo "* Installing Arora..." && echo "Arora" >> README
			aptitude -y install arora > /dev/null
		elif [ "$browser" = '3' ]; then
			echo "* Installing Chromium..." && echo "Chromium" >> README
			aptitude -y install chromium-browser > /dev/null
		elif [ -z "$browser" ] || [ "$browser" = '1' ]; then
			echo "* Installing Midori..." && echo "Midori" >> README
			aptitude -y install midori > /dev/null
		fi
		
		if [ "$im" = '2' ]; then
			echo "* Installing Instantbird..." && echo "Instantbird" >> README
			aptitude -y install instantbird > /dev/null
		elif [ "$im" = '3' ]; then
			true
		elif [ -z "$im" ] || [ "$im" = '1' ]; then
			echo "* Installing Ayttm..." && echo "Ayttm" >> README
			aptitude -y install ayttm > /dev/null
		fi

		if [ "$email" = '2' ]; then
			echo "* Installing Claws..." && echo "Claws" >> README
			aptitude -y install claws-mail > /dev/null
		elif [ "$email" = '3' ]; then
			true
		elif [ -z "$email" ] || [ "$email" = '1' ]; then
			echo "* Installing Sylpheed..." && echo "Sylpheed" >> README
			aptitude -y install sylpheed > /dev/null
		fi

		if [ "$player" = '2' ]; then
			echo "* Installing Audacious..." && echo "Audacious" >> README
			aptitude -y install audacious > /dev/null
		elif [ "$player" = '3' ]; then
			echo "* Installing MPlayer..." && echo "MPlayer" >> README
			aptitude -y install mplayer > /dev/null
		elif [ "$player" = '4' ]; then
			echo "* Installing Quod Libet..." && echo "Quod Libet" >> README
			aptitude -y install quodlibet > /dev/null
		elif [ "$player" = '5' ]; then
			true
		elif [ -z "$player" ] || [ "$player" = '1' ]; then
			echo "* Installing VLC..." && echo "VLC" >> README
			aptitude -y install vlc > /dev/null
		fi

		if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
			true
		elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
			echo "* Installing restricted extras..." && echo "Ubuntu restricted extras" >> README
			aptitude -y install ubuntu-restricted-addons gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse libavcodec-extra-52 libmp4v2-0 unrar > /dev/null
			if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
				true
			elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
				echo "  DVD playback support" >> README
				sudo aptitude install -y libdvdread4 > /dev/null
				ARCH="$(uname -m |grep 64)"
				if [ -z "$ARCH" ]; then
					wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
				else
					wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
				fi
				dpkg -i libdvdcss2.deb > /dev/null
				rm libdvdcss2.deb
			fi
		fi

		echo "* Performing some clean-up..."
		aptitude -yf install > /dev/null
		aptitude clean > /dev/null

	elif [ -z "$de" ] || [ "$de" = '1' ]; then

		echo -e "Which browser would you like to install?\n1. Firefox*\n2. Epiphany\n3. Chromium\n4. Opera"
		read browser

		echo -e "Which Instant Messaging client would you like to install?\n1. Pidgin*\n2. Empathy IM\n3. None"
		read im

		echo -e "Which productivity suite would you like to install?\n1. GNOME Office Suite*\n2. OpenOffice.org\n3. None"
		read office

		echo -e "Which e-mail client would you like to install?\n1. Evolution*\n2. Thunderbird\n3. None"
		read email

		echo -e "Which media player would you like to install?\n1. Rhythmbox*\n2. Totem\n3. Banshee\n4. VLC Media Player\n5. None"
		read player

		echo -e "Which network connection tool would you like to install?\n1. GNOME Network Manager*\n2. Wicd\n3. None"
		read wireless

		echo -e "Do you want to install restricted software, including Flash player\nand Java? [y*|n]"
		read restrict
		if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
			true
		elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
			echo "Do you want to enable DVD playback support? [y*|n]"
			read dvd
			if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
				true
			elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
				echo -e "WARNING: This format is restricted in some countries. Are you sure you wish\nto continue? [y*|n]"
				read dvd
			fi
		fi

		echo -e "Do you want to install printing support? [y*|n]"
		read printing

		echo "Would you like to install some extra Ubuntu artwork and themes? [y*|n]"
		read theme

		echo -e "Installation will now begin. Please do not interrupt installation by powering\noff the machine, pressing Ctrl+C, or otherwise killing this process. Press ENTER\nto continue."
		read dummy

		echo -e "The following software was installed:\nX.org\nGNOME\nLinux Sound base system\nBrasero" > README

		echo "* Preparing the installation..."

		if [ "$browser" = '4' ]; then
			echo "deb http://deb.opera.com/opera/ stable non-free" >> /etc/apt/sources.list
			wget -o /dev/null -O - http://deb.opera.com/archive.key | apt-key add -
			echo -e "sleep 5m\nwget -O - http://deb.opera.com/archive.key | apt-key add -\nexit 0" > /etc/rc.local
		fi

		sed -i -e '/deb cdrom:/d' /etc/apt/sources.list
		sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
		apt-key adv --keyserver keyserver.ubuntu.com --recv 3E5C1192 > /dev/null
		aptitude update > /dev/null

		echo "* Updating the system..."
		aptitude -y safe-upgrade > /dev/null

		echo "* Installing X.org and the Linux Sound base system..."
		aptitude -y install alsa-utils xinit > /dev/null

		echo "* Installing GNOME and other essentials..."
		aptitude -y install gdm gnome-core gnome-themes-selected gnome-themes-ubuntu light-themes indicator-applet-session > /dev/null

		if [ "$wireless" = '2' ]; then
			echo "Wicd" >> README
			aptitude -y install wicd > /dev/null
		elif [ "$wireless" = '3' ]; then
			true
		elif [ -z "$wireless" ] || [ "$wireless" = '1' ]; then
			echo "GNOME Network Manager" >> README
			aptitude -y install network-manager-gnome > /dev/null
		fi

		echo "* Installing some important software..."
		aptitude -y install brasero file-roller gcalctool gdebi gnome-screensaver gnome-utils jockey-gtk update-manager evince > /dev/null

		if [ "$browser" = '2' ]; then
			echo "* Installing Epiphany..." && echo "Epiphany" >> README
			aptitude -y install epiphany-browser > /dev/null
		elif [ "$browser" = '3' ]; then
			echo "* Installing Chromium..." && echo "Chromium" >> README
			aptitude -y install chromium-browser > /dev/null
		elif [ "$browser" = '4' ]; then
			echo "* Installing Opera..." && echo "Opera" >> README
			aptitude -y install opera > /dev/null
		elif [ "$browser" = '5' ]; then
			true
		elif [ -z "$browser" ] || [ "$browser" = '1' ]; then
			echo "* Installing Firefox..." && echo "Firefox" >> README
			aptitude -y install firefox > /dev/null
		fi
		

		if [ "$im" = '2' ]; then
			echo "* Installing Empathy IM..." && echo "Empathy IM" >> README
			aptitude -y install empathy > /dev/null
		elif [ "$im" = '3' ]; then
			true
		elif [ -z "$im" ] || [ "$im" = '1' ]; then
			echo "* Installing Pidgin..." && echo "Pidgin" >> README
			aptitude -y install pidgin > /dev/null
		fi


		if [ "$office" = '2' ]; then
			echo "* Installing OpenOffice.org..." && echo -e "OpenOffice.org Suite:\n  Writer\n  Calc\n  Impress\n  Draw\n  Base" >> README
			aptitude -y install openoffice.org-writer openoffice.org-impress openoffice.org-calc openoffice.org-gtk openoffice.org-style-tango > /dev/null
		elif [ "$office" = '3' ]; then
			true
		elif [ -z "$office" ] || [ "$office" = '1' ]; then
			echo "* Installing GNOME Office Suite..." && echo -e "GNOME Office suite:\n  Abiword\n  Gnumeric" >> README
			aptitude -y install abiword gnumeric > /dev/null
		fi


		if [ "$email" = '2' ]; then
			echo "* Installing Thunderbird..." && echo "Thunderbird" >> README
			aptitude -y install thunderbird > /dev/null
		elif [ "$email" = '3' ]; then
			true
		elif [ -z "$email" ] || [ "$email" = '1' ]; then
			echo "* Installing Evolution..." && echo "Evolution" >> README
			aptitude -y install evolution > /dev/null
		fi

		if [ "$player" = '2' ]; then
			echo "* Installing Totem..." && echo "Totem" >> README
			aptitude -y install totem-gstreamer > /dev/null
		elif [ "$player" = '3' ]; then
			echo "* Installing Banshee..." && echo "Banshee" >> README
			aptitude -y install banshee > /dev/null
		elif [ "$player" = '4' ]; then
			echo "* Installing VLC Media Player..." && echo "VLC Media Player" >> README
			aptitude -y install vlc > /dev/null
		elif [ "$player" = '5' ]; then
			true
		elif [ -z "$player" ] || [ "$player" = '1' ]; then
			echo "* Installing Rhythmbox..." && echo "Rhythmbox" >> README
			aptitude -y install rhythmbox > /dev/null
		fi

		if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
			true
		elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
			echo "* Installing restricted extras..." && echo "Ubuntu restricted extras" >> README
			aptitude -y install ubuntu-restricted-addons gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse libavcodec-extra-52 libmp4v2-0 unrar > /dev/null
			if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
				true
			elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
				echo "  DVD playback support" >> README
				sudo aptitude install -y libdvdread4 > /dev/null
				ARCH="$(uname -m |grep 64)"
				if [ -z "$ARCH" ]; then
					wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
				else
					wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
				fi
				dpkg -i libdvdcss2.deb > /dev/null
				rm libdvdcss2.deb
			fi
		fi

		if [ "$printing" = 'n' ] || [ "$printing" = 'N' ]; then
			true
		elif [ -z "$printing" ] || [ "$printing" = 'y' ] || [ "$printing" = 'Y' ]; then
			echo "* Instlling the printing subsystem..." && echo "CUPS subsystem" >> README
			aptitude -y install cups system-config-printer-gnome > /dev/null
		fi

		if [ "$theme" = 'n' ] || [ "$theme" = 'N' ]; then
			true
		elif [ -z "$theme" ] || [ "$theme" = 'y' ] || [ "$theme" = 'Y' ]; then
			echo "* Instlling extra themes..." && echo "Extra GNOME themes" >> README
			aptitude -y install gnome-themes gnome-themes-extras gnome-theme-gilouche ubuntu-artwork > /dev/null
		fi

		echo "* Performing some clean-up..."
		aptitude -y -f install > /dev/null
		aptitude clean > /dev/null

	fi

	chmod a+rw README

	echo -e "\nIf there are any problems with this script, please send an email to:\nminimal-desktop-drivers@lists.launchpad.net\n\nIf you believe this script contains bugs, please report them in our Launchpad page:\nhttps://edge.launchpad.net/minimal-desktop-for-ubuntu\n\nThanks for using this script!" >> README

	echo -e "Congratulations! Minimal Desktop for Ubuntu has been installed. Please read\nthe README generated by this script, located in your home folder. It contains\nsome very important information.\n\nA reboot is required to use your new system.\nWould you like to reboot now? [y*|n]"
	read reboot

	if [ "$reboot" = 'n' ] || [ "$reboot" = 'N' ]; then
		true
	elif [ -z "$reboot"] || [ "$reboot" = 'y' ] || [ "$reboot" = 'Y' ]; then
		reboot
	fi

fi

exit 0
```

---


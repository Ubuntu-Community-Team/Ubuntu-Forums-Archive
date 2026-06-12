---
title: "ubuntu 9.10 touchpad taps"
date: 2009-11-11
forum: General Help
---

### Post by burakvarhan on 2009-11-11
Hello,

While I was using Ubuntu 9.04 I had this nice feature that the top-right corner of my touchpad was behaving as middle-button. Particularly on firefox it was opening the links in new tab.

However, I updated to 9.10 and that feature has gone! I did some search and learned that I need to modify xorg.conf but I am still using my old xorg.conf file. Then I installed gpointing-device-settings but still cannot fix it.

My xorg.conf file is below, Can somebody please help me to solve this issue.

Thanks

[COLOR="DarkRed"]

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	# Power saving mode
	Option		"DPMS"
	HorizSync       30 - 110
	VertRefresh     50 - 150
	#1280x800 @ 70.00 Hz (GTF) hsync: 58.31 kHz; pclk: 98.89 MHz
	Modeline "1280x800_70.00"  98.89  1280 1352 1488 1696  800 801 804 833  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Modes	"1280x800_70.00"
	EndSubSection
EndSection

[/COLOR]

---

### Post by mihai.ile on 2009-11-15
Hello.

try to do a 
> 
synclient -l


and check the value of RTCornerButton. It should be =2 for middle mouse.
If not, just type
> 
synclient RTCornerButton=2

and after that it works.

---

### Post by burakvarhan on 2009-11-19
Thank you very much mihai007. With your tips my problem has been solved.

---

### Post by mihai.ile on 2009-11-23
To make changes permanent:

Edit the .profile folder
> $ gedit ~/.profile
 and add 
> synclient RTCornerButton=2
to the end of it.

This is how mine looks:
> 
mihai007@mihai007-dell:~$ cat ~/.profile
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

synclient RTCornerButton=2
mihai007@mihai007-dell:~$ 



Then use
> $ sudo visudo
command and add
> MY_USERNAME_OVER_HERE ALL = NOPASSWD: /usr/bin/synclient
at the end of it, just make sure you put your username instead of MY_USERNAME_OVER_HERE. Then just hit "CTRL+X" then press "Y" to save the file as sudoers.tmp as suggested.
After a restart the middle mouse on corner continued to work perfectly

---

### Post by cascagrossa on 2009-12-15
Another way to make changes permanent is to let hal configure your XOrg.

Probabilly you already have the file "/etc/hal/fdi/policy/shmconfig.fdi", if not crate it.

Type in aterminal.
> gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi

Make it look like that:
> <?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="input.x11_driver" string="synaptics">
<merge key="input.x11_options.SHMConfig" type="string">True</merge>
<merge key="input.x11_options.RTCornerButton" type="string">2</merge>
</match>
</device>
</deviceinfo>

Reboot and be hapy:)

---

### Post by armageddon1 on 2010-02-21
I have the same problem but the solution suggested above does not work. RTCornerButton = 2 according to synclient -l, but nothing happens when I click at the RT corner.

---


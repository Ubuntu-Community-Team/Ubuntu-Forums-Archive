---
title: "Sakis3g causing system to crash? Log file in debug mode incomplete."
date: 2011-08-16
forum: General Help
---

### Post by New00Folder on 2011-08-16
Hi!

I'm running Ubuntu 10.10 (Linux 2.6.35) and my system crashes approx. once a month. Initially I was clueless about what was causing it, but I after a few crashes I had an idea that maybe Sakis3g (with all its waiting for modem-manager) was behind it. (All the crashes occurred while/just after using Sakis3g and sometimes it would be the only thing I was running.) So I started running it in debug mode and keeping a log file. I also made sure that it was the first thing I ran after starting up and nothing else beside it.

Today, as usual, I ran it and waited for the "/dev/ttyUSB3 being used by modem-manager" error. After that I'd have waited for a couple of minutes more and tried to connect (This is how it works.) but a few seconds later my system crashed. I have to use the power button after a system crash because "alt+sys rq" magic key doesn't work after crashing. (It is enabled and works fine when the system hasn't crashed.)

On restarting I found the log file incomplete. I ran Sakis script again to check for differences with the new log file. Waited for the error message and checked the log. It ran way ahead of the "crash-causing" log file.

Now I don't know what to do. Here is the log:-

The "crash-causing" incomplete log:-

```

-------------------------------------------
Sakis3G 0.2.0e running on DEBUG mode.
-------------------------------------------
Tue Aug 16 16:58:14 IST 2011
-------------------------------------------
Command line was: /tmp/sakis3gz.2257.sakis3g "connect" "--interactive" "--console" "--debug"
Running with PID: 2340
-------------------------------------------
Environment is:
COLORTERM='gnome-terminal'
DEBUG='on'
DESKTOP=''
DISPLAY=':0.0'
EXTRACTED='/tmp/sakis3gz.2257.sakis3g'
HOME='/home/voldemort'
IFS=' 	
'
LANG='en_IN'
LOGNAME='root'
LS_COLORS='rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:'
MEGZ='/home/voldemort/****/ModemKand/sakis3g'
MYVERSION='0.2.0e'
NOFUNCNAME='1'
OPTIND='1'
PATH='/bin:/sbin:/usr/bin:/usr/sbin'
PPID='2257'
PROVIDER='/home/voldemort/****/ModemKand/sakis3g'
PS1='# '
PS2='> '
PS4='+ '
PWD='/home/voldemort'
SHELL='/bin/bash'
SUDO_COMMAND='/home/voldemort/****/ModemKand/sakis3g connect --interactive --console --debug'
SUDO_GID='1000'
SUDO_UID='1000'
SUDO_USER='voldemort'
TERM='screen-bce'
TRAPS='cleanscreen '
USER='root'
USERNAME='root'
XAUTHORITY='/var/run/gdm/auth-for-voldemort-HQuNaR/database'
allargs='"connect" "--interactive" "--console" "--debug"'
binaryvariable='grep'
cutbin='/usr/bin/cut'
grepbin='/bin/grep'
interactive='yes'
lastverbosetext='Starting up'
me='/tmp/sakis3gz.2257.sakis3g'
printfbin='/usr/bin/printf'
sedbin='/bin/sed'
stick_to_console='yes'
trbin='/usr/bin/tr'
verbosecurrentcount='7'
whichbin='/bin/which'
-------------------------------------------
Will now proceed with Sakis3G execution.
-------------------------------------------
[02340] [16:58:14] Located "echo" within PATH (/bin/echo).
[02340] [16:58:14] Level 1 dependencies met.
[02340] [16:58:14] Dir "/bin" exists in PATH.
[02340] [16:58:14] Dir "/usr/bin" exists in PATH.
[02340] [16:58:14] Dir "/sbin" exists in PATH.
[02340] [16:58:14] Dir "/usr/sbin" exists in PATH.
[02340] [16:58:14] Done setting up PATH.
[02340] [16:58:14] Located "readlink" within PATH (/bin/readlink).
[02340] [16:58:14] My location is "/home/voldemort/****/ModemKand/sakis3g".
[02340] [16:58:14] Located "wc" within PATH (/usr/bin/wc).
[02340] [16:58:14] Located "cat" within PATH (/bin/cat).
[02340] [16:58:14] Located "tail" within PATH (/usr/bin/tail).
[02340] [16:58:14] Located "head" within PATH (/usr/bin/head).
[02340] [16:58:14] Located "sort" within PATH (/usr/bin/sort).
[02340] [16:58:14] Located "uniq" within PATH (/usr/bin/uniq).
[02340] [16:58:14] Located "ls" within PATH (/bin/ls).
[02340] [16:58:14] Located "setsid" within PATH (/usr/bin/setsid).
[02340] [16:58:14] Located "getent" within PATH (/usr/bin/getent).
[02340] [16:58:14] Located "ps" within PATH (/bin/ps).
[02340] [16:58:14] Located "chmod" within PATH (/bin/chmod).
[02340] [16:58:14] Located "chown" within PATH (/bin/chown).
[02340] [16:58:14] Located "touch" within PATH (/bin/touch).
[02340] [16:58

```

I don't have the "error-message but no system crash" log now but I'll post it later if someone wants to see it.

---

### Post by New00Folder on 2011-08-17
Two more consecutive crashes today. Here's what I hope to be the complete log file (just before crash).

```

-------------------------------------------
Sakis3G 0.2.0e running on DEBUG mode.
-------------------------------------------
Wed Aug 17 09:03:30 IST 2011
-------------------------------------------
Command line was: /tmp/sakis3gz.2188.sakis3g "connect" "--interactive" "--console" "--debug"
Running with PID: 2279
-------------------------------------------
Environment is:
COLORTERM='gnome-terminal'
DEBUG='on'
DESKTOP=''
DISPLAY=':0.0'
EXTRACTED='/tmp/sakis3gz.2188.sakis3g'
HOME='/home/voldemort'
IFS=' 	
'
LANG='en_IN'
LOGNAME='root'
LS_COLORS='rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:'
MEGZ='/home/voldemort/****/ModemKand/sakis3g'
MYVERSION='0.2.0e'
NOFUNCNAME='1'
OPTIND='1'
PATH='/bin:/sbin:/usr/bin:/usr/sbin'
PPID='2188'
PROVIDER='/home/voldemort/****/ModemKand/sakis3g'
PS1='# '
PS2='> '
PS4='+ '
PWD='/home/voldemort'
SHELL='/bin/bash'
SUDO_COMMAND='/home/voldemort/****/ModemKand/sakis3g connect --interactive --console --debug'
SUDO_GID='1000'
SUDO_UID='1000'
SUDO_USER='voldemort'
TERM='screen-bce'
TRAPS='cleanscreen '
USER='root'
USERNAME='root'
XAUTHORITY='/var/run/gdm/auth-for-voldemort-jlLul9/database'
allargs='"connect" "--interactive" "--console" "--debug"'
binaryvariable='grep'
cutbin='/usr/bin/cut'
grepbin='/bin/grep'
interactive='yes'
lastverbosetext='Starting up'
me='/tmp/sakis3gz.2188.sakis3g'
printfbin='/usr/bin/printf'
sedbin='/bin/sed'
stick_to_console='yes'
trbin='/usr/bin/tr'
verbosecurrentcount='7'
whichbin='/bin/which'
-------------------------------------------
Will now proceed with Sakis3G execution.
-------------------------------------------
[02279] [09:03:30] Located "echo" within PATH (/bin/echo).
[02279] [09:03:31] Level 1 dependencies met.
[02279] [09:03:31] Dir "/bin" exists in PATH.
[02279] [09:03:31] Dir "/usr/bin" exists in PATH.
[02279] [09:03:31] Dir "/sbin" exists in PATH.
[02279] [09:03:31] Dir "/usr/sbin" exists in PATH.
[02279] [09:03:31] Done setting up PATH.
[02279] [09:03:31] Located "readlink" within PATH (/bin/readlink).
[02279] [09:03:31] My location is "/home/voldemort/****/ModemKand/sakis3g".
[02279] [09:03:31] Located "wc" within PATH (/usr/bin/wc).
[02279] [09:03:31] Located "cat" within PATH (/bin/cat).
[02279] [09:03:31] Located "tail" within PATH (/usr/bin/tail).
[02279] [09:03:31] Located "head" within PATH (/usr/bin/head).
[02279] [09:03:31] Located "sort" within PATH (/usr/bin/sort).
[02279] [09:03:31] Located "uniq" within PATH (/usr/bin/uniq).
[02279] [09:03:31] Located "ls" within PATH (/bin/ls).
[02279] [09:03:31] Located "setsid" within PATH (/usr/bin/setsid).
[02279] [09:03:31] Located "getent" within PATH (/usr/bin/getent).
[02279] [09:03:31] Located "ps" within PATH (/bin/ps).
[02279] [09:03:31] Located "chmod" within PATH (/bin/chmod).
[02279] [09:03:31] Located "chown" within PATH (/bin/chown).
[02279] [09:03:31] Located "touch" within PATH (/bin/touch).
[02279] [09:03:31] Located "expr" within PATH (/usr/bin/expr).
[02279] [09:03:31] Located "seq" within PATH (/usr/bin/seq).
[02279] [09:03:31] Located "cp" within PATH (/bin/cp).
[02279] [09:03:31] Located "rm" within PATH (/bin/rm).
[02279] [09:03:31] Located "who" within PATH (/usr/bin/who).
[02279] [09:03:31] Located "mv" within PATH (/bin/mv).
[02279] [09:03:31] Located "basename" within PATH (/usr/bin/basename).
[02279] [09:03:31] Located "dirname" within PATH (/usr/bin/dirname).
[02279] [09:03:31] Level 2 dependencies met.
[02279] [09:03:31] Basic binaries are resolved.
[02279] [09:03:31] Parent process is: bash
[02279] [09:03:31] Running by user request.
[02279] [09:03:31] Person behind screen is voldemort.
[02279] [09:03:31] Configuration file /etc/default/sakis3g does not exist or is not readable.
[02279] [09:03:31] Configuration file /etc/sysconfig/sakis3g does not exist or is not readable.
[02279] [09:03:31] Loading system-wide configuration file /etc/sakis3g.conf.
/-------------------------------------------------------------------------------
[02279] [09:03:31] Will now display contents of: \'/etc/sakis3g.conf\'
/-------------------------------------------------------------------------------
OTHER=USBMODEM
USBMODEM=1c9e:9605
APN=bsnlnet
APN_USER=user
APN_PASS=pass
\-------------------------------------------------------------------------------
-rw-r--r-- 1 root root 74 2011-03-10 12:40 /etc/sakis3g.conf
\-------------------------------------------------------------------------------
[02279] [09:03:31] Configuration arguments are: "OTHER=USBMODEM" "USBMODEM=1c9e:9605" "APN=bsnlnet" "APN_USER=user" "APN_PASS=pass" 
[02279] [09:03:31] Parsing configuration value: OTHER=USBMODEM.
[02279] [09:03:31] Command line set variable OTHER to "USBMODEM".
[02279] [09:03:31] Parsing configuration value: USBMODEM=1c9e:9605.
[02279] [09:03:31] Command line set variable USBMODEM to "1c9e:9605".
[02279] [09:03:31] Parsing configuration value: APN=bsnlnet.
[02279] [09:03:31] Command line set variable APN to "bsnlnet".
[02279] [09:03:31] Parsing configuration value: APN_USER=user.
[02279] [09:03:31] Command line set variable APN_USER to "user".
[02279] [09:03:31] Parsing configuration value: APN_PASS=pass.
[02279] [09:03:31] Command line set variable APN_PASS to "pass".
[02279] [09:03:31] Finished loading file /etc/sakis3g.conf.
[02279] [09:03:31] Configuration file(s) loaded.
[02279] [09:03:31] Not using an X display due to stick-to-console variable.
[02279] [09:03:31] Selecting GUI.
[02279] [09:03:31] Unable to locate "dialog" within PATH.
[02279] [09:03:31] Located "whiptail" within PATH (/usr/bin/whiptail).
[02279] [09:03:31] whiptail selected as GUI.
[02279] [09:03:31] Locale en_IN found in environment.
[02279] [09:03:31] Reported locale is not UTF-8. Will not be using translations.
[02279] [09:03:31] Loaded default value for foldwrapping: 60
[02279] [09:03:31] Located "ifconfig" within PATH (/sbin/ifconfig).
[02279] [09:03:31] Root level dependencies met.
[02279] [09:03:31] Loading Usb-ModeSwitch device database.
[02279] [09:03:31] Embedded device database loaded.
[02279] [09:03:31] Switchable devices within embedded device database:
0421:0610 0471:1210 0471:1237 0482:024d 04e8:f000 057c:84ff 05c6:1000 05c6:2001 05c6:f000 072f:100d 0930:0d46 0ace:2011 0ace:20ff 0af0:6711 0af0:6731 0af0:6751 0af0:6771 0af0:6791 0af0:6811 0af0:6911 0af0:6951 0af0:6971 0af0:7011 0af0:7031 0af0:7051 0af0:7071 0af0:7111 0af0:7211 0af0:7251 0af0:7271 0af0:7301 0af0:7311 0af0:7361 0af0:7381 0af0:7401 0af0:7501 0af0:7601 0af0:7701 0af0:7801 0af0:7901 0af0:8200 0af0:8201 0af0:8300 0af0:8302 0af0:8304 0af0:8400 0af0:c031 0af0:c100 0af0:d013 0af0:d031 0af0:d033 0af0:d035 0af0:d055 0af0:d057 0af0:d058 0af0:d155 0af0:d157 0af0:d255 0af0:d257 0af0:d357 0b3c:c700 0fce:d0cf 0fce:d0e1 0fce:d103 1004:1000 1004:607f 1004:613a 1004:613f 1033:0035 106c:3b03 106c:3b06 1076:7f40 1199:0fff 1266:1000 12d1:1001 12d1:1003 12d1:101e 12d1:1414 12d1:1446 12d1:1520 12d1:1521 12d1:1557 1410:5010 1410:5020 1410:5030 1410:5031 1410:5041 148f:2578 16d8:6803 16d8:700a 16d8:f000 198f:bccd 19d2:0003 19d2:0026 19d2:0040 19d2:0053 19d2:0083 19d2:0101 19d2:0103 19d2:0115 19d2:1001 19d2:1007 19d2:1009 19d2:2000 19d2:fff5 19d2:fff6 1a8d:1000 1ab7:5700 1b7d:0700 1bbb:f000 1c9e:1001 1c9e:9200 1c9e:f000 1dd6:1000 1e0e:f000 1f28:0021 1fac:0130
[02279] [09:03:31] Switched devices within embedded device database:
0421:0612 0471:1206 0471:1234 04e8:6601 057c:8401 05c6:9000 072f:90cc 0930:0d45 0af0:6600 0af0:6701 0af0:6901 0b3c:c000 0b3c:c001 0b3c:c002 1004:6114 1004:6124 1004:6141 106c:3715 106c:3717 1076:7f00 1199:0017 1199:0018 1199:0019 1199:0020 1199:0021 1199:0022 1199:0024 1199:0026 1199:0027 1199:0028 1199:0029 1199:0112 1199:0120 1199:0218 1199:0220 1199:0224 1199:6802 1199:6803 1199:6804 1199:6805 1199:6808 1199:6809 1199:6812 1199:6813 1199:6815 1199:6816 1199:6820 1199:6821 1199:6822 1199:6832 1199:6833 1199:6834 1199:6835 1199:6838 1199:6839 1199:683a 1199:683b 1199:683c 1199:683d 1199:683e 1199:6850 1199:6851 1199:6852 1199:6853 1199:6855 1199:6856 1199:6859 1199:685a 1266:1002 1266:1003 1266:1004 1266:1005 1266:1006 1266:1007 1266:1008 1266:1009 1266:100a 1266:100b 1266:100c 1266:100d 1266:100e 1266:100f 1266:1011 1266:1012 12d1:1001 12d1:1003 12d1:1406 12d1:140c 12d1:141b 12d1:1464 12d1:1465 12d1:14a5 12d1:14ac 1410:4100 1410:4400 1410:6000 1410:6002 1410:7001 1410:7003 148f:9021 16d5:6502 16d8:6006 16d8:680a 198f:0220 19d2:0001 19d2:0002 19d2:0015 19d2:0016 19d2:0017 19d2:0022 19d2:0031 19d2:0037 19d2:0052 19d2:0055 19d2:0063 19d2:0064 19d2:0094 19d2:0104 19d2:0116 19d2:0124 19d2:0128 19d2:1003 19d2:1008 19d2:1010 19d2:fff1 19d2:ffff 1a8d:1002 1a8d:1009 1ab7:5731 1b7d:0001 1bbb:0000 1c9e:6061 1c9e:9000 1c9e:9063 1c9e:9202 1c9e:9603 1dbc:0005 1dd6:1002 1e0e:9000 1e0e:9200 1e0e:ce16 1e0e:cefe 1f28:0020 1fac:0131 1fe7:0100
[02279] [09:03:31] Embedded Usb-ModeSwitch device database contains 260 entries.
[02279] [09:03:31] Folder "/etc/usb_modeswitch.d" exists. Will check if it contains configuration files.
[02279] [09:03:31] Loading system supplied device database.
[02279] [09:03:31] Finished starting up.
[02279] [09:03:31] Loaded default value for pppint: ppp0
[02279] [09:03:31] Verbosing: 7% Locating device
[02279] [09:03:32] Fetching connected USB devices by using "/sys/bus/usb/devices".
[02279] [09:03:32] Connected USB devices are:
0408:13ba:LG Webcam
04f3:0230:USB+PS/2 Optical Mouse
0bda:0158:USB2.0-CRW
1c9e:9605:Modem Configuration
[02279] [09:03:32] Connected USB modems are:
1c9e:9605:Modem Configuration
[02279] [09:03:32] Autoselecting unique USB modem plugged: 1c9e:9605
[02279] [09:03:32] Setting up modem.
[02279] [09:03:32] We are root already. Proceeding.
[02279] [09:03:32] Setting up USB modem 1c9e:9605.
[02279] [09:03:32] Fetching connected USB devices by using "/sys/bus/usb/devices".
[02279] [09:03:32] Connected USB devices are:
0408:13ba:LG Webcam
04f3:0230:USB+PS/2 Optical Mouse
0bda:0158:USB2.0-CRW
1c9e:9605:Modem Configuration
[02279] [09:03:32] Located "lsusb" within PATH (/usr/bin/lsusb).
[02279] [09:03:32] Using information of lsusb to determine usable interfaces.
[02279] [09:03:32] USB Device 1c9e:9605 provides 1 interruptable endpoint(s).
[02279] [09:03:32] Interfaces collected from lsusb are: 3
[02279] [09:03:32] Collected 1 interface(s): 3
[02279] [09:03:32] Only one interface available. Will use that one unconditionally.
[02279] [09:03:32] Got valid USB interface 3 of USB modem "1c9e:9605".
[02279] [09:03:32] Device 1c9e:9605 sysfs dir found: /sys/bus/usb/devices/usb2/2-1
[02279] [09:03:32] Kernel provides AVOID_RESET_QUIRK for device 1c9e:9605.
[02279] [09:03:32] Succesfully enabled AVOID_RESET_QUIRK for device 1c9e:9605.
[02279] [09:03:32] Failed to enable AVOID_RESET_QUIRK for device 1c9e:9605.
[02279] [09:03:32] Device has storage part on interface #4.
[02279] [09:03:32] Device 1c9e:9605, provides storage interface #4.
[02279] [09:03:32] Device 1c9e:9605 sysfs dir found: /sys/bus/usb/devices/usb2/2-1
[02279] [09:03:32] Storage interface #4 is binded by usb_storage driver.
[02279] [09:03:32] Device 1c9e:9605 sysfs dir found: /sys/bus/usb/devices/usb2/2-1
[02279] [09:03:32] Information from sysfs:
USB Manufacturer: USB_Modem
USB Product:      Modem_Configuration
USB Serial:       1234567890ABCDEF
[02279] [09:03:32] Checking interface #4 of device 1c9e:9605.
[02279] [09:03:32] SCSI device is settled:
SCSI Vendor:      USBModem
SCSI Model:       Disk____________
SCSI Revision:    2.31
[02279] [09:03:32] No storage device(s) with inserted media exist. Safe to unlock HAL.
[02279] [09:03:32] Device 1c9e:9605 sysfs dir found: /sys/bus/usb/devices/usb2/2-1
[02279] [09:03:32] No driver attached to interface #3 of "1c9e:9605".
[02279] [09:03:32] Located "uname" within PATH (/bin/uname).
[02279] [09:03:32] No perfect match found for device "1c9e:9605".
[02279] [09:03:32] Will seek if exists a driver for other devices from vendor "1c9e".
[02279] [09:03:32] Found driver(s) for other devices of same vendor: option
[02279] [09:03:32] No information found for 1c9e within files/usb_devices.db database.
[02279] [09:03:32] Only one candidate, will use it unconditionally: option
[02279] [09:03:32] Verbosing: 14% Loading driver option
[02279] [09:03:33] Checking if module "option" is currently loaded.
[02279] [09:03:33] Module "option" is not currently loaded.
[02279] [09:03:33] Located "modprobe" within PATH (/sbin/modprobe).
[02279] [09:03:33] Attempting to load module "option".
[02279] [09:03:33] Loaded default value for SERIALDRIVERS: ftdi_sio ipaq safe_serial usbserial visor
/-------------------------------------------------------------------------------
[02279] [09:03:33] Will now run command: \'/sbin/modprobe option \'
/-------------------------------------------------------------------------------
\-------------------------------------------------------------------------------
[02279] [09:03:33] Command returned 0.
\-------------------------------------------------------------------------------
[02279] [09:03:33] Waiting for module to get loaded.
[02279] [09:03:33] Checking if module "option" is currently loaded.
[02279] [09:03:33] Module "option" is currently loaded and occupied.
[02279] [09:03:33] Checking if module "option" is currently loaded.
[02279] [09:03:33] Module "option" is currently loaded and occupied.
[02279] [09:03:33] Module "option" succesfully loaded.
[02279] [09:03:33] Device 1c9e:9605 sysfs dir found: /sys/bus/usb/devices/usb2/2-1
[02279] [09:03:33] Module "option" not yet attached to "1c9e:9605".
[02279] [09:03:33] Sent "1c9e 9605" to "/sys/module/option/drivers/usb-serial:option1/new_id".
[02279] [09:03:33] Device 1c9e:9605 sysfs dir found: /sys/bus/usb/devices/usb2/2-1
[02279] [09:03:33] Device 1c9e:9605 sysfs dir found: /sys/bus/usb/devices/usb2/2-1
[02279] [09:03:33] Module "option" attached to device "1c9e:9605".
[02279] [09:03:33] Driver "option" loaded for interface #3 of device "1c9e:9605".
[02279] [09:03:33] Verbosing: 21% Locating tty
[02279] [09:03:33] Device 1c9e:9605 sysfs dir found: /sys/bus/usb/devices/usb2/2-1
[02279] [09:03:33] Interface #3 sysfs dir is: /sys/bus/usb/devices/usb2/2-1/2-1:1.3
[02279] [09:03:33] Interface #3 tty string is: ttyUSB3/tty/ttyUSB3/dev:188:3
[02279] [09:03:33] Will check if "/dev/ttyUSB3" exists, or will create it with major 188 and minor 3.
[02279] [09:03:33] Device node "/dev/ttyUSB3" already exists.
[02279] [09:03:33] Found tty device node of interface #3 from device "1c9e:9605": /dev/ttyUSB3
[02279] [09:03:33] Nothing more to do for setting it up device "1c9e:9605".
[02279] [09:03:33] Modem is now setup and resides on /dev/ttyUSB3.
[02279] [09:03:33] Located "wvdial" within PATH (/usr/bin/wvdial).
[02279] [09:03:33] Located "chat" within PATH (/usr/sbin/chat).
[02279] [09:03:33] Verbosing: 28% Preparing modem
[02279] [09:03:33] Loaded default value for CHAT_ABORT_STRINGS: ABORT BUSY ABORT ERROR ABORT BLOCKED ABORT NOCARRIER
[02279] [09:03:33] Unknown command "STAGE0".
[02279] [09:03:33] Command "PROBEGSM" refers to AT commands: ATI OK 'AT+GCAP' OK 'AT+CGSN' OK
[02279] [09:03:33] Will send PROBEGSM commands to tty /dev/ttyUSB3: "" '\pAT' OK ATI OK 'AT+GCAP' OK 'AT+CGSN' OK '\pAT' OK
[02279] [09:03:33] We are root already. Proceeding.
[02279] [09:03:33] Device /dev/ttyUSB3 is not busy.

```

---


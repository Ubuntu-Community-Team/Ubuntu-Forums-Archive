---
title: "&quot;sudo apt-get autoclean&quot; broke permissions for filesystem"
date: 2011-11-30
forum: General Help
---

### Post by isisgrimalkin on 2011-11-30
Hello,

Thanks in advance for helping me. I ran "sudo apt-get autoclean" and it appears to have broken permissions for my entire filesystem.

Here's the output of the apt-get autoclean command:
```

Del kdebase-workspace-kgreet-plugins 4:4.6.5-0ubuntu1 [38.3 kB]
Del libkabc4 4:4.6.5-0ubuntu1 [262 kB]
Del kinfocenter 4:4.6.5-0ubuntu1 [458 kB]
Del libplasmaclock4b 4:4.6.5-0ubuntu1 [75.5 kB]
Del update-manager-kde 1:0.150.5 [7,632 B]
Del tzdata 2011l-0ubuntu0.11.04 [725 kB]
Del tzdata-java 2011j-0ubuntu0.11.04 [135 kB]
Del thunderbird-globalmenu 3.1.12+build1+nobinonly-0ubuntu0.11.04.1 [60.3 kB]
Del libkcal4 4:4.6.5-0ubuntu1 [336 kB]
Del tzdata-java 2011l-0ubuntu0.11.04 [140 kB]
Del kcalc 4:4.6.5-0ubuntu1 [116 kB]
Del libprocesscore4b 4:4.6.5-0ubuntu1 [43.1 kB]
Del kdelibs5-plugins 4:4.6.5-0ubuntu1 [905 kB]
Del libplasma-geolocation-interface4 4:4.6.5-0ubuntu1 [20.6 kB]
Del linux-headers-generic 2.6.38.12.27 [2,498 B]
Del libkntlm4 4:4.6.5-0ubuntu1 [30.0 kB]
Del libkwineffects1a 4:4.6.5-0ubuntu1 [79.0 kB]
Del libkfile4 4:4.6.5-0ubuntu1 [213 kB]
Del libsolidcontrol4a 4:4.6.5-0ubuntu1 [71.9 kB]
Del firefox-globalmenu 6.0.2+build2+nobinonly-0ubuntu0.11.04.1 [60.6 kB]
Del libkio5 4:4.6.5-0ubuntu1 [789 kB]
Del libsolidcontrolifaces4a 4:4.6.5-0ubuntu1 [25.2 kB]
Del kdegraphics-strigi-plugins 4:4.6.5-0ubuntu1 [51.2 kB]
Del tzdata 2011j-0ubuntu0.11.04 [630 kB]
Del update-manager-kde 1:0.150.4 [7,686 B]
Del firefox-globalmenu 6.0.1+build1+nobinonly-0ubuntu0.11.04.1 [60.5 kB]
Del libkdnssd4 4:4.6.5-0ubuntu1 [66.4 kB]
Del libkjsembed4 4:4.6.5-0ubuntu1 [306 kB]
Del libmailtransport4 4:4.6.5-0ubuntu1 [138 kB]
Del icedtea-plugin 1.1.1-0ubuntu1~11.04.1 [201 kB]
Del okular 4:4.6.5-0ubuntu1 [970 kB]
Del linux-image-generic 2.6.38.12.27 [2,514 B]
Del libkparts4 4:4.6.5-0ubuntu1 [113 kB]
Del libkpty4 4:4.6.5-0ubuntu1 [34.3 kB]
Del libkexiv2-9 4:4.6.5-0ubuntu1 [176 kB]
Del libkdeui5 4:4.6.5-0ubuntu1 [1,240 kB]
Del libkdcraw9 4:4.6.5-0ubuntu1 [178 kB]
Del libsyndication4 4:4.6.5-0ubuntu1 [182 kB]
Del flashplugin-nonfree 10.3.183.10ubuntu0.11.04.1 [1,772 B]
Del kstars-data 4:4.6.5-0ubuntu1 [10.9 MB]
Del libkmediaplayer4 4:4.6.5-0ubuntu1 [38.3 kB]
Del thunderbird 3.1.13+build1+nobinonly-0ubuntu0.11.04.1 [12.3 MB]
Del libkimap4 4:4.6.5-0ubuntu1 [135 kB]
Del kde-window-manager 4:4.6.5-0ubuntu1 [1,754 kB]
Del firefox-globalmenu 7.0.1+build1+nobinonly-0ubuntu0.11.04.1 [54.1 kB]
Del libkdewebkit5 4:4.6.5-0ubuntu1 [61.0 kB]                                              
Del libpowerdevilcore0 4:4.6.5-0ubuntu1 [70.7 kB]
Del ksysguard 4:4.6.5-0ubuntu1 [208 kB]
Del tzdata-java 2011k-0ubuntu0.11.04 [135 kB]
Del libsyncdaemon-1.0-1 1.6.2-0ubuntu1 [47.7 kB]
Del xul-ext-ubufox 0.9.2-0ubuntu0.11.04.1 [49.2 kB]
Del libweather-ion6 4:4.6.5-0ubuntu1 [20.4 kB]
Del kdm 4:4.6.5-0ubuntu1 [768 kB]
Del tor 0.2.2.32-1~natty+1 [1,040 kB]
Del kdelibs-bin 4:4.6.5-0ubuntu1 [191 kB]
Del xserver-xorg-video-intel 2:2.14.0-4ubuntu7.2 [243 kB]
Del ksnapshot 4:4.6.5-0ubuntu1 [276 kB]
Del firefox 7.0.1+build1+nobinonly-0ubuntu0.11.04.1 [17.2 MB]
Del libkunitconversion4 4:4.6.5-0ubuntu1 [95.9 kB]
Del libksignalplotter4 4:4.6.5-0ubuntu1 [41.7 kB]
Del update-manager-core 1:0.150.4 [165 kB]
Del tor-geoipdb 0.2.2.32-1~natty+1 [1,228 kB]
Del libkscreensaver5 4:4.6.5-0ubuntu1 [24.0 kB]
Del kdebase-workspace-data 4:4.6.5-0ubuntu1 [5,318 kB]
Del libkdesu5 4:4.6.5-0ubuntu1 [53.3 kB]
Del libkprintutils4 4:4.6.5-0ubuntu1 [29.3 kB]
Del libkcmutils4 4:4.6.5-0ubuntu1 [92.4 kB]
Del flashplugin-installer 11.0.1.152ubuntu0.11.04.1 [8,930 B]
Del libakonadi-kcal4 4:4.6.5-0ubuntu1 [11.2 kB]
Del libkutils4 4:4.6.5-0ubuntu1 [22.5 kB]
Del libkpimidentities4 4:4.6.5-0ubuntu1 [55.8 kB]
Del libkemoticons4 4:4.6.5-0ubuntu1 [42.6 kB]
Del libkmime4 4:4.6.5-0ubuntu1 [159 kB]
Del plasma-desktop 4:4.6.5-0ubuntu1 [555 kB]
Del linux-libc-dev 2.6.38-11.50 [804 kB]
Del apt-transport-https 0.8.13.2ubuntu4.2 [19.2 kB]
Del libkde3support4 4:4.6.5-0ubuntu1 [300 kB]
Del ksysguardd 4:4.6.5-0ubuntu1 [61.6 kB]
Del libplasma3 4:4.6.5-0ubuntu1 [843 kB]
Del libkidletime4 4:4.6.5-0ubuntu1 [38.7 kB]
Del libkworkspace4 4:4.6.5-0ubuntu1 [76.6 kB]
Del libknewstuff3-4 4:4.6.5-0ubuntu1 [153 kB]
Del apt 0.8.13.2ubuntu4.2 [2,116 kB]
Del libkhtml5 4:4.6.5-0ubuntu1 [1,893 kB]
Del klipper 4:4.6.5-0ubuntu1 [98.2 kB]
Del libkjsapi4 4:4.6.5-0ubuntu1 [240 kB]
Del tor 0.2.2.33-1~natty+1 [1,041 kB]
Del libnepomukutils4 4:4.6.5-0ubuntu1 [84.1 kB]
Del libkldap4 4:4.6.5-0ubuntu1 [79.9 kB]
Del linux-generic 2.6.38.12.27 [2,488 B]
Del libkrosscore4 4:4.6.5-0ubuntu1 [58.0 kB]
Del libakonadi-kmime4 4:4.6.5-0ubuntu1 [91.9 kB]
Del kdebase-workspace-bin 4:4.6.5-0ubuntu1 [2,141 kB]
Del ubuntuone-client 1.6.2-0ubuntu1 [45.7 kB]
Del libthreadweaver4 4:4.6.5-0ubuntu1 [52.5 kB]
Del tzdata 2011m-0ubuntu0.11.04 [629 kB]
Del kdepimlibs-kio-plugins 4:4.6.5-0ubuntu1 [231 kB]
Del libktexteditor4 4:4.6.5-0ubuntu1 [87.4 kB]
Del libkblog4 4:4.6.5-0ubuntu1 [89.4 kB]
Del libprocessui4a 4:4.6.5-0ubuntu1 [91.9 kB]
Del okular-extra-backends 4:4.6.5-0ubuntu1 [51.5 kB]
Del freespacenotifier 4:4.6.5-0ubuntu1 [32.8 kB]
Del plasma-scriptengine-python 4:4.6.5-0ubuntu1 [20.1 kB]
Del libkdecorations4 4:4.6.5-0ubuntu1 [49.0 kB]
Del libnepomuk4 4:4.6.5-0ubuntu1 [202 kB]
Del libplasmagenericshell4 4:4.6.5-0ubuntu1 [122 kB]
Del libknewstuff2-4 4:4.6.5-0ubuntu1 [133 kB]
Del flashplugin-nonfree 10.3.183.7ubuntu0.11.04.1 [1,772 B]
Del kdebase-workspace 4:4.6.5-0ubuntu1 [16.2 kB]
Del tzdata-java 2011m-0ubuntu0.11.04 [136 kB]
Del plasma-netbook 4:4.6.5-0ubuntu1 [170 kB]
Del flashplugin64-installer 11.0.1.129-0ubuntu0~sevenmachines1 [9,122 B]
Del libgpgme++2 4:4.6.5-0ubuntu1 [128 kB]
Del libksgrd4 4:4.6.5-0ubuntu1 [39.1 kB]
Del kamera 4:4.6.5-0ubuntu1 [53.5 kB]
Del libqgpgme1 4:4.6.5-0ubuntu1 [14.5 kB]
Del libtaskmanager4b 4:4.6.5-0ubuntu1 [94.4 kB]
Del libakonadi-kde4 4:4.6.5-0ubuntu1 [696 kB]
Del printer-applet 4:4.6.5-0ubuntu1 [32.2 kB]
Del kstars 4:4.6.5-0ubuntu1 [775 kB]
Del libkipi8 4:4.6.5-0ubuntu1 [35.1 kB]
Del libkxmlrpcclient4 4:4.6.5-0ubuntu1 [28.1 kB]
Del ark 4:4.6.5-0ubuntu1 [246 kB]
Del update-manager-core 1:0.150.5 [164 kB]
Del kdelibs5-data 4:4.6.5-0ubuntu1 [2,196 kB]
Del tzdata 2011k-0ubuntu0.11.04 [629 kB]
Del flashplugin-installer 10.3.183.7ubuntu0.11.04.1 [9,040 B]
Del libakonadi-kabc4 4:4.6.5-0ubuntu1 [11.5 kB]
Del firefox 6.0.2+build2+nobinonly-0ubuntu0.11.04.1 [17.4 MB]
Del libkcalcore4 4:4.6.5-0ubuntu1 [228 kB]
Del thunderbird-globalmenu 3.1.13+build1+nobinonly-0ubuntu0.11.04.1 [60.4 kB]
Del ubufox 0.9.2-0ubuntu0.11.04.1 [1,208 B]
Del libfreetype6-dev 2.4.4-1ubuntu2.1 [770 kB]
Del plasma-dataengines-workspace 4:4.6.5-0ubuntu1 [486 kB]
Del libokularcore1 4:4.6.5-0ubuntu1 [199 kB]
Del libsolid4 4:4.6.5-0ubuntu1 [239 kB]
Del python-ubuntuone-client 1.6.2-0ubuntu1 [210 kB]
Del libkresources4 4:4.6.5-0ubuntu1 [61.5 kB]
Del libkpimutils4 4:4.6.5-0ubuntu1 [35.9 kB]
Del openjdk-6-jdk 6b22-1.10.2-0ubuntu1~11.04.1 [11.1 MB]
Del plasma-widgets-workspace 4:4.6.5-0ubuntu1 [400 kB]
Del icedtea6-plugin 6b21.1.1-0ubuntu1~11.04.1 [934 B]
Del libkdecore5 4:4.6.5-0ubuntu1 [888 kB]
Del libkcalutils4 4:4.6.5-0ubuntu1 [119 kB]                                                  
Del kdoctools 4:4.6.5-0ubuntu1 [173 kB]
Del apt-utils 0.8.13.2ubuntu4.2 [223 kB]
Del libknotifyconfig4 4:4.6.5-0ubuntu1 [40.8 kB]
Del kwalletmanager 4:4.6.5-0ubuntu1 [335 kB]
Del flashplugin-installer 10.3.183.4ubuntu0.11.04.1 [9,110 B]
Del firefox 6.0.1+build1+nobinonly-0ubuntu0.11.04.1 [17.4 MB]
Del kdegraphics-libs-data 4:4.6.5-0ubuntu1 [146 kB]
Del thunderbird 3.1.12+build1+nobinonly-0ubuntu0.11.04.1 [12.3 MB]
Del libkholidays4 4:4.6.5-0ubuntu1 [133 kB]
Del libkephal4a 4:4.6.5-0ubuntu1 [23.6 kB]
Del libkontactinterface4 4:4.6.5-0ubuntu1 [35.4 kB]
Del libkatepartinterfaces4 4:4.6.5-0ubuntu1 [707 kB]
Del libkimproxy4 4:4.6.5-0ubuntu1 [44.0 kB]
Del libakonadi-contact4 4:4.6.5-0ubuntu1 [328 kB]
Del systemsettings 4:4.6.5-0ubuntu1 [206 kB]
Del flashplugin-installer 10.3.183.10ubuntu0.11.04.1 [8,934 B]
Del libmicroblog4 4:4.6.5-0ubuntu1 [17.0 kB]
Del libktnef4 4:4.6.5-0ubuntu1 [47.3 kB]
Del linux-libc-dev 2.6.38-12.51 [786 kB]
Del libkpimtextedit4 4:4.6.5-0ubuntu1 [27.6 kB]
Del libnepomukquery4a 4:4.6.5-0ubuntu1 [104 kB]
Del tor-geoipdb 0.2.2.33-1~natty+1 [1,244 kB]
Del gwenview 4:4.6.5-0ubuntu1 [1,788 kB]

```Which then caused me to start getting read-only file system errors:
```

isis@wintermute:~$ sudo apt-get autoremove
sudo: Can't open /var/lib/sudo/isis/2: Read-only file system
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

root@wintermute:/home/isis# stat .
  File: `.'
  Size: 16384           Blocks: 32         IO Block: 4096   directory
Device: 15h/21d Inode: 1703945     Links: 60
Access: (0700/drwx------)  Uid: ( 1000/    isis)   Gid: ( 1000/    isis)
Access: 2011-11-30 04:17:53.000000000 -0800
Modify: 2011-11-30 04:06:17.359872232 -0800
Change: 2011-11-30 04:06:17.359872232 -0800

```Which I then made a possible blunder (again) in trying to fix by doing:
```

root@wintermute:/home/isis# sudo chmod -R 0766 .
chmod: changing permissions of `./.config/akonadi/agent_config_akonadi_contacts_resource_2': 
Input/
output error
chmod: changing permissions of `./.config/akonadi/agent_config_akonadi_contacts_resource_2_ch
anges.
dat': Input/output error
chmod: changing permissions of `./.config/google-chrome/Safe Browsing Bloom_new': Input/outpu
t erro
r
chmod: changing permissions of `./.config/google-chrome/Safe Browsing Download_new': Input/ou
tput e
rror
chmod: changing permissions of `./.config/google-chrome/Safe Browsing Csd Whitelist_new': Inp
ut/out
put error
chmod: changing permissions of `./.local/share/akonadi/db_data/mysql.err': Input/output error
chmod: changing permissions of `./.cache/zeitgeist/daemon.log': Input/output error
chmod: changing permissions of `./.cache/google-chrome/Default/Cache/f_000643': Input/output 
error
chmod: changing permissions of `./.cache/google-chrome/Default/Cache/f_0005c0': Input/output 
error
chmod: changing permissions of `./.cache/google-chrome/Default/Cache/f_000642': Input/output 
error
root@wintermute:/home/isis# stat .
  File: `.'
  Size: 16384           Blocks: 32         IO Block: 4096   directory
Device: 15h/21d Inode: 1703945     Links: 60
Access: (0766/drwxrw-rw-)  Uid: ( 1000/    isis)   Gid: ( 1000/    isis)
Access: 2011-11-30 04:05:53.169872225 -0800
Modify: 2011-11-30 04:06:17.359872232 -0800
Change: 2011-11-30 04:19:29.119872516 -0800
root@wintermute:/home/isis# cat > oops
bash: oops: Read-only file system

```Please tell me this is recoverable! Please help! I was only able to pull the terminal output by ssh'ing to another box and copy/pasting text.

Here's the output of uname -a, and I use KDE for my GUI.
[CODE]
root@wintermute:/# uname -a
Linux wintermute 2.6.38-13-generic #52-Ubuntu SMP Tue Nov 8 16:53:51 UTC 2011 x86_64 x86_64 x
86_64 GNU/Linux
[CODE]

---

### Post by claracc on 2011-11-30
Commans sudo apt-get autoclean doesn't change permissions of filesystem.

What this command do is to delete .deb packages which releases are older than what you have installed. 

what are you trying to do?

Messing with permissions is a bad thing.

---

### Post by Orange_and_Green on 2011-11-30
This sounds to me like there is an error when the hard disk is mounted during boot, and the "errors=remount-ro" option in /etc/fstab kicks in.

This might be a hardware failure of the disk, or an integrity problem of the file system.

If I were you, I would:

a) Back up all important data ASAP, and then

b) follow yetiman64's advice on the last post of [this thread]("http://ubuntuforums.org/showthread.php?t=845912").

(EDIT: thinking about it again, if the file system is mounted as read-only, chances are the touch command proposed in the linked post will probably fail. In this case, your best bet would probably be booting from a live CD and running fsck on your hard disk from the live session. I still recommend backing up as the very first thing to do though)

Are there any error messages displayed during boot? What do the logs say? Did you do any changes to /etc/fstab?

Wish you the very best of luck,

O&G

---


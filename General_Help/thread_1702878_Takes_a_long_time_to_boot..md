---
title: "Takes a long time to boot."
date: 2011-03-08
forum: General Help
---

### Post by RobinJ1995 on 2011-03-08
When I first installed Mint (wich is based of Ubuntu for those of you who don't know it), it booted up in about 20 seconds.
Now it takes rather a long time in my opinion, must be at least 1 and a half minute. Also when I log in, it takes me a longer time than ever before to be presented with my desktop, and even longer to see the mintMenu button.
I've already tried to disable a few things using *bum*, but it doesn't help very much.
Could someone who knows what he's doing please take a look at my boot chart and advice me on how to speed up the boot process?
It's really starting to annoy me, as it seems to keeps slowing down with a few seconds by every day that passes.

[[img]http://www.imgdumper.nl/uploads4/4d766fa3c1e33/4d766fa35d4f0-LaptopVanRobin-julia-20110308-3.thumb.jpg[/img]](http://www.imgdumper.nl/uploads4/4d766fa3c1e33/4d766fa35d4f0-LaptopVanRobin-julia-20110308-3.png)

---

### Post by runeh76 on 2011-03-08
Hi 

Maybe ur Hard Disk is dieing..?

---

### Post by blueridgedog on 2011-03-08
Looks like a lot of IO wait.  What amount of memory, free disk space and swap do you have?

Memory:

```
free
```

Disk:

```
df
```

---

### Post by RobinJ1995 on 2011-03-08
> **runeh76 said:**
> Hi 

Maybe ur Hard Disk is dieing..?

This computer isn't even half a year old yet.


> **blueridgedog said:**
> Looks like a lot of IO wait.  What amount of memory, free disk space and swap do you have?

Memory:

```
free
```

Disk:

```
df
```

```
$ free
             total       used       free     shared    buffers     cached
Mem:       2059408    1994108      65300          0     610412     705524
-/+ buffers/cache:     678172    1381236
Swap:            0          0          0

$ df
Bstndsystm           1K-blokken Gebruikt Beschikbr Geb% Aangekoppeld op
/dev/sda6             18385004  17351380     99848 100% /
none                   1021444       320   1021124   1% /dev
none                   1029704      1088   1028616   1% /dev/shm
none                   1029704       432   1029272   1% /var/run
none                   1029704         0   1029704   0% /var/lock
/dev/sda5            110251008  89101486  21149522  81% /media/Data
/dev/sr0                 25796     25796         0 100% /media/Driver
/dev/sda1              7617500   7512500    105000  99% /media/WinXP
/dev/sda8             17667892   3535852  13234556  22% /media/e1d4fa8e-8a29-4367-9608-b2a39a4e02b1

```

---

### Post by blueridgedog on 2011-03-08
Looks like / is full.  Empty your trash and see if you can remove some large files files.

If you can't find the source of the disk filling up, then post the output of:

```
sudo du --max-depth=1 | sort -g
```

---

### Post by RobinJ1995 on 2011-03-08
> **blueridgedog said:**
> Looks like / is full.  Empty your trash and see if you can remove some large files files.

If you can't find the source of the disk filling up, then post the output of:

```
sudo du --max-depth=1 | sort -g
```

From my home folder:
```
$ sudo du --max-depth=1 | sort -g
du: kan geen toegang krijgen tot &#8216;./.gvfs&#8217;: Toegang geweigerd
4	./.aptoncd
4	./.crack-attack
4	./.gfceu
4	./.gnome2_private
4	./.hplip
4	./.mono
4	./.nautilus
4	./.utube
4	./.xine
4	./.xinput.d
8	./.avast
8	./Bureaublad
8	./.gtkdiskfree2
8	./.mplayer
8	./.qt
8	./.ssh
8	./.tuxtype
8	./.wallpapoz
12	./.avidemux
12	./.dbus
12	./.easytag
12	./.gtodo
12	./.links2
12	./.mission-control
12	./.qemu-launcher
12	./.supertux2
16	./.aptitude
16	./.dosbox
16	./.dvdcss
16	./.frozen-bubble
16	./.gegl-0.0
16	./.gnome-commander
16	./.lmms
16	./.netbeans-registration
16	./.supertuxkart
16	./.teamspeak2
16	./.vavoom
20	./.appdata
20	./.clamtk
20	./.lgames
20	./.mania_drive
20	./.mc
20	./.snes9x
20	./.tremulous
24	./.bloodfrontier
24	./.etracer
28	./.gnupg
28	./.hardinfo
32	./.burg-manager
32	./.easystroke
32	./.fceultra
32	./.stellarium
32	./.webapps
36	./.multisystem
36	./.pki
36	./.scorched3d
40	./.audacity-data
40	./.freemind
40	./.zsnes
44	./.amsn
48	./.subversion
76	./.Screenr
84	./.prboom
104	./.gconfd
152	./.Skype
204	./.gnome2
216	./.pulse
276	./.nexuiz
280	./.assaultcube_v1.04
284	./.fretsonfire
296	./.ts3client
308	./.fontconfig
340	./.torcs
400	./.java
412	./.macromedia
412	./.qemulator
416	./.mixxx
428	./WhatPulse
468	./.gimp-2.6
548	./.tuxpaint
604	./.logs
624	./.spumux
700	./.legends
724	./.rpmdb
776	./.compiz
972	./.purple
1160	./.opera
1280	./.openoffice.org
1340	./.linuxmint
1344	./.libreoffice
1520	./.fonts
1752	./.gstreamer-0.10
1920	./.adobe
2464	./.teamviewer
2572	./.gconf
2868	./.python-eggs
3488	./.warsow-0.5
4588	./.themes
4612	./.eclipse
6060	./.prism
6780	./.moovida
11380	./.TileRacer
12384	./.thumbnails
13884	./.smc
17432	./.winethemes
21092	./.dropbox
25684	./.dropbox-dist
32824	./.netbeans
39472	./.mozilla
44144	./.xchat2
47808	./.icons
53820	./.jdownloader
63852	./.jagex_cache_32
69160	./.kde
76888	./.minecraft
83180	./.teeworlds
83560	./.google
98584	./.maniadrive
114608	./.cache
170824	./.local
190656	./.config
199388	./.thunderbird
307356	./.winetrickscache
517280	./.PlayOnLinux
938052	./.wine
1824464	./Dropbox
5121804	.
```

From the filesystem's root folder:
```
$ sudo du --max-depth=1 | sort -g
du: kan geen toegang krijgen tot &#8216;./proc/14759/task/14759/fd/3&#8217;: Bestand of map bestaat niet
du: kan geen toegang krijgen tot &#8216;./proc/14759/task/14759/fdinfo/3&#8217;: Bestand of map bestaat niet
du: kan geen toegang krijgen tot &#8216;./proc/14759/fd/3&#8217;: Bestand of map bestaat niet
du: kan geen toegang krijgen tot &#8216;./proc/14759/fdinfo/3&#8217;: Bestand of map bestaat niet
du: kan geen toegang krijgen tot &#8216;./home/robin/.gvfs&#8217;: Toegang geweigerd
0	./proc
0	./sys
4	./mnt
4	./selinux
12	./.kde
16	./.local
16	./lost+found
180	./mint
200	./srv
232	./tmp
752	./.rpmdb
1080	./dev
2020	./build
6780	./bin
7248	./root
11908	./sbin
18976	./etc
110816	./boot
258820	./opt
371268	./lib
561660	./var
5121640	./home
10340428	./usr
100257145	./media
117071209	.

```

---

### Post by blueridgedog on 2011-03-08
Sorry, you need to change to the root directory first:

```
cd /
sudo du --max-depth=1 | sort -g
```

---

### Post by Snoman314 on 2011-03-08
I hav't used mint myself, so not sure what the normal disk use would look like, but from what I can see, you have an 18GB / partition, 5GB in your /home/ and 10GB in your /usr/ alone. Basically you need to delete some files and uninstall some programs. That sucker is full up!

---

### Post by runeh76 on 2011-03-08
Maybe ur Hard Disk is dieing..trash!   :D

---

### Post by blueridgedog on 2011-03-08
10 gig in /usr and 5 gig in /home.  The next step is to look in those and see if there is something you can delete or something that has gone awry.

```
cd /usr
sudo du --max-depth=1 | sort -g
```

Then

```
cd /home
sudo du --max-depth=1 | sort -g
```

I bet the excess files are going to be items in /usr.

---

### Post by RobinJ1995 on 2011-03-08
> **runeh76 said:**
> Maybe ur Hard Disk is dieing..trash!   :D
If you haven't got something to add to this topic except for common nonsense, then don't reply at all please ;)
This reply was already posted and my answer has not changed.


> **blueridgedog said:**
> 10 gig in /usr and 5 gig in /home.  The next step is to look in those and see if there is something you can delete or something that has gone awry.

```
cd /usr
sudo du --max-depth=1 | sort -g
```


```
$ sudo du --max-depth=1 | sort -g
12	./lib32
16	./etc
92	./lib64
53768	./sbin
81820	./games
112248	./include
185372	./src
311804	./local
462616	./bin
3392184	./lib
5740492	./share
10340428	.
```

> **blueridgedog said:**
> 
Then

```
cd /home
sudo du --max-depth=1 | sort -g
```


```
$ sudo du --max-depth=1 | sort -g
du: kan geen toegang krijgen tot &#8216;./.gvfs&#8217;: Toegang geweigerd
4	./.aptoncd
4	./.crack-attack
4	./.gfceu
4	./.gnome2_private
4	./.hplip
4	./.mono
4	./.nautilus
4	./.utube
4	./.xine
4	./.xinput.d
8	./.avast
8	./Bureaublad
8	./.gtkdiskfree2
8	./.mplayer
8	./.qt
8	./.ssh
8	./.tuxtype
8	./.wallpapoz
12	./.avidemux
12	./.dbus
12	./.easytag
12	./.gtodo
12	./.links2
12	./.mission-control
12	./.qemu-launcher
12	./.supertux2
16	./.aptitude
16	./.dosbox
16	./.dvdcss
16	./.frozen-bubble
16	./.gegl-0.0
16	./.gnome-commander
16	./.lmms
16	./.netbeans-registration
16	./.supertuxkart
16	./.teamspeak2
16	./.vavoom
20	./.appdata
20	./.clamtk
20	./.lgames
20	./.mania_drive
20	./.mc
20	./.snes9x
20	./.tremulous
24	./.bloodfrontier
24	./.etracer
28	./.gnupg
28	./.hardinfo
32	./.burg-manager
32	./.easystroke
32	./.fceultra
32	./.stellarium
32	./.webapps
36	./.multisystem
36	./.pki
36	./.scorched3d
40	./.audacity-data
40	./.freemind
40	./.zsnes
44	./.amsn
48	./.subversion
76	./.Screenr
84	./.prboom
96	./.gconfd
152	./.Skype
204	./.gnome2
216	./.pulse
276	./.nexuiz
280	./.assaultcube_v1.04
284	./.fretsonfire
296	./.ts3client
308	./.fontconfig
340	./.torcs
400	./.java
412	./.macromedia
412	./.qemulator
416	./.mixxx
428	./WhatPulse
468	./.gimp-2.6
548	./.tuxpaint
604	./.logs
624	./.spumux
700	./.legends
724	./.rpmdb
784	./.compiz
988	./.purple
1160	./.opera
1280	./.openoffice.org
1340	./.linuxmint
1344	./.libreoffice
1520	./.fonts
1752	./.gstreamer-0.10
1920	./.adobe
2464	./.teamviewer
2572	./.gconf
2868	./.python-eggs
3488	./.warsow-0.5
4588	./.themes
4612	./.eclipse
6060	./.prism
6780	./.moovida
9336	./Lmint
11380	./.TileRacer
13140	./.thumbnails
13884	./.smc
17432	./.winethemes
19916	./.dropbox
25684	./.dropbox-dist
32824	./.netbeans
39472	./.mozilla
44144	./.xchat2
47808	./.icons
53820	./.jdownloader
63852	./.jagex_cache_32
69160	./.kde
76888	./.minecraft
83180	./.teeworlds
83560	./.google
98584	./.maniadrive
121788	./.cache
170824	./.local
189260	./.config
199388	./.thunderbird
307356	./.winetrickscache
517280	./.PlayOnLinux
938052	./.wine
1824464	./Dropbox
5136304	.

```

> **blueridgedog said:**
> 
I bet the excess files are going to be items in /usr.

Also...if you edit a prior post with new information, those helping you do not see it as an update and might not check back.  it is better to post a new comment.
Ok :p

---

### Post by blueridgedog on 2011-03-08
> **ErJeeB said:**
> I did, I've posted the output of both /home/user/ and /.

Just saw it...

---

### Post by RobinJ1995 on 2011-03-08
> **blueridgedog said:**
> Just saw it...
Hadn't seen yet that you'd posted a message after that, and edited my post a little bit too late :p

---

### Post by lithopsian on 2011-03-08
Many things to look at in addition to the main one already mentioned.

Your machine is taking a long time to initially mount root.  Btrfs filesystem?  Is it normal?  I wouldn't have thought so.  Driver might be on the way out, or it might be a symptom of being full.

ureadahead is taking nearly 20 seconds, and it looks to be reading at a decent speed for that time.  How much stuff is it loading?  It doesn't even look to be loading all your desktop because that seems to be IO bound, from about the time compiz kicks in.  Is it doing something really dumb like reading a swap file?

You are starting an awful lot of applications on your desktop.  How are you defining when you are booted?  Are all those apps auto-started?  Can you kick some of them to later so you get your desktop quicker?

Dropbox is being a real hog.  I don't use it.  Is that normal?

Something is getting really hung up in the middle.  gnome-power-manager?  Or is that just an unlucky victim and something else is actually hung?

---

### Post by RobinJ1995 on 2011-03-08
> **lithopsian said:**
> Many things to look at in addition to the main one already mentioned.

Your machine is taking a long time to initially mount root.  Btrfs filesystem?  Is it normal?  I wouldn't have thought so.  Driver might be on the way out, or it might be a symptom of being full.

ureadahead is taking nearly 20 seconds, and it looks to be reading at a decent speed for that time.  How much stuff is it loading?  It doesn't even look to be loading all your desktop because that seems to be IO bound, from about the time compiz kicks in.  Is it doing something really dumb like reading a swap file?

You are starting an awful lot of applications on your desktop.  How are you defining when you are booted?  Are all those apps auto-started?  Can you kick some of them to later so you get your desktop quicker?

Dropbox is being a real hog.  I don't use it.  Is that normal?

Something is getting really hung up in the middle.  gnome-power-manager?  Or is that just an unlucky victim and something else is actually hung?

I've already disabled a bunch of startup applications, but it doesn't help a damn. Also, lately my system's been running much slower than usual, even after it's finally started.

---

### Post by lithopsian on 2011-03-08
Have you reprofiled ureadahead?  It may still be reading your entire disk even though half the stuff isn't running any more.  Boot is heavily IO limited on your machine (on most modern machines) so the only major gain (to the boot itself) will come from making ureadahead faster, either by reading less or by reading it faster.

All the desktop apps like Thunderbird, Pidgin, etc. don't look like they are profiled by ureadahead so they are just going to be slow.  If you don't consider the machine to be booted until all those apps are loaded then you probably want ureadahead to profile them.  If you consider the machine to be booted when you have a usable desktop then only profile up to that point.

A full disk will slow stuff down pretty badly.  Files fragment when the disk is full and everything gets slow.  Unfortunately freeing up disk space doesn't cure things immediately, but it will improve over time.

---

### Post by blueridgedog on 2011-03-08
I would look in /usr/lib and /usr/share, 3 gig and almost siz gig in there.  You can cd to the directories and do an ls or use the command I already posted as a way of seeing the size if directories.  Curious to know what is in /usr/share that is almost six gig.

I am certain that your issue is the full drive, but finding the unexpected files will take some looking...

---

### Post by RobinJ1995 on 2011-03-08
> **blueridgedog said:**
> I would look in /usr/lib and /usr/share, 3 gig and almost siz gig in there.  You can cd to the directories and do an ls or use the command I already posted as a way of seeing the size if directories.  Curious to know what is in /usr/share that is almost six gig.

I am certain that your issue is the full drive, but finding the unexpected files will take some looking...

```
 /usr/share $ sudo du --max-depth=1 | sort -g
4	./dotnet
4	./im-switch
4	./libsensors4
8	./adduser
8	./alien
8	./alsa-base
8	./apt
8	./binfmt-support
8	./debianutils
8	./desktopcouch
8	./e2fsprogs
8	./enchant
8	./foo2hiperc
8	./foo2hp
8	./foo2lava
8	./foo2oak
8	./foo2slx$ df
Bstndsystm           1K-blokken Gebruikt Beschikbr Geb% Aangekoppeld op
/dev/sda6             18385004  15893708   1557520  92% /

8	./foo2xqx
8	./gksu
8	./ifupdown
8	./imageshack-uploader
8	./indicator-application
8	./initscripts
8	./jackd
8	./jarwrapper
8	./java-config
8	./keyutils
8	./libvirtodbc0
8	./mono
8	./NetworkManager
8	./nvidia-common
8	./pidgin-ppa
8	./readline
8	./rsyslog
8	./sane
8	./ssl-cert
8	./sysv-rc
12	./base-passwd
12	./bridge-utils
12	./brltty
12	./bsd-mailx
12	./build-essential
12	./directfb-1.2.10
12	./gnome-sound-recorder
12	./gst-python
12	./indi
12	./initrd-tools
12	./iptables
12	./libgnomekbd
12	./linda
12	./linux-sound-base
12	./locales
12	./lupin-support
12	./man-db
12	./metacity
12	./mutter
12	./nvidia-current
12	./os-prober
12	./popularity-contest
12	./scilab-cli
12	./sgml-data
12	./unattended-upgrades
12	./vte
12	./xml-core
12	./xserver-xorg
12	./yorick-doc
16	./apturl
16	./avahi
16	./cmake
16	./firebird2.5-common
16	./gnupg
16	./libffado2
16	./lua
16	./mozilla
16	./mplayer
16	./mysql-common
16	./sgml-base
20	./binfmts
20	./cdrdao
20	./dpkg
20	./ecryptfs-utils
20	./et
20	./gnome-screenshot
20	./GraphicsMagick-1.3.12
20	./gstreamer-0.10
20	./lftp
20	./localechooser
20	./nautilus-share
20	./netpbm
20	./ppp
20	./tabset
20	./texlive-bin
24	./dpatch
24	./foomatic
24	./GConf
24	./gnome-menus
24	./gnome-session
24	./gnome-utils
24	./gtags
24	./indicators
24	./nfs-common
24	./pam-configs

24	./pnm2ppa
28	./acpi-support
28	./autofs5
28	./debconf
28	./gdict-1.0
28	./gnome-voice-control
28	./gweled
28	./jetty
28	./libgksu
28	./padevchooser
28	./xsessions
32	./dictionaries-common
32	./icu
32	./libparse-debianchangelog-perl
32	./ndisgtk
32	./tasksel
36	./base-files
36	./console-setup
36	./gnome-dictionary
36	./gnome-settings-daemon
36	./nautilus-sendto
36	./purple
36	./texinfo
40	./gnome-vpn-properties
40	./paprefs
40	./po-debconf
40	./ubuntu-sso-client
40	./ubuntu-system-adjustments
40	./vino
44	./autostart
44	./blends
44	./gcj
44	./nautilus-dropbox
44	./pam
44	./pycentral-data
44	./recovery-mode
44	./soprano
44	./w3m
48	./application-registry
48	./baobab
48	./bum
48	./gcr0
48	./keyrings

48	./language-support
48	./libdjconsole
48	./telepathy
48	./update-notifier
52	./applnk
52	./compizconfig
52	./gconf-editor
52	./gnome-keyring
52	./launchpad-integration
52	./mono-1.0
56	./computertemp
56	./devhelp
56	./pavucontrol
56	./usb-creator
60	./computer-janitor
60	./gdebi
60	./matchbox-keyboard
60	./screen-resolution-extra
64	./gfceu
64	./insserv
64	./pkgconfig
64	./prism
64	./vim
68	./gnome-background-properties
68	./gstreamer-properties
68	./librarian
72	./easymp3gain
72	./gnome-screensaver
72	./seed
80	./awk
80	./giver
84	./autodl
84	./lmbench
88	./modass
92	./gnome-bluetooth
92	./gv
92	./ladspa
92	./language-selector
96	./akonadi
96	./gvfs
96	./mousetweaks
96	./speech-dispatcher
100	./intltool-debian
108	./gnome-js
108	./texlive-base
108	./xawtv
112	./byobu
112	./consoletrans
112	./gdb
112	./gdm
116	./ant
116	./gnome-2.0
116	./gnome-mag
116	./libvisual-plugins-0.4
120	./nano
124	./glib-2.0
124	./libavogadro
124	./software-properties
128	./evolution-data-server-2.30
128	./pulseaudio
128	./python3
128	./vbam
128	./whereami
132	./camorama
132	./seabios
132	./soundconverter
136	./gnome-phone-manager
136	./rlwrap
140	./defoma
140	./graphviz
140	./VisualBoyAdvance
144	./gjs-1.0
144	./simple-ccsm
148	./ffmpeg
148	./python-apt
148	./zenity
152	./ncat
156	./vgabios
160	./gwget
160	./mibs
164	./ca-certificates-java
164	./gnome-sudoku
164	./mobile-broadband-provider-info
164	./servicetypes
164	./simple-scan
168	./aclocal-1.11
168	./rdesktop
172	./file-roller
172	./ImageMagick-6.6.2
172	./qemu
172	./wwwconfig-common
176	./myspell
180	./qemu-launcher
192	./common-licenses
196	./apt-xapian-index
196	./libtextcat
196	./PackageKit
196	./startupmanager
200	./cowsay
204	./alacarte
208	./deskbar-applet
208	./php5
208	./python
212	./gnome-nettool
212	./tomboy
216	./totem
228	./calendar
228	./xvidcap
232	./jockey
232	./update-manager
240	./paman
248	./aptoncd
252	./pitivi
260	./aspell
264	./gnome-terminal
264	./nautilus-actions
264	./tex-common
276	./python-wxgtk2.8
288	./nm-applet
292	./evince
296	./debhelper
308	./eog
312	./gtk-engines
312	./hardinfo
316	./glchess
316	./gnome-applets
320	./plplot5.9.5
324	./screen
328	./gnome-about
328	./gnome-doc-utils
328	./gtkhtml-3.14
328	./initramfs-tools
336	./gnupg2
344	./samba
344	./ufw
348	./emoticons
352	./adium
352	./computerjanitor
352	./desktop-directories
360	./gtkvncviewer
372	./idl
384	./gcalctool
388	./libindicator
388	./minitube
392	./djvu
396	./gufw
416	./alsa
436	./services
452	./doc-base
452	./strigi
464	./audacity
472	./firebird
492	./gnome-system-tools
492	./pyshared-data
504	./snmp
512	./onboard
512	./polkit-1
528	./transmission
536	./libthai
540	./emacs23
544	./gnome-panel
548	./boostbook
548	./winff
556	./seahorse
560	./mixxx-data
572	./f-spot
576	./apport
580	./qalculate
580	./system-tools-backends-2.0
604	./google-gadgets
612	./ca-certificates
668	./geany
672	./hyphen
676	./ontology
688	./aclocal
720	./cheese
728	./ubiquity
736	./libgphoto2
736	./misc
740	./ppd
744	./bleachbit
744	./python-support
748	./alarmclock
748	./stk
776	./nautilus
780	./gnome-media
784	./dbus-1
800	./cli-common
816	./media-player-info
824	./gnomebaker
828	./rhythmbox
840	./espeak-data
852	./menu
896	./moo
896	./pong2
920	./gnuplot
920	./omf
928	./libgweather
940	./thunderbird-locale-zh-cn
956	./thunderbird-locale-en-us
960	./thunderbird-locale-en-gb
972	./xscreensaver
992	./gtksourceview-2.0
992	./thunderbird-locale-nl
1008	./automake-1.11
1008	./qt3
1020	./gnome-shell
1076	./omf-langpack
1088	./libtool
1092	./yelp
1096	./glade3
1096	./rbot
1148	./synaptic
1156	./xplanet
1164	./javascript
1164	./sgml
1184	./namebench
1188	./branding
1196	./bug
1220	./pygobject
1232	./lirc
1268	./avogadro
1280	./consolefonts
1344	./couchdb
1408	./hwdata
1412	./brasero
1436	./foo2qpdl
1476	./gettext
1484	./lintian
1488	./openbabel
1524	./playonlinux
1536	./gnome-control-center
1556	./gapi-2.0
1564	./gwibber
1580	./mimelnk
1584	./gedit-2
1628	./gnome-packagekit
1668	./vlc
1672	./autoconf
1672	./hal
1716	./burg
1780	./guile
1812	./foo2zjs
1848	./mysql
1860	./gccxml-0.9
1904	./javazi
1912	./xmodmap
1960	./pygtk
1996	./yorick
2016	./mime-info
2088	./foxit
2088	./mc
2124	./software-center
2236	./qemulator
2324	./file
2368	./command-not-found
2492	./php
2544	./grub
2552	./gnome-power-manager
2552	./webkit-1.0
2660	./system-config-printer
2744	./aptitude
2800	./gconf
2816	./applications
2828	./ccsm
2860	./qt4
3044	./matplotlib
3256	./cmake-2.8
3316	./freemind
3516	./ibus-pinyin
3744	./themes
4060	./maven-repo
4460	./burg-manager
4552	./liblouis
4776	./octave
4788	./proj
4796	./teamspeak-client
4836	./gnome-games-common
4988	./groff
5124	./dict
5348	./GeoIP
5352	./mime
5524	./hunspell
5584	./X11
5624	./gutenprint
5640	./nmap
5772	./R
5808	./tuxguitar
6060	./gnome-games
6216	./tcltk
6224	./zoneinfo
6228	./i18n
6368	./cups
6500	./terminfo
6552	./lilypond
7096	./m17n
7136	./pixmaps
7228	./compiz
7512	./notify-osd
7600	./skype
7616	./sounds
7744	./gir-1.0
7744	./info
8356	./opencc
9300	./smplayer
9480	./ghostscript
9544	./wine
11100	./hplip
11412	./local-repository
11624	./pocketsphinx
12072	./locale
12592	./apps
12688	./fet
13084	./tuxtype
13888	./opera
14384	./festival
14880	./lmms
16028	./libreoffice
16228	./gtk-doc
16440	./perl5
16708	./mixxx
17264	./maxima
17724	./xml
18008	./perl
21144	./mythes
22140	./sphinx2
24216	./freemat
25608	./dbench
26156	./app-install
30268	./texmf-texlive
30460	./linuxmint
31896	./gambas2
32852	./midi
33948	./gimp
34476	./stellarium
34484	./gnome
35584	./eclipse
39792	./man
42492	./texmf
47312	./wallpapers
49076	./virtualbox
49212	./backgrounds
60676	./emacs
68660	./locale-langpack
69708	./tuxpaint
72700	./java
93884	./pyshared
98824	./netbeans
122576	./scilab
151292	./kde4
182744	./fonts
350628	./icons
1172472	./doc
2019932	./games
5740540	.

```

Think I should take a look inside /usr/share/games.

--EDIT--

Freed up some space... Made a few seconds difference.
[s]I think I may have solved the slow login problem, the mintMenu was being a bastard xD[/s] --> And it still is.

[[IMG]http://www.imageshack.us/thumbnail.png[/IMG]](http://img200.imageshack.us/i/laptopvanrobinjulia2011.png/)

Any other ideas...?

---

### Post by RobinJ1995 on 2011-03-10
... Anyone?

---

### Post by Jouke74 on 2011-03-10
Please make some more space in your root file system. Moving or deleting movie files, music, unused virtual machines and programs will go the quickest. 

You can use BleachBit to help you get rid of other unneeded stuff as well as deborphan. See this post for an excellent tutorial: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920). 

A second thing you can do is check your SMART values of your harddisk.
Go to Main Menu > System > Administration > Disk utility. 

Check your Harddrive speed as well as the SMART status, disk should be ok.

Be careful with both the cleaning as well as the Disk Utility because randomly selecting options and running stuff can seriously damage your Ubuntu install (een gewaarschuwt mens telt voor twee)! Backup the stuff of which you are not certain that they can be removed.

As a final step reprofile the boot.

---

### Post by simonmoon42 on 2011-03-10
Have you tried Ubuntu Tweak to get rid of old kernels and unnecessary install scripts... things like that?

---

### Post by troymius on 2011-03-10
I tried this:

> **sdennie said:**
> 
```

sudo rm /var/lib/ureadahead/*pack

```Then reboot twice (once to regenerate those files and twice to see if it fixed the problem).

... and it seems to help quite a bit. My computer now boots in 28 seconds (from hitting enter on grub to launching firefox... including my clumsy password typing.)

---

### Post by RobinJ1995 on 2011-03-11
> **Jouke74 said:**
> Please make some more space in your root file system. Moving or deleting movie files, music, unused virtual machines and programs will go the quickest. 
I've already freed up 2GB of my 20GB, all personal data is on a seperate partition, and I can't find any huge programs in synaptic.

> **Jouke74 said:**
> You can use BleachBit to help you get rid of other unneeded stuff as well as deborphan. See this post for an excellent tutorial: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920).
I already run BleachBit almost daily, I'll check out deborphan now.

> **Jouke74 said:**
> A second thing you can do is check your SMART values of your harddisk.
Go to Main Menu > System > Administration > Disk utility. 

Check your Harddrive speed as well as the SMART status, disk should be ok.
It's a new hard drive so there shouldn't be a problem with the speed of my hard drive I think, but I'll run a read-only benchmark to be sure...
Results:
* Minimum reading speed: 40,6 MB/s
* Maximum reading speed: 87,9 MB/s
* Avarage reading speed: 68,8 MB/s
* Avarage access time: 16,2 ms

> **Jouke74 said:**
> Be careful with both the cleaning as well as the Disk Utility because randomly selecting options and running stuff can seriously damage your Ubuntu install (een gewaarschuwt mens telt voor twee)! Backup the stuff of which you are not certain that they can be removed.
I know, it's the same with Windows, except that there you don't even have to do anything random, it will just generate random errors for you xD
> *[SIZE="2"]"Een gewaarschuwt man is er twee waard, een gewaarschuwd vrouw anderhalf."[/SIZE]*

> **Jouke74 said:**
> As a final step reprofile the boot.
You mean post a new bootchart? Ok.

---

### Post by RobinJ1995 on 2011-03-11
Lol you gotta be kidding me xD
Now it takes 5 seconds LONGER -.-

New bootchart:
[[IMG]http://www.imageshack.us/thumbnail.png[/IMG]](http://img851.imageshack.us/i/laptopvanrobinjulia2011.png/)

---


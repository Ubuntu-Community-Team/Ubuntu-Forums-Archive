---
title: "sudo dpkg"
date: 2009-08-13
forum: General Help
---

### Post by lotusalive on 2009-08-13
Would anyone happen to know how I might correct this Error Msg:

sol@sol-desktop:~$ sudo dpkg--configure -a
[sudo] password for sol: 
sudo: dpkg--configure: command not found
sol@sol-desktop:~$ sudo dpkg --configure -a
dpkg: failed to write status record about `computer-janitor' to `/var/lib/dpkg/status': No space left on device
sol@sol-desktop:~$

gparted says I have to unmount the / partition manually to increase its size from 18.7 GiB, which is full, and I do not know how to do.

---

### Post by bchurchill on 2009-08-13
The first command had the wrong syntax: you need the space between dpkg and --configure like you had the second time.  

The error message from the second command suggests your hard drive is out of space.  You may need to clear room or get a new drive.

---

### Post by lotusalive on 2009-08-13
It looks to be the root / partition only that is Full.  I have plenty of unallocated space to resize root /, but I will have to unmount it manually, and don't know how to do that. 

All info welcome, and thanks.

---

### Post by P4man on 2009-08-13
you can only unmount / if.. well, its not your current / :)
Easiest is booting of a livecd, then resize it from there.

---

### Post by lotusalive on 2009-08-13
o' so I've lost my install somehow ? ? ?  Not Again !  Yikes, what's happening...  I installed too much software, and that's what kills availability of dpkg to function ? ?:confused:

Could I perhaps trash some of the weirdly named tmp files from my File System to help alleviate 'full' / ? ?

---

### Post by P4man on 2009-08-13
nonono, im not telling you to reinstall :)
Just boot the live cd, run partition editor there (from systm > administration) and use it to grow your root partition on the harddisk.

Then reboot and all should be ok :)

---

### Post by lotusalive on 2009-08-13
A bit scary for me, to say the least !  But I'll try it. Thx P4man, so 
much !

---

### Post by P4man on 2009-08-13
you should be a bit scared, messing with partitions isn't without risk. but it seems you have no other option here.

Anyway, the livecd will let you browse the web, so if you have any questions while running partition editor, feel free to make a screenshot and post here from the live cd, before doing anything catastrophically wrong.

---

### Post by lotusalive on 2009-08-13
Am I going into the 'Install' part of the livecd for this partition change ?  Or, am I going to 'Try Ubuntu Without Changes to your System' part of livecd ?  Either way, it seems I won't be able to make any changes ? ? :confused:

Nevermind I'm in and fiddling with Partition Editor

eek, the Unallocated Partition will ONLY assign as 'Primary' (no Logical option highlighted) in ext3, confusing. Should I let it BE 'Primary,' in order to move home and then resize root ?

---

### Post by wfp on 2009-08-13
You could run in terminal df -h /var to see if your root is full. Are you running backups of any kind? You can run from a terminal du -h /var will show you what is using up all your space if indeed it is full.

---

### Post by P4man on 2009-08-13
> **lotusalive said:**
> 
eek, the Unallocated Partition will ONLY assign as 'Primary' (no Logical option highlighted) in ext3, confusing. Should I let it BE 'Primary,' in order to move home and then resize root ?

can you post a screenshot ?
i wouldnt create a new partition, it will just make things harder and may mess up your boot. Moving and resizing sounds like a better idea, but Id like to see it

---

### Post by slakkie on 2009-08-13
Maybe the tips in this thread will help you clean some bits and pieces:

[http://ubuntuforums.org/showthread.php?t=1238309](http://ubuntuforums.org/showthread.php?t=1238309)

---

### Post by lotusalive on 2009-08-13
Yes, keeping 2 weeks of back-ups. Partition Editor and gparted both show / as 'full.'

ubuntu@ubuntu:~$ df -h /var
Filesystem            Size  Used Avail Use% Mounted on
rootfs                500M   35M  465M   7% /
ubuntu@ubuntu:~$


Also:
ubuntu@ubuntu:~$ du -h /var
0	/var/tmp
du: cannot read directory `/var/spool/cups': Permission denied
0	/var/spool/cups
0	/var/spool/anacron
du: cannot read directory `/var/spool/cron/atjobs': Permission denied
0	/var/spool/cron/atjobs
du: cannot read directory `/var/spool/cron/atspool': Permission denied
0	/var/spool/cron/atspool
du: cannot read directory `/var/spool/cron/crontabs': Permission denied
0	/var/spool/cron/crontabs
0	/var/spool/cron
11K	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
0	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry
12K	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
0	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
0	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
0	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
0	/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
23K	/var/spool/openoffice/uno_packages/cache/registry
12K	/var/spool/openoffice/uno_packages/cache/uno_packages/fjNhrO_
12K	/var/spool/openoffice/uno_packages/cache/uno_packages
48K	/var/spool/openoffice/uno_packages/cache
48K	/var/spool/openoffice/uno_packages
48K	/var/spool/openoffice
48K	/var/spool
0	/var/crash
4.0K	/var/run/console
4.0K	/var/run/ConsoleKit
8.0K	/var/run/hald
du: cannot read directory `/var/run/cups/certs': Permission denied
0	/var/run/cups/certs
8.0K	/var/run/cups
8.0K	/var/run/avahi-daemon
4.0K	/var/run/dbus
8.0K	/var/run/klogd
du: cannot read directory `/var/run/PolicyKit': Permission denied
0	/var/run/PolicyKit
0	/var/run/screen
0	/var/run/pppconfig
4.0K	/var/run/network
96K	/var/run
0	/var/lib/xkb
20K	/var/lib/acpi-support
du: cannot read directory `/var/lib/gdm': Permission denied
0	/var/lib/gdm
4.0K	/var/lib/dbus
4.0K	/var/lib/urandom
0	/var/lib/apt/lists/partial
11M	/var/lib/apt/lists
7.0K	/var/lib/apt/keyrings
0	/var/lib/apt/mirrors/partial
0	/var/lib/apt/mirrors
0	/var/lib/apt/periodic
11M	/var/lib/apt
6.0K	/var/lib/x11
48K	/var/lib/belocs
7.0K	/var/lib/locales/supported.d
7.0K	/var/lib/locales
64K	/var/lib/gconf/debian.defaults
64M	/var/lib/gconf/defaults
64M	/var/lib/gconf
24M	/var/lib/dpkg/info
2.5K	/var/lib/dpkg/triggers
0	/var/lib/dpkg/updates
36K	/var/lib/dpkg/alternatives
0	/var/lib/dpkg/parts
29M	/var/lib/dpkg
0	/var/lib/NetworkManager
du: cannot read directory `/var/lib/PolicyKit': Permission denied
0	/var/lib/PolicyKit
0	/var/lib/PolicyKit-public
0	/var/lib/alsa
0	/var/lib/apparmor
8.8M	/var/lib/apt-xapian-index/index.1
8.8M	/var/lib/apt-xapian-index
0	/var/lib/aptitude
3.4M	/var/lib/aspell
0	/var/lib/avahi-autoipd
1.0K	/var/lib/binfmts
109K	/var/lib/defoma/fontconfig.d
0	/var/lib/defoma/gs.d/dirs/CMap
23K	/var/lib/defoma/gs.d/dirs/fonts
23K	/var/lib/defoma/gs.d/dirs
114K	/var/lib/defoma/gs.d
131K	/var/lib/defoma/libwmf0.2-7.d
117K	/var/lib/defoma/pango.d
1.1M	/var/lib/defoma/psfontmgr.d
69K	/var/lib/defoma/scripts
0	/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID
111K	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
111K	/var/lib/defoma/x-ttcidfont-conf.d/dirs
462K	/var/lib/defoma/x-ttcidfont-conf.d
2.5M	/var/lib/defoma
0	/var/lib/dhcp3
512	/var/lib/dictionaries-common/aspell
1.0K	/var/lib/dictionaries-common/wordlist
1.5K	/var/lib/dictionaries-common
16K	/var/lib/doc-base/documents
31K	/var/lib/doc-base/info
1.5K	/var/lib/doc-base/omf/dc
1.0K	/var/lib/doc-base/omf/doc-base
1.0K	/var/lib/doc-base/omf/gimp-help-en
1.0K	/var/lib/doc-base/omf/gnupginterface
1.0K	/var/lib/doc-base/omf/install-docs-man
2.0K	/var/lib/doc-base/omf/libpng12
1.0K	/var/lib/doc-base/omf/man-db
1.0K	/var/lib/doc-base/omf/nano-faq
1.0K	/var/lib/doc-base/omf/nat
1.0K	/var/lib/doc-base/omf/packet-filter
1.0K	/var/lib/doc-base/omf/pnm2ppa-calibrate
1.0K	/var/lib/doc-base/omf/pnm2ppa-color
1.5K	/var/lib/doc-base/omf/pnm2ppa-ppa-networking
1.0K	/var/lib/doc-base/omf/python-policy
1.0K	/var/lib/doc-base/omf/time
17K	/var/lib/doc-base/omf
64K	/var/lib/doc-base
0	/var/lib/hal
512	/var/lib/initramfs-tools
0	/var/lib/initscripts
0	/var/lib/libuuid
1.0K	/var/lib/libxml-sax-perl/ParserDetails.d
1.0K	/var/lib/libxml-sax-perl
0	/var/lib/localechooser
0	/var/lib/logrotate
340K	/var/lib/misc
2.5M	/var/lib/mlocate
0	/var/lib/os-prober
2.5K	/var/lib/pam
512	/var/lib/partconf/fstab.d
512	/var/lib/partconf
19K	/var/lib/python-support/python2.5/GMenuSimpleEditor
63K	/var/lib/python-support/python2.5/atom
67K	/var/lib/python-support/python2.5/cupshelpers
2.0K	/var/lib/python-support/python2.5/dbus/mainloop
124K	/var/lib/python-support/python2.5/dbus
105K	/var/lib/python-support/python2.5/debian_bundle
31K	/var/lib/python-support/python2.5/gdata/apps
35K	/var/lib/python-support/python2.5/gdata/base
60K	/var/lib/python-support/python2.5/gdata/calendar
12K	/var/lib/python-support/python2.5/gdata/docs
33K	/var/lib/python-support/python2.5/gdata/spreadsheet
323K	/var/lib/python-support/python2.5/gdata
50K	/var/lib/python-support/python2.5/glchess/chess/fics
120K	/var/lib/python-support/python2.5/glchess/chess
64K	/var/lib/python-support/python2.5/glchess/ggz
99K	/var/lib/python-support/python2.5/glchess/gtkui
40K	/var/lib/python-support/python2.5/glchess/scene/cairo
164K	/var/lib/python-support/python2.5/glchess/scene/opengl
217K	/var/lib/python-support/python2.5/glchess/scene
24K	/var/lib/python-support/python2.5/glchess/ui
656K	/var/lib/python-support/python2.5/glchess
69K	/var/lib/python-support/python2.5/gnome_sudoku/gtk_goodies
296K	/var/lib/python-support/python2.5/gnome_sudoku
2.0K	/var/lib/python-support/python2.5/gtk-2.0/bonobo
512	/var/lib/python-support/python2.5/gtk-2.0/evolution
1.0K	/var/lib/python-support/python2.5/gtk-2.0/gio
13K	/var/lib/python-support/python2.5/gtk-2.0/glib
2.0K	/var/lib/python-support/python2.5/gtk-2.0/gnome
1.5K	/var/lib/python-support/python2.5/gtk-2.0/gnomedesktop
512	/var/lib/python-support/python2.5/gtk-2.0/gnomeprint
1.0K	/var/lib/python-support/python2.5/gtk-2.0/gnomevfs
17K	/var/lib/python-support/python2.5/gtk-2.0/gobject
54K	/var/lib/python-support/python2.5/gtk-2.0/gtk
512	/var/lib/python-support/python2.5/gtk-2.0/pynotify
512	/var/lib/python-support/python2.5/gtk-2.0/totem
112K	/var/lib/python-support/python2.5/gtk-2.0
41K	/var/lib/python-support/python2.5/invest
19K	/var/lib/python-support/python2.5/orca/scripts/apps/Thunderbird
35K	/var/lib/python-support/python2.5/orca/scripts/apps/evolution
8.5K	/var/lib/python-support/python2.5/orca/scripts/apps/gcalctool
13K	/var/lib/python-support/python2.5/orca/scripts/apps/gedit
5.0K	/var/lib/python-support/python2.5/orca/scripts/apps/gnome-window-properties
33K	/var/lib/python-support/python2.5/orca/scripts/apps/pidgin
8.0K	/var/lib/python-support/python2.5/orca/scripts/apps/planner
8.0K	/var/lib/python-support/python2.5/orca/scripts/apps/rhythmbox
79K	/var/lib/python-support/python2.5/orca/scripts/apps/soffice
281K	/var/lib/python-support/python2.5/orca/scripts/apps
178K	/var/lib/python-support/python2.5/orca/scripts/toolkits/Gecko
17K	/var/lib/python-support/python2.5/orca/scripts/toolkits/J2SE-access-bridge
198K	/var/lib/python-support/python2.5/orca/scripts/toolkits
482K	/var/lib/python-support/python2.5/orca/scripts
1.6M	/var/lib/python-support/python2.5/orca
71K	/var/lib/python-support/python2.5/rdflib/sparql/bison
169K	/var/lib/python-support/python2.5/rdflib/sparql
46K	/var/lib/python-support/python2.5/rdflib/store/FOPLRelationalModel
213K	/var/lib/python-support/python2.5/rdflib/store
57K	/var/lib/python-support/python2.5/rdflib/syntax/parsers/n3p
111K	/var/lib/python-support/python2.5/rdflib/syntax/parsers
39K	/var/lib/python-support/python2.5/rdflib/syntax/serializers
159K	/var/lib/python-support/python2.5/rdflib/syntax
694K	/var/lib/python-support/python2.5/rdflib
0	/var/lib/python-support/python2.5/rdflib-2.4.0.egg-info
7.0K	/var/lib/python-support/python2.5/rdflib_tools
131K	/var/lib/python-support/python2.5/xdg
4.6M	/var/lib/python-support/python2.5
4.6M	/var/lib/python-support
0	/var/lib/samba
0	/var/lib/sgml-base
0	/var/lib/snmp
0	/var/lib/synaptic
512	/var/lib/thunderbird/extensions.d
512	/var/lib/thunderbird
97K	/var/lib/ucf/cache
104K	/var/lib/ucf
11K	/var/lib/ufw/messages
12K	/var/lib/ufw
0	/var/lib/update-manager
1.0K	/var/lib/update-notifier/user.d
1.0K	/var/lib/update-notifier
0	/var/lib/vim/addons
0	/var/lib/vim
16K	/var/lib/xml-core
125M	/var/lib
4.0K	/var/log/cups
4.0K	/var/log/gdm
4.0K	/var/log/ConsoleKit
0	/var/log/news
4.5K	/var/log/fsck
0	/var/log/apparmor
212K	/var/log/apt
0	/var/log/dist-upgrade
0	/var/log/samba
0	/var/log/unattended-upgrades
1.7M	/var/log
206K	/var/cache/fontconfig
956K	/var/cache/hald
0	/var/cache/cups/rss
0	/var/cache/cups/ppd
0	/var/cache/cups
7.9M	/var/cache/debconf
5.1M	/var/cache/app-install
0	/var/cache/apt/archives/partial
0	/var/cache/apt/archives
6.3M	/var/cache/apt
5.0K	/var/cache/dictionaries-common
0	/var/cache/gnome-system-tools/backup
0	/var/cache/gnome-system-tools
0	/var/cache/hwtest
0	/var/cache/jockey
du: cannot read directory `/var/cache/ldconfig': Permission denied
0	/var/cache/ldconfig
0	/var/cache/man/X11R6
0	/var/cache/man/cat1
0	/var/cache/man/cat2
0	/var/cache/man/cat3
0	/var/cache/man/cat4
0	/var/cache/man/cat5
0	/var/cache/man/cat6
0	/var/cache/man/cat7
0	/var/cache/man/cat8
14K	/var/cache/man/cs
17K	/var/cache/man/de
15K	/var/cache/man/es
13K	/var/cache/man/fi
28K	/var/cache/man/fr
13K	/var/cache/man/fr.ISO8859-1
13K	/var/cache/man/fr.UTF-8
0	/var/cache/man/fsstnd
13K	/var/cache/man/gl
13K	/var/cache/man/hu
13K	/var/cache/man/id
17K	/var/cache/man/it
13K	/var/cache/man/it.ISO8859-1
13K	/var/cache/man/it.UTF-8
18K	/var/cache/man/ja
13K	/var/cache/man/ko
0	/var/cache/man/local
0	/var/cache/man/oldlocal
0	/var/cache/man/opt
13K	/var/cache/man/pa
17K	/var/cache/man/pl
13K	/var/cache/man/pl.ISO8859-2
13K	/var/cache/man/pl.UTF-8
14K	/var/cache/man/pt_BR
19K	/var/cache/man/ru
16K	/var/cache/man/sv
14K	/var/cache/man/tr
13K	/var/cache/man/zh_CN
13K	/var/cache/man/zh_TW
711K	/var/cache/man
0	/var/cache/pppconfig
0	/var/cache/samba
21M	/var/cache
2.0K	/var/backups
0	/var/games
0	/var/local
0	/var/lock
0	/var/mail
0	/var/opt
147M	/var
ubuntu@ubuntu:~$


So sorry, I don't know how to post that screenshot of GParted for you P4man...

---

### Post by slakkie on 2009-08-13
Could you boot your regular OS and show us the output of df -kh ?

---

### Post by lotusalive on 2009-08-13
Screenshot does not have a URL, and Attachments says that it is an invalid file, lol:confused:

---

### Post by P4man on 2009-08-13
> **lotusalive said:**
> Screenshot does not have a URL, and Attachments says that it is an invalid file, lol:confused:

upload it to [http://imageshack.us/](http://imageshack.us/)

---

### Post by lotusalive on 2009-08-13
sol@sol-desktop:~$ df -kh
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              19G   19G     0 100% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  240K  496M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  164K  496M   1% /dev
tmpfs                 497M   96K  497M   1% /dev/shm
lrm                   497M  2.2M  495M   1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda7              19G  2.9G   15G  17% /home
overflow              1.0M   24K 1000K   3% /tmp
sol@sol-desktop:~$ 

Also, Add/Remove Software doesn't seem to be working, nor will Computer Janitor allow me to remove linux-restricted-modules-2.6.27-7-generic and adobereader-enu, but DID remove one other ? ! ?  Saying: 'Could not clean up properly: E:Sub-process /usr/bin/dpkg returned an error code (2)'

Going to imageshack.us to upload the screenshot for P4man.[IMG]http://img219.imageshack.us/img219/1997/19887633.png[/IMG]

fyi: I have my first partition as a 30GiB NTFS, but do not use it currently at all, then swap, then /, then home, then unallocated (sort of a mess)

---

### Post by P4man on 2009-08-13
you should have unchecked the resize thing in imageshack, but its ok, I can read. barely lol.

Its indeed a bit of a mess. You have your ubuntu partitions inside an extended partition. Thats like a container for them. You'll have to resize that first (the light blue one). sda2 I think, but its hard to read :).  Grow it to the right.

After that you can move and resize the other partitions inside the extended partitions as you see fit.

Warning: this will take a long time to complete (could be hours). Dont interrupt it no matter what.

---

### Post by lotusalive on 2009-08-13
Yeah, been there, done that, too ! lol (sorry for the s-shot)  Thx for your 

efforts...  See, in one of my other posts, I accidentally had 'highest 

version' ticked in Synaptic, instead of Jaunty, and had to use one of my 

back-ups... Wasn't sure it worked, messed up my YouTube streaming ever 

since, and both firehol and firestarter (fails on restart, un-

installed !), which I uninstalled and then could not get back in to 

Synaptics after that !  It's been sort of a 'ride,' lol.  As I said 

before, I've made every mistake possible, and I don't really understand 

what you mention I've done with my partitioning, but it's all one.  After 

I attempt this move and resize, is there a way I might 'fix' it, undo 

what I've done, do it better, (har, you don't _have_ to answer that 

if you don't think it's possible, lol !)  I was hoping to back-install 

W's, just to play secondlife, but have never got into its very 

trickiness, in the whole year I planned to do so !  So, I hope to soon 

just buy a new GC.  And maybe I'll just re-install now, since I've gotten 

good at choosing software that I don't have time to use ! lol :guitar:  

I've had fun looking at it all, tho' !  Thanks again for the assistance.


Better Screenshot: [IMG]http://img229.imageshack.us/img229/5480/10591342.png[/IMG]

---

### Post by P4man on 2009-08-13
There is no real point in undoing what you're about to do.. but I guess its possible to shrink those partitions again using the same procedure, provided you dont fill them first :)

you can always reinstall later if you think you must, but you should be ok resizing them. unmount them first if need be (right click > unmount). Shrink the blue one first. It will work :)

---

### Post by slakkie on 2009-08-13
> **lotusalive said:**
> sol@sol-desktop:~$ df -kh
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              19G   19G     0 100% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  240K  496M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  164K  496M   1% /dev
tmpfs                 497M   96K  497M   1% /dev/shm
lrm                   497M  2.2M  495M   1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda7              19G  2.9G   15G  17% /home
overflow              1.0M   24K 1000K   3% /tmp
sol@sol-desktop:~$ 



To clean some stuff, have a look at this thread. It will not remove all your troubles but should be able to remove some stuff.

Although, increasing your root would help. Boot with the gparted liveCD and use clonezilla to backup your files so you can recover from any mistake. Best option would be to create a smallish slice/partition (over 10 Gb) at the end of your disk and let clonezilla write the backup on that slice. Or backup to external USB disks.

---

### Post by lotusalive on 2009-08-13
Thanks for being helpful with these ideas, and mortifying me !  I have a 

few tasks to complete before I get time to start this process in a few 

days.  I'm a little overwhelmed, but willing to make an attempt.  I'm just 

ready to reinstall, in case I fail.  Is there a 'short answer' or even a 

generic answer as to WHY dpkg quits functioning ?  It's happened to me at 

least once, more like twice, during the past year, probably over the same 

'full' problem, but thought I'd ask if there were any other reasons it 

might be, so I'd know 'why.' lol

---

### Post by P4man on 2009-08-14
If your / is 100% full, all kind of weird things can happen.

---

### Post by lotusalive on 2009-08-14
lol, thx P4man.  I watched a movie, then it would not unmount, finally ejected, and then computer would not reboot, so I'm stuck doing this tonight ! I'll give it a go.


I don't have clonezilla on my livecd for 8.10, so that option is out.

Also, the extended partition has no option to do anything except 'Create' or 'Manage Flags.'  There is no option to 'shrink' anywhere.

So, all I'm doing is resizing home to about 7 GiB, and enlarging root by about 10 GiB, and Applying.

Please confirm this is correct, if you have a moment.

---

### Post by lotusalive on 2009-08-14
Also, in this partition set-up, will I ever be able to utilize my unallocated space of 76.8 GiB, if it only offers the 'Primary' and not Logical Partition option ?

---

### Post by P4man on 2009-08-14
have a look here:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

scroll down to 3- How to resize Extended partition

---

### Post by P4man on 2009-08-14
hmm googling on it, it seems others have trouble reszing an extended partition too. 

If you want me to have a look at it, enable remote desktop in system > preferences, set a password on it and send me a pm with the password and your current ip (http;//www.whatismyip.com)

---

### Post by lotusalive on 2009-08-14
Thanks again P4man, that explanation is what I have done, and am now going to Apply the changes.  I'll let you know here, if it succeeds.:)

---

### Post by lotusalive on 2009-08-14
It's not really an 'extended partition' that I have, as you say, it is rather a 'container' of my swap, root and home linux partitions.  (I wonder if Linux did this automatically in the wizard when I created the fat32 as Primary, (because it has to be primary), in order to separate itself from dos...  After install it let me change it to ntfs.)  

His example IS NOT going into any of his unallocated space, either, which is the only reason I would want to resize the WHOLE of 'extended.'  Also, I do not need that much home space, as I back everything that is mine up on USB, since I can't trust my installs to last long enough, and have lost far too many documents by not storing them elsewhere. (One install even erased my USB, when it failed !  I hope that has not happened this time...)

Thanks for the offer to come in and do it for me.  I think I'm not sharp enough tonight to go through it tho,' lol.  Tell me if you really think it is necessary, as I don't understand the reasoning behind increasing 'extended' at all !  LOL

I have not started Applying yet.

---

### Post by P4man on 2009-08-14
an extended partition IS a container that holds other logical partitions.

You are right about the example not being quite the same tho, but I figured it might help you on the right path. 

What you posted earlier about resizing both logical linux partitions (root and home) should work, but it wont reclaim the unallocated space. You can make yet another, new (primary) partition there, but its much easier if you can grow the extended partition so it includes the unallocated space, then resize home and root inside the extended partition. Otherwise you end up dividing your drive space over 4 partitions (not counting swap) and you may end up having your root or home partitions full again in a few months.

as for the remote assistance; of course thats not strictly necessary, just offering ;)

---

### Post by lotusalive on 2009-08-14
Got it !  I'd like to be able to utilize ALL Unallocated space for Linux ?  (I know I can't do it on my own !  Too obtuse !)

Okay, not as involved as I thought, half-way to remote use.  You'll get the p/w.

---

### Post by P4man on 2009-08-14
well that went smooth :)
For those following, the trick was to swapoff the .. well swap partition inside the extended. thats why gparted didnt want to resize it. hadnt thought of that until I saw it.

remote desktop FTW :)

---

### Post by lotusalive on 2009-08-14
Thank you !:KS

---

### Post by lotusalive on 2009-08-14
Still getting dpkg errors on Updates, if anyone is willing to take a look:

"- Not all changes and updates succeeded. For further details...:

dpkg: unrecoverable fatal error, aborting: syntax error: unknow group 'postdrop' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover: "

And: 

sol@sol-desktop:~$ sudo apt-get upgrade
[sudo] password for sol: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libxml2 libxml2-dev libxml2-utils python-libxml2
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1881kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Reading changelogs... Done
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group `postdrop' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)
sol@sol-desktop:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages
Reading package lists... Done
sol@sol-desktop:~$ 

Thanks in advance for all suggestions !

---

### Post by P4man on 2009-08-15
Try this:

```
sudo groupadd postdrop
sudo useradd postfix
```

---

### Post by lotusalive on 2009-08-15
lol, didn't look like much, no reply at all, but commands worked: Updates installed without a hitch.  Thank you again for saving my install P4man.:P:P:P:P:P

---


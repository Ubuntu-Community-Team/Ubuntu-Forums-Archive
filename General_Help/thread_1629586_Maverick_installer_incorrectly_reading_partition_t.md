---
title: "Maverick installer incorrectly reading partition table"
date: 2010-11-23
forum: General Help
---

### Post by infurnus on 2010-11-23
I think I found a bug with the maverick installer. [http://img843.imageshack.us/img843/6923/screenshot4c0.png](http://img843.imageshack.us/img843/6923/screenshot4c0.png)  

The installer is incorrectly reading my partition table I'm afraid it might overwrite data. /dev/sda3 is the target for the install. 

/dev/sda1 = 200M = Windows system partition
/dev/sda2 = 239G = Windows install
/dev/sda3 = 50G  = Where I want to install Linux
/dev/sda4 = 45G  = NTFS storage

At first I had /dev/sda3 as a RAW type. In fact the only way I could create ext4 is via mkfs.


EDIT: I did unmount them before proceeding - mounted just as a reference in the screenshot.
fdisk reads the same thing. Fresh install from LiveCD. Any help would be appreciated.

FYI I only have Wipe entire disk or Advanced in the installer. I don't have the "Install along side another OS" option.

---

### Post by garvinrick4 on 2010-11-23
Is there do a manual install? I just noticed it does.
You have to use manual install and choose sda3 as / with ext4 format.
If over 2 gig of ram ignore swap.
#Just click on sda3 when comes up in install and use the previous.
#If need swap have to make a partition in with gparted 2 times the size of installed RAM

---

### Post by infurnus on 2010-11-23
Even though it shows as 200+gb and its only actually 50Gb? It appears to have both partitions included in sda3. I'm worried about losing one of those partitions.

EDIT: I'm not going to use swap.

---

### Post by garvinrick4 on 2010-11-23
Here is a thread:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by infurnus on 2010-11-23
> **garvinrick4 said:**
> Here is a thread:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

D'oh. Thanks, I'll search harder next time.

---

### Post by infurnus on 2010-11-23
I think I found a bug with the maverick installer. [http://img843.imageshack.us/img843/6923/screenshot4c0.png](http://img843.imageshack.us/img843/6923/screenshot4c0.png)

The installer is incorrectly reading my partition table I'm afraid it might overwrite data. /dev/sda3 is the target for the install.

This is how parted should read the data (If you see the SS df -Th reads it correctly!)
----------------------------------------
/dev/sda1 = 200M = Windows system partition
/dev/sda2 = 239G = Windows install
/dev/sda3 = 50G = Where I want to install Linux
/dev/sda4 = 45G = NTFS storage


This is how the installer reads the partitions (incorrectly)
--------------------------------------------
/dev/sda1 = 1Mb     = no type
/dev/sda2 = 208Mb   = ntfs
/dev/sda3 = 256Gb   = ntfs
/dev/sda4 = 243Gb   = ext4

At first I had /dev/sda3 as a RAW type. In fact the only way I could create ext4 is via mkfs.


EDIT: I did unmount them before proceeding - mounted just as a reference in the screenshot.
fdisk reads the same thing. Fresh install from LiveCD. Any help would be appreciated.

FYI I only have Wipe entire disk or Advanced in the installer. I don't have the "Install along side another OS" option.

---

### Post by oldfred on 2010-11-23
Either way you have used all 4 primary partitions and the installer cannot create any more.

You have to convert one partition to an extended partition which then can hold many logical partitions. Windows has to be a primary partition, but Ubuntu works just fine from logical partitions.

Use gparted from the liveCD or a gparted liveCD download and create your partitions from that. Then use manual install to choose & format / (root), /home (if desired), & if you defined swap in gparted it will auto find it.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by garvinrick4 on 2010-11-23
In a Ubuntu installation Cd boot up and choose Try Ubuntu:
In a terminal Applications to Accessories to Terminal: copy and paste:
```
sudo parted -l
```lower case L
#will tell you the size linux reads your partitions.
or of course gparted.

---

### Post by infurnus on 2010-11-24
EDIT: oldfred I just saw your post, I'll try to make it extended tomorrow. I did set it as a primary through fdisk. I won't be creating a swap or anything on a different partition. Everything will go on one partition. I figured primary would be sufficient enough.

Think I might have found relevant info. Going to go through this later on. The only partition modified was /dev/sda3 and it was deleted, left raw, then formated to NTFS then booted into linux. Off to bed for tonight.

```
Nov 24 04:47:22 ubuntu ubiquity[19225]: last message repeated 2 times
Nov 24 04:47:22 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Nov 24 04:47:22 ubuntu ntfsresize: Failed to startup volume: Invalid argument.
Nov 24 04:47:22 ubuntu ntfsresize: ERROR(22): Opening '/dev/sda3' as NTFS failed: Invalid argument
Nov 24 04:47:22 ubuntu ntfsresize: The device '/dev/sda3' doesn't have a valid NTFS.
Nov 24 04:47:22 ubuntu ntfsresize: Maybe you selected the wrong partition? Or the whole disk instead of a
Nov 24 04:47:22 ubuntu ntfsresize: partition (e.g. /dev/hda, not /dev/hda1)? This error might also occur
Nov 24 04:47:22 ubuntu ntfsresize: if the disk was incorrectly repartitioned (see the ntfsresize FAQ).
Nov 24 04:47:22 ubuntu partman: Error running 'ntfsresize --info'
Nov 24 04:47:23 ubuntu ubiquity: tune2fs: Bad magic number in super-block while trying to open /dev/sda4
Nov 24 04:47:23 ubuntu ubiquity: Couldn't find valid filesystem superblock.
Nov 24 04:47:23 ubuntu partman: Error running 'tune2fs -l /dev/sda4'
Nov 24 04:47:38 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Nov 24 04:47:38 ubuntu ntfsresize: Device name        : /dev/sda2
Nov 24 04:47:38 ubuntu ntfsresize: NTFS volume version: 3.1
Nov 24 04:47:38 ubuntu ntfsresize: Cluster size       : 4096 bytes
Nov 24 04:47:38 ubuntu ntfsresize: Current volume size: 256426111488 bytes (256427 MB)
Nov 24 04:47:38 ubuntu ntfsresize: Current device size: 256426115072 bytes (256427 MB)
Nov 24 04:47:38 ubuntu ntfsresize: Checking filesystem consistency ...
Nov 24 04:47:38 ubuntu ntfsresize: Accounting clusters ...
Nov 24 04:47:38 ubuntu ntfsresize: Space in use       : 213814 MB (83.4%)
Nov 24 04:47:38 ubuntu ntfsresize: Collecting resizing constraints ...
Nov 24 04:47:38 ubuntu ntfsresize: You might resize at 213813161984 bytes or 213814 MB (freeing 42613 MB).
Nov 24 04:47:38 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Nov 24 04:47:38 ubuntu partman: ntfsresize reported minimum size 213813161984, but current partition size is 208666624

```


```
ubuntu@ubuntu:/var/log/installer$ cat version
ubiquity 2.4.8
```


```
ubuntu@ubuntu:/var/log/installer$ cat debug
Ubiquity 2.4.8
update_release_notes_label()
update_release_notes_label()
update_release_notes_label()
update_release_notes_label()
update_release_notes_label()
update_release_notes_label()
update_release_notes_label()
WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs is disabled since running on read-only media
Ubiquity 2.4.8
update_release_notes_label()
update_release_notes_label()
update_release_notes_label()
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1383, in watch_debconf_fd_helper
    return callback(source, debconf_condition)
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 252, in process_input
    self.status = self.wait()
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 148, in wait
    self.cleanup()
  File "/usr/lib/ubiquity/plugins/ubi-language.py", line 742, in cleanup
    i18n.reset_locale(self.frontend)
  File "/usr/lib/ubiquity/ubiquity/i18n.py", line 45, in reset_locale
    di_locale = frontend.db.get('debian-installer/locale')
AttributeError: 'NoneType' object has no attribute 'get'

Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1383, in watch_debconf_fd_helper
    return callback(source, debconf_condition)
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 252, in process_input
    self.status = self.wait()
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 148, in wait
    self.cleanup()
  File "/usr/lib/ubiquity/plugins/ubi-language.py", line 742, in cleanup
    i18n.reset_locale(self.frontend)
  File "/usr/lib/ubiquity/ubiquity/i18n.py", line 45, in reset_locale
    di_locale = frontend.db.get('debian-installer/locale')
AttributeError: 'NoneType' object has no attribute 'get'
Ubiquity 2.4.8
update_release_notes_label()
update_release_notes_label()
update_release_notes_label()
WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

Ubiquity 2.4.8
update_release_notes_label()
update_release_notes_label()
update_release_notes_label()
WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

Ubiquity 2.4.8
update_release_notes_label()
update_release_notes_label()
update_release_notes_label()
WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

Ubiquity 2.4.8
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 530, in <module>
    main(oem_config)
  File "/usr/lib/ubiquity/bin/ubiquity", line 515, in main
    install(args[0], query=options.query)
  File "/usr/lib/ubiquity/bin/ubiquity", line 240, in install
    open_terminal()
  File "/usr/lib/ubiquity/bin/ubiquity", line 78, in open_terminal
    ttyn = os.ttyname(0)
OSError: [Errno 25] Inappropriate ioctl for device
Ubiquity 2.4.8
update_release_notes_label()
update_release_notes_label()
update_release_notes_label()
WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:1636: GtkWarning: Unable to show '': Operation not supported
  gtk.main()
```



```
ubuntu@ubuntu:/var/log/installer$ cat dm

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64
Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
Build Date: 16 September 2010  06:18:41PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 23 20:34:41 2010
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Window manager warning: Type mismatch: Expected `int' got `bool' for key /apps/metacity/general/num_workspaces
Window manager warning: 0 stored in GConf key /apps/metacity/general/num_workspaces is out of range 1 to 36
** (panel:3064): DEBUG: Looking at Module: /usr/lib/indicators/4/libsession.so
** (panel:3064): DEBUG: Loading Module: /usr/lib/indicators/4/libsession.so
** Message: applet now removed from the notification area

** (nm-applet:3065): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:3065): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/0
** (nm-applet:3065): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:3065): DEBUG: old state indicates that this was not a disconnect 0

(panel:3064): LIBDBUSMENU-GLIB-WARNING **: Unable to get property proxy for org.ayatana.indicator.session on /org/ayatana/indicator/session/menu: Could not get owner of name 'org.ayatana.indicator.session': no such name
** (panel:3064): DEBUG: Signal: Entry Added
** (panel:3064): DEBUG: Looking at Module: /usr/lib/indicators/4/libapplication.so
** (panel:3064): DEBUG: Loading Module: /usr/lib/indicators/4/libapplication.so
** (panel:3064): DEBUG: Looking at Module: /usr/lib/indicators/4/libsoundmenu.so
** (panel:3064): DEBUG: Loading Module: /usr/lib/indicators/4/libsoundmenu.so
(panel:3064): Indicator-Sound-DEBUG: At start-up attempting to set the image to audio-volume-muted-panel

(panel:3064): LIBDBUSMENU-GLIB-WARNING **: Unable to get property proxy for org.ayatana.indicator.sound on /org/ayatana/indicator/sound/menu: Could not get owner of name 'org.ayatana.indicator.sound': no such name
** (panel:3064): DEBUG: Signal: Entry Added
** (nm-applet:3065): DEBUG: foo_client_state_changed_cb
** (nm-applet:3065): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:3065): DEBUG: going for offline with icon: notification-network-disconnected

(panel:3064): LIBDBUSMENU-GLIB-WARNING **: Unable to get property proxy for org.ayatana.indicator.session on /org/ayatana/indicator/session/menu: Could not get owner of name 'org.ayatana.indicator.session': no such name

(panel:3064): libindicator-WARNING **: Unable to create service proxy on 'org.ayatana.indicator.session': Could not get owner of name 'org.ayatana.indicator.session': no such name
** Message: applet now embedded in the notification area

(panel:3064): libindicator-WARNING **: Unable to create service proxy on 'org.ayatana.indicator.application': Could not get owner of name 'org.ayatana.indicator.application': no such name
(panel:3064): libindicator-DEBUG: Restarting service 'org.ayatana.indicator.session' count 1
(panel:3064): libindicator-DEBUG: Restarting service 'org.ayatana.indicator.application' count 1
(panel:3064): Indicator-Application-DEBUG: Connected to Application Indicator Service.
(panel:3064): Indicator-Application-DEBUG: Setup proxy signals
(panel:3064): Indicator-Application-DEBUG: Connect to them.
(panel:3064): Indicator-Application-DEBUG: Request current apps

(panel:3064): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(panel:3064): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(panel:3064): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(panel:3064): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(panel:3064): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID
(panel:3064): Indicator-Sound-DEBUG: about to connect to the signals
(panel:3064): Indicator-Sound-DEBUG: indicator-sound: new_volume_slider_widget
(panel:3064): Indicator-Sound-DEBUG: VolumeWidget::volume_widget_init
(panel:3064): Indicator-Sound-DEBUG: volume_widget_set_twin_item initial level = 0.000000
(panel:3064): Indicator-Sound-DEBUG: volume_widget_parent_changed
(panel:3064): Indicator-Sound-DEBUG: scrub-widget::property_update for prop enabled
(panel:3064): Indicator-Sound-DEBUG: scrub-widget::property_update for prop visible
(panel:3064): Indicator-Sound-DEBUG: signal caught - sink availability update with  value: 1
(panel:3064): Indicator-Sound-DEBUG: scrub-widget::property_update for prop x-canonical-ido-volume-level
(panel:3064): Indicator-Sound-DEBUG: volume-widget - update level with value 35.481262
(panel:3064): Indicator-Sound-DEBUG: signal caught - sink mute update with mute value: 0
(panel:3064): Indicator-Sound-DEBUG: scrub-widget::property_update for prop enabled
(panel:3064): Indicator-Sound-DEBUG: scrub-widget::property_update for prop visible
(panel:3064): Indicator-Sound-DEBUG: signal caught - sink availability update with  value: 1
(panel:3064): Indicator-Sound-DEBUG: scrub-widget::property_update for prop x-canonical-ido-volume-level
(panel:3064): Indicator-Sound-DEBUG: volume-widget - update level with value 35.481262
(panel:3064): Indicator-Sound-DEBUG: signal caught - sink mute update with mute value: 0
** (nm-applet:3065): DEBUG: foo_client_state_changed_cb

(nm-connection-editor:4111): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings: addresses

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings: addresses

** (nm-connection-editor:4111): WARNING **: ui_to_setting: IPv4 address '<none>' missing or invalid!

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings
(panel:3064): Indicator-Sound-DEBUG: signal caught - sink input while muted with value 0

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings

** (nm-connection-editor:4111): WARNING **: Invalid setting IPv4 Settings
** (nm-applet:3065): DEBUG: foo_client_state_changed_cb
** (nm-applet:3065): DEBUG: going for offline with icon: notification-network-ethernet-disconnected

** (nm-connection-editor:4111): WARNING **: dispose: CEPolkitButton object 0x1a79240 disposed twice
** (nm-applet:3065): DEBUG: going for offline with icon: notification-network-ethernet-disconnected
** (nm-applet:3065): DEBUG: foo_client_state_changed_cb
(EE) intel(0): Couldn't create pixmap for fbcon
** Message: Caught signal 15, shutting down...
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1686 requests (1685 known processed) with 0 events remaining.
 ddxSigGiveUp: Closing log
Generating locales...
  en_US.UTF-8... up-to-date
Generation complete.

```

---

### Post by infurnus on 2010-11-24
> **garvinrick4 said:**
> In a Ubuntu installation Cd boot up and choose Try Ubuntu:
In a terminal Applications to Accessories to Terminal: copy and paste:
```
sudo parted -l
```lower case L
#will tell you the size linux reads your partitions.
or of course gparted.

Gparted and parted read the table incorrectly. The only app that reads the partitions correctly is df -Th. Not sure why.

---

### Post by oldfred on 2010-11-24
The df -Th only shows mounted partitions. gparted & parted or even fdisk should show all partitions whether mounted or not.

Post each.

---

### Post by infurnus on 2010-11-24
I cross posted thinking this was an install issue. Thread reported for mod to delete - continued [http://ubuntuforums.org/showthread.php?p=10158636](http://ubuntuforums.org/showthread.php?p=10158636) here

---

### Post by infurnus on 2010-11-24
I deleted the windows system partition and made some room. Here are some screenshots on what happens and what the various tools report.

NOTE: The Disk Utility GUI app is correct on the current partition table. This is how I would like it to be setup. ** Except the invalid 0 space where it shows negative TB free. idk wth that is.

[http://img842.imageshack.us/img842/5997/invalidspace.png](http://img842.imageshack.us/img842/5997/invalidspace.png)

Tried to partition
[http://img337.imageshack.us/img337/7746/partition.png](http://img337.imageshack.us/img337/7746/partition.png)

Error
[http://img221.imageshack.us/img221/5628/afterpartitioncration.png](http://img221.imageshack.us/img221/5628/afterpartitioncration.png)

/dev/sda1 = windows install
/dev/sda2 = ntfs storage
/dev/sda3 = ntfs storage
/dev/sda4 = ubuntu install

I don't care about the ordering, again no swap file and no separate user folder. Its a dev env.

fdisk and sfdisk are showing the correct partitions now. However, parted is reporting an invalid file system. I don't have anything partitioned out with ext4. Not sure why this is occurring. It should be NTFS.

The info in gedit is from the Disk Utility window when I tried to create an ext4 partition out of the 50gb of unused space.

In the mean time I'm going to burn 10.04 and see if I have the same issues. I hope this is a ubiquity issue and not my partition table.

One thing to note is that it did wipe out the bootable flag on my windows partition. Not sure if I did this in fdisk or by error.

---

### Post by oldfred on 2010-11-24
You somewhere tried to create more than 4 partitions with windows. Windows then automatically converts to SFS which is its logical volume manager that is compatible with nothing but windows. Window says you cannot convert back without totally erasing drive or backup each partition and reformat and recover partitions.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec)

---

### Post by infurnus on 2010-11-24
Tried booting into windows. Something ate my windows partition for lunch.

I can mount the drive and see the data however I can no longer boot windows. I get a BSOD as soon as I choose safemode or last known good or normal boot.

I wish I could generate proof of such occurrence. I believe either gparted or the ubiquity install caused this error. Windows had no issues reading the partition and df -Th gave the correct type. 

I now have to do backup/reimage of my windows install as it has jacked it up so much so that the Windows 7 recover disk crashes when trying to scan for problems. I've tried chkdsk but to no avail, this installer royally screwed me.

I'll format and stick with 10.04 until next release. Thanks for the assistance.

---

### Post by oldfred on 2010-11-24
I think you deleted the hidden windows boot/recovery partition. It is normally just 100MB. You can move boot flag (active partition) to main windows system partition and then run windows repairs.

oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

---

### Post by infurnus on 2010-11-24
I see where its getting the ext4 data from, the Wubi install I forgot about. It failed and I left the remainders over on my HD. I appreciate it oldfred. I think Imma reformat as I can't spend any more time repairing. I used a super grub boot disk to boot windows but I get a quick BSOD that i cannot read.

Thank you again.

```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 409600. But according to the info from 
                       fdisk, sda1 starts at sector 63. The info in boot 
                       sector on the starting sector of the MFT is wrong. The 
                       info in the boot sector on the starting sector of the 
                       MFT Mirror is wrong. According to the info in the boot 
                       sector, sda1 has 500832255 sectors, but according to 
                       the info from fdisk, it has 409536 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 606099456. But according to the info from 
                       fdisk, sda2 starts at sector 409600. According to the 
                       info in the boot sector, sda2 has 92628991 sectors, 
                       but according to the info from fdisk, it has 500832255 
                       sectors.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 698731110. But according to the info from 
                       fdisk, sda3 starts at sector 501241856. According to 
                       the info in the boot sector, sda3 has 278036954 
                       sectors, but according to the info from fdisk, it has 
                       475529263 sectors.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       409,599       409,537  42 SFS
/dev/sda2    *        409,600   501,241,855   500,832,256  42 SFS
/dev/sda3         501,241,856   976,771,119   475,529,264  42 SFS
/dev/sda4         976,771,120   976,771,120             1  83 Linux

```

---

### Post by oldfred on 2010-11-24
Windows will not do anything unless the boot flag is on sda1 as that is where the boot files are. You need to install a windows boot loader in the MBR to boot windows, I do not think syslinux boots windows.

Try moving boot flag to sda1 and then run the windows repairs.  Because the partitions are SFS I would not use any Linux tools, but just windows. Windows has a makeactive command and other command line repair tools.

---


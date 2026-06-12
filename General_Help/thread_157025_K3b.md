---
title: "K3b"
date: 2006-04-08
forum: General Help
---

### Post by topic58 on 2006-04-08
Hi all, I posted a thread a week ago about K3b. The problem is that K3b thinks my CD/DVD-burner wants double-layer DVD:s. I tried to play a double-layer DVD a week ago. And after that K3b went crazy. No way I can burn or erase RW or R. Can someone please help me out with this problem?? There must be a way to change some settings in a file back to single-layer... Tried to uninstall and then re-install K3b, with no success. Maybe a .conf-file somewhere?? Before trying a double-layer DVD everything was smooth with K3b. Getting desperate here - so please help me out someone! I have used Nautilus for DVD-burning the last couple of days, but I can't erase RW in Nautilus. And Gnomebaker doesn't work for me. Using Ubuntu Breezy and Gnome. My burner is a TSSCorpCD/DVDW-TS-H552U.
When trying to erase a DVD-RW I got this message in K3b:
System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
TSSTcorp CD/DVDW TS-H552U US02 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=15 -tao driveropts=burnfree -eject blank=fast -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-10-386

/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/X11/cdrecord: Found DVD media but DVD-R/DVD-RW support code is missing.
/usr/bin/X11/cdrecord: If you need DVD-R/DVD-RW support, ask the Author for cdrecord-ProDVD.
/usr/bin/X11/cdrecord: Free test versions and free keys for personal use are at [ftp://ftp.berlios.de/pub/cdrecord/ProDVD/](ftp://ftp.berlios.de/pub/cdrecord/ProDVD/)
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identifikation : 'CD/DVDW TS-H552U'
Revision       : 'US02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0014
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0014 (current)
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 
Profile: 0x0008 
Using generic SCSI-3/mmc   CD/DVD driver (checks media) (mmc_cd_dvd).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1376256 = 1344 KB
Current Secsize: 2048
Waiting for drive to calm down.
Starting to write CD/DVD at speed 15 in real force BLANK mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
/usr/bin/X11/cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 51 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x51 Qual 0x00 (erase failure) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 13.993s timeout 9600s
Starting to write CD/DVD at speed 15 in real force BLANK mode for single session.
No chance to quit anymore. Operation starts.
/usr/bin/X11/cdrecord: Cannot blank disk, aborting.
/usr/bin/X11/cdrecord: Some drives do not support all blank types.
/usr/bin/X11/cdrecord: Try again with cdrecord blank=all.
This drive or media does not support the 'BLANK media' command

---

### Post by Monster_user on 2006-04-08
Open your home folder, and select "View -> Show hidden files". Then look for either '.k3b', or '.kde/share/apps/k3b'. Just rename that folder, to reset k3b back to its defaults.

> /usr/bin/X11/cdrecord: Found DVD media but DVD-R/DVD-RW support code is missing.
/usr/bin/X11/cdrecord: If you need DVD-R/DVD-RW support, ask the Author for cdrecord-ProDVD.
/usr/bin/X11/cdrecord: Free test versions and free keys for personal use are at [ftp://ftp.berlios.de/pub/cdrecord/ProDVD/](ftp://ftp.berlios.de/pub/cdrecord/ProDVD/)
That is interesting...

---

### Post by topic58 on 2006-04-08
I have found it: .kde/share/apps/k3b
What folder should I change the name on? k3b? Will K3b work after renaming it? And what should I call it? There are no settings in this folder for k3b.

---

### Post by Monster_user on 2006-04-08
No settings file such as "k3bui.conf"?
That is odd. Just change the name to k3b.old, or k3b~. Anything will work, your just "deleting" the old settings, but "backing them up" first.

Do you normally have to put in a password to run k3b? (in which case it would be in the root's home folder '/root/.kde/share/apps/k3b').

Have you checked under both of the K3B config options, in the menu? One is "Configure K3B", and the other is "K3B Setup", or similiar, it may depend on the version your using. You may need to run k3b as a sudoer.

sudo k3b

---

### Post by topic58 on 2006-04-09
Found a file called k3bui.rc under /usr/share/apps/k3b

<!DOCTYPE kpartgui SYSTEM "kpartgui.dtd">
<kpartgui name="k3b" version="5">
<MenuBar>
  <Menu name="project"><text>&amp;Project</text>
  	<Action name="project_add_files" />
	<Action name="project_clear_project" />
  </Menu>

  <Menu name="tools"><text>&amp;Tools</text>
	<Action name="tools_copy_cd" />
  	<Action name="tools_copy_dvd" />
	<Separator />
	<Action name="tools_blank_cdrw" />
	<Action name="tools_format_dvd" />
	<Separator />
	<Action name="tools_write_cd_image" />
	<Action name="tools_write_dvd_iso" />
	<Separator />
	<Action name="tools_encode_video" />
	<Action name="tools_disk_info" />
  </Menu>

  <Menu name="settings">
  	<Action name="view_show_project_view" append="show_merge" />
  	<Action name="view_dir_tree" append="show_merge" />
  	<Action name="view_contents" append="show_merge" />
  	<Action name="view_audio_player" append="show_merge" />
  	<Action name="view_document_header" append="show_merge" />
	<Action name="settings_k3bsetup" append="configure_merge" />
  </Menu>

  <Menu name="help"><text>&amp;Help</text>
	<Action name="help_check_system" />	
  </Menu>
</MenuBar>

<ToolBar name="mainToolBar" noMerge="1"><text>Main Toolbar</text>
	<Action name="file_new" />
	<Action name="file_open" />
	<Action name="file_save" />
</ToolBar>

<ToolBar name="toolsToolBar"><text>Tools</text>
	<Action name="tools_copy_cd" />
	<Action name="tools_clone_cd" />
	<Action name="tools_blank_cdrw" />
	<Action name="tools_format_dvd" />
</ToolBar>
	
<ToolBar name="quickDirSelector" fullWidth="true"><text>Quick Dir Selector</text>
	<Action name="quick_dir_selector" />
	<Action name="go_url" />
</ToolBar>

<State name="state_project_active">
	<enable>
		<Action name="file_save" />
		<Action name="file_save_as" />
		<Action name="file_close" />
		<Action name="file_close_all" />
	  	<Action name="project_add_files" />		
		<Action name="project_clear_project" />
	</enable>
</State>
</kpartgui>
 Don't seem to help much though. But found something under .kde/share/config

[CDRW Erasing]
erase_mode=fast
writer_device=/dev/hdc
writing_app=Auto
writing_speed=0

[Cddb]
cddb server=Http freedb.org:80
cgi path=/~cddb/cddb.cgi
local cddb dirs=~/.cddb/
save cddb entries locally=true
use local cddb query=true
use manual cgi path=false
use remote cddb=false

[DVD image writing]
last written image=$HOME/clabbe/tempCJ/image_film/image.iso

[Devices]
TSSTcorp CD/DVDW TS-H552U=8400,8400,auto,auto
device_search_path=/dev/hdc

[Docking Config]
Main:Geometry=0,0,1075,920
Main:dock=project_view
Main:view=directory_tree,contents_view,project_view
Main:visible=true
NameList=project_view,directory_tree,contents_view,directory_tree\\,contents_view,directory_tree\\,contents_view\\,project_view
Version=0.0.5
contents_view:stayButton=false
contents_view:tabCaption=Contents View
contents_view:tabToolTip=
contents_view:type=DOCK
directory_tree,contents_view,project_view:first_name=directory_tree,contents_view
directory_tree,contents_view,project_view:last_name=project_view
directory_tree,contents_view,project_view:orientation=0
directory_tree,contents_view,project_view:parent=yes
directory_tree,contents_view,project_view:sepPos=4121
directory_tree,contents_view,project_view:stayButton=false
directory_tree,contents_view,project_view:type=GROUP
directory_tree,contents_view:first_name=directory_tree
directory_tree,contents_view:last_name=contents_view
directory_tree,contents_view:orientation=1
directory_tree,contents_view:parent=yes
directory_tree,contents_view:sepPos=2679
directory_tree,contents_view:stayButton=false
directory_tree,contents_view:type=GROUP
directory_tree:stayButton=false
directory_tree:tabCaption=Sidepanel
directory_tree:tabToolTip=
directory_tree:type=DOCK
project_view:stayButton=false
project_view:tabCaption=Project View
project_view:tabToolTip=
project_view:type=DOCK

[External Programs]
cdrdao default=/usr/bin/X11/cdrdao
cdrdao user parameters=
cdrecord default=/usr/bin/X11/cdrecord.mmap
cdrecord user parameters=
dvd+rw-format default=/usr/bin/X11/dvd+rw-format
dvd+rw-format user parameters=
eMovix user parameters=
growisofs default=/usr/bin/X11/growisofs
growisofs user parameters=
mkisofs default=/usr/bin/X11/mkisofs
mkisofs user parameters=
normalize user parameters=
readcd default=/usr/bin/X11/readcd
readcd user parameters=
search path=/usr/bin/,/usr/local/bin/,/usr/sbin/,/usr/local/sbin/,/opt/schily/bin/,/sbin
sox default=/usr/bin/X11/sox
sox user parameters=
tccat user parameters=
tcdecode user parameters=
tcextract user parameters=
tcprobe user parameters=
tcscan user parameters=
transcode user parameters=
vcdxbuild user parameters=
vcdxminfo user parameters=
vcdxrip user parameters=

[General Options]
Allow overburning=false
Audio Output System=arts
Fifo buffer=4
Manual buffer size=false
Manual writing app selection=false
No cd eject=false
Show Document Header=true
Show progress OSD=true
Show splash=true
Temp Dir=/tmp/kde-clabbe
ask_for_saving_changes_on_exit=true
auto rewritable erasing=false
burnfree=true
check system config=true
config version=0.12
current theme=crystal
current_writer=/dev/hdc
hide main window while writing=false

[KFileDialog Settings]
Recent Files=$HOME/clabbe/DVD/The_perfect_storm/the_perfect_storm.iso,$HOME/clabbe/tempCJ/image_film/image.iso

[OSD Position]
Position=0,0
Screen=0

[TipOfDay]
RunOnStart=false
TipLastShown=2005,11,5,19,47,28

[Video project settings]
Play each Sequence/Segment=1
Time to wait after each Sequence/Segment=2
Use Playback Control=false
Use numeric keys to navigate chapters=false

[Welcome Widget]
show info text=true
welcome_actions=file_new_audio,file_new_data,file_new_dvd,tools_copy_cd

[file view]
Separate Directories=false
Show Preview=false
Show hidden files=false
Sort by=Name
Sort case insensitively=true
Sort directories first=true
Sort reversed=false
View Style=Simple
last url=/media/hdd7fat32/

[last used CD Copy]
copies=1
copy cdtext=true
copy mode=normal
delete_images=true
ignore read errors=false
no correction=false
on_the_fly=false
only_create_image=false
paranoia_mode=0
prefer cdtext=false
retries=128
simulate=false
source_device=/dev/hdc
writer_device=/dev/hdc
writing_app=Auto
writing_mode=auto
writing_speed=0

[last used CDRW Erasing]
erase_mode=fast
writer_device=/dev/hdc
writing_app=Auto
writing_speed=0

[last used DVD Formatting]
force=false
quick format=true
writer_device=/dev/hdc
writing_app=Auto
writing_mode=auto
writing_speed=0

[last used DVD image writing]
image path=$HOME/clabbe/DVD/The_perfect_storm/the_perfect_storm.iso
simulate=false
verify_data=false
writer_device=/dev/hdc
writing_app=Auto
writing_mode=auto
writing_speed=0

[last used default audio settings]
cd_text=false
hide_first_track=false
ignore read errors=false
normalize=false
on_the_fly=true
only_create_image=false
paranoia mode=0
read retries=128
remove_image=true
simulate=false
writer_device=/dev/hdc
writing_app=Auto
writing_mode=auto
writing_speed=0

[last used default data settings]
allow 31 character filenames=true
allow beginning period=false
allow lowercase filenames=false
allow multible dots=false
application id=K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM
create TRANS_TBL=false
data_track_mode=auto
discard broken symlinks=false
discard symlinks=false
follow symbolic links=false
force input charset=false
hide TRANS_TBL=false
input charset=iso8859-1
iso_level=2
joliet=true
joliet long=false
max ISO filenames=false
multisession mode=auto
no iSO translation=false
omit trailing period=false
omit version numbers=false
on_the_fly=true
only_create_image=false
preparer=
preserve file permissions=false
publisher=
relaxed filenames=false
remove_image=true
rock_ridge=true
simulate=false
system id=LINUX
udf=false
untranslated filenames=false
verify data=false
volume id=K3b data project
volume set id=
volume set number=1
volume set size=1
white_space_treatment=noChange
whitespace replace string=_
writer_device=/dev/hdc
writing_app=Auto
writing_mode=auto
writing_speed=0

[last used default dvd settings]
allow 31 character filenames=true
allow beginning period=false
allow lowercase filenames=false
allow multible dots=false
application id=K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM
create TRANS_TBL=false
discard broken symlinks=false
discard symlinks=false
follow symbolic links=false
force input charset=false
hide TRANS_TBL=false
input charset=iso8859-1
iso_level=2
joliet=true
joliet long=false
max ISO filenames=false
multisession mode=auto
no iSO translation=false
omit trailing period=false
omit version numbers=false
on_the_fly=true
only_create_image=false
preparer=
preserve file permissions=false
publisher=
relaxed filenames=false
remove_image=true
rock_ridge=true
simulate=false
system id=LINUX
udf=false
untranslated filenames=false
verify data=false
volume id=K3b data project
volume set id=
volume set number=1
volume set size=1
white_space_treatment=noChange
whitespace replace string=_
writer_device=/dev/hdc
writing_app=Auto
writing_mode=auto
writing_speed=0

[main_window_settings]
Height 1200=840
Width 1600=1075

[main_window_settings Toolbar mainToolBar]
Index=0

[main_window_settings Toolbar quickDirSelector]
IconText=IconOnly
Index=2

[main_window_settings Toolbar toolsToolBar]
IconText=IconOnly
Index=1

Maybe something need to be changed in this one?

---

### Post by Monster_user on 2006-04-09
[QUOTE=topic58]Found a file called k3bui.rc under /usr/share/apps/k3b

 Don't seem to help much though. But found something under .kde/share/config[/quote]
No it doesn't. I did expect you to find some other files... I don't normally go mucking around in K3B's config files, so I did not remember where they were. I'm glad you found the right one '.kde/share/config'.

Side note, you left your name in the config when you pasted it... CJ.

I did a little research, and k3B is supposed to use **growisofs** instead of cdrecord for DVDs. However your system is trying to use cdrecord. 

Do a search in '/usr/bin/X11' for "growisofs", just to make sure that it is still present.

[QUOTE=topic58]Starting to write CD/DVD at speed 15 in real force BLANK mode for single session.
No chance to quit anymore. Operation starts.
/usr/bin/X11/cdrecord: Cannot blank disk, aborting.
/usr/bin/X11/cdrecord: Some drives do not support all blank types.
/usr/bin/X11/cdrecord: Try again with cdrecord blank=all.
This drive or media does not support the 'BLANK media' command[/QUOTE]
[QUOTE=topic58][DVD image writing]
last written image=

[Devices]
TSSTcorp CD/DVDW TS-H552U=8400,8400,auto,auto
device_search_path=/dev/hdc

[External Programs][last used DVD Formatting]
force=false
quick format=true
writer_device=/dev/hdc
writing_app=**Auto**
writing_mode=auto
writing_speed=0

[last used DVD image writing]
image path=$HOME
simulate=false
verify_data=false
writer_device=/dev/hdc
writing_app=**Auto**
writing_mode=auto
writing_speed=0[/QUOTE]


You may want to change the "DVD formating" app, to "/usr/bin/X11/dvd+rw-format". Then the DVD writing app to "/usr/bin/X11/growisofs".

That should get it working.

---


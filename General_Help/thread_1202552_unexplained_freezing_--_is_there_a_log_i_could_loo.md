---
title: "unexplained freezing -- is there a log i could look at to identify the cause?"
date: 2009-07-02
forum: General Help
---

### Post by Pitt Stains on 2009-07-02
Hello,

I am running Ubuntu 9.04, and I am getting frequent (pretty much daily) freezing.  I'm working and then all of a sudden my screen locks up, and my mouse and keyboard become unresponsive.  I haven't been able to identify a pattern, but I suspect Firefox is the culprit.

Anyway, I doubt this is the case, but I'm hoping there's some kind of log somewhere that I could look at next time this happens to get some clues as to the source of the problem.  Any suggestions?

Thanks!

---

### Post by lykwydchykyn on 2009-07-02
The system-wide logs are stored in /var/log.

The best ones to start with in this case would probably be syslog and Xorg.0.log.old.

Your session logs are stored in ~/.xsession-errors.  Keep in mind, this gets overwritten every time you log in to a GUI, so if you want to check it out after a freeze-up, you'll want to log in to a text-mode tty and make a copy of the file.

---

### Post by John Cheng on 2009-07-02
When I first installed Ubuntu, my system froze frequently. It turned out to be hardware related and difficult to debug. It might be worthwhile to read about my experience on my [blog]("http://thechong.blogspot.com/2009/04/ubuntu-problems.html"). 

Can you think of any significant changes to your system lately?

---

### Post by Pitt Stains on 2009-07-02
> **lykwydchykyn said:**
> Your session logs are stored in ~/.xsession-errors.  Keep in mind, this gets overwritten every time you log in to a GUI, so if you want to check it out after a freeze-up, you'll want to log in to a text-mode tty and make a copy of the file.

Hmm, I'm a little embarrassed to admit that, even though I've been using Ubuntu for a while, the only way I know how to log in to my laptop is through the GUI (now a server I know what to do with!).  Do I need to hold down some key or something when I start up?

Thanks!

---

### Post by lykwydchykyn on 2009-07-02
> **Pitt Stains said:**
> Hmm, I'm a little embarrassed to admit that, even though I've been using Ubuntu for a while, the only way I know how to log in to my laptop is through the GUI (now a server I know what to do with!).  Do I need to hold down some key or something when I start up?

Thanks!

Hit ctrl-alt-f1 when it gets to the login screen.
ctrl-alt-f7 will take you back to the GUI.

You can also use ctrl-alt-f2 through ctrl-alt-f6 to access text mode logins.

---

### Post by Pitt Stains on 2009-07-02
> **John Cheng said:**
> When I first installed Ubuntu, my system froze frequently. It turned out to be hardware related and difficult to debug. It might be worthwhile to read about my experience on my [blog]("http://thechong.blogspot.com/2009/04/ubuntu-problems.html"). 

Can you think of any significant changes to your system lately?

Thanks, John.  I update the linux headers whenever they get updated, but I haven't made any hardware changes to my machine.

lshw says this about my wifi card:

```
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wmaster0
                version: 61
                serial: 00:1d:e0:b6:df:8d
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=10.6.0.3 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

```

My graphics card is a GeForce 8400M GS, and I'm using the proprietary NVIDIA accerlerated graphics driver (version 180).

I'm not sure how to run the memory tests you describe in your blog, which is unfortunate, because that seemed to solve the problem for you.

I'll write back in a moment with info regarding the suggestions others made.

Thanks for your help!

---

### Post by Pitt Stains on 2009-07-02
I just locked up again.

> **lykwydchykyn said:**
> The system-wide logs are stored in /var/log.

The best ones to start with in this case would probably be syslog and Xorg.0.log.old.


At the end of Xorg.0.log.old, I've got this:
```

(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000b5a4, 0x0000b75c)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x0000b5a4, 0x0000b75c)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000b5a4, 0x0000bf0c)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x0000b5a4, 0x0000bf0c)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0xffffffff, 0x0000bfdc)

```

My understanding is that the WW are warnings.

I couldn't make sense of anything in the syslog, or at least nothing jumped out at me.

> **lykwydchykyn said:**
> Your session logs are stored in ~/.xsession-errors.

Yikes, there's a lot in my .xsession-errors log.
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-p1bi0g/socket
SSH_AUTH_SOCK=/tmp/keyring-p1bi0g/socket.ssh

(gnome-settings-daemon:3378): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3378): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
I/O warning : failed to load external entity "/home/username/.compiz/session/106d812a18c724a42e124654873693329700000032330025"
Failure: Module initalization failed
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
Initializing trackerd...
Tracker-Message: Checking XDG_DATA_HOME is writable and exists
Tracker-Message:   XDG_DATA_HOME is '(null)'
Tracker-Message:   XDG_DATA_HOME set to '/home/username/.local/share'
Tracker-Message:   Path is OK
Tracker-Message: Setting IO priority
Tracker-Message: Setting up monitor for changes to config file:'/home/username/.config/tracker/tracker.cfg'
** (gnome-panel:3455): DEBUG: Adding applet 0.
** (gnome-panel:3455): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:3455): DEBUG: Adding applet 1.
** (gnome-panel:3455): DEBUG: Adding applet 2.
Tracker-Message: Loading defaults into GKeyFile...
Tracker-Message: Legacy config option 'IndexEvolutionEmails' found
Tracker-Message:   This option has been replaced by 'DisabledModules'
Tracker-Message:   Option 'DisabledModules' removed 'evolution'
Tracker-Message: Legacy config option 'IndexThunderbirdEmails' found
Tracker-Message:   This option is no longer supported and has no effect
Tracker-Message: Legacy config option 'SkipMountPoints' found
Tracker-Message:   Option 'IndexMountedDirectories' set to true
Tracker-Message: Setting up stopword list for language code:'en'
Tracker-Message: Setting up stemmer for language code:'en'
Tracker-Message: Checking directory exists:'/home/username/.local/share/tracker/data'
Tracker-Message: Checking directory exists:'/home/username/.cache/tracker'
Tracker-Message: Registering DBus service...
  Name:'org.freedesktop.Tracker'
Starting log:
  File:'/home/username/.local/share/tracker/trackerd.log'
** (gnome-panel:3455): DEBUG: Adding applet 3.
** (gnome-panel:3455): DEBUG: Adding applet 4.
** (gnome-panel:3455): DEBUG: Adding applet 5.
** (gnome-panel:3455): DEBUG: Adding applet 6.
** (gnome-panel:3455): DEBUG: Adding applet 7.
[DEBUG]: NoteManager created with note path "/home/username/.tomboy".
[INFO]: Initializing Mono.Addins
Starting gtk-window-decorator
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG]: 	       Name: Tomboy.Tomboy,0.10
[DEBUG]: 	Description: 
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/Tomboy.exe
** (nm-applet:3467): DEBUG: applet_common_device_state_changed
** (nm-applet:3467): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:3467): DEBUG: applet_common_device_state_changed
** (nm-applet:3467): DEBUG: applet_common_device_state_changed
** (nm-applet:3467): DEBUG: applet_common_device_state_changed
** (nm-applet:3467): DEBUG: foo_client_state_changed_cb
WARNING: The add-in 'Tomboy.Reminder,0.9.1' is trying to extend '/Tomboy/NoteAddins', but there isn't any compatible add-in defining this extension point
** (nm-applet:3467): DEBUG: applet_common_device_state_changed

** (nautilus:3456): WARNING **: Unable to add monitor: Not supported
** (nm-applet:3467): DEBUG: applet_common_device_state_changed
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.ExportToHtmlAddin
[DEBUG]: 	       Name: Export to HTML
[DEBUG]: 	Description: Exports individual notes to HTML.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/ExportToHtml.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.EvolutionAddin
[DEBUG]: 	       Name: Evolution Mail Integration
[DEBUG]: 	Description: Allows you to drag an email from Evolution into a tomboy note.  The message subject is added as a link in the note.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/Evolution.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.BacklinksAddin
[DEBUG]: 	       Name: Backlinks
[DEBUG]: 	Description: See which notes link to the one you're currently viewing.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/Backlinks.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FixedWidthAddin
[DEBUG]: 	       Name: Fixed Width
[DEBUG]: 	Description: Adds fixed-width font style.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FixedWidth.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.PrintNotesAddin
[DEBUG]: 	       Name: Printing Support
[DEBUG]: 	Description: Allows you to print a note.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/PrintNotes.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.StickyNoteImportAddin
[DEBUG]: 	       Name: Sticky Notes Importer
[DEBUG]: 	Description: Import your notes from the Sticky Notes applet.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/StickyNoteImport.dll
[DEBUG]: StickyNoteImporter: Sticky Notes XML file does not exist or is invalid!
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Reminder
[DEBUG]: 	       Name: Reminder
[DEBUG]: 	Description: Allows you to tell Tomboy to pop up a note when you want to be reminded
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /home/username/.tomboy/addins/tomboy-reminder.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.WebDavSyncServiceAddin
[DEBUG]: 	       Name: WebDav Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes to a WebDav URL
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/WebDavSyncService.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FileSystemSyncServiceAddin
[DEBUG]: 	       Name: Local Directory Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes to a local file system path
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FileSystemSyncService.dll
[DEBUG]: Unable to locate 'gnomesu' in your PATH
[DEBUG]: Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG]: Successfully found all system tools
[DEBUG]: Unable to locate 'wdfs' in your PATH
[DEBUG]: Tomboy remote control active.
** (nm-applet:3467): DEBUG: foo_client_state_changed_cb
[DEBUG]: EnableDisable Called: enabling... True
[DEBUG]: Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'
[DEBUG]: Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'
** (gnome-panel:3455): DEBUG: Adding applet 8.
** (gnome-panel:3455): DEBUG: Adding applet 9.
** (gnome-panel:3455): DEBUG: Adding applet 10.
** (gnome-panel:3455): DEBUG: Adding applet 11.

(gnome-panel:3455): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
/usr/lib/python2.6/dist-packages/spectlib/notifier.py:272: DeprecationWarning: PyArray_FromDimsAndDataAndDescr: use PyArray_NewFromDescr.
  for row in pixbuf.get_pixels_array():
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (gnome-panel:3455): DEBUG: Adding applet 12.
** (gnome-panel:3455): DEBUG: Adding applet 13.

(gnome-panel:3455): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 24
evolution-alarm-notify-Message: Setting timeout for 30428 1246579200 1246548772
evolution-alarm-notify-Message:  Thu Jul  2 20:00:00 2009

evolution-alarm-notify-Message:  Thu Jul  2 11:32:52 2009

** (update-notifier:3481): DEBUG: /usr/lib/update-notifier/apt-check returned 22 (security: 8)
** (update-notifier:3481): DEBUG: crashreport_check

/var/lib/python-support/python2.6/dbus/connection.py:242: DeprecationWarning: object.__init__() takes no parameters
  super(Connection, self).__init__(*args, **kwargs)
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
** (update-notifier:3481): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)

```

It's possible the crashes are related to scrolling, whether I'm scrolling in Firefox, or scrolling some other window in Gnome, but I'm not certain about this correlation yet.  This would suggest a graphics card problem, I think.  Yes?

---

### Post by John Cheng on 2009-07-02
It sounds like your hardware has not changed for a while, but I suppose kernel updates could've brought out some problems. So I'll try to suggest some ways to isolate hardware issues. 

Man, as much as I love Linux, it does require a certain amount of frustration to get everything stable. It is nice to just buy an OS and not worry about stability.

**Pitt**, the memtest utility is a part of the Ubutntu ISO. What I did was download an [ISO]("http://www.ubuntu.com/getubuntu/download"). On boot, there is an option to run memtest86. It helped me identify the cause, but my solution was to lower the memory settings. 

To test video, I'd try running the specview test. It will put stress on your video card. If that test doesn't freeze your system. I'd try running with Compiz disabled for 1 day. Compiz does use 3d acceleration, which could subtly trigger a problem. The last thing is to try switching between the 180 and 173 drivers.

I could not find a good test for network/wireless drivers. If you do some googling, you'd probably find netperf as one way to do network testing. However, I'm not sure if that's a more valid test compared to, say, downloading or uploading a large file. 

I don't see much problems in your xsession-errors file. About half of it consists of "debug" statements. Then again, I've never found log files to help much with hardware issues/

Now back to you gut feeling, which is freezing happens when you scroll. I do suspect that it could be a video card problem, which is why I recommend running without compiz. But I'm not sure, because according to Nvidia, this card is supported:

[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

But that may only be for the [185.18.14 driver]("http://www.nvidia.com/object/linux_display_amd64_185.18.14.html"), which is where I got the link from. 

Since this is not my machine, I do not recommending installing new drivers unless you are sure the video card is a problem - either by triggering the problem with a video stress test, or running without problems by disabling compiz.

Do you only have one machine? Sometimes I try to ssh or ping a frozen machine to made sure it is really frozen, not just a freeze of the video system.

---

### Post by Pitt Stains on 2009-07-10
Hey, John,

Thanks for your help and sorry for the delay; it's turned into a busy week for me.  Here's the latest update:

I ran memcheck with no errors, so I think we can rule out memory.

I remembered that I had a problem with this machine before: though the hard drive was brand new, it started showing signs of failure quickly.  After replacing the drive, things ran smoothly for close to a year before the current set of problems came up.  I emailed with the laptop's manufacturer to see if I was still under warranty for a new drive, and the person I spoke with said they'd gotten a lot of reports from users having their hard drives corrupted by tracker (see here for more: [http://ubuntuforums.org/showthread.php?p=7225556](http://ubuntuforums.org/showthread.php?p=7225556)).

So I checked to make sure I had the latest version of tracker-utils, then I ran:

```

tracker-processes -r

```

This command stops tracker and purges all the index files, which apparently is a necessary step for recovering from the problems caused by the buggy tracker-processes.  However, the next day, I experienced another freeze, so this isn't my problem.

So, continuing to follow my suspicion of hard drive issues, I ran the following tests from a live CD to check out the health of my drive:

```

ubuntu@ubuntu:~$ sudo fsck -f
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 232980/9371648 files (1.8% non-contiguous), 8150816/37475620 blocks

```

I'm not sure how to read these results (did it only check 232,980 out of 9,371,648 files?) but it didn't report any errors and it didn't prompt me to correct or ignore any problems.

Then I ran:

```

ubuntu@ubuntu:~$ sudo badblocks /dev/sda1 -o /home/ubuntu/badblocks.txt

```

This one ran for a long time.  When it finished, there was nothing on STDOUT and the file was empty.  So I guess that means no bad blocks.

I've been running Ubuntu off the live CD for over 12 hours now.  If I were running this off my hard drive, it would certainly have locked up by now.  This suggests to me that the problem is not with my hardware per se, but how it is configured.

The suggestion to try to ping/ssh the machine while it appears to be locked up is a good one.  I'll try that next time it goes down.

I haven't tried the specview tests yet because the download was so big -- it scared me off!  Also, I noticed a few times it would freeze when nothing seemed to be going on -- just displaying a web page, no scrolling or typing or anything like that.  So I thought I'd investigate the hard drive health first.  It seems like I'm running out of options, though, so I'm going to have to start exploring this.

Thanks for your help -- I'll post again when I have something to report.  Feel free to post any other insights that may come to you.

-Pitt

---

### Post by lykwydchykyn on 2009-07-10
I would highly suspect a video driver issue here. The only freeze-up experiences I've ever had with Linux in six years involved video/X11 issues, usually due to drivers for video hardware.

The LiveCD does not load the proprietary Nvidia driver, it's using the old nv driver.  Although it will not give you 3D support or compositing (so no desktop effects), it would be worth trying it just to see if the computer doesn't lock up.

To switch to the nv driver:

 - edit xorg.conf as root
```
gksudo gedit /etc/X11/xorg.conf
```
 - change the line that says:
```
Driver "nvidia"
```
 to say:
```
Driver "nv"
```
Then just log out and select "restart X server" from the actions menu.  Or reboot, whatever is easier.

I think you can also switch back using that driver tool GUI app, I'm just not sure of the particulars on that since I"m using Kubuntu.


On the fsck output, I'm not really sure but I THINK what its saying is that it check 232 thousand files out of a POSSIBLE 9 million (in other words, your filesystem can hold 9 million some odd files, but you only have 232 thousand or so).  Not entirely sure, but I'd be pretty impressed if you had 9 million files on your system.

---

### Post by nadamsieee on 2009-07-24
FYI, there is also a simple GUI for viewing log files.

Click System -> Administration -> Log File Viewer

---

### Post by Pitt Stains on 2009-07-24
Sorry for the long delay in my response.

Switching to the nv driver stopped the crashing, but this isn't really an acceptable long-term solution since by all accounts my graphics card should work with the driver.

I'm setting up a new installation on a second hard drive and will resume using the driver once it's complete.

---


---
title: "Software Center Downloads won't start..."
date: 2010-01-07
forum: General Help
---

### Post by Zyrtec on 2010-01-07
I've been trying to download some software stuff off of the Ubuntu Software Center, but every time I try it tells me "Waiting for other software managers to quit", and just sits there at 0%. I've been waiting for 45 minutes for it to start the download of Pidgin.

I looked in the Processes of System Monitor, and I dunno what other Software manager would be running. The only processes that are running are System Monitor... and then the process

"software-center" under the Waiting Channel tab goes from 0 to "do_wait" to "poll_schedule_timeout", and its status goes from Running to Sleeping. 


How can I fix this?

---

### Post by michy99 on 2010-01-07
Are you sure you don't have Synaptic Package Manager, Update Manager or Software Sources open?

---

### Post by Zyrtec on 2010-01-07
Yeah, I'm positive. There is one process running titled "sh" and it's waiting channel is "do_wait". I have no idea if that has anything to do with it, though.

I dunno what to look for...but neither of those programs are open.

---

### Post by michy99 on 2010-01-07
Have you tried rebooting to see if that will fix it?

---

### Post by Zyrtec on 2010-01-07
Yeah, I've done a reboot, and a complete shutdown/restart and it's still the same thing.

---

### Post by michy99 on 2010-01-07
What happens if you try to install from a terminal?```
sudo apt-get update && sudo apt-get install pidgin
```

---

### Post by Zyrtec on 2010-01-07
I'm still pretty new with this whole terminal thing...lol

I ran that code as the same thing, was I supposed to do it separate? Anyways, it did do something...and it got the end and says

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

To be sure, I did the Pidgin part separately, and it does the same thing...

---

### Post by michy99 on 2010-01-07
It is definitely saying that another package manager program is running. What is the output of```
top
```

---

### Post by Sef on 2010-01-07
I had the same problem and this command fixed it for me:

(just copy and paste it into your terminal)

```
sudo dpkg --configure -a
```

---

### Post by NoaHall on 2010-01-07
Run these - one at a time
```
sudo killall apt
sudo killall apt-get
sudo killall aptitude
sudo killall synaptic
sudo killall dpkg
sudo killall software-center
```
Then run
```

sudo apt-get update && sudo apt-get install pidgin
``` again and see if it works.

---

### Post by Zyrtec on 2010-01-07
It won't let me copy and paste it...I'm assuming because it's refreshing itself. 

Under the command column, it lists 

```
Xorg
top
init
kthreadd
migration/0
ksoftirqd/0
watchdog/0
migration/1
ksoftirqd/1
watchdog/1
migration/2
ksoftirqd/2
watchdog/2
migration/3
ksoftirqd/3
watchdog/3
events/0
events/1
events/2
events/3
cpuset
khelper
netns
async/mgr
kintegrityd/0
kintegrityd/1
kintegrityd/2
kintegrityd/3
kblockd/0
kblockd/1
kblockd/2
kblockd/3
kacpid
kacpi_notify
kacpi_hotplug
ata/0
ata/1
ata/2
ata/3
```A couple of commands pop up randomly called Phyo, gnome-panel, apt-check, gnome terminal, and compiz.real

These commands pop up randomly and then go away.

Edit: This is to michy's post of course...lol I was typing this out when the other replies were made.



2nd Edit: Okay, I did what Sef said, and I don't think it worked...reading from what the terminal outputted. There's kind of a lot, but this is what it said...

```
--2010-01-07 19:03:53--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-07 19:04:03--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net [following]
--2010-01-07 19:04:09--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-07 19:04:19--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2010-01-07 19:04:29--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... 194.95.236.6
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net [following]
--2010-01-07 19:04:35--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-07 19:04:45--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net [following]
--2010-01-07 19:04:50--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-07 19:05:00--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2010-01-07 19:05:10--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `nchc.dl.sourceforge.net'
--2010-01-07 19:05:20--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `ufpr.dl.sourceforge.net'
--2010-01-07 19:05:30--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internode.dl.sourceforge.net'
--2010-01-07 19:05:40--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `voxel.dl.sourceforge.net'
--2010-01-07 19:05:50--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2010-01-07 19:06:00--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internap.dl.sourceforge.net'
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer

```

---

### Post by michy99 on 2010-01-07
Sorry, I should have mentioned to use Ctrl+C to stop it and then copy. Anyway, try the other stuff suggested.

---

### Post by NoaHall on 2010-01-07
Now try ```
sudo apt-get install -f
```

---

### Post by Zyrtec on 2010-01-07
Alright, after doing that... I still don't think it worked. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsdl-ttf2.0-0 xorg-driver-fglrx fglrx-kernel-source fakeroot libftdi1
  libsdl-mixer1.2 libmikmod2 dkms patch libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2010-01-07 19:12:22--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-07 19:12:32--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net [following]
--2010-01-07 19:12:37--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-07 19:12:47--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2010-01-07 19:12:57--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... 194.95.236.6
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net [following]
--2010-01-07 19:13:03--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-07 19:13:13--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net [following]
--2010-01-07 19:13:19--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-07 19:13:29--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2010-01-07 19:13:39--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net [following]
--2010-01-07 19:13:44--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-07 19:13:54--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net [following]
--2010-01-07 19:14:00--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-07 19:14:10--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net [following]
--2010-01-07 19:14:16--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-07 19:14:26--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `voxel.dl.sourceforge.net'
--2010-01-07 19:14:36--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2010-01-07 19:14:46--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internap.dl.sourceforge.net'
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What is it doing? It's timing out and aborting, and all kinds of things D:

By the way, I have to get off my Ubuntu system right now, but I'll be on my laptop to check on the thread and all. Thanks for all the help so far, guys!

---

### Post by NoaHall on 2010-01-07
Try ```
sudo apt-get remove ttf-mscorefonts-installer
```

---

### Post by ShadenSys on 2010-02-01
tried all of those and it just gives me "no process found" for each, then tried the "sudo apt-get update && sudo apt-get install pidgin", that one gives me "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem", and when i do that it tells me "dpkg parse error, in file ' /var/lib/dpkg/updates/0002' near like 0: field name '   ".... what does all that mean?

---

### Post by raktarok on 2010-02-02
Looks like the file /var/lib/dpkg/updates/0002 is the source of the problem..

try these - the commands copy the file to the desktop(in case you need it later) and then deletes the file.
```

sudo cp /var/lib/dpkg/updates/0002 ~/Desktop/
sudo rm /var/lib/dpkg/updates/0002
```

Then do this:
```

sudo dpkg --configure -a
```

If you have it working now, remove the file in the desktop.
```
sudo rm ~/Desktop/0002
```

Be careful with the rm command, make sure that you don't mess up the paths.

---


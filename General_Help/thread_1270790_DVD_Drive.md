---
title: "DVD Drive"
date: 2009-09-20
forum: General Help
---

### Post by asbloodrunsblack on 2009-09-20
I am currently using a dell vostro 1510 with ubuntu.
my drive will read cd's but when i put in a dvd it will not recognize it.
i got the unlicensed extras or w/e they are.. but it still does not work

---

### Post by asbloodrunsblack on 2009-09-20
Bump

---

### Post by Tipped OuT on 2009-09-20
> **asbloodrunsblack said:**
> I am currently using a dell vostro 1510 with ubuntu.
my drive will read cd's but when i put in a dvd it will not recognize it.
i got the unlicensed extras or w/e they are.. but it still does not work

If it doesn't recognize the DVD at all (the drive doesn't acknowledge the DVD's existence) then it's a hardware problem. Not Ubuntu.

---

### Post by asbloodrunsblack on 2009-09-20
i had no problem on windows.. so.. yes.. ubuntu

---

### Post by HereInOz on 2009-09-20
If it refuses to read ALL DVDs, then I would suggest a hardware issue.  

If it will read data DVDs but will not play video DVDs, then perhaps you need to install (or re-install) libdvdcss.  (check out Medibuntu). By the sound of it, you already have, but I figured it was worth a mention.

If it does play commercial (stamped) DVDs, but will not read a burnt DVD, then I would suspect an incompatibility between the burner and the reader.

---

### Post by HereInOz on 2009-09-20
Just a thought:  

Install Device Manager (gnome-device-manager in Synaptic), and have a look at what it sees as the optical drive.  Could give you a clue or two.

---

### Post by asbloodrunsblack on 2009-09-20
it won't read commercial dvds... havent checked a burnt dvd

---

### Post by HereInOz on 2009-09-20
I take it you are currently and feverishly sourcing a burnt data DVD for testing?

---

### Post by asbloodrunsblack on 2009-09-20
i don't have a burnt dvd around :(

---

### Post by HereInOz on 2009-09-20
Sometimes life just sucks, doesn't it?

---

### Post by asbloodrunsblack on 2009-09-20
correct.. did get this for you tho

[http://img38.imageshack.us/i/screenshotdevicemanager.png/](http://img38.imageshack.us/i/screenshotdevicemanager.png/)
[IMG]http://img38.imageshack.us/i/screenshotdevicemanager.png/[/IMG]

---

### Post by asbloodrunsblack on 2009-09-20
bump

---

### Post by pcjunkie on 2009-09-20
Has the system got ununtu restricted drivers? VLC? dvdread installed?
Commercial DVD's sometimes don't even work in windows but unless you have all of the right files in Ubuntu, Ubuntu is unable to read the encrypted drive headers. 

ps DRM sucks and it should die by nuking from Orbit.

---

### Post by asbloodrunsblack on 2009-09-21
i'm positive i have all the restricted drivers.. i've tried everything i've seen on every forum and helpsite.. and no luck yet

---

### Post by asbloodrunsblack on 2009-09-21
Bump

---

### Post by asbloodrunsblack on 2009-09-21
Bump

---

### Post by pcjunkie on 2009-09-22
Have you tested a burnt - non encrypted DVD?

---

### Post by asbloodrunsblack on 2009-09-22
burnt dvd didn't work either..

---

### Post by asbloodrunsblack on 2009-09-22
don't know if it matters.. but.. my cd drive is an internal dell slot drive

---

### Post by StuartN on 2009-09-22
> **asbloodrunsblack said:**
> don't know if it matters.. but.. my cd drive is an internal dell slot drive

Beg, borrow or burn a *data* DVD and see what happens.

---

### Post by asbloodrunsblack on 2009-09-22
i had a dvd i burnt from avi's which was unencrypted.. it picks up when i enter a blank dvd into the drive

---

### Post by asbloodrunsblack on 2009-09-23
~Bump~

---

### Post by StuartN on 2009-09-23
1. Run the command **sudo lshw -class disk** and check that your output includes something like **logical name: /dev/dvd1**. If it does not list a dvd then your hardware is not recognised. If it does list a dvd then:

2. Stick a *data* dvd in the drive and check that you can see a directory listing of the files on the disk. If you can not see the directory listing then your hardware is not installed correctly. If you can see the directory listing then:

3. Install gstreamer0.10-plugins-good, gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ugly. Install mplayer.

---

### Post by asbloodrunsblack on 2009-09-23
kris@kris-laptop:~$ sudo lshw -class disk
[sudo] password for kris: 
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD+-RW AD-7640A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: JD05
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-disk
       description: ATA Disk
       product: FUJITSU MJA2160B
       vendor: Fujitsu
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0085
       serial: K950T9625WVL
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=a42d04a3

---

### Post by asbloodrunsblack on 2009-09-23
and i had all those plugins installed :(

---

### Post by StuartN on 2009-09-23
> **asbloodrunsblack said:**
>        logical name: /dev/dvd
       logical name: /dev/dvdrw


You have a dvd drive installed and apparently recognised. If you put a dvd disk with data into the drive then you should be able to browse it with Nautilus, or in the terminal. If you can do that successfully, then your problem is missing codecs for dvd video disks.

---

### Post by asbloodrunsblack on 2009-09-23
idk what codecs i'd be missing.. i have downloaded everything.. and more of what i've been told

---

### Post by asbloodrunsblack on 2009-09-23
need help :(

---

### Post by 3rdalbum on 2009-09-23
libdvdcss2 and non-free-codecs from Medibuntu. VLC from the Ubuntu repositories. Use VLC as your DVD player.

---

### Post by asbloodrunsblack on 2009-09-23
got it and got it... still a negative

---

### Post by asbloodrunsblack on 2009-09-23
p, li { white-space: pre-wrap; }  [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]

[COLOR=#000000][/COLOR]

[COLOR=#000000][/COLOR]
  p, li { white-space: pre-wrap; }  [COLOR=#00008B]*main*[/COLOR][COLOR=#0000FF]* info: *[/COLOR][COLOR=#000000]Running vlc with the default interface. Use 'cvlc' to use vlc without interface.[/COLOR]
 [COLOR=#00008B]*main*[/COLOR][COLOR=#FF0000]* error: *[/COLOR][COLOR=#000000]no access module matched "dvd"[/COLOR]
 [COLOR=#00008B]*main*[/COLOR][COLOR=#FF0000]* error: *[/COLOR][COLOR=#000000]open of `dvd:///dev/sr0' failed: could not create access: no access module matched "dvd"[/COLOR]
 [COLOR=#000000][/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]
[/COLOR]
 [COLOR=#000000][/COLOR]

---

### Post by StuartN on 2009-09-23
1. If you put a commercial dvd in the drive and then navigate to the dvd title, can you see folders AUDIO_TS and VIDEO_TS?

2. There are several VIDEO_TS files and several VTS_01_ files in the VIDEO_TS folder. What happens if you double-click any .VOB file? The VIDEO_TS.VOB (often an intro) is not usually encrypted.

3. Run "mplayer dvd://1" in a terminal and see what error message you get. It is much more informative than the GUI error messages.

---

### Post by asbloodrunsblack on 2009-09-23
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T9500  @ 2.60GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
Couldn't open DVD device: /dev/dvd
No stream found to handle url dvd://1


Exiting... (End of file)
kris@kris-laptop:~$

---

### Post by StuartN on 2009-09-23
> **asbloodrunsblack said:**
> Playing dvd://1.
Couldn't open DVD device: /dev/dvd
No stream found to handle url dvd://1

Did double-clicking on a .VOB file launch and play it? If it did play then you have the codecs.

You could try "mplayer -dvd-device /dev/scd0 dvd://1" which tells mplayer to treat the first CD drive as the DVD.

You could also try "sudo cp /dev/dvd1 /dev/dvd", which will create a /dev/dvd device if one does not exist already.

---

### Post by asbloodrunsblack on 2009-09-23
kris@kris-laptop:~$ mplayer -dvd-device /dev/scd0 dvd://1
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T9500  @ 2.60GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
Couldn't open DVD device: /dev/scd0
No stream found to handle url dvd://1


Exiting... (End of file)
kris@kris-laptop:~$ 
kris@kris-laptop:~$ sudo cp /dev/dvd1 /dev/dvd
[sudo] password for kris: 
cp: cannot stat `/dev/dvd1': No such file or directory

---

### Post by StuartN on 2009-09-23
1. > **StuartN said:**
> Did double-clicking on a .VOB file launch and play it?

2. You seem to have no DVD device setup - run "ls -al /dev/dvd*" to check.

3. Insert a DVD disk, wait for it to settle and then run "mount" and look for a line like "/dev/**scd0** on /media/DVD_VIDEO type udf (ro,nosuid,nodev,uhelper=hal,uid=1000)", where the /dev refers to your cd drive - mine is /dev/scd0, yours might be different.

4. Run "sudo ln -s /dev/**scd0** /dev/dvd" to create a dvd device pointing to your cd drive, where /dev/**scd0** matches your device in 3.

5. Try the "mplayer -dvd-device /dev/scd0 dvd://1" command again with your cd device name.

---

### Post by asbloodrunsblack on 2009-09-23
says unable to mount

---

### Post by StuartN on 2009-09-23
1. Did double-clicking on a .VOB file launch and play it?

2. > **asbloodrunsblack said:**
> says unable to mount

Just the command "mount", with nothing else. It will list all the mounted file systems. Your CD drive should be listed if Linux has detected and mounted a DVD disk.

---

### Post by asbloodrunsblack on 2009-09-23
kris@kris-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kris)




and.. it wont let me explore the disc to even show vob files..

---

### Post by StuartN on 2009-09-23
> **asbloodrunsblack said:**
> and.. it wont let me explore the disc to even show vob files..

There is no CD or DVD disk listed. There must be a DVD disk in the drive tray and Linux must have recognized it before you run "mount", otherwise there is no filesystem.

About three days ago someone asked if you could read the disk directory, in fact it was the very first question...

Go back through the thread and see if you can read an unencrypted, not a video DVD, not a music CD, plain data DVD disk. In about three days time you might get to questions about codecs.

---

### Post by asbloodrunsblack on 2009-09-23
could i get a url please?

---

### Post by asbloodrunsblack on 2009-09-23
bump

---

### Post by StuartN on 2009-09-24
When you have found a disk of any kind (even a music CD) that you can read in your PC, post the results of "mount", "ls -al /dev/cd*" and "ls -al /dev/dv*".

---

### Post by asbloodrunsblack on 2009-09-29
Mount
"kris@kris-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kris)
"

kris@kris-laptop:~$ ls -al /dev/cd*
lrwxrwxrwx 1 root root 3 2009-09-29 00:13 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root 3 2009-09-29 00:13 /dev/cdrw -> sr0

kris@kris-laptop:~$ ls -al /dev/dv*
lrwxrwxrwx 1 root root 3 2009-09-29 00:13 /dev/dvd -> sr0
lrwxrwxrwx 1 root root 3 2009-09-29 00:13 /dev/dvdrw -> sr0

---

### Post by StuartN on 2009-09-29
> **StuartN said:**
> When you have found a disk of any kind (even a music CD) that you can read in your PC, post the results of "mount", "ls -al /dev/cd*" and "ls -al /dev/dv*".

There is no disk file system mounted in your optical drive. Find a disk you can read and try again, and post all the output.

---

### Post by asbloodrunsblack on 2009-09-29
that was an output of an audio cd burnt from ubuntu

---

### Post by StuartN on 2009-09-29
> **asbloodrunsblack said:**
> kris@kris-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kris)


There is only one device, /dev/sda1 (your hard disk), listed. That means that there was no optical disk mounted at the time you ran the mount command.

---

### Post by asbloodrunsblack on 2009-10-02
there was a burnt cd in there

---

### Post by StuartN on 2009-10-02
> **asbloodrunsblack said:**
> there was a burnt cd in there

If it was an audio CD then it will have no filing system (an audio CD is raw sample data and an index). You need to find a data CD, mp3 CD, data DVD, any disk with a filesystem that your computer manages to mount.

But I take it that you can do all of the following: play an audio CD, read the track listing in Nautilus and copy an audio CD?

---

### Post by asbloodrunsblack on 2009-10-02
pretty much. i can burn also though.

---

### Post by asbloodrunsblack on 2009-10-02
bump

---


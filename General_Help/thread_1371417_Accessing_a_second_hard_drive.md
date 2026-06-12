---
title: "Accessing a second hard drive"
date: 2009-12-31
forum: General Help
---

### Post by hakimoerton on 2009-12-31
Now I am really getting pissed off!

Not much help at all from here, the place for help, that's for sure.

Given the paucity of words of wisdom I have reinstalled karmic, formatting the / as part of the re-installation from cd. I have two hard drives. Immediately after the reinstallation I was able to mount the second hard disk with my password.

I then updated repostories; added the medibuntu repository as per the instructions of psychocat's website and updated again.

I have added my wife as a second user and that is it, all I have done.

Now I cannot access the 2nd hard drive (Unable to mount 310 GB Filesystem, authentication is required). Again I visit the System/Admin/Users and Groups, and I am unable to make changes.

Again I ask, what is going on here? Where do I start to look to identify the problem so that I can rectify the problem and once again access that which I used to?

Hakim

---

### Post by hakimoerton on 2010-01-02
Any clues are most welcome!

Logs to check?

Having reinstalled, am I right to assume the problem lies in the /home partition?

Hakim

---

### Post by bapoumba on 2010-01-03
Moved to its own thread.

---

### Post by Leppie on 2010-01-03
you can access the users and groups applet from the cli:
```
$gksudo users-admin
```

you may also want to check your /etc/fstab entries.

---

### Post by hakimoerton on 2010-01-04
This is the content of fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5dec3c4d-e77d-4981-bf0b-44290334c162 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=3517877e-addc-472d-b66b-fdadfbaabd6f /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=b6d2b0a7-e8d3-4db0-affd-b785e0833f02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Thanks for your interest.

Perhaps related or a whole new kettle of ...

Added a new line to software sources and then ran update. Was instructed to run a partial update which failed, then advising me to file a bug report which I did, attaching the [email]hakim@hakim-desktop:/var/log/dist-upgrade/apt.log[/email]

the last few lines of the log are:

Package software-properties-gtk has broken Depends on synaptic
  Considering synaptic 10000 as a solution to software-properties-gtk 1
  Removing software-properties-gtk rather than change synaptic
Investigating python-aptdaemon-gtk
Package python-aptdaemon-gtk has broken Depends on python-aptdaemon
  Considering python-aptdaemon 10000 as a solution to python-aptdaemon-gtk 10000
    Reinst Failed because of python-aptdaemon
  Removing python-aptdaemon-gtk rather than change python-aptdaemon
Investigating ubuntu-desktop
Package ubuntu-desktop has broken Depends on gdebi
  Considering gdebi 10000 as a solution to ubuntu-desktop 10000
  Considering gdebi 10000 as a solution to ubuntu-desktop 10000
Package ubuntu-desktop has broken Depends on language-selector
  Considering language-selector 10000 as a solution to ubuntu-desktop 10000
Package ubuntu-desktop has broken Depends on software-center
  Considering software-center 10000 as a solution to ubuntu-desktop 10000
  Considering software-center 10000 as a solution to ubuntu-desktop 10000
Package ubuntu-desktop has broken Depends on software-properties-gtk
  Considering software-properties-gtk 10000 as a solution to ubuntu-desktop 10000
  Considering software-properties-gtk 10000 as a solution to ubuntu-desktop 10000
Package ubuntu-desktop has broken Depends on synaptic
  Considering synaptic 10000 as a solution to ubuntu-desktop 10000
  Considering synaptic 10000 as a solution to ubuntu-desktop 10000
Package ubuntu-desktop has broken Depends on update-manager
  Considering update-manager 10000 as a solution to ubuntu-desktop 10000
  Considering update-manager 10000 as a solution to ubuntu-desktop 10000
Package ubuntu-desktop has broken Depends on update-notifier
  Considering update-notifier 10000 as a solution to ubuntu-desktop 10000
  Considering update-notifier 10000 as a solution to ubuntu-desktop 10000
Done
ERROR:root:failed to mark 'ubuntu-desktop' for install (E:Unable to correct problems, you have held broken packages.)


I am now off to seach for any info on 'held broken packages'.

Hakim

---

### Post by hakimoerton on 2010-01-06
Searched for 'held broken packages' and came across [http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434) which advises not to accept the offer of a partial upgrade. A couple of posts suggested using 'sudo aptitude update && sudo aptitude safe-upgrade'. I did so after having already accepted the offered 'partial upgrade' and having no joy.

After glibly typing in 'sudo aptitude update && sudo aptitude safe-upgrade' my beloved PC downloaded and updated 980+ packages leaving 8 broken. Being sensible, (tongue in cheek!) I then rebooted to see what effect this marathon had produced.

Machine locks up. Reboot into safe mode - machine locks up but tells me in somewhat amusing terms that my machine is stopped dead. Reboot a couple of times just to make sure and get the same message, which basically says:

Begin loading essential drivers Done
lots of other stuff up to ...
Starting AppArmour profiles  Done
/sbin/init: relocation error:/sbin/init: symbol_abort_messages version GLIBC_PRIVATE not defined in file libc.so.6 with linktime reference
Kernal Panic - not syncing: Attempted to kill init!
Pid: l,comm: init Not tainted 2.6.31.16-heneric #53 Ubuntu
Call Trace and lots of stuff including
printk
panic
find new reaper
forget original parent
exit notify
do exit
?vfs_writev
drm:intelflo_panic *ERROR* Panic occured switching back to text console

(leaving me with one flashing light on my keyboard but little else)

Read forums hoping pointlessly for suggestions; helpful would be good, any would at least be reassuring that I am not alone out here with the reaper and someone who wants to kill my init, my abondoned parents and who knows what else ...

Search forums again. While no answers Do search forums again ...

Download new copy of Ubuntu 9.10, no longer trusting existing CD which has now been reinstalled numerous times. (The joys of a second hard disk with 9.10 RT installed)
Reinstall Ubuntu, manual partitioning, preserve existing /home partition unchanged, format / and change journaling to ext4 from 3. (It was ext4 until a couple of reinstalls ago)

Reboot. Ubuntu One mismatch of some sort. Updates available - ignore for now.
Try to access 2nd hard disk - success.
Install suggested updates.
Reboot
Try to access 2nd hard disk - fail, same as after last 2 reinstalls.
Try to access Users and Groups via System/Administration: Again NO rights, not even to my own stuff!
Seach forums for response - none, solutions, none yet ...

---

### Post by Leppie on 2010-01-06
after burning the ubuntu cd's, did you perform a medium check before installing?

what does synaptic come up with? system>administration>synaptic package manager

---

### Post by warfacegod on 2010-01-06
Sorry for jumping in hakimoerton.

Leppie, a tiny piece of advice. Please don't be offended.

> **Leppie said:**
> you can access the users and groups applet from the cli:
```
$gksudo users-admin
```

you may also want to check your /etc/fstab entries.

When you're posting code, don't put the $ terminal prompt thing in there. When I first started with trying terminal stuff it drove me crazy that no commands worked. It took me a bit to realize that I wasn't supposed to actually type $. I'll betcha lots of others have done this too!

---

### Post by Leppie on 2010-01-06
Warfacegod, I'm not offended by this. However, if you look around on the internet (or even on this forum) you will find that I am by far the only using the leading $ ;)

---

### Post by warfacegod on 2010-01-06
Oh! Thanks for the code by the way. I couldn't remember it and I needed it to fix an unrelated problem. I spent most of yesterday looking for an answer and that I'm not looking, I find it by accident!

And thanks to hakimoerton for starting a thread that I got help from that had nothing to do with my issue. Thanks.

---

### Post by Leppie on 2010-01-06
> **warfacegod said:**
> Oh! Thanks for the code by the way. I couldn't remember it and I needed it to fix an unrelated problem. I spent most of yesterday looking for an answer and that I'm not looking, I find it by accident!

And thanks to hakimoerton for starting a thread that I got help from that had nothing to do with my issue. Thanks.

lol, i'm at a loss now... which code?
anyways, glad to help ;)
(and i'll try to omit the leading $ )

---

### Post by warfacegod on 2010-01-06
> **Leppie said:**
> Warfacegod, I'm not offended by this. However, if you look around on the internet (or even on this forum) you will find that I am by far the only using the leading $ ;)

Could you clarify that, I'm not sure if you're saying you are or are not the only one. 2.5 - 3 years ago, I ran into the $ thing allot. Not as much now but I still see it. I just thought I'd mention it to you because You've helped me twice in the last two days *intentionally and unintentionally* (wow, say that ten times fast! I can't even think it once!), I figured I'd help you help other folk.

The gksudo users-admin you posted here.

---

### Post by Leppie on 2010-01-06
yeah, i've noticed that especially on this forum the $ to represent the prompt isn't used that often anymore. it's actually not only $, but since the root account is disabled by default in ubuntu it's not very likely you'll see the trailing # (root shell prompt).
however, it is a good way to distinguish between the 2. and of course it is still possible to get to the root shell without enabling the root account ;)

---

### Post by warfacegod on 2010-01-06
sudo su Cha! Cha! Cha!

---

### Post by hakimoerton on 2010-01-07
I am glad to have stimulated some discussion between you guys but would really like some help with this ...

---

### Post by DJonsson2008 on 2010-01-07
For accessing a second hard drive I've found 
the following tools helpful.

mountconfig - a KDE gui that vastly simplyfies the process.

ntfs-config - another gui that if working with ntfs drives
              can be a big help.

---

### Post by Leppie on 2010-01-07
have you tried creating a test account to see if the issue replicates?
```
sudo adduser test
```
if you want to put it into the admin groups once created:
```
sudo adduser test adm,admin
```

is this an internal or external drive?

---

### Post by warfacegod on 2010-01-07
Have you checked permissions to see who owns the drive. If it's not you, this will change the ownership to you.

```
sudo chown -R warfacegod:warfacegod /media/drive name
```

Change my name to yours. The first is user name the second is user group. In your case it should be the same.

Then you should put your wife's account under your user group. If that doesn't work, try the code again in her account like this:

```
sudo chown -R hername:yournamme /media/drive name
```

Drive name is to be found in the /medie folder, browse to it and the name is probably some long string of numbers and letters.

(Leppie, I saw Zeitgeist last year, it's excellent.)

---

### Post by hakimoerton on 2010-01-07
I can add users manually as you suggest but not via the GUI. The GUI doesn't seem to recognise my password and I can make no changes. The second drive is internal and the installed ubuntu 9.10 RT works fine and recognises the other disk with no problems (I use the same password on both disks, GRUB gives me a choice of which to boot from).

I am thinking the problem is either a bug in the GUI, or a problem with settings saved in my separate /home partition.

I posted my fstab file contents earlier at your request (I think ...)

---

### Post by hakimoerton on 2010-01-10
I am starting again and remain surprised at the lack of support on this thread. My problem is real and persistent and I would like some input from anyone willing to actually read what I have written before offering half-cocked answers.

I have re-installed three times now and the pattern is the same each time.

The PC has a ASUS P5KPL-CM mother board and an Intel 5200 dual core cpu with 2 gig of ram. I am using onboard sound and graphics chips. Karmic 32bit is the OS. I have two internal hard drives, the first a PATA 320GB and the second a SATA 30GB. The second has Karmic RT and functions perfectly. I can boot from either drive via the GRUB menu.

Problems began when I installed some 'edger' graphic packages. I had random graphic crashes and re-installed.

Since then I have been left with several permission related problems:

1. I cannot access the second drive from the first, the error message being "Unable to mount 310 GB Filesystem  Authentication is required."

2. I cannot make any changes in Administration/Users and Groups as all options are greyed out. I am not able to add users or edit my own permissions.

3. I can sudo from the command line and can change permissions, add users etc from the command line. I can use Synaptic to add or remove packages.

4. Only immediately after a fresh install can I use the all the above normally. As soon as the system is updated after a fresh install, I then have problems 1 & 2 again.

Any clues?

Is this thread better anywhere else?

Hakim

---

### Post by Jackzor on 2010-01-10
try 

gksudo nautilus

When the file browser comes up try to mount it. Dunno if this will work or not. but its the first thing I would try.

---

### Post by hakimoerton on 2010-01-10
"hakim@hakim-desktop:~$ gksudo nautilus
Initializing nautilus-gdu extension

** (nautilus:4824): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4824): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:4824): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing."

I am not sure how to mount the second drive from the command line. I normally use Places and select the partition I want

---

### Post by warfacegod on 2010-01-10
Jackzor's suggestion should have brought up a file browser for you to go to Places with. No need to do it from command line.


And as far as half cocked answers go, Leppie and I were both trying to help you with this to the best of our ability even if we did get side tracked. Making comments like you did seems like it's a little... well, half cocked. 

Besides, I only use the forums when I'm totally cocked, not half cocked.

---

### Post by hakimoerton on 2010-01-11
gksudo nautilus brings up a file browser but there is no option for 'places' and my other drive is not found in gksudo nautilus. In the gui, Places shows the drive but clicking on it give the warning above.

Sorry you were offended but I don't think your conversation helped me one bit. Since we last talked I have installed samba with no change and read through [http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic). The only thing useful there was reference to fstab and If you get a permissions error, try the following:

sudo chown -R user /home/user 

        Note: Replace user with the actual username. This command changes the owner of the folder /home/user to user. -R means "recursively", i.e. including all subfolders. 

The latter did not work with the error message: chown: cannot access `/home/hakim/.gvfs': Permission denied

I presented my fstab file and you guys made no comment on it. I can see that my second disk is not mentioned but you guys made no mention of it ...

Again I say, I think I have a problem that is either related to settings retained in /home on reinstallation, or something goes wrong on an update.

Any help appreciated.
Hakim

---

### Post by warfacegod on 2010-01-11
> sudo chown -R user /home/user

That should read sudo chown -R username:usergroup /media/drivename

Did you use it in the Terminal your way or my way?

---

### Post by warfacegod on 2010-01-11
> gksudo nautilus brings up a file browser but there is no option for 'places' and my other drive is not found in gksudo nautilus.

Places is also the left pane in the file browser. It should look something like this:


yourhomefolder
Desktop
Filesystem
1000 GB Filesy...
Network
etcetera
etcetera...

---

### Post by hakimoerton on 2010-01-11
It gives home folder and filesystem and IPOD which my daughter is currently charging and is extra to what is normally there.

what do you mean by your way or my way?

---

### Post by hakimoerton on 2010-01-11
Sorry, understand now. I did it as typed and now with try your suggestion.

---

### Post by hakimoerton on 2010-01-11
chown: cannot access `/media/sdb': No such file or directory

/Media contains cdrom cdrom0 floppy floppy0 and IPOD

With a default install and udate, the system should have been installed properly. What continues to prevent this? These are symptoms, not the cause.

---

### Post by warfacegod on 2010-01-11
Unplug the usb cord from computer.

Terminal:

```
gksudo nautilus
```

When the file browser comes up plug the usb back in. Does the drive then appear in the left pane?

---

### Post by hakimoerton on 2010-01-11
hakim@hakim-desktop:~$ gksudo nautilus
Initializing nautilus-gdu extension

** (nautilus:3333): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3333): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3333): WARNING **: No marshaller for signature of signal 'ShareCreateError'

Nautilus does show the IPOD and a box asks if I want to open with Rhythmbox.

---

### Post by warfacegod on 2010-01-11
> **hakimoerton said:**
> hakim@hakim-desktop:~$ gksudo nautilus
Initializing nautilus-gdu extension

** (nautilus:3333): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3333): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3333): WARNING **: No marshaller for signature of signal 'ShareCreateError'

Nautilus does show the IPOD and a box asks if I want to open with Rhythmbox.

No need to keep posting the Nautilus:3333 warning thing.

A few questions then off to bed for me. I'll get back to this in the morning. And pardon me if you've post the answers already.

What filesystem is the drive?

Do you have anything on it?

If so do you have drive space and the ability to move the data temporarily?

Do you have Gparted installed?

---

### Post by hakimoerton on 2010-01-11
Drive 1 has 3 partitions /, /swap and /home. 1 & 3 are linux (0x83) ie ext4, and the swap is linus 0x82.

It has data in the /home partition that can be moved to sdb or dvd.

Sleep well.
Hakim from Au where it is 1700 ish.

---

### Post by warfacegod on 2010-01-11
I've read through the thread a couple of times now and I'm staring to think this has to do with your inability to change user settings with User & Groups as you mentioned in your initial post.

I'm also having trouble visualizing your drive set up from reading your fstab post and your descriptions. So, if you are willing, please do this:

Go to System> Admin.> Disk Utility and maximize the window

Is the drive displayed in the left pane? If so, highlight it and take a screen shot and attach it to a post.

Applications> Accessories> Take Screenshot (set delay for 2 seconds)

It should look something like this:

---

### Post by warfacegod on 2010-01-11
Sorry, forgot to attach screenshot in last post.

---

### Post by Leppie on 2010-01-11
I'm starting to think that you may be better off removing and re-installing the whole desktop environment...

could you issue the following command in a terminal, then give a couple of new lines so to mark the start of the mounting process:
```
sudo tail -f /var/log/messages
```
then plug in the usb drive and try to mount it.
after that post the output of the tail command, please.

---

### Post by warfacegod on 2010-01-11
He hasn't specifically stated that it's an external. I thought it was at first but now I think it might be an internal, having reread his first post for the nth time. That's why I asked him for the screenshot.

---

### Post by Leppie on 2010-01-11
if it's not an external, then just try to mount it and post the tail output ;)

---

### Post by warfacegod on 2010-01-11
hakimoerton
I think I *may* have found the culprit.

Go to Applications> System Tools> Configuration Editor> apps> gnome-system-tools> users and check show all. That should fix your Users & Groups changes problem which should then allow you to fix your hard drive permissions problem.

---


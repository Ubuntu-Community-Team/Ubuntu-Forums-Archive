---
title: "Backup to USB: Recommendation Request"
date: 2010-04-05
forum: General Help
---

### Post by windfix on 2010-04-05
I've been on Ubuntu for 3 years, but have not yet found a straightforward, simple, and routine method to do incremental backups of my home directory (on its own partition) to a USB drive that is not continuously connected to my laptop.  One downside of being a Linux user is too MUCH choice sometimes. 

The last thing I tried was Simple Backup... which seemed really cool until it crashed my system by putting a huge file on my system partition (/root/.local/share/Trash/files/2009-04-05_08.30.17.835626.laptop-mckimmy.ful/files.tgz) which both freaked me out and lost me many hours trying to figure out what happened.

There are a lot of backup utilities, but I'd like to know what you recommend, and why.

---

### Post by nothingspecial on 2010-04-05
> **windfix said:**
> I've been on Ubuntu for 3 years, but have not yet found a straightforward, simple, and routine method to do incremental backups of my home directory (on its own partition) to a USB drive that is not continuously connected to my laptop.

If you use fstab, so that the usb drive is mounted at the same point, with the sane permissions etc etc, then you may find it easier.

---

### Post by windfix on 2010-04-05
I can find (backup) and edit fstab, but wouldn't know what to put in there to achieve what you're suggesting.

---

### Post by nothingspecial on 2010-04-05
I`m assuming that the main problem is that the usb drive isn`t connected all the time.

And that if it was, your backup stratergy would work.

If this is not the case, I`m (as it were) barking up the wrong tree.

---

### Post by colorlessprism on 2010-04-05
for something like this rsync is probably the way to go. 
your usb drive is probably mounted in /media under the wonderful name of '[numbersanddashes]&#8217;. 

open a terminal and cd /media/[numbersanddashes]
mkdir <backup name>cd <backup name>

 the home directory is what you want to backup you can type:
rsync -arvu /home

the switches mean.    *a=  archive, **r= recursive, **v= verbose, **u= update*.
 
the first time rsync does take a while  time to copy all of these files and folders,but the next time it&#8217;s run it only adds new stuff. if you run this once a  week only the changes that were made  will be added. if you added several new documents to your home directory, it will only copy those new files.


If you deleted an file you need, you could use Nautilus, browse to the usb and copy it back. but if you delete yout /home directory just rsync it back  by reversing the command:
cd /home
rsync -arvu  /media/[numbersanddashes]/<backup name>/home .

*note the dot at the end! that is not a mistake it must be added*

one thing to remember is rsync copies information exactly, if you copy a 100mb file using rsync it is still 100mb on the backup end

---

### Post by windfix on 2010-04-05
I am learning to use command-line, and understand your suggestion - which I will try.  I'd love to find a GUI that sets this up and looks for my USB-drive, performing the backup the next time it's available.  (I switch my laptop between docks at work and at home daily).

Command line is cool, and I get that it's more flexible and powerful, but I am also on a mission to show education professionals that Ubuntu is a completely viable alternative - and Joe User would just cut and run if I told them to do this at the terminal.

---

### Post by inforce on 2010-04-05
Haven't used it extensively but ['[COLOR="DarkRed"]Back in Time[/COLOR]']("http://backintime.le-web.org/") seems a pretty good GUI to backup to USB drives using rsync.

You can schedule jobs, although I do not know what happens if the drive is not plugged in!

There is a quick tip ['[COLOR="#8b0000"]If you have any network shares mounted[/COLOR]']("http://phoward.com/tag/ubuntu")

Tim

---

### Post by colorlessprism on 2010-04-05
there are a ton of rsync guis out there. even some web interface ones. just type "rsync gui" into google and find one that suits you. you will move more and more into using the terminal for more and more things (Alt+F2 gets you hooked quickly as well), sometimes i even shutdown from the terminal since im already there. good luck

---

### Post by akakingess on 2010-04-05
Grsync is the built-in 'gui' version of rsync and I use it to backup my home folder to an NTFS 'backup' drive that I have permanently mounted via FSTAB, so that I think would be an ideal choice for your situation.

---

### Post by windfix on 2010-04-09
Thanks, I will try grsync.  Any chance you can tell me how to permanently mount via fstab?   My eSATA drive mounts as /mount/RAID.  My fstab contents are:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8842a3b0-be00-4927-b837-9a6be269b924 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=8655381a-d80a-4744-8682-e42354d63a57 /home           ext3    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=6a35447a-4ec9-4c40-b2bc-4438f2174946 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by akakingess on 2010-04-09
Sorry, but I am short on time (got to get to bed to get a couple hours sleep), but check out the official documentation [here]("https://help.ubuntu.com/community/Fstab") and if you can't figure it out, let us know and I will check back in the morning.

---

### Post by windfix on 2010-04-09
Cool, thanks for the link.  I will play with it this evening, pretty sure I can get it.

---

### Post by akakingess on 2010-04-09
> **windfix said:**
> Cool, thanks for the link.  I will play with it this evening, pretty sure I can get it.

I will be watching the forums quite a bit this evening, so please let me know if you need to see the way that I have mine set up or any other questions. Good Luck!!!

---

### Post by windfix on 2010-04-11
I got it to automount withe by adding this line.  Thanks for the link to the fstab documentation.  It does, however, interrupt my boot sequence if that drive is powered off or not plugged in.  Any tips on avoiding that?  It's a laptop and the RAID is only available at home.. not work or elsewhere.

UUID=20C4920CC491E476 /media/RAID ntfs defaults 0 0

---

### Post by akakingess on 2010-04-11
How does it 'interrupt' your boot sequence? It MAY take a few seconds more upon boot looking for that drive/partition, but shouldn't do much more than just slow it down by a few seconds. Let us know if it is more severe than that. Glad you got it to automount, at least we have passed that hurdle, now on to the next one, but I consider this the fun part of the game. Let me know how severely it affects you, but it may have to be one of those things you have to deal with (it shouldn't be that bad, though, so please let us know).

---

### Post by windfix on 2010-04-11
Hmmm. Well, seems that was a one-time issue.  It gave me a message about 'unable to mount a filesystem' and dropped out to a command line, provided me with a key-combo to re-attempt.

On subsequent reboots, it seems fine, so I'll leave well enough alone.  Thanks for the help!

---

### Post by akakingess on 2010-04-11
> **windfix said:**
> Hmmm. Well, seems that was a one-time issue.  It gave me a message about 'unable to mount a filesystem' and dropped out to a command line, provided me with a key-combo to re-attempt.

On subsequent reboots, it seems fine, so I'll leave well enough alone.  Thanks for the help!

Very glad to hear that it seems to be working, but if you have all of your issues resolved within this thread I would just ask that you mark it SOLVED, it is available for you under the thread tools menu at the top of the thread. Other than that, looks great!!! Glad we got you up and running like you wanted. Have fun learning even more :)

---

### Post by windfix on 2010-04-11
Done, thanks for the reminder.  Appreciate you taking the time to help!!

---


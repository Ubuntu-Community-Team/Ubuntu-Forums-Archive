---
title: "Had 20Gb free, now have nothing free, why??"
date: 2011-01-16
forum: General Help
---

### Post by typos1 on 2011-01-16
I have about 20 Gb free on my 160gb hard drive, but lately for some reason, Ubuntu thinks I ve only got a few mb left. 

I ve looked through the filesystem to see what the extra is taken up by, but I cant find anything. Its really strange. 

There is a folder called "lost and found" in filesystem, but access is denied to me strangely.

I know I had about 20Gb left cos I download stuff (legally of course), after its downloaded, I put it on an external hard drive. Thought maybe there could be hidden copies in temp folders and I did find some, but they were only a few mb. I ve changed transmission so it downloads direct to the hard drive, but it tells me there is no sopace left, evven though there is loads of space on it. Transmissikojn seems to be looking at the computer's hard drive rather than the external hard drive, even though it's set to put things on the external one

Anyone know what could be the problem?

---

### Post by oldos2er on 2011-01-16
Can you run **df -h** in a terminal, and post the output here?

---

### Post by corncob on 2011-01-16
Did you copy your downloads to the external drive and then delete them?  They could be in your recycle bin (.Trash) still taking up space.

---

### Post by typos1 on 2011-01-16
jason@jason-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              70G   65G  2.0G  98% /
none                  998M  292K  998M   1% /dev
none                 1005M  3.9M 1001M   1% /dev/shm
none                 1005M  216K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
jason@jason-desktop:~$ 


Hard drive on pc is 2x70 Gb, the other 70 is for windows, it says only 2 Gb is left (I ve deleted some stuff since I posted this thread, was nothing left), thing is a few weeks ago I had approx 20Gb free, so I m confused as to what is now taking up all that space when I put all downloads on an external hard drive.

---

### Post by oldos2er on 2011-01-16
Your root partition is 98% full, so I'd say that's your problem. Try [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by cogier on 2011-01-16
You could try [Ubuntu Tweak]("http://ubuntu-tweak.com/") it has several clean up options to get rid of downloaded packages, kernels etc. (Provided you have the room to install it!)

---

### Post by typos1 on 2011-01-16
Corncob-I regularly empty the trash and I have AWN which tells you how many items are in the trash bin so thats not the prob, thanks though.

Cogier-I have Ubuntu tweak, not used that facility before so will try that, but I checked in var/cache/apt and the only things in there are updates and packages but they only take up less than 1 Gband I cant remember any new kernels from update manger recently.

Oldos2er-I ve tried a few things in the thread you suggested but terminal says I ve put in the wrong password, I havent but it keeps saying I have, I also tried another suggestion in the same thread (something to do with Nautilus I think) and that asked ne for the system password (same as terminal one) and it accepted it, so I really dont know whats going on with my system at the moment.

---

### Post by typos1 on 2011-01-18
Anyone got any more ideas?

---

### Post by Is Mise on 2011-01-18
Have you tried using Disk Usage Analyzer to figure out where the space is going?

---

### Post by oldfred on 2011-01-18
Are you running backups? Are they copied into root?

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by typos1 on 2011-01-19
I ve tried to do several things ion this thread and the disc space thread someone else suggested, but I keep getting weird messages or "access denied". 

If I code "sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB" I find that the prob seems to be that my  /var folder has 43Gb of stuff in and 42Gb of that is .gz or .log files in /var/log.

I ve also used disc usage analyser with the same result. I ve freed some space by deleting old packages etc, but theres about 15Gb that SHOULD be free.

In system monitor it says that theres 3.5 Gb available under the "system" tab but under the "file systems" tab it says there 7.0Gb free but only 3.5 is available.

Also right clicking doesnt give me the delete option anymore, only move to rubbish bin, which means that I cannot delete 2.1Gb of data from the external hard drive's rubbish bin. Seems to me it might be something to do with permissions. I tried emptying lost&found folders a few days ago but it wouldnt let me as it said that user sharing was not enabled, but I checked in users and groups and it was. When I first checked where the prob might be it appeared to be in the lost and found folders, now it seems to be in /var/log. All very strange.

---

### Post by oldfred on 2011-01-19
I saved these notes from other posts incase I ever needed them, but have not used them:


Trash
Here is where these files normally reside.

    * ~/.local/share/Trash User's Trash (hardy and later)
    * ~/.Trash User's Trash (pre-hardy)
    * /root/.local/share/Trash System Trash (hardy and later)
    * /root/.Trash System Trash (pre-hardy):
    * /.local/share/.Trash-1000 NTFS/FAT32/etc: Trash deleted in these partitions is placed in a Trash bin named in accordance with the user deleting the file, e.g. -1000, 1002, -0, etc

rm -rf ~/.local/share/Trash/*

If you get permission problems try to slip a sudo in front of the commands, but be sure that the path is correct.

Sometimes it is necessary to change the ownership of the trash files:
sudo chown -R yourusername /home/yourusername/.local/share/Trash

In a file browser, typing "trash:/" in the location window will take you to the user's trash folder.

---

### Post by typos1 on 2011-01-19
I tried most of those the other day and I had problems.

Tried today coded "sudo chown -R yourusername /home/yourusername/.local/share/Trash" and it kept saying "missing operand after username/home/username/.local/share/Trash"

tried it 3 times.

Then I tried "rm -rf ~/.local/share/Trash/* and that sorted the space probs-Thanks...but I still havent got "delete" back when I right click.


And when I try and delete the trash on the external hard drive it cant delete it and locks the folder!

---

### Post by typos1 on 2011-01-19
I tried most of those the other day and I had problems.

Tried today coded "sudo chown -R yourusername /home/yourusername/.local/share/Trash" and it kept saying "missing operand after username/home/username/.local/share/Trash"

tried it 3 times.

Then I tried "rm -rf ~/.local/share/Trash/* and that sorted the space probs-Thanks...but I still havent got "delete" back when I right click.

And when I ry and delte the trash on the external hard drive it cant delete it and locks the folder!

---

### Post by oldfred on 2011-01-19
Did you have the space after your username? Missing space means it read command wrong and gave error. Best to copy & paste then edit in your username for username.

---

### Post by typos1 on 2011-01-19
Cant edit in a terminal, checked everything letter for letter-it was definately correct, but the rm thing worked, its just that I havent got "delete" back on right click and cant empty the trash on the external hard drive. 

suppose I could try and mod the rm command with the address of the ext hd trash, but dont want to mess anything up!

---

### Post by corncob on 2011-01-19
> **typos1 said:**
> 

Also right clicking doesnt give me the delete option anymore, only move to rubbish bin, which means that I cannot delete 2.1Gb of data from the external hard drive's rubbish bin. 

In the file browser click on Edit, then on Preferences in the drop down menu.  Go to the Behavior tab and check "Include a Delete command that bypasses Trash".

---

### Post by tgm4883 on 2011-01-19
> **typos1 said:**
> I ve tried to do several things ion this thread and the disc space thread someone else suggested, but I keep getting weird messages or "access denied". 

If I code "sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB" **I find that the prob seems to be that my  /var folder has 43Gb of stuff in and 42Gb of that is .gz or .log files in /var/log.**

I ve also used disc usage analyser with the same result. I ve freed some space by deleting old packages etc, but theres about 15Gb that SHOULD be free.

In system monitor it says that theres 3.5 Gb available under the "system" tab but under the "file systems" tab it says there 7.0Gb free but only 3.5 is available.

Also right clicking doesnt give me the delete option anymore, only move to rubbish bin, which means that I cannot delete 2.1Gb of data from the external hard drive's rubbish bin. Seems to me it might be something to do with permissions. I tried emptying lost&found folders a few days ago but it wouldnt let me as it said that user sharing was not enabled, but I checked in users and groups and it was. When I first checked where the prob might be it appeared to be in the lost and found folders, now it seems to be in /var/log. All very strange.

Well there is your problem. What log files are the largest in there? Seems like you have a program that is excessively logging.

---

### Post by typos1 on 2011-01-19
Lol, sorry didnt realise it was so simple, but always had the delete option so never had to do that before. 

Dont know why it happened though, at the same time I lost delete it also changed from single click to open folders to double, I didnt change the settings, they changed themselves!

---

### Post by typos1 on 2011-01-19
Lol, sorry didnt realise it was so simple, but always had the delete option so never had to do that before. 

Dont know why it happened though, at the same time I lost delete it also  changed from single click to open folders to double, I didnt change the  settings, they changed themselves!

---

### Post by typos1 on 2011-01-19
Lol, sorry didnt realise it was so simple, but always had the delete option so never had to do that before. 

Dont know why it happened though, at the same time I lost delete it also  changed from single click to open folders to double, I didnt change the  settings, they changed themselves!

---

### Post by tgm4883 on 2011-01-19
> **typos1 said:**
> I ve tried to do several things ion this thread and the disc space thread someone else suggested, but I keep getting weird messages or "access denied". 

If I code "sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB" **I find that the prob seems to be that my  /var folder has 43Gb of stuff in and 42Gb of that is .gz or .log files in /var/log.**

I ve also used disc usage analyser with the same result. I ve freed some space by deleting old packages etc, but theres about 15Gb that SHOULD be free.

In system monitor it says that theres 3.5 Gb available under the "system" tab but under the "file systems" tab it says there 7.0Gb free but only 3.5 is available.

Also right clicking doesnt give me the delete option anymore, only move to rubbish bin, which means that I cannot delete 2.1Gb of data from the external hard drive's rubbish bin. Seems to me it might be something to do with permissions. I tried emptying lost&found folders a few days ago but it wouldnt let me as it said that user sharing was not enabled, but I checked in users and groups and it was. When I first checked where the prob might be it appeared to be in the lost and found folders, now it seems to be in /var/log. All very strange.

Well there is your problem. What log files are the largest in there? Seems like you have a program that is excessively logging.

---

### Post by corncob on 2011-01-19
I understand why there are multiple posts saying the same thing.  The server seems to hang and you tend to keep pushing the Submit button.  It happened to me the other day on another thread.

---

### Post by typos1 on 2011-01-19
Server kept timing out, so didnt think it had posted, but it had!

It appeared to be log files, tgm4883 but then /log was empty, then it appeared to be /lost&found, but later they showed empty, in the end was trash.

Still very strange that delete/single click settings changed on thier own though!

---

### Post by typos1 on 2011-01-19
Duplicate post!

---

### Post by typos1 on 2011-01-20
Caant understand this-I ve lost 2Gb again, but in /var/log/ I ve got 26Gb worth of stuff. Is this normal?

In /var/log I ve got a folder called "gdm" with a cross by it that is unreadable and "lost&found" in file system is the same.

---

### Post by tgm4883 on 2011-01-20
> **typos1 said:**
> Caant understand this-I ve lost 2Gb again, but in /var/log/ I ve got 26Gb worth of stuff. Is this normal?

In /var/log I ve got a folder called "gdm" with a cross by it that is unreadable and "lost&found" in file system is the same.

26GB in /var/log isn't normal. I'm assuming you mean a lost+found folder rather than a lost&found folder. This might explain lost+found a little better 
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

---

### Post by typos1 on 2011-01-21
Yes I did mean "lost+found".

Not sure how to work out which programe IS escessively logging.

---

### Post by typos1 on 2011-01-21
And I ve tried "rm -rf ~/.local/share/Trash/*" again but its not working.

---

### Post by corncob on 2011-01-21
> **typos1 said:**
> Caant understand this-I ve lost 2Gb again, but in /var/log/ I ve got 26Gb worth of stuff. Is this normal?

In /var/log I ve got a folder called "gdm" with a cross by it that is unreadable and "lost&found" in file system is the same.

gdm =Gnome Display Manager?  I'm running that but have no file named "gdm" in /var/log/ (which, incidentally, only takes up 747 Mb).  There's a link to the mailing list at [http://projects.gnome.org/gdm/](http://projects.gnome.org/gdm/) where you can ask questions of the developers.

---

### Post by typos1 on 2011-01-21
I cant tell how large those files with a cross on are as it says the contents are unreadable. The logs seem to be from a variety of programmes, not just one. All the folders in /log are small, its the masses of little .gz , .1 , .old, .log etc icons that seems to be taking up the space.

---

### Post by corncob on 2011-01-21
> **typos1 said:**
> Lol, sorry didnt realise it was so simple, but always had the delete option so never had to do that before. 

Dont know why it happened though, at the same time I lost delete it also  changed from single click to open folders to double, I didnt change the  settings, they changed themselves!

You can also delete files directly by holding down the SHIFT key while you press DELETE.

---

### Post by typos1 on 2011-01-21
Shift and delete together dont work-nothing happens.

Thanks-have you any idea how I can find out what is causing the problem and how I can stop it?

---

### Post by tgm4883 on 2011-01-21
> **typos1 said:**
> Shift and delete together dont work-nothing happens.

Thanks-have you any idea how I can find out what is causing the problem and how I can stop it?

Well the link I posted indicates the stuff in lost+found is from improper shutdowns and system crashes. So if you system is crashing that is something that shouldn't happen. If you are improperly shutting down, then don't do that.

As for the many small .gz, .1, .log, .old files, how many are you talking here, 30? 300? 3000?

If you have too many, it sounds like logrotate isn't doing it's job.

---

### Post by typos1 on 2011-01-22
My system has never crashed to my knowledge.

Have no idea what an improper shutdown is.

Didnt count the small files, but they take up 26Gb!

---

### Post by corncob on 2011-01-22
> **typos1 said:**
> 
Didnt count the small files, but they take up 26Gb!

In the terminal, cd to the directory in question, for example
```
cd /var
```
Then type
```
du -ah
```
and see if any one file is taking up an outlandish amount of space.  Maybe it could be deleted.  The last line, represented by a dot (.), will be the total size of the working directory (/var in this example).

---

### Post by typos1 on 2011-01-22
No they are virtually all just kilobytes with a couple at about 100 megabaytes, but it all adds up to 39Gb!

---

### Post by corncob on 2011-01-22
> **typos1 said:**
> No they are virtually all just kilobytes with a couple at about 100 megabaytes, but it all adds up to 39Gb!

Must be a lot of files to add up to that!  I don't know what else to say -- just giving the thread a bump.

---

### Post by typos1 on 2011-01-22
I could just try and delete them all, but not sure if I ll mess anything up!

---

### Post by tgm4883 on 2011-01-23
> **typos1 said:**
> I could just try and delete them all, but not sure if I ll mess anything up!

Should be all log files, but some programs may not make the files if they don't already exist. I say do an ls -l of that directory and post the contents here. It sounds like logrotate isn't doing its job, but whatever program is making all of those files may have never set itself up with logrotate.

---

### Post by typos1 on 2011-01-23
Ok, can you give me the exact "ls -l command, I ve not used that one before?-Thanks

---

### Post by decrepit on 2011-01-23
In a terminal, "cd" to the directory, then just ls -l. it will list all the files with their permissions.

> michael@Percy:~$ ls -l
total 40
drwxr-xr-x 2 michael michael 4096 2011-01-21 12:18 Desktop
drwxr-xr-x 3 michael michael 4096 2011-01-12 21:47 Documents
drwxr-xr-x 2 michael michael 4096 2011-01-03 19:57 Downloads
drwx------ 8 michael michael 4096 2010-12-21 18:20 GpsarPro
drwxr-xr-x 2 michael michael 4096 2010-12-22 21:24 Music
drwxr-xr-x 2 michael michael 4096 2010-12-22 22:36 MyHeritage
drwxr-xr-x 3 michael michael 4096 2010-12-22 13:05 Pictures
drwxr-xr-x 2 michael michael 4096 2010-12-21 13:51 Public
drwxr-xr-x 2 michael michael 4096 2010-12-21 13:51 Templates
drwxr-xr-x 2 michael michael 4096 2010-12-21 13:51 Videos
michael@Percy:~$ cd Documents
michael@Percy:~/Documents$ ls -l
total 8
drwxr-xr-x 2 michael michael 4096 2011-01-18 19:04 computer
-rw-r--r-- 1 michael michael 3558 2011-01-12 21:47 dec10 phone bill
michael@Percy:~/Documents$ cd computer
michael@Percy:~/Documents/computer$ ls -l
total 3556
-rw-r--r-- 1 michael michael    2147 2010-12-22 14:25 Dec 10 partion uuid.txt
-rw-r--r-- 1 michael michael    9859 2011-01-09 20:38 fedora8-smb.conf
-rwxrwxrwx 1 michael michael    1293 2006-03-19 16:33 firewalltables
-rwxrwxrwx 1 michael michael 1289216 2006-03-01 13:51 Iptables.doc
-rwxrwxrwx 1 michael michael 2213054 2006-01-29 17:43 iptables-tutorial.html.tgz
-rw-r--r-- 1 michael michael    2397 2011-01-10 20:53 log.nmbd after smb-conf swap
-rw-r--r-- 1 michael michael    6693 2011-01-18 19:04 Masquerade.txt
-rw-r--r-- 1 michael michael      41 2011-01-05 21:36 mount smb shares.txt
-rwxrwxrwx 1 michael michael    1716 2009-03-15 21:34 network-info
-rw-r--r-- 1 michael michael     605 2010-12-27 17:50 realspeed registration.reg
-rwxrwxrwx 1 michael michael   81408 2004-08-22 05:34 Setting up a Local Area Network.doc
-rw-r--r-- 1 michael michael     155 2011-01-09 21:38 start service
-rw-r--r-- 1 michael michael    1224 2011-01-09 22:39 testparm 9-1-11
michael@Percy:~/Documents/computer$ 

---

### Post by typos1 on 2011-01-23
Ok here it is:

jason@jason-desktop:~$ ls -l
total 512
drwxrwxr--  2 jason jason   4096 2009-06-28 12:22 32
drwxrwxr--  2 jason jason   4096 2009-06-28 12:22 64
drwxrwxr--  3 jason jason   4096 2010-12-05 17:15 amsn_received
drwxr-xr-x  2 jason jason   4096 2010-10-24 21:17 Audiobooks
-rw-r--r--  1 jason jason    666 2010-08-26 21:05 audio.cddb
-rw-r--r--  1 jason jason   1274 2010-08-26 21:05 audio.cdindex
drwxr-xr-x  2 jason jason   4096 2010-03-27 14:17 bin
drwxrwxr--  8 jason jason  12288 2011-01-22 15:55 Desktop
drwxrwxr--  7 jason jason   4096 2011-01-11 13:51 Documents
-rwxrwxr--  1 jason jason    247 2000-02-03 03:12 Dte.exe.lnk
drwxr-xr-x  3 jason jason   4096 2010-11-15 21:18 dvdrip-data
drwxrwxr--  2 jason jason   4096 2009-07-09 22:44 dwhelper
-rw-r--r--  1 jason jason    128 2010-11-20 17:56 edid.bin
-rwxrwxr--  1 jason jason    551 2008-05-16 12:54 ePER.lnk
-rwxrwxr--  1 jason jason    357 2009-06-25 21:31 examples.desktop
drwxrwxr--  3 jason jason  12288 2010-08-08 02:40 Funny Stuff
drwxrwxr--  4 jason jason   4096 2009-07-05 19:28 GNUstep
drwxrwxr--  5 jason jason   4096 2009-06-28 12:24 java
drwxr-xr-x  4 jason jason   4096 2010-10-23 22:18 mplayer_build
drwxrwxr-- 18 jason jason   4096 2010-12-03 23:11 Music
drwxrwxr--  5 jason jason   4096 2009-06-28 00:49 omniabackup
-rw-------  1 jason jason      0 2010-03-20 19:50 out_8zpxOD
-rw-------  1 jason jason      0 2010-03-20 19:50 out_d1V0YM
drwxrwxr--  5 jason jason   4096 2010-05-11 20:58 Phone
drwxrwxr--  8 jason jason   4096 2010-11-05 23:14 Pictures
drwxr-xr-x  2 jason jason   4096 2010-05-02 15:00 Podcasts
-rw-r--r--  1 jason jason    180 2010-08-11 21:11 references.bib
drwxrwxr--  7 jason jason   4096 2009-01-10 21:13 synce-gnomevfs-0.13
drwxrwxr--  2 jason jason   4096 2009-06-25 21:38 Templates
drwxrwxr-- 12 jason jason   4096 2009-08-24 17:02 thunderbird
drwxr-xr-x  2 jason jason   4096 2010-03-19 01:31 Video Projects
drwxr-xr-x  2 jason jason   4096 2010-05-02 15:00 Videos
-rw-r--r--  1 jason jason 190672 2010-11-06 04:43 winetricks
-rw-r--r--  1 jason jason 190672 2010-11-06 04:43 winetricks.1

---

### Post by tgm4883 on 2011-01-23
> **typos1 said:**
> Ok here it is:

jason@jason-desktop:~$ ls -l
total 512
drwxrwxr--  2 jason jason   4096 2009-06-28 12:22 32
drwxrwxr--  2 jason jason   4096 2009-06-28 12:22 64
drwxrwxr--  3 jason jason   4096 2010-12-05 17:15 amsn_received
drwxr-xr-x  2 jason jason   4096 2010-10-24 21:17 Audiobooks
-rw-r--r--  1 jason jason    666 2010-08-26 21:05 audio.cddb
-rw-r--r--  1 jason jason   1274 2010-08-26 21:05 audio.cdindex
drwxr-xr-x  2 jason jason   4096 2010-03-27 14:17 bin
drwxrwxr--  8 jason jason  12288 2011-01-22 15:55 Desktop
drwxrwxr--  7 jason jason   4096 2011-01-11 13:51 Documents
-rwxrwxr--  1 jason jason    247 2000-02-03 03:12 Dte.exe.lnk
drwxr-xr-x  3 jason jason   4096 2010-11-15 21:18 dvdrip-data
drwxrwxr--  2 jason jason   4096 2009-07-09 22:44 dwhelper
-rw-r--r--  1 jason jason    128 2010-11-20 17:56 edid.bin
-rwxrwxr--  1 jason jason    551 2008-05-16 12:54 ePER.lnk
-rwxrwxr--  1 jason jason    357 2009-06-25 21:31 examples.desktop
drwxrwxr--  3 jason jason  12288 2010-08-08 02:40 Funny Stuff
drwxrwxr--  4 jason jason   4096 2009-07-05 19:28 GNUstep
drwxrwxr--  5 jason jason   4096 2009-06-28 12:24 java
drwxr-xr-x  4 jason jason   4096 2010-10-23 22:18 mplayer_build
drwxrwxr-- 18 jason jason   4096 2010-12-03 23:11 Music
drwxrwxr--  5 jason jason   4096 2009-06-28 00:49 omniabackup
-rw-------  1 jason jason      0 2010-03-20 19:50 out_8zpxOD
-rw-------  1 jason jason      0 2010-03-20 19:50 out_d1V0YM
drwxrwxr--  5 jason jason   4096 2010-05-11 20:58 Phone
drwxrwxr--  8 jason jason   4096 2010-11-05 23:14 Pictures
drwxr-xr-x  2 jason jason   4096 2010-05-02 15:00 Podcasts
-rw-r--r--  1 jason jason    180 2010-08-11 21:11 references.bib
drwxrwxr--  7 jason jason   4096 2009-01-10 21:13 synce-gnomevfs-0.13
drwxrwxr--  2 jason jason   4096 2009-06-25 21:38 Templates
drwxrwxr-- 12 jason jason   4096 2009-08-24 17:02 thunderbird
drwxr-xr-x  2 jason jason   4096 2010-03-19 01:31 Video Projects
drwxr-xr-x  2 jason jason   4096 2010-05-02 15:00 Videos
-rw-r--r--  1 jason jason 190672 2010-11-06 04:43 winetricks
-rw-r--r--  1 jason jason 190672 2010-11-06 04:43 winetricks.1

You didn't change to the /var/log directory first as the previous poster said. 

Do a 
```
ls -l /var/log/
```

And use code tags when you post it.

---

### Post by typos1 on 2011-01-23
Soz, did it and its a bit bigger than yours! 

jason@jason-desktop:~$ ls -l /var/log/
total 44419436
-rw-r--r-- 1 root              root        1963 2011-01-20 13:16 alternatives.log
-rw-r--r-- 1 root              root        7515 2010-12-14 10:51 alternatives.log.1
-rw-r--r-- 1 root              root        1295 2010-11-30 17:32 alternatives.log.2.gz
-rw-r--r-- 1 root              root        5352 2010-10-29 13:07 alternatives.log.3.gz
drwxr-xr-x 2 root              root        4096 2009-04-08 15:40 apparmor
drwxr-xr-x 2 root              root        4096 2011-01-01 12:33 apt
-rw-r--r-- 1 root              root           0 2009-10-22 17:38 aptitude
-rw-r--r-- 1 root              root         236 2009-10-22 17:33 aptitude.1.gz
-rw-r----- 1 syslog            adm        78537 2011-01-23 22:27 auth.log
-rw-r----- 1 syslog            adm       191290 2011-01-19 14:04 auth.log.1
-rw-r----- 1 syslog            adm         6425 2011-01-09 00:17 auth.log.3.gz
-rw-r----- 1 syslog            adm         4575 2011-01-02 13:17 auth.log.4.gz
-rw-r----- 1 syslog            adm        34684 2009-09-30 11:18 auth.log.6.gz
-rw-r----- 1 syslog            adm        26018 2009-09-21 12:13 auth.log.7.gz
-rw-r----- 1 root              adm           31 2009-04-20 15:00 boot
-rw-r--r-- 1 root              root         801 2011-01-23 17:06 boot.log
-rw-r--r-- 1 root              root       38772 2009-04-20 15:01 bootstrap.log
-rw-rw---- 1 root              utmp         384 2011-01-18 14:40 btmp
-rw-rw---- 1 root              utmp         114 2010-12-23 11:00 btmp.1.gz
-rw-r--r-- 1 root              root           0 2010-03-04 13:45 checkbox.log
-rw-r--r-- 1 root              root       56434 2010-03-04 13:45 checkbox.log.1
-rw-r--r-- 1 root              root        4241 2009-12-24 13:03 checkbox.log.2.gz
-rw-r--r-- 1 root              root        1149 2009-08-08 15:20 checkbox.log.3.gz
-rw-r--r-- 1 root              root        1130 2009-06-26 11:50 checkbox.log.4.gz
drwxr-xr-x 2 root              root        4096 2011-01-01 12:33 ConsoleKit
drwxr-xr-x 2 root              root        4096 2011-01-08 11:45 cups
-rw-r----- 1 syslog            adm       210837 2011-01-23 22:27 daemon.log
-rw-r----- 1 syslog            adm       438690 2011-01-19 14:12 daemon.log.1
-rw-r----- 1 syslog            adm        11403 2011-01-09 00:00 daemon.log.3.gz
-rw-r----- 1 syslog            adm        14457 2011-01-02 13:07 daemon.log.4.gz
-rw-r----- 1 syslog            adm       212127 2011-01-23 23:00 debug
-rw-r----- 1 syslog            adm       431299 2011-01-19 13:53 debug.1
-rw-r----- 1 syslog            adm         9154 2011-01-09 00:01 debug.3.gz
-rw-r----- 1 syslog            adm        15959 2011-01-02 13:07 debug.4.gz
drwxr-xr-x 5 root              root        4096 2010-10-10 20:24 dist-upgrade
-rw-r--r-- 1 root              root       30471 2010-07-13 14:48 dkms_autoinstaller
-rw-r----- 1 root              adm        51938 2011-01-23 17:06 dmesg
-rw-r----- 1 root              adm        50091 2011-01-23 13:38 dmesg.0
-rw-r----- 1 root              adm        13684 2011-01-22 10:56 dmesg.1.gz
-rw-r----- 1 root              adm        13452 2011-01-22 10:54 dmesg.2.gz
-rw-r----- 1 root              adm        13513 2011-01-22 10:52 dmesg.3.gz
-rw-r----- 1 root              adm        14514 2011-01-21 14:10 dmesg.4.gz
-rw-r--r-- 1 root              root      108892 2011-01-21 10:39 dpkg.log
-rw-r--r-- 1 root              root       95595 2010-12-29 12:17 dpkg.log.1
-rw-r--r-- 1 root              root        8704 2010-04-30 16:36 dpkg.log.10.gz
-rw-r--r-- 1 root              root       16079 2010-03-30 16:24 dpkg.log.11.gz
-rw-r--r-- 1 root              root        8881 2010-02-27 16:21 dpkg.log.12.gz
-rw-r--r-- 1 root              root       19565 2010-11-30 17:32 dpkg.log.2.gz
-rw-r--r-- 1 root              root      153504 2010-10-29 13:07 dpkg.log.3.gz
-rw-r--r-- 1 root              root       14330 2010-09-30 12:03 dpkg.log.4.gz
-rw-r--r-- 1 root              root       15184 2010-08-25 14:01 dpkg.log.5.gz
-rw-r--r-- 1 root              root        1145 2010-08-01 23:50 dpkg.log.6.gz
-rw-r--r-- 1 root              root      152804 2010-07-27 14:50 dpkg.log.7.gz
-rw-r--r-- 1 root              root        5512 2010-07-02 12:09 dpkg.log.8.gz
-rw-r--r-- 1 root              root        4851 2010-05-26 15:09 dpkg.log.9.gz
-rw-r--r-- 1 root              root       32032 2010-11-28 14:30 faillog
-rw-r--r-- 1 root              root        3414 2010-12-23 11:09 fontconfig.log
drwxr-xr-x 2 root              root        4096 2009-04-20 15:00 fsck
drwxrwx--T 2 root              gdm         4096 2011-01-23 17:06 gdm
-rw-r--r-- 1 root              root         671 2010-04-21 12:28 gufw_log.txt
drwxr-xr-x 2 root              root        4096 2009-06-25 21:33 installer
-rw-r--r-- 1 root              root           0 2010-10-23 15:04 jockey.log
-rw-r--r-- 1 root              root       62349 2010-10-23 15:04 jockey.log.1
-rw-r--r-- 1 root              root        3251 2010-03-02 01:01 jockey.log.10.gz
-rw-r--r-- 1 root              root        3192 2010-10-16 11:22 jockey.log.2.gz
-rw-r--r-- 1 root              root        3207 2010-10-12 16:34 jockey.log.3.gz
-rw-r--r-- 1 root              root        3156 2010-10-11 12:57 jockey.log.4.gz
-rw-r--r-- 1 root              root        3442 2010-09-27 11:17 jockey.log.5.gz
-rw-r--r-- 1 root              root        3398 2010-09-19 13:23 jockey.log.6.gz
-rw-r--r-- 1 root              root        3402 2010-09-15 11:40 jockey.log.7.gz
-rw-r--r-- 1 root              root        3440 2010-08-18 00:32 jockey.log.8.gz
-rw-r--r-- 1 root              root        3392 2010-08-10 09:53 jockey.log.9.gz
-rw-r----- 1 syslog            adm   5591986143 2011-01-23 23:06 kern.log
-rw-r----- 1 syslog            adm   7261044296 2011-01-19 14:14 kern.log.1
-rw-r----- 1 syslog            adm    461983970 2011-01-09 00:32 kern.log.3.gz
-rw-r----- 1 syslog            adm     93660338 2011-01-02 13:31 kern.log.4.gz
-rw-r----- 1 syslog            adm       155899 2009-08-13 16:01 kern.log.6.gz
-rw-r----- 1 syslog            adm        56854 2009-07-23 15:51 kern.log.7.gz
-rw-rw-r-- 1 root              utmp      292292 2010-11-28 14:30 lastlog
-rw-r----- 1 syslog            adm          309 2011-01-21 14:10 lpr.log
-rw-r----- 1 syslog            adm          309 2011-01-20 13:29 lpr.log.1
-rw-r----- 1 syslog            adm          131 2011-01-10 17:07 lpr.log.2.gz
-rw-r----- 1 syslog            adm          131 2010-12-24 10:22 lpr.log.3.gz
-rw-r----- 1 syslog            adm          131 2010-12-01 13:23 lpr.log.4.gz
-rw-r----- 1 syslog            adm            0 2009-04-20 15:01 mail.err
-rw-r----- 1 syslog            adm            0 2009-04-20 15:01 mail.info
-rw-r----- 1 syslog            adm            0 2009-04-20 15:01 mail.log
-rw-r----- 1 syslog            adm            0 2009-04-20 15:01 mail.warn
-rw-r----- 1 syslog            adm   5591756336 2011-01-23 23:06 messages
-rw-r----- 1 syslog            adm   7260560894 2011-01-19 14:14 messages.1
-rw-r----- 1 syslog            adm    461973741 2011-01-09 00:32 messages.2.gz
-rw-r----- 1 syslog            adm     93641250 2011-01-02 13:31 messages.3.gz
-rw-r----- 1 syslog            adm    153810634 2010-12-26 11:34 messages.4.gz
-rw-r----- 1 syslog            adm        12808 2009-07-23 16:12 messages.6.gz
-rw-r----- 1 syslog            adm        51174 2009-07-02 03:48 messages.7.gz
drwxr-xr-x 2 mpd               audio       4096 2010-12-05 11:17 mpd
drwxr-sr-x 2 news              news        4096 2009-04-20 15:01 news
-rw-r--r-- 1 root              root      229542 2011-01-23 22:27 pm-powersave.log
-rw-r--r-- 1 root              root      325115 2011-01-01 12:17 pm-powersave.log.1
-rw-r--r-- 1 root              root        2408 2010-12-01 13:23 pm-powersave.log.2.gz
-rw-r--r-- 1 root              root        2624 2010-11-02 13:45 pm-powersave.log.3.gz
-rw-r--r-- 1 root              root         425 2010-10-01 00:44 pm-powersave.log.4.gz
-rw-r--r-- 1 root              root      501363 2011-01-23 22:27 pm-suspend.log
-rw-r--r-- 1 root              root      609710 2011-01-01 12:17 pm-suspend.log.1
-rw-r--r-- 1 root              root       18196 2010-12-01 04:12 pm-suspend.log.2.gz
-rw-r--r-- 1 root              root       20779 2010-11-02 02:43 pm-suspend.log.3.gz
-rw-r--r-- 1 root              root        6115 2010-10-01 00:44 pm-suspend.log.4.gz
-rw-r--r-- 1 root              root      126566 2011-01-04 07:56 popularity-contest
-rw-r--r-- 1 root              root      126706 2010-12-28 10:43 popularity-contest.0
-rw-r--r-- 1 root              root       33534 2010-12-21 16:29 popularity-contest.1.gz
-rw-r--r-- 1 root              root       33486 2010-12-14 10:52 popularity-contest.2.gz
-rw-r--r-- 1 root              root       33391 2010-12-07 15:13 popularity-contest.3.gz
-rw-r--r-- 1 root              root       33282 2010-11-30 17:24 popularity-contest.4.gz
-rw-r--r-- 1 root              root       33365 2010-11-23 13:08 popularity-contest.5.gz
-rw-r--r-- 1 root              root       33267 2010-11-16 10:36 popularity-contest.6.gz
-rw-r----- 1 root              adm            0 2009-07-12 18:24 ppp-connect-errors
-rw-r--r-- 1 root              root         323 2010-07-13 20:59 pycentral.log
drwxr-x--- 3 root              adm         4096 2011-01-19 14:19 samba
drwxr-xr-x 2 speech-dispatcher root        4096 2009-10-13 06:27 speech-dispatcher
-rw-r----- 1 syslog            adm   2576431758 2011-01-23 23:06 syslog
-rw-r----- 1 syslog            adm   1878889251 2011-01-21 10:41 syslog.1
-rw-r----- 1 syslog            adm     76664887 2011-01-20 11:48 syslog.2.gz
-rw-r----- 1 syslog            adm     50605445 2011-01-19 14:10 syslog.3.gz
-rw-r----- 1 syslog            adm    291102560 2011-01-18 15:04 syslog.4.gz
-rw-r----- 1 syslog            adm     31288440 2011-01-12 12:17 syslog.5.gz
-rw-r----- 1 syslog            adm     35860571 2011-01-10 13:35 syslog.6.gz
-rw-r----- 1 syslog            adm      8305933 2011-01-09 00:30 syslog.7.gz
-rw-r--r-- 1 root              root      284392 2011-01-23 17:06 udev
-rw-r----- 1 syslog            adm   5588980541 2011-01-23 23:06 ufw.log
-rw-r----- 1 syslog            adm   7261447473 2011-01-19 14:19 ufw.log.1
-rw-r----- 1 syslog            adm    461881059 2011-01-09 00:34 ufw.log.2.gz
-rw-r----- 1 syslog            adm     93239339 2011-01-02 13:32 ufw.log.3.gz
-rw-r----- 1 syslog            adm    153825494 2010-12-26 11:37 ufw.log.4.gz
drwxr-xr-x 2 root              root        4096 2009-03-02 10:07 unattended-upgrades
-rw-r----- 1 syslog            adm        40089 2011-01-23 22:27 user.log
-rw-r----- 1 syslog            adm        74430 2011-01-19 00:51 user.log.1
-rw-r----- 1 syslog            adm         1125 2011-01-09 00:00 user.log.3.gz
-rw-r----- 1 syslog            adm         2136 2011-01-02 13:07 user.log.4.gz
-rw-r--r-- 1 root              root           0 2010-10-10 12:55 wpa_supplicant.log
-rw-r--r-- 1 root              root          20 2010-10-09 15:07 wpa_supplicant.log.1.gz
-rw-r--r-- 1 root              root          20 2010-10-08 12:23 wpa_supplicant.log.2.gz
-rw-r--r-- 1 root              root          20 2010-10-07 12:34 wpa_supplicant.log.3.gz
-rw-r--r-- 1 root              root          20 2010-10-06 12:09 wpa_supplicant.log.4.gz
-rw-r--r-- 1 root              root          20 2010-10-05 11:54 wpa_supplicant.log.5.gz
-rw-rw-r-- 1 root              utmp      132096 2011-01-23 23:06 wtmp
-rw-rw-r-- 1 root              utmp        6020 2010-12-31 13:43 wtmp.1.gz
-rw-r--r-- 1 root              root       16291 2011-01-23 22:27 Xorg.0.log
-rw-r--r-- 1 root              root       16261 2011-01-23 17:05 Xorg.0.log.old
-rw-r--r-- 1 root              root       19420 2011-01-16 17:48 Xorg.1.log
-rw-r--r-- 1 root              root       16134 2010-11-12 12:59 Xorg.1.log.old
-rw-r--r-- 1 root              root        6759 2010-10-04 10:57 Xorg.2.log
-rw-r--r-- 1 root              root        6759 2010-10-03 11:50 Xorg.2.log.old
-rw-r--r-- 1 root              root        6759 2010-10-04 10:57 Xorg.3.log
-rw-r--r-- 1 root              root        6759 2010-10-03 11:50 Xorg.3.log.old
-rw-r--r-- 1 root              root        6759 2010-10-04 10:57 Xorg.4.log
-rw-r--r-- 1 root              root        6759 2010-10-03 11:50 Xorg.4.log.old
-rw-r--r-- 1 root              root        6759 2010-10-04 10:57 Xorg.5.log
-rw-r--r-- 1 root              root        6759 2010-10-03 11:50 Xorg.5.log.old
-rw-r--r-- 1 root              root       37084 2010-10-04 10:57 Xorg.failsafe.log
-rw-r--r-- 1 root              root       37084 2010-10-03 11:50 Xorg.failsafe.log.old
jason@jason-desktop:~$

---

### Post by tgm4883 on 2011-01-23
> **typos1 said:**
> Soz, did it and its a bit bigger than yours! 

jason@jason-desktop:~$ ls -l /var/log/
total 44419436
-rw-r--r-- 1 root              root        1963 2011-01-20 13:16 alternatives.log
-rw-r--r-- 1 root              root        7515 2010-12-14 10:51 alternatives.log.1
-rw-r--r-- 1 root              root        1295 2010-11-30 17:32 alternatives.log.2.gz
-rw-r--r-- 1 root              root        5352 2010-10-29 13:07 alternatives.log.3.gz
drwxr-xr-x 2 root              root        4096 2009-04-08 15:40 apparmor
drwxr-xr-x 2 root              root        4096 2011-01-01 12:33 apt
-rw-r--r-- 1 root              root           0 2009-10-22 17:38 aptitude
-rw-r--r-- 1 root              root         236 2009-10-22 17:33 aptitude.1.gz
-rw-r----- 1 syslog            adm        78537 2011-01-23 22:27 auth.log
-rw-r----- 1 syslog            adm       191290 2011-01-19 14:04 auth.log.1
-rw-r----- 1 syslog            adm         6425 2011-01-09 00:17 auth.log.3.gz
-rw-r----- 1 syslog            adm         4575 2011-01-02 13:17 auth.log.4.gz
-rw-r----- 1 syslog            adm        34684 2009-09-30 11:18 auth.log.6.gz
-rw-r----- 1 syslog            adm        26018 2009-09-21 12:13 auth.log.7.gz
-rw-r----- 1 root              adm           31 2009-04-20 15:00 boot
-rw-r--r-- 1 root              root         801 2011-01-23 17:06 boot.log
-rw-r--r-- 1 root              root       38772 2009-04-20 15:01 bootstrap.log
-rw-rw---- 1 root              utmp         384 2011-01-18 14:40 btmp
-rw-rw---- 1 root              utmp         114 2010-12-23 11:00 btmp.1.gz
-rw-r--r-- 1 root              root           0 2010-03-04 13:45 checkbox.log
-rw-r--r-- 1 root              root       56434 2010-03-04 13:45 checkbox.log.1
-rw-r--r-- 1 root              root        4241 2009-12-24 13:03 checkbox.log.2.gz
-rw-r--r-- 1 root              root        1149 2009-08-08 15:20 checkbox.log.3.gz
-rw-r--r-- 1 root              root        1130 2009-06-26 11:50 checkbox.log.4.gz
drwxr-xr-x 2 root              root        4096 2011-01-01 12:33 ConsoleKit
drwxr-xr-x 2 root              root        4096 2011-01-08 11:45 cups
-rw-r----- 1 syslog            adm       210837 2011-01-23 22:27 daemon.log
-rw-r----- 1 syslog            adm       438690 2011-01-19 14:12 daemon.log.1
-rw-r----- 1 syslog            adm        11403 2011-01-09 00:00 daemon.log.3.gz
-rw-r----- 1 syslog            adm        14457 2011-01-02 13:07 daemon.log.4.gz
-rw-r----- 1 syslog            adm       212127 2011-01-23 23:00 debug
-rw-r----- 1 syslog            adm       431299 2011-01-19 13:53 debug.1
-rw-r----- 1 syslog            adm         9154 2011-01-09 00:01 debug.3.gz
-rw-r----- 1 syslog            adm        15959 2011-01-02 13:07 debug.4.gz
drwxr-xr-x 5 root              root        4096 2010-10-10 20:24 dist-upgrade
-rw-r--r-- 1 root              root       30471 2010-07-13 14:48 dkms_autoinstaller
-rw-r----- 1 root              adm        51938 2011-01-23 17:06 dmesg
-rw-r----- 1 root              adm        50091 2011-01-23 13:38 dmesg.0
-rw-r----- 1 root              adm        13684 2011-01-22 10:56 dmesg.1.gz
-rw-r----- 1 root              adm        13452 2011-01-22 10:54 dmesg.2.gz
-rw-r----- 1 root              adm        13513 2011-01-22 10:52 dmesg.3.gz
-rw-r----- 1 root              adm        14514 2011-01-21 14:10 dmesg.4.gz
-rw-r--r-- 1 root              root      108892 2011-01-21 10:39 dpkg.log
-rw-r--r-- 1 root              root       95595 2010-12-29 12:17 dpkg.log.1
-rw-r--r-- 1 root              root        8704 2010-04-30 16:36 dpkg.log.10.gz
-rw-r--r-- 1 root              root       16079 2010-03-30 16:24 dpkg.log.11.gz
-rw-r--r-- 1 root              root        8881 2010-02-27 16:21 dpkg.log.12.gz
-rw-r--r-- 1 root              root       19565 2010-11-30 17:32 dpkg.log.2.gz
-rw-r--r-- 1 root              root      153504 2010-10-29 13:07 dpkg.log.3.gz
-rw-r--r-- 1 root              root       14330 2010-09-30 12:03 dpkg.log.4.gz
-rw-r--r-- 1 root              root       15184 2010-08-25 14:01 dpkg.log.5.gz
-rw-r--r-- 1 root              root        1145 2010-08-01 23:50 dpkg.log.6.gz
-rw-r--r-- 1 root              root      152804 2010-07-27 14:50 dpkg.log.7.gz
-rw-r--r-- 1 root              root        5512 2010-07-02 12:09 dpkg.log.8.gz
-rw-r--r-- 1 root              root        4851 2010-05-26 15:09 dpkg.log.9.gz
-rw-r--r-- 1 root              root       32032 2010-11-28 14:30 faillog
-rw-r--r-- 1 root              root        3414 2010-12-23 11:09 fontconfig.log
drwxr-xr-x 2 root              root        4096 2009-04-20 15:00 fsck
drwxrwx--T 2 root              gdm         4096 2011-01-23 17:06 gdm
-rw-r--r-- 1 root              root         671 2010-04-21 12:28 gufw_log.txt
drwxr-xr-x 2 root              root        4096 2009-06-25 21:33 installer
-rw-r--r-- 1 root              root           0 2010-10-23 15:04 jockey.log
-rw-r--r-- 1 root              root       62349 2010-10-23 15:04 jockey.log.1
-rw-r--r-- 1 root              root        3251 2010-03-02 01:01 jockey.log.10.gz
-rw-r--r-- 1 root              root        3192 2010-10-16 11:22 jockey.log.2.gz
-rw-r--r-- 1 root              root        3207 2010-10-12 16:34 jockey.log.3.gz
-rw-r--r-- 1 root              root        3156 2010-10-11 12:57 jockey.log.4.gz
-rw-r--r-- 1 root              root        3442 2010-09-27 11:17 jockey.log.5.gz
-rw-r--r-- 1 root              root        3398 2010-09-19 13:23 jockey.log.6.gz
-rw-r--r-- 1 root              root        3402 2010-09-15 11:40 jockey.log.7.gz
-rw-r--r-- 1 root              root        3440 2010-08-18 00:32 jockey.log.8.gz
-rw-r--r-- 1 root              root        3392 2010-08-10 09:53 jockey.log.9.gz
-rw-r----- 1 syslog            adm   5591986143 2011-01-23 23:06 kern.log
-rw-r----- 1 syslog            adm   7261044296 2011-01-19 14:14 kern.log.1
-rw-r----- 1 syslog            adm    461983970 2011-01-09 00:32 kern.log.3.gz
-rw-r----- 1 syslog            adm     93660338 2011-01-02 13:31 kern.log.4.gz
-rw-r----- 1 syslog            adm       155899 2009-08-13 16:01 kern.log.6.gz
-rw-r----- 1 syslog            adm        56854 2009-07-23 15:51 kern.log.7.gz
-rw-rw-r-- 1 root              utmp      292292 2010-11-28 14:30 lastlog
-rw-r----- 1 syslog            adm          309 2011-01-21 14:10 lpr.log
-rw-r----- 1 syslog            adm          309 2011-01-20 13:29 lpr.log.1
-rw-r----- 1 syslog            adm          131 2011-01-10 17:07 lpr.log.2.gz
-rw-r----- 1 syslog            adm          131 2010-12-24 10:22 lpr.log.3.gz
-rw-r----- 1 syslog            adm          131 2010-12-01 13:23 lpr.log.4.gz
-rw-r----- 1 syslog            adm            0 2009-04-20 15:01 mail.err
-rw-r----- 1 syslog            adm            0 2009-04-20 15:01 mail.info
-rw-r----- 1 syslog            adm            0 2009-04-20 15:01 mail.log
-rw-r----- 1 syslog            adm            0 2009-04-20 15:01 mail.warn
-rw-r----- 1 syslog            adm   5591756336 2011-01-23 23:06 messages
-rw-r----- 1 syslog            adm   7260560894 2011-01-19 14:14 messages.1
-rw-r----- 1 syslog            adm    461973741 2011-01-09 00:32 messages.2.gz
-rw-r----- 1 syslog            adm     93641250 2011-01-02 13:31 messages.3.gz
-rw-r----- 1 syslog            adm    153810634 2010-12-26 11:34 messages.4.gz
-rw-r----- 1 syslog            adm        12808 2009-07-23 16:12 messages.6.gz
-rw-r----- 1 syslog            adm        51174 2009-07-02 03:48 messages.7.gz
drwxr-xr-x 2 mpd               audio       4096 2010-12-05 11:17 mpd
drwxr-sr-x 2 news              news        4096 2009-04-20 15:01 news
-rw-r--r-- 1 root              root      229542 2011-01-23 22:27 pm-powersave.log
-rw-r--r-- 1 root              root      325115 2011-01-01 12:17 pm-powersave.log.1
-rw-r--r-- 1 root              root        2408 2010-12-01 13:23 pm-powersave.log.2.gz
-rw-r--r-- 1 root              root        2624 2010-11-02 13:45 pm-powersave.log.3.gz
-rw-r--r-- 1 root              root         425 2010-10-01 00:44 pm-powersave.log.4.gz
-rw-r--r-- 1 root              root      501363 2011-01-23 22:27 pm-suspend.log
-rw-r--r-- 1 root              root      609710 2011-01-01 12:17 pm-suspend.log.1
-rw-r--r-- 1 root              root       18196 2010-12-01 04:12 pm-suspend.log.2.gz
-rw-r--r-- 1 root              root       20779 2010-11-02 02:43 pm-suspend.log.3.gz
-rw-r--r-- 1 root              root        6115 2010-10-01 00:44 pm-suspend.log.4.gz
-rw-r--r-- 1 root              root      126566 2011-01-04 07:56 popularity-contest
-rw-r--r-- 1 root              root      126706 2010-12-28 10:43 popularity-contest.0
-rw-r--r-- 1 root              root       33534 2010-12-21 16:29 popularity-contest.1.gz
-rw-r--r-- 1 root              root       33486 2010-12-14 10:52 popularity-contest.2.gz
-rw-r--r-- 1 root              root       33391 2010-12-07 15:13 popularity-contest.3.gz
-rw-r--r-- 1 root              root       33282 2010-11-30 17:24 popularity-contest.4.gz
-rw-r--r-- 1 root              root       33365 2010-11-23 13:08 popularity-contest.5.gz
-rw-r--r-- 1 root              root       33267 2010-11-16 10:36 popularity-contest.6.gz
-rw-r----- 1 root              adm            0 2009-07-12 18:24 ppp-connect-errors
-rw-r--r-- 1 root              root         323 2010-07-13 20:59 pycentral.log
drwxr-x--- 3 root              adm         4096 2011-01-19 14:19 samba
drwxr-xr-x 2 speech-dispatcher root        4096 2009-10-13 06:27 speech-dispatcher
-rw-r----- 1 syslog            adm   2576431758 2011-01-23 23:06 syslog
-rw-r----- 1 syslog            adm   1878889251 2011-01-21 10:41 syslog.1
-rw-r----- 1 syslog            adm     76664887 2011-01-20 11:48 syslog.2.gz
-rw-r----- 1 syslog            adm     50605445 2011-01-19 14:10 syslog.3.gz
-rw-r----- 1 syslog            adm    291102560 2011-01-18 15:04 syslog.4.gz
-rw-r----- 1 syslog            adm     31288440 2011-01-12 12:17 syslog.5.gz
-rw-r----- 1 syslog            adm     35860571 2011-01-10 13:35 syslog.6.gz
-rw-r----- 1 syslog            adm      8305933 2011-01-09 00:30 syslog.7.gz
-rw-r--r-- 1 root              root      284392 2011-01-23 17:06 udev
-rw-r----- 1 syslog            adm   5588980541 2011-01-23 23:06 ufw.log
-rw-r----- 1 syslog            adm   7261447473 2011-01-19 14:19 ufw.log.1
-rw-r----- 1 syslog            adm    461881059 2011-01-09 00:34 ufw.log.2.gz
-rw-r----- 1 syslog            adm     93239339 2011-01-02 13:32 ufw.log.3.gz
-rw-r----- 1 syslog            adm    153825494 2010-12-26 11:37 ufw.log.4.gz
drwxr-xr-x 2 root              root        4096 2009-03-02 10:07 unattended-upgrades
-rw-r----- 1 syslog            adm        40089 2011-01-23 22:27 user.log
-rw-r----- 1 syslog            adm        74430 2011-01-19 00:51 user.log.1
-rw-r----- 1 syslog            adm         1125 2011-01-09 00:00 user.log.3.gz
-rw-r----- 1 syslog            adm         2136 2011-01-02 13:07 user.log.4.gz
-rw-r--r-- 1 root              root           0 2010-10-10 12:55 wpa_supplicant.log
-rw-r--r-- 1 root              root          20 2010-10-09 15:07 wpa_supplicant.log.1.gz
-rw-r--r-- 1 root              root          20 2010-10-08 12:23 wpa_supplicant.log.2.gz
-rw-r--r-- 1 root              root          20 2010-10-07 12:34 wpa_supplicant.log.3.gz
-rw-r--r-- 1 root              root          20 2010-10-06 12:09 wpa_supplicant.log.4.gz
-rw-r--r-- 1 root              root          20 2010-10-05 11:54 wpa_supplicant.log.5.gz
-rw-rw-r-- 1 root              utmp      132096 2011-01-23 23:06 wtmp
-rw-rw-r-- 1 root              utmp        6020 2010-12-31 13:43 wtmp.1.gz
-rw-r--r-- 1 root              root       16291 2011-01-23 22:27 Xorg.0.log
-rw-r--r-- 1 root              root       16261 2011-01-23 17:05 Xorg.0.log.old
-rw-r--r-- 1 root              root       19420 2011-01-16 17:48 Xorg.1.log
-rw-r--r-- 1 root              root       16134 2010-11-12 12:59 Xorg.1.log.old
-rw-r--r-- 1 root              root        6759 2010-10-04 10:57 Xorg.2.log
-rw-r--r-- 1 root              root        6759 2010-10-03 11:50 Xorg.2.log.old
-rw-r--r-- 1 root              root        6759 2010-10-04 10:57 Xorg.3.log
-rw-r--r-- 1 root              root        6759 2010-10-03 11:50 Xorg.3.log.old
-rw-r--r-- 1 root              root        6759 2010-10-04 10:57 Xorg.4.log
-rw-r--r-- 1 root              root        6759 2010-10-03 11:50 Xorg.4.log.old
-rw-r--r-- 1 root              root        6759 2010-10-04 10:57 Xorg.5.log
-rw-r--r-- 1 root              root        6759 2010-10-03 11:50 Xorg.5.log.old
-rw-r--r-- 1 root              root       37084 2010-10-04 10:57 Xorg.failsafe.log
-rw-r--r-- 1 root              root       37084 2010-10-03 11:50 Xorg.failsafe.log.old
jason@jason-desktop:~$

Hmm, should have had you do an ls -lh to make it a little more human readable. That being said logrotate is doing exactly what it is suppose to do. 

The issue is your system has a serious issue. You need to look into these 4 logs and see what is going on.

kern.log
messages
syslog
ufw.log

These logs are way too large on your system to be normal activity

---

### Post by typos1 on 2011-01-24
I notice lately when I start up I get "writing through drive cache" or something, 3 times on the screen.

---

### Post by typos1 on 2011-01-24
Deleted some logs, but right clicked-didnt do it with shift and delete, so I assume it went to root's trash bin, tried emptying that, doesnt work, I m really stuck now as I ve only got 225mb of space left again and nothing seems to work. 

Anyone know how to establish what is actually creating these logs?.

---

### Post by tgm4883 on 2011-01-24
> **typos1 said:**
> Deleted some logs, but right clicked-didnt do it with shift and delete, so I assume it went to root's trash bin, tried emptying that, doesnt work, I m really stuck now as I ve only got 225mb of space left again and nothing seems to work. 

Anyone know how to establish what is actually creating these logs?.

As I stated before, you need to look at the logs as they are legimate log files. They are larger than they should be indicating an issue on your computer. Please look at the logs. If you need assistance, you can copy the last 100 lines out of each of the logs I listed and post them here (using the code tags)

You can get the last 100 lines using something like this
```
tail -n 100 LOGFILE > last100.log
```

---

### Post by corncob on 2011-01-24
> **typos1 said:**
> Deleted some logs, but right clicked-didnt do it with shift and delete, so I assume it went to root's trash bin, tried emptying that, doesnt work, I m really stuck now as I ve only got 225mb of space left again and nothing seems to work. 

Anyone know how to establish what is actually creating these logs?.

Can you open these log files and see what they say?  Maybe you could delete most of the entries without deleting the file itself.  I'm stumped that
```
du -ah
``` 
didn't show those big files.  Are you sure you were in the /var directory?  
If I find myself locked out of something I use
```
gksudo "dbus-launch nautilus --no-desktop --browser %U"
```
to open the file browser with administrative privliges.  You can look into your lost+found directory too.  If you paste it into the terminal you might get errors but ignore them and let the file browser open.

Just think --- after all this you could have had Ubuntu reinstalled lol.

---

### Post by typos1 on 2011-01-24
I cant do that yet as I ve deleted them, I guess theyre in root's trash but I cant empty root's trash as I ve said and thats the main prob at the moment!

---

### Post by typos1 on 2011-01-24
Actually I can-its creating logs all the time.

I opened a syslog and the processor goes to 90% usage the scomputer sounds like a jet engine, its working so much and it takes a whole minuite for it to load the files, then when you move the sliding bar at the right all the way down and release the left mouse button, it starts to go back up again! Very bizzare behaviour!

I managed to get some of the log as near to the bottom as I could :

Jan 24 22:55:35 jason-desktop kernel: [ 3731.455990] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=1454 TOS=0x00 PREC=0x00 TTL=104 ID=28943 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.456033] [UFW AUDIT] IN= OUT=eth0 SRC=80.0.42.38 DST=110.4.212.183 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=1146 DF PROTO=TCP SPT=43267 DPT=16438 WINDOW=501 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.456067] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=168 TOS=0x00 PREC=0x00 TTL=104 ID=28944 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK PSH URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.456107] [UFW AUDIT] IN= OUT=eth0 SRC=80.0.42.38 DST=110.4.212.183 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=1147 DF PROTO=TCP SPT=43267 DPT=16438 WINDOW=501 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.456909] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=1454 TOS=0x00 PREC=0x00 TTL=104 ID=28951 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.456952] [UFW AUDIT] IN= OUT=eth0 SRC=80.0.42.38 DST=110.4.212.183 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=1148 DF PROTO=TCP SPT=43267 DPT=16438 WINDOW=501 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.456989] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=110 TOS=0x00 PREC=0x00 TTL=104 ID=28952 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK PSH URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.457029] [UFW AUDIT] IN= OUT=eth0 SRC=80.0.42.38 DST=110.4.212.183 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=1149 DF PROTO=TCP SPT=43267 DPT=16438 WINDOW=501 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.583417] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=1454 TOS=0x00 PREC=0x00 TTL=104 ID=29425 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.583480] [UFW AUDIT] IN= OUT=eth0 SRC=80.0.42.38 DST=110.4.212.183 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=1150 DF PROTO=TCP SPT=43267 DPT=16438 WINDOW=501 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.583644] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=1454 TOS=0x00 PREC=0x00 TTL=104 ID=29426 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.583690] [UFW AUDIT] IN= OUT=eth0 SRC=80.0.42.38 DST=110.4.212.183 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=1151 DF PROTO=TCP SPT=43267 DPT=16438 WINDOW=501 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.583725] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=168 TOS=0x00 PREC=0x00 TTL=104 ID=29427 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK PSH URGP=0 

Its approx 500mb in size and so are quite a few of them-obviously way too big, theres a kernlog log that size too.

---

### Post by tgm4883 on 2011-01-24
> **typos1 said:**
> Actually I can-its creating logs all the time.

I opened a syslog and the processor goes to 90% usage the scomputer sounds like a jet engine, its working so much and it takes a whole minuite for it to load the files, then when you move the sliding bar at the right all the way down and release the left mouse button, it starts to go back up again! Very bizzare behaviour!

I managed to get some of the log as near to the bottom as I could :

Jan 24 22:55:35 jason-desktop kernel: [ 3731.455990] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=1454 TOS=0x00 PREC=0x00 TTL=104 ID=28943 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.456033] [UFW AUDIT] IN= OUT=eth0 SRC=80.0.42.38 DST=110.4.212.183 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=1146 DF PROTO=TCP SPT=43267 DPT=16438 WINDOW=501 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.456067] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=168 TOS=0x00 PREC=0x00 TTL=104 ID=28944 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK PSH URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.456107] [UFW AUDIT] IN= OUT=eth0 SRC=80.0.42.38 DST=110.4.212.183 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=1147 DF PROTO=TCP SPT=43267 DPT=16438 WINDOW=501 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.456909] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=1454 TOS=0x00 PREC=0x00 TTL=104 ID=28951 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.456952] [UFW AUDIT] IN= OUT=eth0 SRC=80.0.42.38 DST=110.4.212.183 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=1148 DF PROTO=TCP SPT=43267 DPT=16438 WINDOW=501 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.456989] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=110 TOS=0x00 PREC=0x00 TTL=104 ID=28952 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK PSH URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.457029] [UFW AUDIT] IN= OUT=eth0 SRC=80.0.42.38 DST=110.4.212.183 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=1149 DF PROTO=TCP SPT=43267 DPT=16438 WINDOW=501 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.583417] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=1454 TOS=0x00 PREC=0x00 TTL=104 ID=29425 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.583480] [UFW AUDIT] IN= OUT=eth0 SRC=80.0.42.38 DST=110.4.212.183 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=1150 DF PROTO=TCP SPT=43267 DPT=16438 WINDOW=501 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.583644] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=1454 TOS=0x00 PREC=0x00 TTL=104 ID=29426 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.583690] [UFW AUDIT] IN= OUT=eth0 SRC=80.0.42.38 DST=110.4.212.183 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=1151 DF PROTO=TCP SPT=43267 DPT=16438 WINDOW=501 RES=0x00 ACK URGP=0 
Jan 24 22:55:35 jason-desktop kernel: [ 3731.583725] [UFW AUDIT] IN=eth0 OUT= MAC=00:19:21:5b:09:f0:00:05:74:f7:d8:01:08:00 SRC=110.4.212.183 DST=80.0.42.38 LEN=168 TOS=0x00 PREC=0x00 TTL=104 ID=29427 DF PROTO=TCP SPT=16438 DPT=43267 WINDOW=254 RES=0x00 ACK PSH URGP=0 

Its approx 500mb in size and so are quite a few of them-obviously way too big, theres a kernlog log that size too.

Well thats a single log file, so I suppose we will start from there. After a quick bit of googling I found two comments on a bug report. I suggest you take a look at both of these comments and see if you can figure out if either apply to you. 

From [https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/591181](https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/591181)
> ufw uses logging levels, some of which use rate limiting for packets that are truly the same. See the LOGGING section of 'man ufw' for details. If too much is being logged, as mentioned before, adjust your loglevel and/or add deny rules to block the packets without logging (ie, before they hit your default policy).

Then later
> Finally, not ufw but gufw was responsible for loggings, I disable the logs in gufw and now no more messages ;). It was unusual for me because in Karmic I was using only ufw. Thanks!

---

### Post by typos1 on 2011-02-09
Havent had time to look at this in detail yet, I m deleting logs every session, b ut when I gksudo I get this message (below), it still gives me administrative priviledges though.

jason@jason-desktop:~$ gksudonautilus
gksudonautilus: command not found
jason@jason-desktop:~$ gksudo nautilus
Initializing nautilus-gdu extension

(nautilus:3306): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '3306'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:3306): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:3306): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:3306): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

** (nautilus:3306): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist

** (nautilus:3306): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist

(nautilus:3306): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

---

### Post by typos1 on 2011-04-17
Anyone got any ideas-still got the problem.

---

### Post by tgm4883 on 2011-04-17
> **typos1 said:**
> Anyone got any ideas-still got the problem.

Did you look at the bug report I linked to? Did it apply to you? Simply stating you still have the issue doesn't help.

---


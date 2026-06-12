---
title: "Mutiple copies of Media folders appearing"
date: 2010-10-16
forum: General Help
---

### Post by SuperFreak on 2010-10-16
I am trying to get my network music player (Logitech Squeezebox) to connect consistently with Ubuntu. Most of my music (FLAC files) is on a separate NTFS hard drive as I am dual booting with XP.I have edited the Fstab file somewhat based on suggestions on the forum but I can not seem to consistently connect to the Squeezebox with my music files (FLAC). What appears to happen is I set up my mount point in the media folder as Music and configure this with my Squeezebox which scans the Hard drive and finds all my music. The player works and it all seems fine even after a reboot but after a couple of reboots I get an error message when booting that says "The disk drive for media/Music/Flac is not ready yet or not present".When I go to the media folder it appears that the Music folder is duplicated with a folder called Music_ and after a resetting the Squeezebox scanner to the new Music_ folder the process starts over again and I eventually end up with another folder called Music__ and so on.
My question is 1) can I delete these Music folders without erasing all my Music library , and 2) how do I correct this situation
Here is the Fstab file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda5	/	ext4	errors=remount-ro	0	1
/dev/sda6	/home	ext4	defaults	0	2
/dev/sda8	/media/Data	ntfs-3g	defaults,locale=en_CA.utf8	0	0
/dev/sdb5	/media/Music__	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.utf8	0	0
/dev/sda1	/media/sda1	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/sda7	none	swap	sw	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0

---

### Post by nothingspecial on 2010-10-16
I would suggest removing the _ from fstab (after Music)

I don`t know anything about windows or ntfs, I`m answering mainly because I use squeezebox with Ubuntu successfully. So I may be able to offer assistance. But like I said, mounting ntfs using fstab - knowledge = 0

---

### Post by SuperFreak on 2010-10-16
Thank you,

I am afraid you are right about no knowledge with Ubuntu. I will try your suggestion.

---

### Post by SuperFreak on 2010-10-16
I made the edit to Fstab. I tried rescanning my music library with Squeezebox Server and came up with 0 music files/folders.

---

### Post by nothingspecial on 2010-10-16
> **SuperFreak said:**
> 

I am afraid you are right about no knowledge with Ubuntu.

I was refering to my knowledge of ntfs rather than your knowledge of ubuntu.

May I ask why the drive doesn`t automount? If you label the drive then (theoretically) it should appear in the /media directory the same on every reboot.

Are you running a server? Are you running 64bit?

---

### Post by SuperFreak on 2010-10-16
I am using the Desktop 64bit ed of Maverick Meerkat. I see the drive under places and on my desktop so I think it is mounting automatically.

---

### Post by nothingspecial on 2010-10-16
> **SuperFreak said:**
> I am using the Desktop 64bit ed of Maverick Meerkat. I see the drive under places and on my desktop so I think it is mounting automatically.

Have you tried labeling it?

Also, do you have the 32libs installed? (This is a seperate question, unrelated to your post)

---

### Post by nothingspecial on 2010-10-16
```
sudo apt-get install ntfsprogs
sudo umount /media/Music_
```

or 

```
sudo umount /media/Music
```

Whichever

Then find out what your drive is listed as

```
sudo fdisk -l
```

It will be something like /dev/sdb1

Then label it

```
 sudo ntfslabel /dev/sdb1 Tunes
```

If you want to call the drive Tunes (and it is /dev/sdb1) -- change the
 appropriate bits.

Point squeezeboxserver to /media/Tunes
There should be no need for fstab then :)

---

### Post by SuperFreak on 2010-10-16
Tried your instructions. I have attached a screenshot. Not happy with the possibility of file corruption so I did not proceed further

---

### Post by nothingspecial on 2010-10-16
You have not unmounted your external drive.

You need to do that before you can relabel.

On a side note.......... Please backup your music files now. All drives fail in the end.

[http://ubuntuforums.org/archive/index.php/t-929924.html](http://ubuntuforums.org/archive/index.php/t-929924.html)

---

### Post by SuperFreak on 2010-10-16
Thanks for the reminder about back up. I backed everything up last week end when I installed 10.10
The printer was on which has a card reader ; that is the only external drive . I turned off the printer and tried labeling the drive but got the same error message. See attached
I rebooted the computer once and Squeezebox successfully scanned music files. However I still got error message on boot (The disk drive for Media/Music__ is not ready yet or not present). Rebooted again and almost same thing happened (The disk drive for Media/Music_ is not ready yet or not present) but Squeezebox worked and most of my music files were found. Booted a third time and error was The disk drive for Media/Music is not ready yet or not present. When I opened Squeezebox server the Muisc Folder was empty, but artists genre etc showed music but the player would not play anything (error file could not be opened).
Perhaps it is not worth trying this with NTFS files and I will eventually have to turn my partition into an EXT4 files  system.

---

### Post by SuperFreak on 2010-10-16
One more thing. If I go to the media folder there are three Music folders; Music, Music_ & Music__. If I open them up, Music contains one folder but no files(1 item listed in properties), Music_ has an X marked on the folder and can't be opened and Music__ seems to have all the folders and files it should (over 20,000 items). It would seem that I would want to use Music__ mount as it is not a root protected folder like Music_ but still has all of the directories I need.

---

### Post by SuperFreak on 2010-10-17
I have gone through about 5 reboots and Squeeze Box server works each time, so thank you for your help. However each time I reboot I get the error message "The disk drive for /media/Music___ is not ready yet or not present". If I delete those folders (are they mounting points?) in the media file will that affect my music collection on the NTFS drive in anyway. Also if I right click on those folders the option for move to trash is greyed out. I just thought if I deleted /media/Music___ somehow I would no longer get the error message on boot.

---

### Post by nothingspecial on 2010-10-17
Ok lets try a different tack.

First, if you a running sqbs on a 64bit system you need to install the 32bit libraries for it to play properley.

```
sudo apt-get install ia32-libs
```

Then try linking your music directory to your ~/Music

To do this, open 2 instances of nautilus (the file browser)

One at /media/music and another in your Music folder in your home directory.

Holding down both Ctrl and Shift at the same time, drag your music folder into your Music folder in your home. It should appear there with an arrow above it signifying it is a link. If you click the link you should see your music.

Just so you know, if you delete the link, you will not delete your music. Also, you can add, move, delete, whatever from your music folder now from the link or the actual /media/music directory.
```

Point sqbs to /home/david/Music
```

---

### Post by SuperFreak on 2010-10-17
I tried "holding down both Ctrl and Shift at the same time, drag your music folder into your Music folder in your home". It did not appear to make a link but instead tried to copy all the music files from Music to media/music. As there are over 20,000 files this was not possible and an error message appeared. I am doing this to the Music folder with the hard drive pictured in the right corner of icon (see attached).

By the way I am sorry I did not answer this earlier but the ia32-libs were installed some time ago

---

### Post by nothingspecial on 2010-10-17
That`s why we tend to answer in commands
```

ln -s /media/music ~/Music/Tunes
```You should then have a file called Tunes in your Music folder that thinks it has all your music in it

---

### Post by SuperFreak on 2010-10-17
I have rebooted many times and each time my Squeezebox has worked and I was able to find my music in Music Folder, Artists, Genre, Album etc. So as far as that goes I am satisfied the matter is solved. I was able to delete the media folder called Music___ but still every time I reboot I get the message"The disk for media/Music___   is not ready yet or not present". If I could get rid of that error I would be most happy. However as my initial problem of not be able to use the Squeezebox is now solved I am not too concerned.
One thing that may be hindering your solution is I believe while NTFS files can be read in Linux as I understand it they can't be written to. I am leery of making changes from Linux to my windows files.

---

### Post by SuperFreak on 2010-10-18
I think I have eliminated the error message on boot up. At least I have rebooted three times and it no longer appears.
I removed this line from fstab which seemed to be mounting a nonexistent directory:

/dev/sdc5	/media/Music___	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177	0	0

---

### Post by SuperFreak on 2010-10-20
I am afraid I am getting the error message "The disk drive for /media/music is not ready or present press S to Skip....". Sometimes the computer will boot into Ubuntu fine and sometimes it will have the error message. If it boots straight into Ubuntu then all my drives are mounted and my music folders are recognized by Squeezebox Server. If I get the error message then my music drive is not always mounted and the music folders never recognized by Squeeze Box Server. Also a new folder seems to be created in the media folder such that I have a folder called "Music" which has one empty folder in in it and a another folder or drive in media called "Music_" with all my music in it. Another interesting thing is that any window I open (terminal, Firefox, document , etc) does not have the three dots in the upper right corner that allow me to close or minimize the window. Those dots are present though when the computer boots up with no error messages.


I should add that I tried the command "ln -s /media/music ~/Music/Tunes" as was recommended and it appears as a broken symbolic link in my Music folder

---


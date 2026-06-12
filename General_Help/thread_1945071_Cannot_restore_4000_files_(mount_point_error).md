---
title: "Cannot restore 4000 files (mount point error?)"
date: 2012-03-22
forum: General Help
---

### Post by hihihi100 on 2012-03-22
Hello there:

Recently Rhythmbox deleted 4000 mp3 files from my libraries (I only wanted to get rid of the library entries, no the files themselves)

"good" news is that all the 4000 files are in /media/usb0/.trash-1000/files. No hierarchy, meaning that I only see files, not any folder (folders havent been ereased from their original locations, though...)

bad news is I cannot restore em the traditional way (trash, select all, restore). This is what will appear for every of the 4000 files:

```
Error while moving "\media\usb0\.Trash-1000...20%E6%A5%9A%E6%AD%8C.MP3".
There was an error moving the file into /media/usb0/Music/&#20013;&#33775;&#30340;&#38899;&#27138;/&#31070;&#22855;&#31192;&#35676;.
No such file or directory

```

¿Could it be its looking for media\VOLUME1\.Trash-1000...20%E6%A5%9A%E6%AD%8C.MP3 ?

I can confirm that those folders do exist.

Since I dont know when all my external HDD (2, labelled volume1 and volume2) can only be accessed through mount points usb0 and usb1 respectively. This may have to do because before the deletion took part, I changed the default folder in which Rhythmbox search for music and there were both /media/usb0 and /media/volume1. I chose volume1

Filesystem is EXT4 for every drive.

Help please

---

### Post by nothingspecial on 2012-03-23
Are the files tagged correctly?

The reason I ask is that there are programs that can recreate the folder structure for your music collection based on the tags.

---

### Post by hihihi100 on 2012-08-07
Hiya:

I just remembered I still have this problem, I just though of a different way of doing it:

directory 1000 has 3 subdirectories:

* 1000/expunged (which is empty),

* 1000/files (which has the 4000 mp3 files that I can play, and information about year, album, bitrate, band or author...) and

* 1000/info (which stores the 4000 trashinfo files of each of the mp3 files).

I also havent edited nor deleted the original directories (like Music/Iron Maiden/The Number of The Beast) to which I wish to restore all the mp3 files.

Googling I found unexpunge, but only examples to unexpunge messages. I have no idea how to proceed.

Help appreciated

I was using Rythmbox when this happened

A random trashinfo files appears as: 

1 - Aces High.2.2.2.mp3.trashinfo

Its contents are:

[Trash Info]
Path=Music/Kiss/You Wanted the Best, You Got the Best!/1 - Aces High.2.2.mp3
DeletionDate=2012-03-22T22:29:13

---

### Post by hihihi100 on 2012-08-08
Somebody smart enough with sed suggested me a solution, but apparently Im not saying everything that it is:

He proposed:

```
for f in /1000/files/*; do bname=${f##*/}; path=$(sed -n '/^Path=/s///p' "/1000/info/$bname.trashinfo") && [[ $path ]] || continue; mv "$f" "$path"; done

```

All the files and their original locations are in an external HDD named "Volume-1". /media/Volume-1 acts as my home directory:

/media/Volume-1/1000/expunged
/media/Volume-1/1000/files
/media/Volume-1/1000/info

and the files are to be restored to their respective subdirectories in:


/media/Volume-1/Music

that command, executed from /media/Volume-1 always returns:

```
sed: can't read /1000/info/*.trashinfo: No such file or directory

```

Is there any information I am not giving you?

The names of the files do have empty spaces, is that relevant?

---

### Post by nothingspecial on 2012-08-09
Guayadeque music player has a feature that will copy files and place them in a predefined set of subdirectories based on the files tags.

[http://guayadeque.org/forums/index.php?p=/page/installing#InstallPPA](http://guayadeque.org/forums/index.php?p=/page/installing#InstallPPA)

I would copy the files somewhere, then use guayadeque's file browser to organise the copied files. The default "copy to" option looks like this

[ATTACH]222455[/ATTACH]

which will copy them to genre/artist/album/01-artist-title

you can add your own "copy to" definition and tell it to remove the source files.

I would leave the original files where they are and only use a copy just in case it doesn't work.

---

### Post by dcstar on 2012-08-10
Check the free inode count on the partition:

```
sudo tune2fs -l /dev/sdaN
```

---


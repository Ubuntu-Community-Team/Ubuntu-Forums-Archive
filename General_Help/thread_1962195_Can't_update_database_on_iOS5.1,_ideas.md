---
title: "Can't update database on iOS5.1, ideas?"
date: 2012-04-20
forum: General Help
---

### Post by turqoisehex on 2012-04-20
Hello!

I have an iPhone 3GS running iOS 5.1, on 11.04.
Using GTKpod, Banshee, or Rhythmbox, I'm able to copy files and delete files using these programs, but the database doesn't update.

After the sync, nothing has changed. Deleted songs still show up but cant be played, and added songs don't appear. I'm almost out of ideas, so any help is very much appreciated.

So far, I've tried completely wiping the phone and starting from scratch, pairing and unpairing, adding the hashinfo and Sysinfo files, updating libimobiledevice from the PPA ([http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)), installing a newer version of libgpod from Banshee unstable, added my user to the fuse group, deleted the contents of ~/.config/libimobiledevice, lots of hard and soft restarts, syncing with a iTunes on Windows (This works just fine, but doesn't correct the missing songs), attempted to compile Libgpod and GTKpod from source ([http://ubuntuforums.org/showpost.php?p=10955695&postcount=333](http://ubuntuforums.org/showpost.php?p=10955695&postcount=333)) but got a bizarre error compiling GTKpod "configure: error: *** Requested 'gdk-3.0 >= 3.0.11' but version of GDK is 3.0.8" (I assume it can only be compiled in Gnome3?)...

As far as I can tell, the problem lies with libgpod, since it seems to be the thing that does the database update.

Here's the output from GTKpod:


```
** (gtkpod:8101): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (gtkpod:8101): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed
libitdbprep: itdb_sqlite_generate_itdbs called with file /home/rich/.gvfs/iPhone/iTunes_Control/iTunes/iTunesCDB and uuid aa4bea5329ff17535dfe59eb706a652e9121fcdd
itlp directory='/home/rich/.gvfs/iPhone/iTunes_Control/iTunes/iTunes Library.itlp'
*.itdb files will be stored in '/home/rich/.gvfs/iPhone/iTunes_Control/iTunes/iTunes Library.itlp'
[mk_Dynamic] Processing '/tmp/filebuZZOY/Dynamic.itdb'
[mk_Dynamic] creating table structure
[mk_Dynamic] - processing 72 tracks
[mk_Dynamic] - processing 10 playlists
[mk_Dynamic] done.
[mk_Extras] Processing '/tmp/filebuZZOY/Extras.itdb'
[mk_Extras] re-building table structure
[mk_Extras] done.
[mk_Genius] Processing '/tmp/filebuZZOY/Genius.itdb'
[mk_Genius] re-building table structure
[mk_Genius] done.
library_persistent_id = 0xf41fff3f3003fd92
[mk_Library] Processing '/tmp/filebuZZOY/Library.itdb'
[mk_Library] building table structure
[mk_Library] compiling SQL statements
[mk_Library] - inserting into "version_info"
[mk_Library] - inserting into "genre_map"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'iPhone' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist '90’s Music' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'My Top Rated' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Top 25 Most Played' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Recently Played' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Recently Added' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Music Videos' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Classical Music' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'ACoK' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Podcasts' into "container"
library_persistent_id = 0xf41fff3f3003fd92
device name = iPhone
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 72 tracks
[mk_Library] done.
[mk_Locations] Processing '/tmp/filebuZZOY/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] Processing 72 tracks...
[mk_Locations] done.
[run_post_process_commands] Getting SQL post process commands
[run_post_process_commands]: Error fetching post process commands from device!
[run_post_process_commands] done.
itdbprep: copying 'Dynamic.itdb'
itdbprep: copying 'Extras.itdb'
itdbprep: copying 'Genius.itdb'
itdbprep: copying 'Library.itdb'
itdbprep: copying 'Locations.itdb'
itdbprep: copying 'Locations.itdb.cbk'
libitdbprep: itdb_iphone_stop_sync called
Could not delete '.status-com.apple.itdprep.command.runPostProcess'
Could not delete 'ddd.itdbm'
itdb_iphone_stop_sync: posted syncDidFinish
```

Thanks again for any help.

---

### Post by turqoisehex on 2012-04-25
:popcorn: bump

---

### Post by seventyeights on 2012-04-26
[http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=blob_plain;f=NEWS;hb=HEAD]("http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=blob_plain;f=NEWS;hb=HEAD")

> Overview of changes in libgpod 0.8.2
====================================

iPhone 4/iPod Touch 4/iPad/Nano 6g are still unsupported in this release.
However, libgpod now has a mechanism to dynamically load
a module named $libdir/libgpod/libhashab.so. This will be useful to
easily enable support for these devices if someone comes up with a
way to compute the music database checksum.

---

### Post by bash321 on 2012-07-03
i have the same and similar problem..
on NON Jailbroken devices.

across all of my ios devices..

it does not update the music database.

It transfers the music file to my "the new ipad" running ios 5.1.1 model MD368X but it does not show up on my music app on ios why does this happen? (it is like as if it does not stick!)
when i reconnect my ipad, the song is not in the transfer library. I only have the songs that are on my ipad not from my ubuntu pc. 
same problem occurs on my iphone 4.
i have installed the latest imobiledevice 1.1.4 and gtkpod 2.1.1 that works on ubuntu 12.04, and clementine, with rhythmbox latest 2.97 and they all do not work. to see if any program would sync my music files from my ubuntu computer. 
It does not, happen at the moment. 

ios 6 is released in the fall, would this help solve the problem. or not?
if someone has a copy of ios 6 beta 2 could they test if this problem still occurs on there devices..
can this be fixed?
(a solution that would preferably be without microsoft windows or apple osx)

bash321

---


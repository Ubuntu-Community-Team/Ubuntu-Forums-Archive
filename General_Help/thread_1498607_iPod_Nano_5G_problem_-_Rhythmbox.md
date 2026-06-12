---
title: "iPod Nano 5G problem - Rhythmbox"
date: 2010-06-01
forum: General Help
---

### Post by jason102 on 2010-06-01
Hi guys,

So earlier I heard that 10.04 now supports syncing music to the 5th generation iPod Nanos. Well, I can't get it to work. I recently did a clean install of Lucid, and I ran Rhythmbox and my iPod did come up under the Devices section on the left panel. However, when I try to click and drag music from my library onto the iPod in the Devices section, I just get a bunch of errors printing out in the terminal, and nothing happens:
```
(rhythmbox:1951): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(rhythmbox:1951): GLib-GIO-CRITICAL **: g_file_new_for_uri: assertion `uri != NULL' failed

(rhythmbox:1951): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(rhythmbox:1951): GLib-GIO-CRITICAL **: g_file_query_exists: assertion `G_IS_FILE(file)' failed

(rhythmbox:1951): GLib-GIO-CRITICAL **: g_file_get_parent: assertion `G_IS_FILE (file)' failed

(rhythmbox:1951): GLib-GIO-CRITICAL **: g_file_get_uri: assertion `G_IS_FILE (file)' failed

(rhythmbox:1951): Rhythmbox-WARNING **: filesystem root (null) apparently doesn't exist!

(rhythmbox:1951): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(rhythmbox:1951): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(rhythmbox:1951): Rhythmbox-CRITICAL **: rb_removable_media_source_build_dest_uri: assertion `sane_uri != NULL' failed
```

And when I right click on the device in the player, and click on Properties, Rhythmbox seg faults and crashes:
```
(rhythmbox:2001): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault

```

I have Rhythmbox version 0.12.8 installed, including libgpod4 version 0.7.93-0ubuntu1 (I believe 0.7.90 was when support for the 5th generation Nano was added).

Any ideas why this is happening? My iPod says it's connected on its screen. Thanks!

---

### Post by jason102 on 2010-06-02
Bump - Anyone???

---

### Post by Sandertje on 2010-06-14
I had the exact same problem. I got a new 5th generation iPod nano, plugged it in Rhythmbox, and it seems to transfer the files correctly, but that's not what happens. The music is transferred to the iPod -yes - but in the wrong place; the iPod will *not* recognize it as music. And furthermore, it breaks the iPod. I needed iTunes (on windows) to fully reset it, before I could get it to work again. 

Bottem point is, I can't use Rhytmbox for my iPod, and am stuck with iTunes (and i truly hate that amazingly slow application :P).

---

### Post by Sandertje on 2010-07-05
Bump....

---

### Post by davidmohammed on 2010-07-05
have you done what [this]("http://wolfs-ubuntu.blogspot.com/2010/06/ipod-nano-5g-on-lucid.html") guy suggests?

---

### Post by chaanakya_chiraag on 2010-10-05
I have a similar problem with the iPod Touch 1G (which is now not supported by Apple in any way).  I can open up the iPod Touch in Rhythmbox and it will work just fine.  However, as I'm transferring my songs, Rhythmbox will suddenly crash.  Here's the output from Rhythmbox on the terminal:
```
(process:3290): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(process:3290): Gdk-WARNING **: locale not supported by C library
** (rhythmbox:3290): DEBUG: Loading the real store page
** (rhythmbox:3290): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token

** (rhythmbox:3290): WARNING **: Unknown action (0x2000400) in smart playlist will be ignored.


** (rhythmbox:3290): WARNING **: Unknown smart rule action at 723804: 2000400. Trying to continue.


** (rhythmbox:3290): WARNING **: Unknown action (0x2000400) in smart playlist will be ignored.


** (rhythmbox:3290): WARNING **: Unknown smart rule action at 725116: 2000400. Trying to continue.


** (rhythmbox:3290): WARNING **: Unknown action (0x2000400) in smart playlist will be ignored.


** (rhythmbox:3290): WARNING **: Unknown smart rule action at 726426: 2000400. Trying to continue.


** (rhythmbox:3290): WARNING **: Unknown action (0x2000400) in smart playlist will be ignored.


** (rhythmbox:3290): WARNING **: Unknown smart rule action at 728944: 2000400. Trying to continue.

Device 0 (VID=05ac and PID=1291) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=05ac and PID=1291) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=05ac and PID=1291) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=05ac and PID=1291) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team

(rhythmbox:3290): RhythmDB-WARNING **: attempting to create entry that  already exists:  file:///home/chiraag/.gvfs/Chiraag%2527s%20iPod%20Touch/iTunes_Control/Music/F35/03%20-%20Track%203.m4a

(rhythmbox:3290): RhythmDB-WARNING **: attempting to create entry that  already exists:  file:///home/chiraag/.gvfs/Chiraag%2527s%20iPod%20Touch/iTunes_Control/Music/F34/08%20-%20Track%208.m4a
** (rhythmbox:3290): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=480&partner=983
libitdbprep: itdb_iphone_start_sync called with uuid=bde24831f4765347c27fb0f5d852c14b62fcebba
itdb_iphone_start_sync: posted syncWillStart
itdb_iphone_start_sync: posted syncLockRequest
Locking for sync, attempt 0...
itdb_iphone_start_sync: posted syncDidStart

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed
libitdbprep: itdb_sqlite_generate_itdbs called with file  /home/chiraag/.gvfs/Chiraag%27s iPod  Touch/iTunes_Control/iTunes/iTunesCDB and uuid  bde24831f4765347c27fb0f5d852c14b62fcebba
itlp directory='/home/chiraag/.gvfs/Chiraag%27s iPod Touch/iTunes_Control/iTunes/iTunes Library.itlp'
*.itdb files will be stored in '/home/chiraag/.gvfs/Chiraag%27s iPod Touch/iTunes_Control/iTunes/iTunes Library.itlp'
[mk_Dynamic] Processing '/tmp/fileVBVlBO/Dynamic.itdb'
[mk_Dynamic] creating table structure
[mk_Dynamic] - processing 479 tracks
[mk_Dynamic] - processing 7 playlists
[mk_Dynamic] done.
[mk_Extras] Processing '/tmp/fileVBVlBO/Extras.itdb'
[mk_Extras] re-building table structure
[mk_Extras] done.
[mk_Genius] Processing '/tmp/fileVBVlBO/Genius.itdb'
[mk_Genius] re-building table structure
[mk_Genius] done.
library_persistent_id = 0xe4ceb9c77496bbd9
[mk_Library] Processing '/tmp/fileVBVlBO/Library.itdb'
[mk_Library] building table structure
[mk_Library] compiling SQL statements
[mk_Library] - inserting into "version_info"
[mk_Library] - inserting into "genre_map"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Chiraag's iPod Touch' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Geeta Dutt' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Golden Collection - Duets' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Good Music' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Kalinga Rao' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Kishore Kumar' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Lata Mangeshkar Duets' into "container"
library_persistent_id = 0xe4ceb9c77496bbd9
device name = Chiraag's iPod Touch
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 479 tracks
[mk_Library] done.
[mk_Locations] Processing '/tmp/fileVBVlBO/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] Processing 479 tracks...
[mk_Locations] done.
[run_post_process_commands] Getting SQL post process commands
[run_post_process_commands] WARNING: ignoring non-string value for key 'Version'
[run_post_process_commands] Running 240 post process commands now
[run_post_process_commands] ERROR when executing 'AddIsITunesUColumn': duplicate column name: is_itunes_u
[run_post_process_commands] 239 out of 240 post process commands successfully executed
[run_post_process_commands] done.
itdbprep: copying 'Dynamic.itdb'
itdbprep: copying 'Extras.itdb'
itdbprep: copying 'Genius.itdb'
itdbprep: copying 'Library.itdb'
itdbprep: copying 'Locations.itdb'
itdbprep: copying 'Locations.itdb.cbk'
libitdbprep: itdb_iphone_stop_sync called
Could not delete '.status-com.apple.itdprep.command.runPostProcess'
itdb_iphone_stop_sync: posted syncDidFinish
libitdbprep: itdb_iphone_start_sync called with uuid=bde24831f4765347c27fb0f5d852c14b62fcebba
itdb_iphone_start_sync: posted syncWillStart
itdb_iphone_start_sync: posted syncLockRequest
Locking for sync, attempt 0...
itdb_iphone_start_sync: posted syncDidStart

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed
libitdbprep: itdb_sqlite_generate_itdbs called with file  /home/chiraag/.gvfs/Chiraag%27s iPod  Touch/iTunes_Control/iTunes/iTunesCDB and uuid  bde24831f4765347c27fb0f5d852c14b62fcebba
itlp directory='/home/chiraag/.gvfs/Chiraag%27s iPod Touch/iTunes_Control/iTunes/iTunes Library.itlp'
*.itdb files will be stored in '/home/chiraag/.gvfs/Chiraag%27s iPod Touch/iTunes_Control/iTunes/iTunes Library.itlp'
[mk_Dynamic] Processing '/tmp/fileWjUDvX/Dynamic.itdb'
[mk_Dynamic] creating table structure
[mk_Dynamic] - processing 479 tracks
[mk_Dynamic] - processing 8 playlists
[mk_Dynamic] done.
[mk_Extras] Processing '/tmp/fileWjUDvX/Extras.itdb'
[mk_Extras] re-building table structure
[mk_Extras] done.
[mk_Genius] Processing '/tmp/fileWjUDvX/Genius.itdb'
[mk_Genius] re-building table structure
[mk_Genius] done.
library_persistent_id = 0xe4ceb9c77496bbd9
[mk_Library] Processing '/tmp/fileWjUDvX/Library.itdb'
[mk_Library] building table structure
[mk_Library] compiling SQL statements
[mk_Library] - inserting into "version_info"
[mk_Library] - inserting into "genre_map"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Chiraag's iPod Touch' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Geeta Dutt' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Golden Collection - Duets' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Good Music' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Kalinga Rao' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Kishore Kumar' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Lata Mangeshkar Duets' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'New playlist' into "container"
library_persistent_id = 0xe4ceb9c77496bbd9
device name = Chiraag's iPod Touch
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 479 tracks
[mk_Library] done.
[mk_Locations] Processing '/tmp/fileWjUDvX/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] Processing 479 tracks...
[mk_Locations] done.
[run_post_process_commands] Getting SQL post process commands
[run_post_process_commands] WARNING: ignoring non-string value for key 'Version'
[run_post_process_commands] Running 240 post process commands now
[run_post_process_commands] ERROR when executing 'AddIsITunesUColumn': duplicate column name: is_itunes_u
[run_post_process_commands] 239 out of 240 post process commands successfully executed
[run_post_process_commands] done.
itdbprep: copying 'Dynamic.itdb'
itdbprep: copying 'Extras.itdb'
itdbprep: copying 'Genius.itdb'
itdbprep: copying 'Library.itdb'
itdbprep: copying 'Locations.itdb'
itdbprep: copying 'Locations.itdb.cbk'
libitdbprep: itdb_iphone_stop_sync called
itdb_iphone_stop_sync: posted syncDidFinish
Segmentation fault

```Does anyone know what's going on?  Thanks!

---


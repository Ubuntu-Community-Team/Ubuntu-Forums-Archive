---
title: "Rhythmbox library duplicate songs"
date: 2012-07-07
forum: General Help
---

### Post by Keith_Beef on 2012-07-07
Big problem, and can't seem to find a way around it.

I'm doing the music for a big party in about six hours' time, with all my music on a portable hard drive to play through Ubuntu / Rhythmbox to an amp. This is using my little Sony Vaio with 10.04 LTS (Lucid Lynx), not the system described in my profile and signature.

I used Synaptic to "completely remove" rhythmbox from my computer, then re-installed it. Then I connected the portable drive, started rhythmbox, and *all the music library still showed*...

So I googled, and found that I needed to remove files from ~/.local/share/rhythmbox so I did that.

Then started rhythbox again, and told it that the music was in /media/Backup/Music.

But rythmbox *still* seems to have a record of everything that was on my NAS, even though that was switched off during all the preceding steps.

I used gconf-editor to look for a list of music sources, but didn't find any.

So, how can I make sure that rhythmbox clears out its record of these songs? I will not be using a NAS or any other network, only the external drive.

Please help!

K.

---

### Post by msammels on 2012-07-07
I might be missing something here, but have you selected everything in your Rhythmbox library and removed it from library only, then re-added everything?

---

### Post by stderr on 2012-07-07
Rhythmbox stores the library in rhythmdb.xml (+ playlists.xml), in the location you mentioned. Deleting these files should be sufficient.

edit: an alternative is to force rhythmbox to use different library files. 

E.g., create a library file ~/rdb.xml:

```
<?xml version="1.0" standalone="yes"?>
<rhythmdb version="1.8">
</rhythmdb>
```

and a playlist file ~/pdb.xml:

```
<?xml version="1.0"?>
<rhythmdb-playlists>
</rhythmdb-playlists>
```

and start rhythmbox using those files:

```
rhythmbox --rhythmdb-file=/home/${USER}/rdb.xml --playlists-file=/home/${USER}/pdb.xml
```

---


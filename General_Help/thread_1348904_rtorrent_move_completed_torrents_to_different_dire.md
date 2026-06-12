---
title: "rtorrent move completed torrents to different directory depending on watch directory"
date: 2009-12-07
forum: General Help
---

### Post by kempy1000 on 2009-12-07
Hi

Im trying to get rtorrent to move completed torrents to different directory depending on the watch directory.

However when i use the commands from the website below it doesn't work and spits an error about using depreciated on_finish command:
[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Movecompletedtorrentstodifferentdirectorydependingonwatchdirectory](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Movecompletedtorrentstodifferentdirectorydependingonwatchdirectory)
```

schedule = watch_directory_1,10,10,"load_start=~/Download/watch_stuff1/*.torrent,d.set_custom1=~/Download/stuff1/"
schedule = watch_directory_2,10,10,"load_start=~/Download/watch_stuff2/*.torrent,d.set_custom1=~/Download/stuff2/"

# On completion, move the torrent to the directory from custom1.
on_finished = move_complete,"d.set_directory=$d.get_custom1= ;execute=mv,-u,$d.get_base_path=,$d.get_custom1="

```

So i tried to update it to use the new command and have the result below:

```

schedule = watch_directory_1,10,10,"load_start=/mediadrive/torrent/watch/folder1/*.torrent,d.set_custom1=/mediadrive/torrent/downloaded/folder1/"
schedule = watch_directory_2,10,10,"load_start=/mediadrive/torrent/watch/folder2/*.torrent,d.set_custom2=/mediadrive/torrent/downloaded/folder2/"
schedule = watch_directory_3,10,10,"load_start=/mediadrive/torrent/watch/folder3/*.torrent,d.set_custom3=/mediadrive/torrent/downloaded/folder3/"

# On completion, move the torrent to the directory from custom1.
system.method.set_key = event.download.finished,move_complete,"d.set_directory=$d.get_custom1= ;execute=mv,-u,$d.get_base_path=,$d.get_custom1="
system.method.set_key = event.download.finished,move_complete,"d.set_directory=$d.get_custom2= ;execute=mv,-u,$d.get_base_path=,$d.get_custom2="
system.method.set_key = event.download.finished,move_complete,"d.set_directory=$d.get_custom3= ;execute=mv,-u,$d.get_base_path=,$d.get_custom3="

```

No error is spit out anymore, but the files don't move at all.

Any help is appreciated!

Thanks
Chris

---

### Post by MelvinFalice on 2010-01-23
I don't know if you've figured this out yet, I trawled the internet and couldn't find anything so i did a lot of tinkering. i've got this to work now, good times!

heres the code

```
schedule = watch_directory_1,10,10,"load_start=/mnt/disk1/torrents/watch/auto1/*.torrent,d.set_custom1=/mnt/disk2/complete/test1/"
schedule = watch_directory_2,10,10,"load_start=/mnt/disk1/torrents/watch/auto2/*.torrent,d.set_custom1=/mnt/disk2/complete/test2/"
schedule = watch_directory_3,10,10,"load_start=/mnt/disk1/torrents/watch/auto3/*.torrent,d.set_custom1=/mnt/disk2/complete/test3/"

# On completion, move the torrent to the directory from custom.
system.method.set_key = event.download.finished,move_complete,"d.set_directory=$d.get_custom1= ;execute=mv,-u,$d.get_base_path=,$d.get_custom1="
```Give it a try and let me know how you get on:P

---

### Post by kennny2004 on 2010-05-07
thank you just want i needed = )

---


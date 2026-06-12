---
title: "Where does rtorrent put downloads!?"
date: 2011-04-10
forum: General Help
---

### Post by thasos.a.athens on 2011-04-10
So, after being a transmission fan for quite a while, I decided to  switch to rtorrent because I thought the TUI (textual user interface)  was really cool looking, but after I finished my first torrent I  couldn't find the files! I forgot to change the default directory to  Downloads first, so now it says that it is somewhere called "./" i  checked root and it's not there, i noticed the missing megabytes from my  drive though, so I know that it is somewhere. 


I am using  ubuntu 10.10 on a CR48 in developer mode, so it might be a partition  issue (there are a ton of other partitions on the device from Chromeos)

---

### Post by thasos.a.athens on 2011-04-10
I really need some help, I have almost no space on this thing anyway, so at the least i need to find a way to delete the files so I can free up some space

---

### Post by andrew.46 on 2011-04-10
As you probably now know the location of downloads is manipulated by the $HOME/.rtorrent.rc *directory* option. My own setting is:

```

# Default directory to save the downloaded torrents.
directory = /home/andrew/.rtorrent

```

but I move the completed files onto my Desktop:

```

# Move the completed torrents
system.method.set_key = event.download.finished,move_complete,"execute=mv,-u,$d.get_base_path=,~/Desktop/;d.set_directory=~/Desktop/"

```

If you have used the defaults the completed files will probably be at the root of $HOME, perhaps search for the actual torrent files:

```
find $HOME -iname '*.torrent'
```

and your downloaded files will also be there :). If you have at least a partial filename of your download you can search for it also with a slight variation of the syntax I have given above...

---

### Post by thasos.a.athens on 2011-04-12
Thanks, It worked, I just kinda lost the files in the clutter, I need to change the default directory to ~/Downloads :D

---

### Post by andrew.46 on 2011-04-12
Good to hear that it is all sorted out :).

---


---
title: "Configuring rtorrent"
date: 2010-04-19
forum: General Help
---

### Post by mattsid1 on 2010-04-19
Because my computer is pretty ancient I have been looking for a low resource torrent client and recently came across rtorrent, which seems to fit the bill but I am having a few problems saving sessions.

I got a copy of the rtorrent.rc file and saved it in my home directory. I then tried to edit it as instructed here
[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

the important lines look like this on mine


# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /.session

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start= /Downloads/*.torrent
schedule = untied_directory,5,5,stop_untied=

I have also tried this file

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /home/username/.session

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start= /home/username/Downloads/*.torrent
schedule = untied_directory,5,5,stop_untied=

but everytime I close it down all the torrents have disappeared. It also doesn't load new torrent files directly.

I can't work out what I am doing wrong.

Any help would be appreciated.

---

### Post by andrew.46 on 2010-04-22
Hi mattsid1,

It is well worth jumping the odd hurdle to get rtorrent running :). You need to define a couple of directories for rtorrent to work. Firstly a 'session' directory where rtorrent will do most of its work. Now the username I have on my computer is 'andrew', you will need to use your own username:

```
mkdir -pv $HOME/.session
```

and the following in your ~/.rtorrent.rc:

```
session = /home/andrew/.session
```

Or decide on another location, it is really up to you. You will also need a directory where rtorrent will save your downloaded torrent file, perhaps the one you have suggested in your post might do:

```
mkdir -pv $HOME/Downloads
```

and the following in your ~/.rtorrent.rc:

```
directory = /home/andrew/Downloads
```

And finally I see you want to automatically start downloading torrents in a certain directory (and stop the old ones when they are finished). Perhaps use the same directory? If you are happy with this place the following in your ~/.rtorrent.rc:

```
schedule = watch_directory,5,5,load_start=/home/andrew/Downloads/*.torrent
schedule = untied_directory,5,5,stop_untied=
```

That pretty much covers the basics. You can also move completed torrents to other locations, do some bandwidth scheduling etc etc. Don't forget to change 'andrew' for your own username :).

All the best,

Andrew

---

### Post by nothingspecial on 2010-04-22
A good tutorial [[COLOR="Magenta"]here[/COLOR]]("http://wiki.archlinux.org/index.php/RTorrent")

---


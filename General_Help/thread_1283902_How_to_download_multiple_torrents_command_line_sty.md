---
title: "How to download multiple torrents command line style with Transmissions"
date: 2009-10-06
forum: General Help
---

### Post by Superdude_123 on 2009-10-06
What command do I use to have transmissions download multiple torrents (I already downloaded the torrent file to my box), that are in the same directory, at once through terminal?

---

### Post by shaggy999 on 2009-10-06
Can't help you with transmission except to say check the man pages, but you might want to take a look into rtorrent. It's a full-featured command-line based bittorrent client. I run it inside a screen session so I can close the console window and completely forget about it. I have it set up through a configuration file to monitor a folder for .torrent files and it automatically loads them into the client and moves files to a 'completed' folder when done.

---

### Post by Superdude_123 on 2009-10-06
Could you post your config file or tell me where it is?

---

### Post by shaggy999 on 2009-10-07
Here's my .rtorrent.rc file (located in your home directory)

```

# GLOBAL SETTINGS
directory = ~/torrents/temp
session = ~/torrents/session
encryption = allow_incoming,try_outgoing,enable_retry
peer_exchange = yes
upload_rate = 20
port_range = 6881-6889

schedule = watch_directory,5,5,load_start=~/torrents/watch/*.torrent
schedule = tied_directory,5,5,start_tied=~/torrents/watch/*.torrent
schedule = stop_untied,5,5,stop_untied=
schedule = remove_directory,5,5,remove_untied=

on_finished = rm_torrent,"execute=rm,$d.get_tied_to_file="
on_finished = move_complete,"execute=mv,$d.get_base_path=,~/torrents/completed/ ;d.set_directory=~/torrents/completed/"

```

Yeah, I'm a jerk. I have it set to turn off my torrents when done. Strangely, my ISP has unlimited download but limited upload.

You might want to check out this webpage for other ideas on what you can do with your rc file: [http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks)

**NOTE: Make sure those directories exist before starting rtorrent.**

The above settings ensure only one instance of rtorrent can run and you can quit rtorrent and then start it back up where you left off later. What I do is run it inside screen. Then I just close my terminal and go off and do other things. When I want to check it again I can just "screen -R" and bring it back up.

---

### Post by Superdude_123 on 2009-10-07
I don't see that file in my home directory, am I supposed to create it?

---

### Post by shaggy999 on 2009-10-07
Are you making sure to show hidden files? The filename is ".rtorrent.rc" and the "." in the beginning tells the OS to not show it. Try "ls -la". If it's not there then go ahead and create the file.

---


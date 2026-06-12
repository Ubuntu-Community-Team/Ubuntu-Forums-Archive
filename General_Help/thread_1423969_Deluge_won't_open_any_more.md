---
title: "Deluge won't open any more"
date: 2010-03-07
forum: General Help
---

### Post by Cinemarxism on 2010-03-07
Not quite sure how this happened. Before shutting down my computer I quit deluge, as normal. No error messages or anything like that. Then, after rebooting, I was unable to start the program again. And have been ever since.

What happens when I try to open it from the application list is that my I hear my hard drives start working like they usually do, then after a few second I see a window opening (the deluge window) and the tab appearing on the tab-line, only to disappear again after a fraction of a second.

If I download a torrent and choose to open it with deluge, the program will open, and I get to the "Choose where to download file"-stage. When I click either "OK" or "Cancel", the program disappear (in the same manner that it would when trying to open it from the application list).

I've searched around a bit, and other people have had problems with opening deluge, but they always include an error message. I get nothing.

I've tried to reinstall the program. No difference.

---

### Post by prshah on 2010-03-07
> **Cinemarxism said:**
> other people have had problems with opening deluge, but they always include an error message. I get nothing.

Try opening it from a terminal and look at the output for clues as to what could be wrong: Open a terminal (Applications-Accessories-Terminal) and give the command```
deluge
``` Please check the output for errors. If you have any questions, please post the output here with your questions.

---

### Post by Cinemarxism on 2010-03-07
Thanks for your input.

Here's the output from Terminal:

> no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
save uploaded memory
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin EventLogging
Initialising plugin TorrentFiles
Initialising plugin WebUi
Initialising plugin NetworkGraph
Initialising plugin WebSeed
Initialising plugin Scheduler
Initialising plugin BlocklistImport
Initialising plugin NetworkHealth
Initialising plugin TorrentNotification
Initialising plugin SpeedLimiter
Initialising plugin Search
Initialising plugin DesiredRatio
Initialising plugin MoveTorrent
Initialising plugin TorrentPeers
Initialising plugin FlexRSS
Initialising plugin TorrentCreator
Applying preferences
Starting DHT...
Showing window
no old fastresume to delete
Traceback (most recent call last):
  File "/usr/bin/deluge", line 133, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 117, in start_deluge
    interface.start(get_cmd_line_torrents())
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1029, in start
    self.update()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1208, in update
    self.update_torrent_info_widget()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1282, in update_torrent_info_widget
    self.tab_details.update(unique_id)
  File "/var/lib/python-support/python2.5/deluge/tab_details.py", line 173, in update
    self.paint_customprogress()
  File "/var/lib/python-support/python2.5/deluge/tab_details.py", line 82, in paint_customprogress
    gc = progress_window.new_gc()
AttributeError: 'NoneType' object has no attribute 'new_gc'

---

### Post by Cas07 on 2010-03-12
Visit the support forum for Deluge: [http://forum.deluge-torrent.org/index.php](http://forum.deluge-torrent.org/index.php)

Judging by the libtorrent version you are using an old version of Deluge, did you realise 1.2.1 was released recently and there is a PPA version available.

---


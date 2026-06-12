---
title: "Task Scheduler / scripts in 9.10?"
date: 2009-11-20
forum: General Help
---

### Post by retano on 2009-11-20
Hi all,

I have a small home network setup, with Ubuntu 9.10 as a media server and torrent machine.

Here is what I am trying to achieve: I don't need 9.10 opened 24/7 and want it started on a special event, right now it is a new torrent file to download.

9.10 should wake up if I am trying to save .torrent file and then it should be saved or copied or moved to Ubuntu 9.10 machine and added to torrent-client like Deluge for example.

So far I did only wake on lan thing and shared folders between my Vista and Ubuntu 9.10

Can I do this?

---

### Post by lavinog on 2009-11-20
You could use the web interface to transmission...although I haven't tried it lately...There are other torrent clients that offer web clients also.

---

### Post by retano on 2009-11-20
You see I am a bit lazy - this is why I started all this stuff. Otherwise I can always use remote desktop or web interface. :)

---

### Post by lavinog on 2009-11-20
are you wanting it to wake up, scan your shared folder, and download any torrents in that folder?

---

### Post by retano on 2009-11-20
exactly! :)

---

### Post by retano on 2009-11-20
maybe you can post a link to info, so I can try by myself? ;)

---

### Post by lavinog on 2009-11-20
I don't know of any links, but I have some ideas.

use smbmount to mount the share
then copy all of the torrents to a local torrent folder.
unmount the share.
then use a command to add the torrent to the torrent client (most should have a command line argument to do this...which client do you prefer to use?)

all of these commands can be used to make a bash script.
A crontab entry could be made to execute this script at regular intervals (every 30 mins)

give me a couple of mins, i might have something.

---


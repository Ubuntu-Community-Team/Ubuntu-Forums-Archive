---
title: "Bittorrent syntax help."
date: 2006-02-28
forum: General Help
---

### Post by mleffler on 2006-02-28
I'm trying to figure all this out, but as you can see by my post count i'm new to this all.

btlaunchmany  --minport 59052 --maxport 59059 --close_with_rst 1 --torrent_dir /media/hda5/Torrents --save_in /media/hda5/Linux --max_upload_rate 30 --max_uploads -1

Thanks for the help.

---

### Post by horsefactory on 2006-02-28
What exactly do you need to do with bt? That command line seems pretty sound though I have no experience of the --torrent dir or --save_in switches. Use --max_uploads 1 though rather than -1.

My command line is btlaunchmanycurses --minport 4871 --maxport 4879 --max_uploads_rate 30 --max_uploads 4 /mnt/video/torrents

Ran from /mnt/video/torrents (where I keep the .torrents, and as the end of the command says, the download is saved)

---

### Post by mleffler on 2006-02-28
I'm trying to load torrents in one directory and save to another. I want to have unlimited uploads.  The ones you didn't recognize are probably invalid as I can't get it to work.

---

### Post by ohzopants on 2006-02-28
I say Azureus is the solution to your problem.  You can give it one directory to get .torrent files from (my firefox download folder for example) another to save files in and another to move completed torrents to.  Throw in an ftp server, apache and the azureus webui (sorry I don't have a link handy) and you can control torrents from anywhere!

---

### Post by mleffler on 2006-02-28
If Azureus in linux is anything like it is in Windows I don't want a thing to do with it. I had to restart it at least once a day to clear up the memory it would hog.  I'd really like to have something that I could run in the background and that's why I was trying to get this to work.

---


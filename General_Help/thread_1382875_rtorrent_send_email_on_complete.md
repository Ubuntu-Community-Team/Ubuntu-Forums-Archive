---
title: "rtorrent send email on complete"
date: 2010-01-16
forum: General Help
---

### Post by markp1989 on 2010-01-16
here it says that i can send an email on complete, but i dont havew the newest version of rtorrent, [http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks)

how do i set rtorrent 0.8.2 to send an email when finished?

thanks Markp1989

---

### Post by markp1989 on 2010-01-16
i got it working by adding:

on_finished = notify_me,"execute=/home/mark/rtorrent_mail.sh,$d.get_name="


to my rtorrentrc 

the rtorrent_mail script is the same one as on the site wiki i linked in my last post

---


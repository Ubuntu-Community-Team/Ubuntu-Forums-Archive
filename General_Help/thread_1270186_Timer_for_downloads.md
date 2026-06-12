---
title: "Timer for downloads?"
date: 2009-09-19
forum: General Help
---

### Post by skathmandoo on 2009-09-19
my internet provider gives me peak and off peak downloads. off peak starting at 2.30am - 8.30am. i wanted to use my off peak allowance and wanted to see if there are any programs that would allow me to download stuffs at those hours automatically wi thout having to wake up in the middle of the night and doing it myself! i know my mates can do it through the iCal in their macbook, is there any for us?

---

### Post by ecmatter on 2009-09-19
Before you go to sleep, run something like this:

```

sleep 5h;wget http://www.whatever.com/something_else.iso;done

```

Changing '5h' to however many hours until your off-peak download time, and providing the actual urls for whatever it is you want to download.

---

### Post by JCoster on 2009-09-19
If you're downloading torrents then the latest version of Transmission (certainly in Karmic, not sure about Jaunty) allows you to schedule max-upload/download speeds between certain times so you could set it to 0 for your on-peak hours and unlimited for off-peak.

---

### Post by skathmandoo on 2009-09-19
Thank you very much.

---

### Post by 3rdalbum on 2009-09-19
> **JCoster said:**
> If you're downloading torrents then the latest version of Transmission (certainly in Karmic, not sure about Jaunty) allows you to schedule max-upload/download speeds between certain times so you could set it to 0 for your on-peak hours and unlimited for off-peak.

Oh now that is going to be good! Right now I use cron and the transmission-remote.

skathmandoo: You can use the "sleep 5h" trick if you want, or you can use At:

```
at now + 120 minutes
wget http://www.iprimus.com.au/myfile.iso
```

then press Control-D to save your changes. You can then use the "atq" and "atrm" commands to look at the queue of At jobs and remove them respectively.

For torrents, as I mentioned, I use Cron and Transmission-remote. Cron allows you to schedule commands to run a long time in advance, at certain intervals, or at a specific time each day/week/month/year.

I'm not hardcore enough to write a Crontab myself, so I use the gcrontab program that is in the repositories. At the start of my off-peak time, I run this command:

```
transmission-remote --uplimit 75 --no-downlimit
```

And then at the end of off-peak time:

```
transmission-remote --uplimit 0 --downlimit 0
```

On that box, I run the transmission-daemon and web interface, which depends on the transmission-cli package. You need to run "transmission-daemon", I think, before you can issue commands. I just put it into my /etc/rc.local.

---

### Post by skathmandoo on 2009-09-20
ok i dont download alot nor do i use my computer often. but when i do download some music or movies i used to download the torrent on my desktop and then drag the file to the transmission box. easy as that. i am really grateful for  the tips provided above but m still a bit illiterate when it comes to linux (although i have been using it for quite some time). anyways so i tried the "sleep 5 thing" but m getting this.....

 rajiv@Rajiv:~$ sleep 4m;wget [http://isohunt.com/download/131700209/451ada039a968fd526ae7fe9b645562435c09407.torrent](http://isohunt.com/download/131700209/451ada039a968fd526ae7fe9b645562435c09407.torrent)
--2009-09-21 00:13:07--  [http://isohunt.com/download/131700209/451ada039a968fd526ae7fe9b645562435c09407.torrent](http://isohunt.com/download/131700209/451ada039a968fd526ae7fe9b645562435c09407.torrent)
Resolving isohunt.com... 208.71.112.30
Connecting to isohunt.com|208.71.112.30|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://0.0.0.0](http://0.0.0.0) [following]
--2009-09-21 00:13:08--  [http://0.0.0.0/](http://0.0.0.0/)
Connecting to 0.0.0.0:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 45 [text/html]
Saving to: `index.html.3'

100%[======================================>] 45          --.-K/s   in 0s      

2009-09-21 00:13:08 (2.42 MB/s) - `index.html.3' saved [45/45]


WHATS THAT???? where is the file? is it downloading? did it work? i cant see nothing in the Transmission box or on the desktop??

---


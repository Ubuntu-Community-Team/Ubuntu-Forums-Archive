---
title: "automatic podcast download from rss stream"
date: 2009-11-01
forum: General Help
---

### Post by itlarson on 2009-11-01
I download a number of pod-casts from RSS feeds.  I can get them through Thunderbird, where the mp3 files show up as an attachment, but this means I have to manually click on them to download them.  Is there an app which will automatically download the attachments?

---

### Post by Giblet5 on 2009-11-01
You can use "[bashpodder]("http://www.linux.com/archive/feature/114219")".

Or there's "[localcast]("http://noserose.net/e/localcast/")".

Or you can hack something together with wget and give it a $3 name like those two applications did...

---

### Post by itlarson on 2009-11-01
I don't suppose there's anything which is both graphical and in the repositories?

---

### Post by Giblet5 on 2009-11-01
> **itlarson said:**
> I don't suppose there's anything which is both graphical and in the repositories?

Not yet. You're the first person I've heard ask for one. It's not hard, but you do have to get over terminalphobia. ;)

I use iTunes under Vista Ultimate in VirtualBox for podcasts.

I never save them except to an ipod.

If you just want a GUI podcast organizer, you can use gtkpod (in synaptic).

---

### Post by itlarson on 2009-11-02
The podbasher script doesn't download- the server doesn't seem to be available.  However, the podget program mentioned on the podbasher page actualy seems pretty useful.  Most importantly it keeps a log of what has been downloaded, so as to avoid repetition.  Now if someone would create a graphical front end--

---

### Post by SushiR on 2009-11-02
Maybe gpodder is for you?

---

### Post by itlarson on 2009-11-16
Glad I revisited this thread!  Gpodder is exactly what I was looking for.  It shows you a list of episodes for each podcast you have subscribed to.  you can download them by right clicking.  Icons in the lists tell you which episodes have been downloaded which ones you have deleted.  A separate tab shows download status.

---

### Post by &lt;mike&gt; on 2010-03-14
gpodder is ace. In fact, because it has both a gui and a command line interface, you can schedule it with crontab.

Edit your crontab (crontab -e), and type (on the next available line)

15 4 * * * gpodder -r

Then save & quit [^X].

This sets gpodder to refresh and download all new episodes at 0415. If you want a different time, just change the first two values (minute/hour).

---


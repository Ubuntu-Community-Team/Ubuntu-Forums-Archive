---
title: "Any youtube downloader for Ubuntu out there?"
date: 2010-08-07
forum: General Help
---

### Post by rva1945 on 2010-08-07
There are some but for Windows (EXE files to be installed).

Thanks
Robert

---

### Post by iShurtugal on 2010-08-07
looking in the software center, I find:

gui:
FatRat
SlimRat

terminal:
youtube-dl
clive

and that's in the first 8 results....
next time, check the software center before asking please.

---

### Post by mjneil.81 on 2010-08-07
when the you tube video has finished loading the file appears in the /tmp folder (for me) i'm not sure if this is because i have the flashgot extension for firefox or not but, i just let the video load and drag the file to the desired location.

---

### Post by NFblaze on 2010-08-07
As, mjneil.81, has stated most YT videos should appear in the /tmp
provided they arent streaming or protected and provided you havent closed the tab that has the video.

Alternatively if, you'f like a commandline based grabber you can use get_flash_videos. Then you can supply the URL to the video on the commandline (it does multiple sites too). I'd give it an alias, also.

---

### Post by gabriella on 2010-08-07
> **iShurtugal said:**
> looking in the software center, I find:

gui:
FatRat
SlimRat

terminal:
youtube-dl
clive

and that's in the first 8 results....
next time, check the software center before asking please.

Yes maybe the OP should have checked the software center and other places first but we all make mistakes and ask obvious questions. I know I have!

So please try and be a little less abrupt and a bit more congenial when you respond next time. We all appreciate it :)

---

### Post by rva1945 on 2010-08-07
> **mjneil.81 said:**
> when the you tube video has finished loading the file appears in the /tmp folder (for me) i'm not sure if this is because i have the flashgot extension for firefox or not but, i just let the video load and drag the file to the desired location.


Excuse me, but, where can I find the /tmp folder?

---

### Post by ks07 on 2010-08-07
> **rva1945 said:**
> Excuse me, but, where can I find the /tmp folder?
Places>Computer>Filesystem

Then 'Tmp' :p

---

### Post by rva1945 on 2010-08-07
> **iShurtugal said:**
> looking in the software center, I find:

gui:
FatRat
SlimRat

terminal:
youtube-dl
clive

and that's in the first 8 results....
next time, check the software center before asking please.

Sometimes we (ex) windows users find it difficult to find something in Linux. It seems that arrogance is not that hard to find.

BTW I installed youtube-dl but when trying to install clive I get:

robert@rvasystem:~$ sudo apt-get install clive
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Anyway, once installed where will it appear?

---

### Post by mjneil.81 on 2010-08-07
the /tmp folder can be found by going to to places drop down menu top left of your screen then selecting computer this opens nautilus the file browser. then in the location bar (if the bar is not shown you can use Ctrl L to bring it up) typing /tmp in linux the root folder is / and tmp is located there. see screenshot

as for the Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) make sure synaptic or update manager is not in use

---

### Post by deserthowler on 2010-08-08
I use DownloadHelper, a plugin for Firefox.  I've used for about 3 years.  It works great and is easy to install in Firefox.

Earl

---

### Post by spennie on 2010-08-09
Thanx. found it.

---

### Post by TimEnid on 2010-08-09
> **deserthowler said:**
> I use DownloadHelper, a plugin for Firefox.  I've used for about 3 years.  It works great and is easy to install in Firefox.

Earl
i think this is the best option.

---

### Post by Ginsu543 on 2010-08-09
+1 for Firefox plugin.

---

### Post by konsta82 on 2010-08-10
type in terminal
gksudo nautilus

open filesystem and copy link from /tmp to your desktop

anything you watch on youtube or any other site will appear in that folder with no clicking after buffering is finished. downloaders are the waste of ram , this is the easiest solution !

---

### Post by john.hernandez on 2010-08-10
Can we use downlodhelper in Ubuntu after installing Wine ?

---


---
title: "Transmission deleted most downloaded files, thinks it's running for the first time"
date: 2012-07-25
forum: General Help
---

### Post by L R C on 2012-07-25
First of all I'm not sure if this is the correct subforum but there wasn't really anywhere else to post. I know I should be looking in a forum actually related to Transmission but I didn't want to make another account.

I'm torrenting a large (~6GB) file and my download speed isn't great so I like to leave my computer on overnight. Just now Transmission was saying there were 4 hours left so I followed a guide I found online and made a script (sudo shutdown -h now, nothing special) and ran Transmission as superuser and it came up with the alert it shows when you run Transmission for the first time (about the legality of torrenting). Then I looked and saw all the torrents I had downloaded had been reset to 0% (the .torrent files were still there), apart from those I was partway through with - although the large file in question had also been reset.

The command I ran was gksu transmission-gtk, or it might have been sudo transmission-gtk, I can't remember. Do i have to start downloading again? I recently backed up my downloads folder but there's still at least 10GB of data that I haven't backed up. Can I recover the .part files using a disk recovery tool? Or have they been completely overwritten?

---

### Post by Cheesemill on 2012-07-25
It's because you used gksu to run Transmission which runs it as the root user.

Because applications have different settings for each user and it hadn't been run as root before you get the 'First run' dialog. Simply running Transmission as your normal user might get you back to where you were.

Was there a reason you used gksu? It's a very bad idea....

---

### Post by L R C on 2012-07-25
> **Cheesemill said:**
> It's because you used gksu to run Transmission which runs it as the root user.

Because applications have different settings for each user and it hadn't been run as root before you get the 'First run' dialog. Simply running Transmission as your normal user might get you back to where you were.

Was there a reason you used gksu? It's a very bad idea....

I've run it as the normal user several times, they're all on 0.

I followed this guide: [http://techhamlet.com/2010/09/transmission-auto-shutdown/](http://techhamlet.com/2010/09/transmission-auto-shutdown/)

Edit: the reason I used gksu was because shutting down needs the password, I'm not completely sure on what the difference is between gksu and sudo...

---

### Post by Cheesemill on 2012-07-25
If you used sudo instead of gksu then that could well be another cause of your problems.
Graphical applications should always be run with gksu instead of sudo.

By using sudo you will have caused transmission to change the ownership of it's configuration files for your normal user to be owned by root. This means that when you next run transmission normally it can't write to it's own configuration files. For more info:
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by L R C on 2012-07-25
> **Cheesemill said:**
> If you used sudo instead of gksu then that could well be another cause of your problems.
Graphical applications should always be run with gksu instead of sudo.

By using sudo you will have caused transmission to change the ownership of it's configuration files for your normal user to be owned by root. This means that when you next run transmission normally it can't write to it's own configuration files. For more info:
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

I see... So my stuff is definetely gone? Do I have to do anything else to make transmission run as normal again?

---


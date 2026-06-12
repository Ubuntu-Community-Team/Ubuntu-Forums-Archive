---
title: "Deluge: How to restore torrents after format?"
date: 2009-10-31
forum: General Help
---

### Post by Brain-free on 2009-10-31
My problem is this. I want to make a fresh install of Ubuntu 9.10. My data files - including torrent folders - are in a separate partition. What I'd like to know is if there is a way, after installing Ubuntu, to have Deluge recognize my torrent files and continue from where I was left (e.g. continue a download, partially seed file etc.)

I think it has something to do with the ~/.config/Deluge/state/ folder but I'm not sure...

---

### Post by scouser73 on 2009-10-31
Just re-add the original torrent file and get Deluge to check how much it has downloaded, then you start downloading from where you left off.

---

### Post by Brain-free on 2009-10-31
Thanks for the quick reply. That does work when you're downloading or seeding something. However, my main problem is when I'm partially seeding something, which means seeding only a portion of, say, a torrent pack.

In this case, Deluge tries to download the whole file when it shouldn't. And when you don't recall what you have downloaded and what not, correcting this becomes a boring task.

---

### Post by lovinglinux on 2009-10-31
> **Brain-free said:**
> Thanks for the quick reply. That does work when you're downloading or seeding something. However, my main problem is when I'm partially seeding something, which means seeding only a portion of, say, a torrent pack.

In this case, Deluge tries to download the whole file when it shouldn't. And when you don't recall what you have downloaded and what not, correcting this becomes a boring task.

Just load the torrent, wait for the recheck to complete and pause it. Then go to the tab where you can see the files inside the pack, click those that are incomplete and select the option to not download them. When you restart the torrent it should detect that the download is already completed.

I recommend that you create a separate partition for home, so next time you format your drive you won't need to do that, since Deluge saves torrent states in your home.

---

### Post by wildweathel on 2009-10-31
I've not used Deluge myself, but you should be able to get it to continue where it left off.  You'll have to make sure that:


[list]
[*]Deluge's configuration folder is in your new home folder. (~/.config/Deluge)  I'm pretty sure the .torrent files are in there, too.
[*]Your downloaded data ends up in the the same path as it was before.
[/list]


If you do that, Deluge should start up right where it left off.  Good luck.

---

### Post by Brain-free on 2009-11-01
OK guys, thanks a lot. I'm going to try what lovinglinux has suggested.

Edit:

For later reference, the solution is to copy the ~/.config/deluge folder and paste it in the ~/.config/ folder of the new Ubuntu installation. The torrents and all the previously adjusted preferences should be up and running.

---


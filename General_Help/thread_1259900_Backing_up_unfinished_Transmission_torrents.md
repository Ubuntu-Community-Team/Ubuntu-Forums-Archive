---
title: "Backing up unfinished Transmission torrents?"
date: 2009-09-06
forum: General Help
---

### Post by JonathanConway on 2009-09-06
On my current installation of Ubuntu there are several torrents being downloaded in the 'Transmission' application, which are unfinished (one at 50%, the other at 20%, etc).

I'd like to set up a fresh installation of Ubuntu.

(since I'm having trouble getting an external hard drive to work (it was working previously) and I think it's because I've messed up my configuration. I just want to start again from scratch)

So is it possible to back up the unfinished torrents, install the latest version of Ubuntu, restore the torrents, and continue the downloads?

(Current version of Ubuntu: 8. Upgrading to 9.)

---

### Post by ninjapirate89 on 2009-09-06
If you save a copy of the .torrent file and make a backup of the data you have downloaded so far, you should be able to restart the download by putting the info back into the correct folder and simply opening the .torrent file with Transmission.

---

### Post by JonathanConway on 2009-09-06
OK, sounds like a plan.

I guess it should be obvious, but coming from a Windows background I'm used to stuff being stored in the registry.

So I'm guessing nothing else needs to be copied beyond the files themselves.

---

### Post by Lerxst51 on 2009-09-06
As long as you have the torrents and the data files, Transmission will re-scan the data to see what you have and what you need, and continue your download. I have even changed from the Bittorrent Client to Transmission mid-download, and Transmission picks right up. ;)

---

### Post by chandru155 on 2009-09-07
You can download a something say(ubuntu 9.04 torrent) in Transmisson for 50%. Then you can resume it from another torrent client say KTorrent. While Adding that torrent in Ktorrent, the path to save is the path where u downloaded 50% of ubuntu. Thats all. Ktorrent will resume from 50%. Even you can download 50% in windows(Say Xp) and download remaining in Ubuntu. It ll always work. and it worked for me

---


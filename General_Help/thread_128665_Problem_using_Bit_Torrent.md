---
title: "Problem using Bit Torrent"
date: 2006-02-12
forum: General Help
---

### Post by Piggah on 2006-02-12
Hi,

For the first time today I tried to use bit torrent. I've encountered a whole slew of problems with it and Azureus. I've given up on Azureus, but my problem with the default client or BitTornado is this: 

Whenever I try to start either of them, it asks me for a .torrent file to use. I don't know what this is for one, and I don't know what directory to find it in. 

If anyone could explain this to me, I'd really appreciate it. 

Thanks in advance.

---

### Post by z_diver on 2006-02-12
[QUOTE=Piggah]
Whenever I try to start either of them, it asks me for a .torrent file to use. I don't know what this is for one, and I don't know what directory to find it in. 
Thanks in advance.[/QUOTE]
A .torrent is a file that lets your client know what it's supposed to be downloading and seeding.  i have not seen anything nearly as graceful as the Gnome bittorrent client.  It's completely hidden and automatic.  Just click on a torrent file and it asks you where to save the download.  Click the link below and choose open with gnome-btdownload.  It will take care of the rest.

[http://mirror.yousendit.com/ubuntu/5.10/ubuntu-5.10-install-i386.iso.torrent](http://mirror.yousendit.com/ubuntu/5.10/ubuntu-5.10-install-i386.iso.torrent)

---

### Post by Mishal on 2006-02-12
The only bittorrent client that used to work for me in Windows is Bitcomet because it used random ports and ISP has probably blocked bittorent.

So, now that I have switched to Ubuntu, I can't get the Bittorrent to work. What do I do?

---

### Post by Mishal on 2006-02-12
Can't anyone help? :(

---

### Post by kakashi on 2006-02-16
i use bittornado with a scripts like this that runs all the time. 

```
$HOME/BitTornado-CVS/btlaunchmanycurses.py $HOME/torrent --minport 14000 --maxport 14000 --random_port 0 --saveas $HOME/torrents_save/  --max_upload_rate 50 
```

i put all my torrents in torrent and it saves them in torrents_save. 
i put the above code in a bash script and start it every time with my computer. 

by the way does anyone know how i can get the scripts to automaitcally start in a screen session at startup.

---

### Post by Jeffery Mewtamer on 2006-02-16
I'd personally recommend Ktorrent(although I don't know how well KDE applications run under gnome). The only problem I've had with it(since upgrading to Ktorrent 1.2) is the lack of a .torrent file association(so I have to download the .torrent and then manually load it into ktorrent instead of it being directly loaded from tracker).

---

### Post by nickle on 2006-02-16
I am not sure what your problem is exactly... Please explain the issue more clearly.

If you want to ensure your bittorrent clients (as well as many other applications) are installed properly I can only highly recommend the Automatix application. It will install and configure a whole range of the most useful applications. It succesfully installed Azereus for me.
The next step is to download a torrent file for the software you are interested in and open it with your client (say Azureus). You can search for torrent file using for example:

[http://www.bittorrent.com/](http://www.bittorrent.com/)

The link to the Automatix thread is:

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

I highly recommend running automatix if your are not a strong Linux buff (like me)....

---

### Post by Beej on 2006-02-16
I think what piggah wants to do is use Bit tornado as you would p2p software, to search for a file and download it. In azeurus you can do this.

 I don't know whether this is possible using bitornado. I woudl be interested to find out though.

---

### Post by steve.horsley on 2006-02-16
I have no problems with Azureus, but I have installed Sun's java so it may be worth your installing Sun java and trying again. Search for j2re in synaptic - it's in the Universe package IIRC.

---


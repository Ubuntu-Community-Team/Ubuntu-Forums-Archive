---
title: "Is there a bittorrent command line daemonized client for linux?"
date: 2006-06-17
forum: General Help
---

### Post by solarwind on 2006-06-17
Is there a bittorrent command line daemonized client for linux.

For example, I want to be able to login to my ssh-enabled server from my laptop to download files using bittorrent, but I don't want to keep my laptop on for hours with the connection to my server. There is a program called bittorrent-curses for linux. But using that, I have to keep my laptop on and connected via ssh to my server to use the client on my server to download. I don't want to keep my laptop on. I know of azureus, but is there any other daemonized bittorrent command line linux client that anyone knows of?

---

### Post by jpkotta on 2006-06-17
It might be enough to launch the client in a new shell.  You can do this with```
(exec btdownloadcurses file.torrent &)
```  You would have to use kill or killall to stop it.

---

### Post by Ramses de Norre on 2006-06-17
So the problem is that when you close the terminal you're running of (shut down the laptop) the process stops? In that case you can just run the command with nohup, that will cause the command to run independent of the terminal so you can close it and the process will continue (it's designed exactely for this purpose). Just run ```
nohup btdownloadcurses file.torrent &
```
(man nohup for more info)

---

### Post by solarwind on 2006-06-19
Thanks for the reply, so, let's say that I use nohup... How do I reconnect to the program I was running?

---

### Post by rklauco on 2006-10-16
Should not be better to use GNH screen?
Than you can reconnect anytime using screen -R
Works for me (not for bittorrent, I did not use it yet) for FTP and HTTP download using wget...

---

### Post by djmccormick on 2006-11-01
Yes, what I do is:
```
screen bittorrent-curses SOME_TORRENT.torrent
```

Then use Ctrl+A D to exit the screen. When you want to reconnect, just do:
```
screen -r
```

If you have multiple screens, you'll be shown a list of screen names. Choose one by doing:
```
screen -r SCREEN_NAME
```

---

### Post by exjinn on 2008-01-16
Yes this post is old, but it made my day thanks. :guitar:

---

### Post by PinkFloyd102489 on 2008-01-16
You could use rtorrent from command line or if you have a personal server, use TorrentFlux for web torrent access.

---


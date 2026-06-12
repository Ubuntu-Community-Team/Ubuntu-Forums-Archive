---
title: "how do i open a port in my firewall"
date: 2009-09-03
forum: General Help
---

### Post by parkadodge on 2009-09-03
Can someone tell me how to open my port for transmission in the firewall step by step im using ubuntu 9.10 and the transmission that comes with it. Im not sure what happened it used to work fine and now torrents just stay idle and wont connect to peers. So im hoping thatll fix it, but i i dont know that much about linux i just run it on principle not my knowlege so most of this confuses the crap out of me.

---

### Post by credobyte on 2009-09-03
Show us the output of the following command.

```
sudo iptables -L
```

---

### Post by lovinglinux on 2009-09-03
> **parkadodge said:**
> Can someone tell me how to open my port for transmission in the firewall step by step im using ubuntu 9.10 and the transmission that comes with it. Im not sure what happened it used to work fine and now torrents just stay idle and wont connect to peers. So im hoping thatll fix it, but i i dont know that much about linux i just run it on principle not my knowlege so most of this confuses the crap out of me.

If it used to work, then is probably not a firewall issue, but a tracker issue. If the tracker is down, the torrent client cannot retrieve the list of peers IP addresses and thus cannot connect to peers, so it stays idle. Besides, opening the port only helps to accept remote connections requests. You can still connect to peers and download with a closed port. Your speed will probably not reach the maximum potential, but you will be able to download. Unless of course the torrent has a few peers and they all are rejecting your connection attempts.

I don't remember exactly how to do this on Transmission, since I use Deluge, but there must be an option to edit the torrent trackers. You can try for example:

```
http://tracker.publicbt.com:80/announce
http://tracker.openbittorrent.com:80/announce
```

These are two popular open trackers that are currently online.

Changing the tracker is not necessarily guaranteed that it will work, because the tracker might not be tracking the torrent you are downloading. To look for active trackers for a specific file, grab the file hash and visit:

```
http://www.torrentz.com/<PutTheHashNumberHere>
```

For example, the one below is an Ubuntu torrent:

```
http://www.torrentz.com/20ae692114dc343c86df5b07c276e5077e581766
```

Visit the address, then scroll down until you see the "Torrent Trackers" list. It will give a list of tracker options, that are currently tracking that torrent. Copy one or more addresses and add them to your torrent.

---


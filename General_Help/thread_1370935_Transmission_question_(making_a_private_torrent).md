---
title: "Transmission question (making a private torrent)"
date: 2010-01-02
forum: General Help
---

### Post by ytowndan on 2010-01-02
Can anyone tell me how to make a private torrent on Transmission?  Back when I was on windows I used to do it on utorrent.  I remember that you had to put [http://your_ip:your_port/announce](http://your_ip:your_port/announce) for the announce url.  I figured it would be the same thing on Transmission, but it's not working.  Did I skip something, or do something wrong?  Or is there a whole different way to do it on Transmission?  It's been a while since I've done this. 

Thanks,
-Dan

---

### Post by last1 on 2010-01-02
I don't know what version you're running, but in Transmission 1.75 there's an Extras menu where you select the file(s) and tracker, that lets you check a box labelled Private Torrent.. Not that I know exactly what to do with that or ever read about how it works, but it's there.

---

### Post by warfacegod on 2010-01-02
This might help.


[http://ubuntuforums.org/showthread.php?t=1259923]("http://ubuntuforums.org/showthread.php?t=1259923")

---

### Post by NFblaze on 2010-01-02
When you click File > New to make a torrent there will be checkbox that says Private Torrent.

Check it.

I know this goes for at least versions 1.53 to 1.80b3 if Im not mistaken. Anything earlier Im unsure.

---

### Post by last1 on 2010-01-02
I asked the nice folks over at Transmission's IRC channel, who gave a little clarification on what this does and how to use it.

> 
<amaisya> hey anybody know where the instructions are for using that option to create a Private Torrent, when you select to create a new torrent?
<amaisya> i was chatting with some dude on the ubuntuforums saying he thought you had to put the local machine in as the tracker url, but there doesn't seem to be any documentation on it...
<wereHamster> there should be a checkbox when creating the torrent
<amaisya> Yeah but what about the tracker details? 
<wereHamster> put the normal tracker into the url
<amaisya> oh i get it. so you still have to put in a regular tracker, you're not using transmission as the tracker
<wereHamster> transmission is not a tracker
<wereHamster> T is a client
<wereHamster> if you put the local computer into the tracker url field, two clients will never find each other
<amaisya> then what does checking the private torrent box actually do? i thought maybe it operated as if it were a tracker using dht or something
<wereHamster> it sets a flag in the torrent file
<amaisya> ok, thanks for the help


So i guess you still need to use a tracker, and you're not putting your IP/port into the announce. Just the regular announce of a private tracker. I suppose this disables DHT and the like. If you want to ask the guys at the transmission channel more about it, they're in #transmission on Freenode

---

### Post by NFblaze on 2010-01-03
Yea, if you make the torrent private, it will disable the trackerless protocols PEX and DHT. AS in you will need to get your peers/leechers IPs from the associated tracker in the file.

This is what private torrent sites do, they set up a private tracker, where only authorized users can connect to the tracker to find the peers to connect to to begin sharing data. If they left PEX and DHT enabled than anyone could possibly get the files associated with the torrent without being a cleared authorized member of that private torrent site.

---


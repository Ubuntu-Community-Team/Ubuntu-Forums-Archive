---
title: "Help associating magnet links with Utorrent in Firefox"
date: 2012-02-29
forum: General Help
---

### Post by adlin5000 on 2012-02-29
With sites going to all magnet links now, this is becoming an issue. I've done some searching and all I have found is from '09 about changing some about:config strings which does not work. Any help would be great.

Thanks.

---

### Post by lovinglinux on 2012-02-29
Close Firefox, make a backup then delete the file *mimeTypes.rdf* from your Firefox profile folder, located under ~/.mozilla/firefox/<profilename>

Next time you try to open a magnet link, it should ask which application you want to use and your default torrent client should be listed.

BTW, which Firefox version you are using?

---

### Post by adlin5000 on 2012-02-29
FF 10.0.2

Problem is, it asks for a program and when I choose utorrent (manually, it's not on the list) nothing happens. Then when I check in the options is always defaults back to "ask".

Also, I'm using utorrent through Wine.

---

### Post by lovinglinux on 2012-03-01
> **adlin5000 said:**
> FF 10.0.2

Problem is, it asks for a program and when I choose utorrent (manually, it's not on the list) nothing happens. Then when I check in the options is always defaults back to "ask".

Also, I'm using utorrent through Wine.

If you are using uTorrent through Wine, then things get more complicated. I don't know how to do it or if it is possible.

My advice is to forget about uTorrent entirely and use a native client. Personally, I don't see a good reason to use uTorrent through Wine when there are plenty of excellent torrent clients for Linux. I recommend using qBittorrent, which is super fast, easy to configure and looks like uTorrent.

There are other excellent clients like Transmission (installed by default), Ktorrent and Deluge.

You can install all this clients through the Software Center.

---

### Post by adlin5000 on 2012-03-01
I've tried some of the native clients. I have not found one that works for me yet. 
Deluge was a good one, but it kept crashing and giving me errors. Also the ip blocklist support is very broken. I can't remember why I wrote off Transmission, I think it was no support for downloading individual files in a torrent and limited options. 
Don't think I've tried qBittorrent yet, I'll give it a go. I have nothing against using native apps, but if they don't do what I need them to, I'm not going to keep using them.

---

### Post by lovinglinux on 2012-03-01
> **adlin5000 said:**
> I've tried some of the native clients. I have not found one that works for me yet. 
Deluge was a good one, but it kept crashing and giving me errors. Also the ip blocklist support is very broken. I can't remember why I wrote off Transmission, I think it was no support for downloading individual files in a torrent and limited options. 
Don't think I've tried qBittorrent yet, I'll give it a go. I have nothing against using native apps, but if they don't do what I need them to, I'm not going to keep using them.

Personally, I don't like Transmission. I haven't used Deluge in a long time, but it used to be a great client, specially if you want to run on a server and connect remotely.

I have been using qBitorrent and Ktorrent for a long time. They both work great and have excellent ip blocklist support. They are also very complete clients, with many features. If one of these clients don't work for you, is probably because your router/firewall configuration. Both clients have UPnP support too, btw.

Give qBittorrent a go. You won't be disappointed.

---

### Post by adlin5000 on 2012-03-09
Gave qBitrorrent a try. works great except for one problem. There is a bug in libtorrent that it uses. Every torrent gets stuck on the last piece and stalls out. 

Tried installing the libtorrent from precise. After installing updated dependencies I stated getting into the core files. I'm not going to upgrade the whole system just to get one program to work.

Tried to compile the new version from source, but Ubuntu puts it in /usr/lib/ with a 6 at the end, and the source puts it in /usr/share/lib/. Now I'm just good enough to compile from source, going in and changing stuff thats going to screw with synaptic is getting beyond me and going farther then I'm willing to go with this.

So back to my original question: anyone know how to get magnet links from Firefox to play nice with uTorrent in Wine?

---

### Post by kanoretrue on 2012-08-29
I had the same problem and looking for a solution I found this post and some minutes after I have discovered a workaround to load magnet links with utorrent from Ubuntu with Wine.

It's quite easy: 
Instead of clicking with the left button of the mouse on the magnet, use the right button on it and choose the option to copy link.
Then, on utorrent, go to File on the top bar and choose the option to load torrent from a URL.
Then, paste the link. Accept and it'll work.

I use utorrent 2.2.1 with ubuntu 12.04; but I guess that it will work with other versions.

---


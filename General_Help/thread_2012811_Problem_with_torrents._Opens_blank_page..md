---
title: "Problem with torrents. Opens blank page."
date: 2012-06-29
forum: General Help
---

### Post by Naitogunjin on 2012-06-29
Hello,

I recently installed Lubuntu 12.04 on my system. It runs great and a lot faster! 

When I go to download a torrent from the pirate bay instead of bringing up transmission like in ubuntu, it just opens up a blank webpage. I tried downloading different torrent applications but all with the same outcome.

I don't think it's the pirate bay, but it could be. I'm using google chrome as the browser. 

Has anyone else had this problem? If there is a fix out there let me know!

Thanks

---

### Post by Bucky Ball on 2012-06-29
> **Naitogunjin said:**
> Hello,

I recently installed Lubuntu 12.04 on my system. It runs great and a lot faster! 

When I go to download a torrent from the pirate bay instead of bringing up transmission like in ubuntu, it just opens up a blank webpage. I tried downloading different torrent applications but all with the same outcome.

I don't think it's the pirate bay, but it could be. I'm using google chrome as the browser. 

Has anyone else had this problem? If there is a fix out there let me know!

Thanks

Are you downloading regular torrents or magnet links??? Regular torrents are soon to be a thing of the past as magnet links are the next big thing in the torrent world. Trouble is they are nothing like regular torrents (basically a web address) and I can't get any of them to run in Transmission, despite the fact I have followed the advice and tweaked til they're supposed to.

---

### Post by kdane4 on 2012-06-29
> **Bucky Ball said:**
> Are you downloading regular torrents or magnet links??? Regular torrents are soon to be a thing of the past as magnet links are the next big thing in the torrent world. Trouble is they are nothing like regular torrents (basically a web address) and I can't get any of them to run in Transmission, despite the fact I have followed the advice and tweaked til they're supposed to.

Im guessing the OP is downloading magnet links since thepiratebay removed non-magnet link torrents from their site.. 

To the OP, be sure you're downloading legal torrents. ;)

---

### Post by Bucky Ball on 2012-06-29
> **kdane4 said:**
> Im guessing the OP is downloading magnet links since thepiratebay removed non-magnet link torrents from their site.. 

 
Wrong. There's still plenty of old-school torrents up there. Have a look. They appear to be phasing them out. ;)

---

### Post by kdane4 on 2012-06-29
> **Bucky Ball said:**
> Wrong. There's still plenty of them up there. Have a look. They are phasing them out. ;)

:oops: I feel embarassed.. Just had a look and you're right.. I guess I got so much used to magnets on that site that I didnt notice it... :p

---

### Post by Bucky Ball on 2012-06-29
> **kdane4 said:**
> :oops: I feel embarassed.. Just had a look and you're right.. I guess I got so much used to magnets on that site that I didnt notice it... :p

No probs, don't be, but a question; if you're using magnet links and you are using Ubuntu, what torrent client are you using? I can't get anything to download magnet links (Transmission, Vuze ...).

I've even hunted for some way to turn a magnet link into a regular torrent, seemingly an impossibility! ;)

---

### Post by kdane4 on 2012-06-29
> **Bucky Ball said:**
> No probs, but if you're only using magnet links and you are using Ubuntu, what torrent client are you using? I can't get anything to download magnet links ...

I now usually use windows for torrent downloading as I dual boot.. I have a little work around for Transmission and Qbittorrent before though..

I right click on the magnet link, select copy link address (chromium browser). Open transmission, select file - then add URL, Ill paste the link manually.. Havent done it in a long time though.. :popcorn:

---

### Post by pqwoerituytrueiwoq on 2012-06-29
in firefox
edit->preferences
applications tab
add magnet and set value as transmission

edit:

close chrome
open
"/home/$USER/.config/chromium/Local State"

locate this
```
   "protocol_handler": {
      "excluded_schemes": {
         "afp": true,
         "data": true,
         "disk": true,
         "disks": true,
         "file": true,
         "hcp": true,
         "javascript": true,
         "mailto": false,
         "ms-help": true,
         "news": false,
         "nntp": true,
         "shell": true,
         "snews": false,
         "vbscript": true,
         "view-source": true,
         "vnd": {
            "ms": {
               "radio": true
            }
         }
      }
```add this like in it like so
```
   "protocol_handler": {
      "excluded_schemes": {
         "afp": true,
         **"magnet": false,**
         "data": true,
         "disk": true,
         "disks": true,
         "file": true,
         "hcp": true,
         "javascript": true,
         "mailto": false,
         "ms-help": true,
         "news": false,
         "nntp": true,
         "shell": true,
         "snews": false,
         "vbscript": true,
         "view-source": true,
         "vnd": {
            "ms": {
               "radio": true
            }
         }
      }
```

---

### Post by Bucky Ball on 2012-06-29
Yea, just tried qBittorrent again and it worked with magnets no probs. Just took a slightly different approach as suggested so thanks for the tip. ;)

PS: I tried Transmission first by adding the URL and nothing, but left it running in the background while I played with qBittorrent. Twenty minutes later it has just started downloading so magnets working in that also.

---

### Post by kdane4 on 2012-06-30
> **Bucky Ball said:**
> Yea, just tried qBittorrent again and it worked with magnets no probs. Just took a slightly different approach as suggested so thanks for the tip. ;)

PS: I tried Transmission first by adding the URL and nothing, but left it running in the background while I played with qBittorrent. Twenty minutes later it has just started downloading so magnets working in that also.

Glad to know you got it working.. :) I noticed also a few bugs with Transmission thats why I used other clients.. Sometimes it will show that my download is 0/kbps but the progress bar is moving.. :lolflag:

---

### Post by Naitogunjin on 2012-06-30
Great I just copy and pasted the magnet link in transmission and it worked. Thanks.

I guess i'll jest have to copy link from now on.:-k

---

### Post by kdane4 on 2012-06-30
Glad to hear that my little workaround worked for you.. You can try pqwoerituytrueiwoq's post if you want.. It should change permissions of your browser so whenever you click a magnet link, it will automatically launch a torrent client.. Haven't tried it personally though as I'm alright doing it manually in linux.. You can mark this thread as solved also.

Cheers!! :)

---


---
title: "HELP !?!, Where are my downloaded files?!?"
date: 2011-06-05
forum: General Help
---

### Post by 4thLucky on 2011-06-05
Hi
just before i say anything else, i dont know a whole lot about linux in general, i know a bit more than average but can you just please keep the instructions simple? thanks (:

ok so....  Im running uTorrent 2.2.1 under Wine on 10.10 matty maverick, and i downloaded a couple of music albums, but i cannot find them anywhere on my ubuntu system?, i can go to utorrent and select 'open containing folder' and it opens Wine file manager, and then all i can do is sit and stare at the files? i cant do a thing with them?, because i was wanting to burn a cd or two using the files, but i cant find them in my downloads and ive done a full search in basically all my files and still nothing, i cant copy and paste them, i cant drag them into my music folder, Urghh,

Please Help ?!? :D

---

### Post by Keypel on 2011-06-05
It's in a hidden folder called .wine

(  /home/4thLucky/.wine/dosdevices/c:  )

I think the easiest way for you to find it is to go to Applications->Wine->Browse C Drive

[IMG]http://img32.imageshack.us/img32/2820/screenshotfn.gif[/IMG]



After you find them, Simply copy/cut, paste or drag them to an easier to find location.

BTW uTorrent is now available for Linux as well. I can't run it on my system because it makes my CPU go to 100% but it might work for you. I was a big fan of uTorrent but I now use Transmission bit torrent client. Works just as good as uTorrent IMO.

---

### Post by 4thLucky on 2011-06-05
**:)Thank you So Much Man!! :D**

I have to run it through wine as my laptop does not allow the linux server edition for some weird reason, and its because i was used to windows for years a sudden change, i didnt like so i ran it through wine and i liked :D, just the apperance is about grotty though :/,

but anyway, Thank you so much! :D

---

### Post by Keypel on 2011-06-06
> **4thLucky said:**
> **:)Thank you So Much Man!! :D**

I have to run it through wine as my laptop does not allow the linux server edition for some weird reason, and its because i was used to windows for years a sudden change, i didnt like so i ran it through wine and i liked :D, just the apperance is about grotty though :/,

but anyway, Thank you so much! :D

No prob, Glad I could help.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **4thLucky said:**
> Hi
just before i say anything else, i dont know a whole lot about linux in general, i know a bit more than average but can you just please keep the instructions simple? thanks (

Please Help ?!? :D

Don't download torrents in Wine.  Just do it natively. 

Real simple.. Here you go:

[http://cinderbox.net/2011/04/20/qbittorrent-2-7-3-ppa-alternative-to-%C2%B5torrent-for-ubuntu/]("http://cinderbox.net/2011/04/20/qbittorrent-2-7-3-ppa-alternative-to-%C2%B5torrent-for-ubuntu/")

---

### Post by Keypel on 2011-06-06
To run the linux version of utorrent on your laptop, download utorrent-server.tar.gz to your desktop and right click "extract here". There will now be a folder called utorrent-server on your desktop. Go into that folder and Double click on the utserver file. Then go to your web browser (firefox,chrome,opera,etc) and put [http://localhost:8080/gui/](http://localhost:8080/gui/) into the address bar. When it asks for a pass put "admin" for username and blank for the password.

---


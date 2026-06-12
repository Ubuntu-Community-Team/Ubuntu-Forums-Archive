---
title: "Best Download Manager"
date: 2010-08-13
forum: General Help
---

### Post by Honey_HR on 2010-08-13
Hello Friends,Now i am regular user of ubuntu, don't want to play with windows 7 nd Xp anymore, 
But i never find any Download manager in ubuntu like " Internet download manager", Is there any good And Best download manager for ubuntu, 
I search a lot on net and ubuntu forums, but i never get any solution !!  ANY BEST DOWNLOAD MANAGER, THAT IS FAST ??????

---

### Post by azertyh on 2010-08-13
hi,
there are many in synaptic. search keyword : download.
i use for example multiget.

---

### Post by linux18 on 2010-08-13
the downthemall extention for firefox

---

### Post by azertyh on 2010-08-13
find [how to install flashget]("http://www.ubuntugeek.com/how-to-install-flashget-download-manager-in-ubuntu.html#more-7714").

---

### Post by amime on 2010-08-25
FlashGet is a spyware software , it performs illegal data upload and consumes a lot of network resources ..

---

### Post by inameiname on 2010-08-25
Downthemall works fine in Firefox. I also like Wget. I use Gwget often. Plus you can set it up through the terminal to do all sorts of things.


Here is a poll taken recently about this. In it, seems like Jdownloader is a tad more popular than Gwget.:

[http://www.webupd8.org/2010/08/best-linux-download-manager.html](http://www.webupd8.org/2010/08/best-linux-download-manager.html)

---

### Post by dagdeniz on 2010-08-25
wget and aria2 are my favourites. aria2 supports multithreaded download and torrents, too. I wouldn't suggest download managers with a gui, the ones I tried (multiget, uget, d4x) were too buggy.

---

### Post by Guilden_NL on 2010-08-25
amime has it right, Flashget is evil, stay away from it unless you want to be sending your bank account details to China.

[http://en.wikipedia.org/wiki/FlashGet]("http://en.wikipedia.org/wiki/FlashGet")

---

### Post by Pascal-7 on 2010-08-25
axel works fine for me

---

### Post by fuzzylogic25 on 2010-10-01
have you managed to find a good replacement for internet download manager? because i have been searching too and i havnt come close to finding a single one!

please let me know if you do.

---

### Post by walwal on 2010-10-01
try fatrat, its very powerful.

---

### Post by tareq.mhd on 2010-10-02
JDownloader is another powerfull download manager, but aria2 is awesome command based utility.

---

### Post by wheels666 on 2010-10-10
any suggestions for a GUI based downloader to replace IDM i use in windows which works better than anything i've found so far for linux?

---

### Post by Jose Catre-Vandis on 2010-10-10
aria2 and axel

I run aria2 on my always on server, just plonk links into a text file, and set it running with a short script. Never fails. TYou can use it with file sharing services (Rapidshare/Hotfile etc - you just add the user/pass info)and torrents.

My script
```
#!/bin/bash
aria2c -i /home/user/urlfile -j 1 -s 1 -d /home/user
```

For File sharing
```
#!/bin/bash
aria2c --http-user=username --http-passwd=password -i /home/user/urlfile -j 1 -s 1 -d /home/user
```

urlfile is the text file where the links are
replace username and password with your login in info

---

### Post by masaibana on 2010-10-17
No matter how good the download manager can do, it will depends to the server connection and your computer connection speed. So that a good download manager is something that can handle downloading a single files becomes multitasking download, and support downloading multiple files at a time where the download can be paused and resuming. And the download manager should can handle the download error pretty well, like a connection error or power down on pc without ups. Plus a good adds on with the browser and easy to use.
[hahahah :guitar:]
But I dont find any download manager like that on ubuntu...

---

### Post by macem29 on 2010-10-17
like others mentioned, down them all is a good gadget, firefox addon, I use it in windows and ubuntu

---

### Post by mister_playboy on 2010-10-17
> **Guilden_NL said:**
> amime has it right, Flashget is evil, stay away from it unless you want to be sending your bank account details to China.

[http://en.wikipedia.org/wiki/FlashGet]("http://en.wikipedia.org/wiki/FlashGet")

Considering FlashGet is Windows-only, I'm not sure why it was even mentioned...? :P

---

### Post by masaibana on 2010-10-18
> **macem29 said:**
> like others mentioned, down them all is a good gadget, firefox addon, I use it in windows and ubuntu
Ho Yeaahh.. right. A few hours ago, I used it for downloading kubuntu dvd. Than I paused it.
Pretty well, my download starts from begin though.
But for grabbing it seems working really good.. Yesterday I download a small file with it, than push the reset button. Later I resume my download till complete. No problem..
It just bad luck when it didnt give any message to redownload the file from begin.

Now I'm stuck with KTorrent with 10KBps up and down. It looks gonna take a full week off. Well, at least it can guarantee my download wouldnt be corrupt. As I see, KTorent uses chunks for downloading, unlike gwget, uget and axel which download the file bit by bit while increasing the file size until complete.

---

### Post by Hamad_Spider on 2013-04-18
Hi.
I suggest you to use [**XTreme Download Manager**]("http://xdman.sourceforge.net/").
[IMG]http://xdman.sourceforge.net/400.png[/IMG]
It is so similar to IDM and is my choice after testing many linux download managers.
For more information, plese visit the following link:
[http://www.ubuntubuzz.com/2013/04/xt...t-another.html]("http://www.ubuntubuzz.com/2013/04/xtreme-download-manager-yet-another.html")

---


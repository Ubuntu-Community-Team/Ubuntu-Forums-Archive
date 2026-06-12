---
title: "KTorrent Speed"
date: 2006-05-01
forum: General Help
---

### Post by Hygelac on 2006-05-01
I am new to BitTorrent and have installed KTorrent.  I have no idea what a normal download speed is.  KTorrent usually downloads at about 2kbps, although it occasionally surges for 20min or so at about 30kbps.  Are speeds in the 2-3kbps range normal?  I get 52kbps on a regular download, so I must say that I do not find this 'BitTorrent' thing particularly impressive... [-(

---

### Post by bored2k on 2006-05-01
Have you done port forwarding on your router? find out what port ktorrent is using and open it (both TCP and UDP). Restart the application and try again.

For  information on how to do this: [http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm) .

---

### Post by Hygelac on 2006-05-02
I think that helped a bit (it now runs at mostly 10-30kbps); thanks. :)

---

### Post by bored2k on 2006-05-02
If all else fails, try the official bittorrent.com client and/or azureus.sourceforge.net one.

---

### Post by bobbymcsteels on 2006-05-02
[QUOTE=bored2k]If all else fails, try the official bittorrent.com client and/or azureus.sourceforge.net one.[/QUOTE]
yeah I have been usin azureus for years now.... have tried other clients but none of them compare to azureus.... plus u get the bouncy frog icon:P

---

### Post by Hygelac on 2006-05-02
> yeah I have been usin azureus for years now.... have tried other clients but none of them compare to azureus.... plus u get the bouncy frog icon:P

A bouncing frog?  This changes everything!  :rolleyes:  I do not have anything to download right now, but when I do I will remember to try Azureus.

---

### Post by bobbymcsteels on 2006-05-02
[QUOTE=Hygelac]A bouncing frog?  This changes everything!  :rolleyes:  I do not have anything to download right now, but when I do I will remember to try Azureus.[/QUOTE]

Just watch out tho, there are some site that will ask you to pay for it, get it from sourceforge tho ;)

---

### Post by void_false on 2006-05-02
[QUOTE=Hygelac]A bouncing frog?  This changes everything!  :rolleyes:  I do not have anything to download right now, but when I do I will remember to try Azureus.[/QUOTE]
Search google for list of top bittorent sites and your downloads will never end. %)

---

### Post by jpmontalbo on 2006-05-06
This worked for me... you can try it to see if it makes a difference. Pick a random port that is above 10,000 and make sure you forward that port both udp and tcp in your router settings. I used to try to use 6881 as the port and was too slow usually getting 5kbps :confused: . I also wasn't able to upload to people, stayed at 0 upload. After I selected a random port above 10,000 my downloads showed tremendous increase in speed and I was able to upload.  Now I get speeds comparable to azureus. :D

---

### Post by treris on 2006-05-07
I've switched from azureus to ktorrent because it uses a lot less resources and so far have had few to no problems with it, I am however using version 1.2 which is way more stable than the version which you'll find in the repo's

---

### Post by Hygelac on 2006-05-07
[QUOTE=jpmontalbo]This worked for me... you can try it to see if it makes a difference. Pick a random port that is above 10,000 and make sure you forward that port both udp and tcp in your router settings. I used to try to use 6881 as the port and was too slow usually getting 5kbps. I also wasn't able to upload to people, stayed at 0 upload. After I selected a random port above 10,000 my downloads showed tremendous increase in speed and I was able to upload. Now I get speeds comparable to azureus.[/QUOTE]
I tried this with KTorrent but it made no difference, although I never had the upload problem you mentioned in the first place.  Oh well...

[QUOTE=treris]I've switched from azureus to ktorrent because it uses a lot less resources and so far have had few to no problems with it, I am however using version 1.2 which is way more stable than the version which you'll find in the repo's[/QUOTE]
KTorrent 1.2?  I'll remember to check that one too; I do appreciate its low resource-intensity.

---

### Post by Hygelac on 2006-05-07
[QUOTE=Hygelac]KTorrent 1.2? I'll remember to check that one too; I do appreciate its low resource-intensity.[/QUOTE]
With that new KTorrent, it works as well as my ADSL connection will allow. =D>

---

### Post by treris on 2006-05-07
happy downloading!!!! :D

---

### Post by nykobing on 2006-05-24
I am having a problem installing the deb file from their webpage, the new 2.0 beta, I get the following error:

nykobing@yep:~$ sudo dpkg -i ktorrent_2.0beta1-1_i386.deb
Password:
(Reading database ... 96147 files and directories currently installed.)
Unpacking ktorrent (from ktorrent_2.0beta1-1_i386.deb) ...
dpkg: error processing ktorrent_2.0beta1-1_i386.deb (--install):
 trying to overwrite `/usr/share/mimelnk/application/x-bittorrent.desktop', which is also in package kdelibs-data
Errors were encountered while processing:
 ktorrent_2.0beta1-1_i386.deb


Any idea what I can do?

---

### Post by McQuaid on 2006-05-26
I am getting the same error as nykobing.  This also happens when trying to compile from source.

---

### Post by treris on 2006-05-26
I haven't tried the new beta yet (mostly because I didn't know there was one) but I do remember that when I updated from ktorrent 1.1 to 1.2 I had to completely remove all files and folders related to ktorrent before I could succesfully upgrade.

have you tried doing that??
 
hope that helps

---

### Post by stoeptegel on 2006-05-26
Have you tried?
dpkg --force-overwrite
It's because the default mime-type will be overwritten to have the right icon.

---

### Post by McQuaid on 2006-05-26
stoeptegel, ya I tried that and it did the trick. I only tried the 2.0beta briefly but I wasn't impressed.  It would only seem to connect to a couple of peers,(it was displaying connect to 6 peers out of like 4000 after twenty minutes)  and it would keep saying stalled.  I have the ports set up and have never had issue in other torrent clients.  And I fired up azureus using that same torrent and had no issue.

I did remove /.kde/share/apps/ktorrent prior to running 2.0beta.  Does it leave any other files that I might have missed.  

Otherwise, I'll try some other torrents to confirm but otherwise it's back to azureus and transmission.  I'd like to stick with transmission but it still needs a few features that ktorrent seemed to have.  We really need a good gtk+ client.  Or I wish the port of utorrent would come sooner.

---

### Post by stoeptegel on 2006-05-27
I had a big awnser here, but it got lost because of auto-logout, sry....

---

### Post by skymt on 2006-05-27
[QUOTE=jpmontalbo]This worked for me... you can try it to see if it makes a difference. Pick a random port that is above 10,000 and make sure you forward that port both udp and tcp in your router settings. I used to try to use 6881 as the port and was too slow usually getting 5kbps :confused: . I also wasn't able to upload to people, stayed at 0 upload. After I selected a random port above 10,000 my downloads showed tremendous increase in speed and I was able to upload.  Now I get speeds comparable to azureus. :D[/QUOTE]
Your ISP is probably trying to block Bittorrent by port. Either that, or you picked a torrent where all the other peers had their clients set to ignore those green enough to use the default port.

---

### Post by xanous on 2007-02-11
Arg! everyone says to port forward but my modem does not have a built in router. What should I do then? I am using Ktorrent and my downloads are slooow! Azureus was great in windows but stinks for ubuntu. I read that it will help to set up a static IP but that is way over my head. Any suggestions?

---


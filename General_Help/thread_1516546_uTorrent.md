---
title: "uTorrent"
date: 2010-06-23
forum: General Help
---

### Post by thefallofroy on 2010-06-23
I just recently upgraded to 10.04 so I have to reinstall utorrent. Last time i did it with wine using this method: [http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml](http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml)

it seemed to work fine with 9.10 but now i try it again and when i double click the utorrent launcher on my desktop it literally does nothing. Doesn't open anything, nor does it even report an error message. Any ideas? Thanks in advance.

---

### Post by Smart Viking on 2010-06-23
I want to start by saying that the bittorent clients for linux works perfectly, but if you need uTorrent, thats ok.

Wine have changed some things because of security, when you download a file then it is not marked as executable. So you have to do that either by right click and select "allow for executing" or from the command line(if you are 1337, or you don't have an option):

First change directory to where the folder is stored(usually ~/Downloads):

```
cd ~/Downloads
```Then make the file executable:

```
sudo chmod +x filename.exe
```I hope this helps. :)

EDIT: After looking at the guide, i don't think you have to do that? It should work fine to download the exe installer, do with it as i said above, and then it will install itself.

---

### Post by thefallofroy on 2010-06-25
Chmod command worked wonders, thanks alot! But perhaps maybe you could explain to me how to use Transmission then? 'Cause I tried it before when I first started using ubuntu, but it didnt seem to work. I couldnt figure out how to use it.

---

### Post by thefallofroy on 2010-06-25
Ok never mind, I figured it out. For some reason I couldn't figure out how to make it work last time... Thanks again for your help though.

---


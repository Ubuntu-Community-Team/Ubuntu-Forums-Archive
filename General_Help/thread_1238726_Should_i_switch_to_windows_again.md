---
title: "Should i switch to windows again ??"
date: 2009-08-12
forum: General Help
---

### Post by imcool on 2009-08-12
Hi to all members,

I switched to ubuntu 9.04 GNOME two months ago  thinking that it would be easy but seems that it is not as easy as windows.

so now i will tell my experience so far with ubuntu 9.04 GNOME and major problems that i m facing

PROBLEM 1 - Ok after installing ubuntu 9.04 GNOME i decided to install eclipse IDE ,7 days back  i downloaded the eclipse-SDK-3.4.2-linux-gtk.tar.bz file from the eclipse.org  but since 7 days i m messing up to know that how could i install the downloaded 79MB tar.bz eclipse IDe in ubuntu,i googled a lot in 7 days and found post related to .tar.bz installation but everywhere i got the same answer that extract the .tar file and then ./configure and then make that .tar.bz but i got stuck at ./configure command and i got error that COmmand not found,i also googled this error but no results , also i tired in IRC channels but all said that install that eclipse through manager rather than downloading and then instaling, but i want to install through downloaded file.

PROBLEM 2 - OK then after messing up I leave the installation of eclipse then i decided to install a bittorrent client for ubuntu 9.04 gnome as good as utorrent in windows but here also i got messed up coz in most of the linux torrent clients there is no option for REMOVE TRACKER , so here again i got messed up, i tried all bittorrents available in add/remove of ubuntu.

PROBLEM 3 - I searched a file name "eclipse" in Ubuntu 9.04default file manager and the file is in one of my partition but the ubuntu default file doesn't searched that file and then i searched that file in windows file search tool and got that.


So my question to other members

1.What is the solution to problem 1 i.e. how to install eclipse-SDK-3.4.2-linux-gtk.tar through terminal or any tar.bz please give me any updated and detailed link or video to install the .tar.bz files in linux ubuntu apart from google links.

2. what about the problem 2 and 3.

3.should i switch to windows again???

---

### Post by bodyharvester on 2009-08-12
those arent major problems, mate. just minor ones, ones which could be solved if youd post a thread for each one in the appropriate forum so people with the know-how can help ijnstead of saying "i give up"

good luck and stick with it man, Ubuntu has so much more to offer you!

- joe

---

### Post by llamabr on 2009-08-12
Why would you try to install it by hand?  The best reason to use ubuntu is the package manager.  No more going out to the internet, finding the file, downloading it, trying to install it, learning about dependencies, etc:

```
sudo apt-get install eclipse
```

---

### Post by orlox on 2009-08-12
The installation of eclipse is the same as in windows with zip they distribute. The tar.gz is only a compressed file. Extract it to your directory of choice, and the eclipse executable will be inside.

---

### Post by orlox on 2009-08-12
> **llamabr said:**
> Why would you try to install it by hand?  The best reason to use ubuntu is the package manager.  No more going out to the internet, finding the file, downloading it, trying to install it, learning about dependencies, etc:

```
sudo apt-get install eclipse
```

Eclipse in the repos is way out of date. The downloadable file from the eclipse.org site is very simple to install, and doesnt require any additional download on a fresh install of ubuntu.

---

### Post by llamabr on 2009-08-12
> **orlox said:**
> Eclipse in the repos is way out of date. The downloadable file from the eclipse.org site is very simple to install, and doesnt require any additional download on a fresh install of ubuntu.

I don't know anything about elicpse, obviously.  But can't you find a more up to date deb, rather than messing with the tarball?

But, if it installs as simply as you say, then go for it.

---

### Post by imcool on 2009-08-13
> **orlox said:**
> The installation of eclipse is the same as in windows with zip they distribute. The tar.gz is only a compressed file. Extract it to your directory of choice, and the eclipse executable will be inside.

I extracted the eclipse on the desktop could you tell me where is the executable file?

also what about bittorrent problem ?

---

### Post by P4man on 2009-08-13
I dont see what bittorrent problem you have to be honest. The default BT client is transmission and it sure has a 'remove torrent" function. But if you dont like transmission, try deluge (my favorite) or if you want a big huge fat client with all possible bells and whistels, azureus.  Or rtorrent, or bittornado.. heck, if you like none other than µtorrent, then run µtorrent. The windows version  works just fine after installing wine.

---

### Post by cascade9 on 2009-08-13
I cant speak for transmision (I really didnt like it), but Deluge does have a way to remove trackers....its just not labeled as such. 

Right click on the torrent-> tracker options-> edit tracker. 

Quite often you need to actually check carefully what options there are, and dont assume that things will be labeled in linux the same way they are in windows

---

### Post by bodyharvester on 2009-08-13
> **imcool said:**
> I extracted the eclipse on the desktop could you tell me where is the executable file?

when i tried to play the linux port of DOOM3 the "executable" file was "doom3.x86"

maybe the file you are looking for is "eclipse.x86", or something like that

---

### Post by imcool on 2009-08-13
I extracted the eclipse on the desktop could you tell me where is the executable file? so that I can install or eclipse ..

---

### Post by bodyharvester on 2009-08-13
> **imcool said:**
> I extracted the eclipse on the desktop could you tell me where is the executable file? so that I can install or eclipse ..

if its extracted then its installed, i think, im not sure, im just used to everything working now ;)

---

### Post by P4man on 2009-08-13
I dont have it here, but the file is probably called "eclipse".
If its not, copy paste the file list here, I dont feel like downloading 200Mb to find out :)

edit: also check this out:
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

if you scroll down, you'll find how to install it "properly"

---


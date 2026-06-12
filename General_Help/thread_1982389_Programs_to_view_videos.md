---
title: "Programs to view videos?"
date: 2012-05-18
forum: General Help
---

### Post by Camilia on 2012-05-18
bump already posted.

---

### Post by 2F4U on 2012-05-18
What kind of videos, what desktop environment?

---

### Post by lukeiamyourfather on 2012-05-18
Install VLC which is in the Ubuntu Software Centre or use this command.

```
sudo apt-get install vlc
```

If it can be played, it'll play it.

---

### Post by bruno9779 on 2012-05-18
I prefer Mplayer with the SMplayer frontend.

It needs some tweaking and installation of libraries, but I get better results on encrypted DVDs and some other file format.

Also I don't like the shift/ctrl+arrow approach that VLC has for fast-forward and rewind.

---

### Post by Camilia on 2012-05-18
> **lukeiamyourfather said:**
> 
```
sudo apt-get install vlc
```

Pasted in terminal. Still not able to view you tube videos or comcast.

Have ubuntu 12.04

---

### Post by plucky on 2012-05-18
> **Camilia said:**
> Pasted in terminal. Still not able to view you tube videos or comcast.

Have ubuntu 12.04

Try ```
sudo apt-get install ubuntu-restricted-extras
```


Good Luck

---

### Post by 0011235813 on 2012-05-18
> **Camilia said:**
> Pasted in terminal. Still not able to view you tube videos or comcast.

Have ubuntu 12.04

Your problem has nothing to do with video programs, like the excellent vlc or mplayer. Ubuntu comes with Totem (called "video player" or "movie player") that is nice if you like the YouTube plugins and stuff.

However, your issue appears to be Flash-related. Open Ubuntu Software Center, and search for "Flash". Click "Install" on "Mozilla flashplugin-installer" and enter your password. If it says no, open the terminal with Ctrl+Alt+T and enter:
```
sudo apt-get install flashplugin-installer
```
It will as you for your password. Note that you will not be able to see it as you type.

---

### Post by tumutanzi.com on 2012-05-18
I personally prefer mplayer, it is really great.

---

### Post by voodoo123 on 2012-05-18
If it is Youtube that you are having an issue with, then it is indeed a flash related issue. One of the above terminal commands for either the restricted extras or for flash plugin should work, but if you prefer a more graphical way to install Flash Player you can also go to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and download the .deb installer as well.

---

### Post by andrew.46 on 2012-05-18
SMPlayer + MPlayer is a great combination and you will find that the most recent version of SMPlayer plays youtube videos directly. For that matter you could try UMPlayer which even contains a youtube browser....

**Edit:** And of course SMPlayer can use smtube for youtube browsing as well (code taken from UMPlayer).

---

### Post by Camilia on 2012-05-19
Flash player and ubuntu-restricted-extras installed.

I am thinking of going back to ubuntu 11.10

---

### Post by zombifier25 on 2012-05-19
In Firefox, open the Addon Manager and go to the Plugin tabs, see if Flash Player is listed.

---


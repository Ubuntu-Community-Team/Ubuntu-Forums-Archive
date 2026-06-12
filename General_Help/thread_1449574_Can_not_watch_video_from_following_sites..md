---
title: "Can not watch video from following sites."
date: 2010-04-08
forum: General Help
---

### Post by bhishan on 2010-04-08
I can not watch videos from the following site:

 [http://stagevu.com](http://stagevu.com)


Anyone got any idea why?

---

### Post by Rasa1111 on 2010-04-08
get GNOME Mplayer

 sudo apt-get install gnome-mplayer

i ran into this the other day. 
couldnt play from any of those sites, 
after a few searches, and an install
they work fine now . :)

some kind of "missing plugin" for those sites. 

hope it helps

---

### Post by darolu on 2010-04-08
[http://stagevu.com/](http://stagevu.com/) works for me, the video I watched (few seconds only though) was encoded with DivX, you may need to install this codec (ubuntu-restricted-extras should have it).

The other sites required registration and honestly I can't be arsed; they seem like hosting sites like rapidshare or megaupload though, so you not being able to watch videos from these sites may depend on the video (and its codec) you download.

---

### Post by bhishan on 2010-04-09
> **Rasa1111 said:**
> get GNOME Mplayer

 sudo apt-get install gnome-mplayer

i ran into this the other day. 
couldnt play from any of those sites, 
after a few searches, and an install
they work fine now . :)

some kind of "missing plugin" for those sites. 

hope it helps

I tried it, did not work. :(

---

### Post by bhishan on 2010-04-09
> **darolu said:**
> [http://stagevu.com/](http://stagevu.com/) works for me, the video I watched (few seconds only though) was encoded with DivX, you may need to install this codec (ubuntu-restricted-extras should have it).

The other sites required registration and honestly I can't be arsed; they seem like hosting sites like rapidshare or megaupload though, so you not being able to watch videos from these sites may depend on the video (and its codec) you download.

I already had ubuntu-restricted-extras. Anyway I removed it and installed it again, but still does not work.

---

### Post by wojox on 2010-04-09
You can't watch them at all? I can view them but the buffering is real bad. If you have the medibuntu repo's enabled try installing the non-free-codecs: [http://wojox.homelinux.net/?p=77](http://wojox.homelinux.net/?p=77)

---

### Post by ron999 on 2010-04-09
Hi
Those videos play ok for me in Firefox.
The plugin that I'm using is **gecko-mediaplayer** from the repository.
So look in Firefox > Tools > Add-ons > Plugins
See which plugins you have got installed.

---

### Post by steveneddy on 2010-04-09
try this:

```
sudo apt-get install mozilla-mplayer
```

restart the browser and try it again

---

### Post by bhishan on 2010-04-12
> **wojox said:**
> You can't watch them at all? I can view them but the buffering is real bad. If you have the medibuntu repo's enabled try installing the non-free-codecs: [http://wojox.homelinux.net/?p=77](http://wojox.homelinux.net/?p=77)

No I cant watch at all. In Firefox the whole browser freezes, it has to force quit to run again. In Google Chrome when I click play the player disappears leaving a white background.

---

### Post by bhishan on 2010-04-12
> **steveneddy said:**
> try this:

```
sudo apt-get install mozilla-mplayer
```

restart the browser and try it again

Tried it, did not work. Thanks for the reply anyways.

---

### Post by bhishan on 2010-04-12
> **ron999 said:**
> Hi
Those videos play ok for me in Firefox.
The plugin that I'm using is **gecko-mediaplayer** from the repository.
So look in Firefox > Tools > Add-ons > Plugins
See which plugins you have got installed.

Could not find the plugin you are talking about. When I enter the name and search, a plugin named "System Video" shows up. Is it the one you are talking about?

---

### Post by 2hot6ft2 on 2010-04-12
Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
You will have to enter your password which wont be displayed just type it in and hit Enter
Then install gecko media player:
```
sudo apt-get install gecko-mediaplayer
```
Then restart firefox and try it out.

I'm publishing another one there right now.

---

### Post by greenstar on 2010-09-02
> **2hot6ft2 said:**
> Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```You will have to enter your password which wont be displayed just type it in and hit Enter
Then install gecko media player:
```
sudo apt-get install gecko-mediaplayer
```Then restart firefox and try it out.

I'm publishing another one there right now.

Worked great for me on the 1st try. Thanks.

---

### Post by envis on 2010-12-18
thank you, just a "sudo apt-get install gecko-mediaplayer" did it for me

i skipped the "sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc" cos i knew i had none of it installed but if youre not sure might be safer to do it first

---


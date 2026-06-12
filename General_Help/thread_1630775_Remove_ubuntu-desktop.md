---
title: "Remove ubuntu-desktop"
date: 2010-11-25
forum: General Help
---

### Post by buffchick on 2010-11-25
*please be patient. New to linux and ubuntu*  So I was hoping my poor little old PC that I've been using as a media server could handle X but it can't. I'm running Maverick Meerkat server as a media server and I was going to install a gui on it so I could remote desktop in and download torrents as well. However, this poor little old PC with it's cheap junky static HDD just can't handle it. tightVNC client keeps saying it's loading but nothing happens so I wanted to remove all the packages I just installed but, if you apt-get remove ubuntu-desktop it only removes this little 64k file. I think it's where all the packages that it installs are listed but I want to remove all the packages it installed. Could someone point me in the right direction on how to do this? I'd really appreciate it.

---

### Post by tredegar on 2010-11-25
```
sudo apt-get clean
```
might help you after "it only removes this little 64k file"
Do a **df -h** before and after the above command to see if it is helpful.

If not, please tell us exactly what "little old PC with it's cheap junky static HDD" really is. I am happily running 10.04 on my EEE701 with its 4GB SSD "HDD", but I do also have an 8MB SD-whatever card plugged into it.

Old, cheap stuff still works well with today's linux, if you know which choices to choose, and do not mind a little bit of puzzle-solving ;)

---

### Post by zvacet on 2010-11-25
```
sudo tasksel remove ubuntu-desktop
```

Maybe you can get GUI with Lubuntu.

```
sudo apt-get install lubuntu-desktop
```

---

### Post by itang sanjana on 2010-11-25
Ubuntu-desktop is a meta package, thats why. Try using options clean, autoclean and then autoremove? But read apt-get man page first ```
man apt-get
``` .. HTH

EDIT:
oops, a bit too late .. :)

---

### Post by ajgreeny on 2010-11-25
**sudo apt-get clean** and **autoclean** do not remove any applications, only the packages that were downloaded in order to install the applications.

I also don't think that the mentioned **autoremove** will do much either, as it only removers applications and packages that are no longer needed as dependencies of any other package, and because of all the gnome interconnections and inter-dependencies in ubuntu-desktop, I think there will be very few of those.

You could try using the command shown in this page
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
for removing gnome, but I think even that will not do it completely.

I am sure there is a way using the terminal and either apt-get or aptitude, but I'm afraid I do not know more detail than that.  Try a full search in google or [www.googlubuntu.com]("http://www.googlubuntu.com") and you may come up with something more definite

---

### Post by Hippytaff on 2010-11-25
I agree with zvacet, maybe get rid of ubuntu and try something lighter...I prefer fluxbox to lxde

see here - [http://xwinman.org/](http://xwinman.org/)

---

### Post by buffchick on 2010-11-26
> **Hippytaff said:**
> I agree with zvacet, maybe get rid of ubuntu and try something lighter...I prefer fluxbox to lxde

see here - [http://xwinman.org/](http://xwinman.org/)

right on. I only went with ubuntu because it's what we use at work and I'm familiar with the command line interface. All I need is something that will run samba and mediatomb and will accept the LVG RAID 1 mirrors I have setup already from a previous install of rpath.

---

### Post by wilee-nilee on 2010-11-26
> **buffchick said:**
> right on. I only went with ubuntu because it's what we use at work and I'm familiar with the command line interface. All I need is something that will run samba and mediatomb and will accept the LVG RAID 1 mirrors I have setup already from a previous install of rpath.

check post 5 and the psychocats link for getting rid of the whole Ubuntu desktop.

---

### Post by nothingspecial on 2010-11-26
> **buffchick said:**
>  I was going to install a gui on it so I could remote desktop in and download torrents as well.

You don`t need a gui to go torrenting

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

[https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

### Post by matt_symes on 2010-11-26
Hi

> **nothingspecial said:**
> You don`t need a gui to go torrenting

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

[https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

.....or for browsing (Lynx) and mail (Mutt)

You don't really need a gui

Kind regards

---

### Post by nothingspecial on 2010-11-26
> **matt_symes said:**
> Hi



or for browsing (Lynx) and mail (mutt)

Kind regards

links2/elinks and alpine (in my case);)

---

### Post by matt_symes on 2010-11-26
Hi

> links2/elinks and alpine (in my case):wink::popcorn:. Nice :)

Kind regards

---

### Post by buffchick on 2010-11-26
thanks for all the help guys. worked like a charm. I'm looking into torrents from the command line now! :)

---

### Post by buffchick on 2010-11-26
> **tredegar said:**
> ```
sudo apt-get clean
```might help you after "it only removes this little 64k file"
Do a **df -h** before and after the above command to see if it is helpful.

If not, please tell us exactly what "little old PC with it's cheap junky static HDD" really is. I am happily running 10.04 on my EEE701 with its 4GB SSD "HDD", but I do also have an 8MB SD-whatever card plugged into it.

Old, cheap stuff still works well with today's linux, if you know which choices to choose, and do not mind a little bit of puzzle-solving ;)
It's an old Dell Optiplex GX150 with an 8GB ide to compact flash adapter (the original cheapo solid state drive!) and 6 1.5Tb drives for storage. It's the CF SSD that is the bottleneck point. It's really really really slow. I should probably replace it now that real SSD's are cheaper.

---

### Post by zvacet on 2010-11-28
If you want to use CLI for torrents,then install rtorrentt from synaptic.Read [this.]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/")

---


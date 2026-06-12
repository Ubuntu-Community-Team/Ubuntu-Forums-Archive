---
title: "Synaptic Package Manager fails to download anything"
date: 2011-11-29
forum: General Help
---

### Post by nikeair on 2011-11-29
Hi I recently installed Ubuntu 9.04, sorry old version, but can't seem to get my package manager to work. It fails to download anything i try. Any help would be greatly appreciated I want to install GStreamer plugins and VLC but can't because of that.

---

### Post by buntudawg on 2011-11-29
Ubuntu 9.04 has reached the end of its support life (over 12 months ago).

Is there a reason you aren't using a more recent version?

If you have to use it, you could try editing your sources.list so you replace:
 [I][COLOR=Black]archive.ubuntu.com[/COLOR]
with:[/I]
 *[COLOR=Black]old-releases.ubuntu.com[/COLOR]*

---

### Post by nikeair on 2011-11-29
Ok I will try replacing my sources. The reason I am still using it is I found it on an old CD I ordered once and was going to try it again. I am going to try downloading the newest one soon. It would be nice if I could get a torrent for it because my connection isn't the best.

Edit: Ok I tried replacing the repositories but it still fails to fetch on all. I must be doing something wrong.

---

### Post by buntudawg on 2011-11-29
What are the errors?

You can get the torrent from here:
[http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt)

---

### Post by nikeair on 2011-11-30
Thanks for the torrent.
Errors are "Could not download all repository indexes" and it gives a big list of failed addresses. I think i must have not changed the main repository. I don't exactly know how. I see the 3rd party source list but nothing else when I go to change it.

---

### Post by buntudawg on 2011-11-30
Basically you need to:

Backup sources.list:
```
[FONT=monospace]sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak[/FONT]
```Then edit the list using:
```
sudo gedit /etc/apt/sources.list
```Save.
Then 
```
sudo apt-get update
```Then try installing packages. Personally I would recommend downloading the torrent and installing a newer version.

---

### Post by nikeair on 2011-12-01
I took your advice and got the newest version. I am glad I did it is way better. Thanks for the help.

---

### Post by buntudawg on 2011-12-01
No Problems. Enjoy.  Don't forget to mark thread solved.

---


---
title: "how to see source code of open source software"
date: 2010-09-12
forum: General Help
---

### Post by Praveen30 on 2010-09-12
i want to see the source code of smplayer software.from where i can see source code of open source  softwares?

---

### Post by TeoBigusGeekus on 2010-09-12
[Try this.]("http://lmgtfy.com/?q=smplayer+source+code")

---

### Post by Praveen30 on 2010-09-12
> **TeoBigusGeekus said:**
> [Try this.]("http://lmgtfy.com/?q=smplayer+source+code")
Well thanks for googling for me.i have already tried this but i am unable to find.it would be good if you refer some sites or any links...

---

### Post by TeoBigusGeekus on 2010-09-12
The first link google provides will lead to [this]("ftp://ftp.berlios.de/pub/smplayer/source/") after a couple of clicks.

---

### Post by pbrane on 2010-09-12
How about this?
[http://smplayer.sourceforge.net/downloads.php?tr_lang=en]("http://smplayer.sourceforge.net/downloads.php?tr_lang=en")
Then select **mplayer-0.6.9.tar.bz2 (1.64 MB)** under **Linux**

---

### Post by jerome1232 on 2010-09-12
well to see the source for the version in ubuntu repos you can

```
apt-get source smplayer
```

To get the latest source go to their site. Do a little poking around and find it.

I did the poking around for you. Their latest and greatest source is here.

[http://sourceforge.net/apps/mediawiki/smplayer/index.php?title=Unstable_releases](http://sourceforge.net/apps/mediawiki/smplayer/index.php?title=Unstable_releases)

---

### Post by Praveen30 on 2010-09-12
> **jerome1232 said:**
> well to see the source for the version in ubuntu repos you can

```
apt-get source smplayer
```To get the latest source go to their site. Do a little poking around and find it.

I did the poking around for you. Their latest and greatest source is here.

[http://sourceforge.net/apps/mediawiki/smplayer/index.php?title=Unstable_releases](http://sourceforge.net/apps/mediawiki/smplayer/index.php?title=Unstable_releases)
Thanks bro.really helpful!!!!:p

---

### Post by Praveen30 on 2010-09-12
after executing this command--apt-get source smplayer

i  am getting  this error-

$ apt-get source smplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 2,155kB of source archives.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse smplayer 0.6.7-1 (dsc) [1,055B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse smplayer 0.6.7-1 (tar) [2,144kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse smplayer 0.6.7-1 (diff) [9,146B]
Fetched 2,155kB in 5min 14s (6,851B/s)                                         
sh: dpkg-source: not found
Unpack command 'dpkg-source -x smplayer_0.6.7-1.dsc' failed.
Check if the 'dpkg-dev' package is installed.
E: Child process failed

---

### Post by jerome1232 on 2010-09-12
> **Praveen30 said:**
> after executing this command--apt-get source smplayer

i  am getting  this error-

$ apt-get source smplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 2,155kB of source archives.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse smplayer 0.6.7-1 (dsc) [1,055B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse smplayer 0.6.7-1 (tar) [2,144kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse smplayer 0.6.7-1 (diff) [9,146B]
Fetched 2,155kB in 5min 14s (6,851B/s)                                         
sh: dpkg-source: not found
Unpack command 'dpkg-source -x smplayer_0.6.7-1.dsc' failed.
[COLOR="Red"]Check if the 'dpkg-dev' package is installed.[/COLOR]
E: Child process failed

Did you try what the error message suggested?

---

### Post by Praveen30 on 2010-09-12
> **jerome1232 said:**
> Did you try what the error message suggested?

i didn't see it.now it is done!!! thanks!!!
Go here for detail procedure--
[http://http://tricksfind.blogspot.com/2010/09/how-to-see-source-code-of-open-source.html]("http://http//tricksfind.blogspot.com/2010/09/how-to-see-source-code-of-open-source.html")

---

### Post by Praveen30 on 2010-09-12
Go here for detail procedure--
[http://http://tricksfind.blogspot.com/2010/09/how-to-see-source-code-of-open-source.html]("http://http//tricksfind.blogspot.com/2010/09/how-to-see-source-code-of-open-source.html")

---


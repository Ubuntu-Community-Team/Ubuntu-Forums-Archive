---
title: "What I did to make the mplayer-plugin work better with Firefox"
date: 2006-03-14
forum: General Help
---

### Post by s|k on 2006-03-14
I was having trouble with the mplayer-plugin in Firefox. It worked, but man was it choppy and slow. It was unbearable to use. I decided to upgrade to a non-ubuntu repository version. The version in the repository is 3.17, and the latest stable version is 3.21.

[http://mplayerplug-in.sourceforge.net/download.php](http://mplayerplug-in.sourceforge.net/download.php)
Download mplayerplug-in-3.21.tar.gz
I downloaded this file and moved it to my Home directory.

I then had to install some development libraries from the repository:

libglib2.0-dev (I found it in Synaptic).
and then from the terminal I ran this:
```
sudo  apt-get build-dep mozilla-mplayer
```

I also looked for mozilla dev packages in Synaptic, but I don't know how necessary that was.

I then followed the instructions on the installation help page:
[http://mplayerplug-in.sourceforge.net/install.php](http://mplayerplug-in.sourceforge.net/install.php)
Scroll down to the mplayer-plugin section.

It was really simple:
```

tar -xzvf mplayerplug-in-3.21.tar.gz
cd mplayerplug-in
./configure
make
make install
```
Then you have to configure it:
[http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php)

```
 sudo nano ./.mplayer/config

```

In the config file put in:
```
ao=esd
```

I then removed the Synaptic version of the mplayer plugin using the Synaptic Package Manager (maybe I should have done this first?).

I restarted Firefox, went over to Comedy Central's web page and played a DailyShow video and no more choppyness! 

It works great now. Hopefully that was helpful and wont kill gnome. :)

---

### Post by yanik on 2006-03-14
How you could've save yourself a lot of troubles:

```
nano -w /etc/mplayerplug-in.conf
```

add/uncomment

```
ao=esd
```

Then restart firefox

Goodbye choppy video...

---

### Post by s|k on 2006-03-14
[QUOTE=yanik]How you could've save yourself a lot of troubles:

```
nano -w /etc/mplayerplug-in.conf
```

add/uncomment

```
ao=esd
```

Then restart firefox

Goodbye choppy video...[/QUOTE]
I thought so too, but I didn't know about configuring it until I did all that work. :0
Anyways, it all works nicely now.

By the way, what does that line in the config do?

---

### Post by yanik on 2006-03-14
ao stands for audio out, it specifies the output to use so mplayer doesn't have to probe or guess or whatever it does.

---

### Post by jalm111 on 2006-03-14
esd=enlightened sound daemon

runs EsounD

---


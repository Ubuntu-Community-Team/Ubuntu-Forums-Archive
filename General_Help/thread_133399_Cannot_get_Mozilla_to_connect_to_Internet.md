---
title: "Cannot get Mozilla to connect to Internet"
date: 2006-02-20
forum: General Help
---

### Post by AlFresco on 2006-02-20
Hi,

I am a new user to Linux and have recently installed 'Ubuntu'. My problem is that I cannot get Firefox to connect to the Internet although on my other computer which is running Windows Me I have no problems.
I connect via an ADSL router and have my setting as
'connect directly to the internet'
'no proxy'
These settings are the same as they are for my WinME machine so I do not understand what I am doing wrong.
Can anyone please help?
:confused:

---

### Post by chimera on 2006-02-20
How did you try to connect so far? The "normal" way of activating an ADSL connection is 

```

sudo pppoeconf

```

, but I have no experience whatsoever with routers.

---

### Post by AlFresco on 2006-02-23
Hi Chimera,
Thanks for the info, but still no luck.
All I get when typing the command in (in root) is
'command not found'

Mozilla works a treat in Win2K, Konqueror (and Kmail) connects using Mandriva so I'm sticking with what works and damn the rest.

---

### Post by yootje on 2006-02-23
But do you get an internet conncetion with Ubuntu? Can you use apt-get? Can you receive e-mail, can you get internet via an other browser?

---

### Post by lamego on 2006-02-23
I believe it does not have network at all.

If you need pppoeconf and it is not installed (and I am assuming it comes with the ubuntu cd), you will need to install it with:
```
sudo apt-get install pppoeconf
```

---

### Post by hdagelic on 2006-02-23
I did it like this (I am using an ethernet modem):

download rp-pppoe 3.7 (tar.gz file) from

[http://freshmeat.net/projects/rp-pppoe/](http://freshmeat.net/projects/rp-pppoe/)

Extract and compile:

sudo tar zxvf rp-pppoe-3.7.tar.gz -C /opt/
sudo chown -R root:root /opt/rp-pppoe-3.7/
gksudo /opt/rp-pppoe-3.7/go-gui

The howto on [http://ubuntuguide.org/](http://ubuntuguide.org/) sais that you run it with 

gksudo /opt/rp-pppoe-3.7/go-gui

but this is wrong because it compiles the program every time and it takes ages to launch...

Create a new launcher with the command: 

gksudo /usr/bin/tkpppoe (this is how you should run it)

---


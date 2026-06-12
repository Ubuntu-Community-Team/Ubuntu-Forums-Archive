---
title: "Google Earth stoped working"
date: 2009-12-12
forum: General Help
---

### Post by Sisophon2001 on 2009-12-12
When I start Google earth in Ubuntu 9.10 I get a black screen, and after a while I get a message that GE cannot connect to the Google earth servers. Following the advise in the help links GE displayed, it tells me to check my network connection and firewall settings. It also advises to un-install and reinstall. All of this I have tried without success. I tried both the version in Ubuntu repositories and a direct download from Google. I cleared the cache as recommended. I installed GE on a windows laptop, and that works perfectly when connected to the same router my Ubuntu computer is connected to. 

GE worked before I upgraded from 9.04, but I am not 100% sure if I tested it immediately after I upgraded. It could be the problem started when I upgraded. It could also be that I did something wrong while trying to get a printer to work using samba.

As far as I understand Ubuntu has no firewall installed by default, so if I can connect from windows, why not from Ubuntu? Is there anything else I can test? Could I have blocked Google Earth in anyway while messing with samba?

Thanks for any advice.

Garvan

---

### Post by Sisophon2001 on 2009-12-15
Three days and no reply - I am going to try one more time. 

BUMP

Garvan

Additional Information.
I installed Google Earth on a netbook running UNR 9.10 and it did not work when connected to my router, but it works when connected to my mobile phone (different service provider).

UBUNTU 9.10 Connected to router == Does not work
UBUNTU UNR 9.10 Connected to router == Does not work
WINXP Connected to router == Okay
UBUNTU UNR 9.10 Connected to mobile phone == Okay

In the past, but can no longer test
UBUNTU 9.04 Connected to router == Okay

EDIT 19 January 2010
The problem was fixed most likely by an automatic update to Ubuntu, certainly not by anything I did. I can now use Google earth again.

---

### Post by HectorG on 2010-02-01
Having same issue. I have also tried reinstalling from various sources still nothing

---

### Post by HectorG on 2010-02-03
I just got my google earth to work and I am not sure exactly why itw working now but here is what I did...

Uninstalled all versions of my googleearth.

bin from earth.google.com 

cd /opt/google-earth/bin
sudo ./uninstall

then go to synapic and uninstall googleearth

Download latest nvidia drivers fro their site (not sure if this had anything to do with it)
exit from X
/etc/init.d/gdm stop

you should be in the terminal now
cd Downloads
sudo ./nvidiadrivername.bin

reboot

get the bin from earth.google.com for googleearth

mv the bin to /opt/google-earth

run it as the user NOT ROOT
./GoogleEarth.bin

dont click run when it ends

click button on left to exit

from the internet menu select google earth... 

Hope it works...

---

### Post by retlolo on 2010-02-09
same exact problem; nothing I've seen or tried helps: it starts for 2 seconds, then returns to the desktop.  This after visual effects disabled, etc.  Help?  RW

---

### Post by Sisophon2001 on 2011-06-02
I had this problem again recently - and I found a good solution here.

[http://rohieb.wordpress.com/2011/01/22/google-earth-and-ipv6-dns-lookups/]("http://rohieb.wordpress.com/2011/01/22/google-earth-and-ipv6-dns-lookups/")

I added this

nameserver 208.67.222.222
nameserver 208.67.220.220

to my **/etc/resolv.conf** file.

And it worked!

Garvan

---


---
title: "Successfull installation of Ekiga 2.0.1 on Ubuntu 5.10"
date: 2006-03-15
forum: General Help
---

### Post by swamytk on 2006-03-15
Hi,

I have installed Ekiga 2.0.1 successfully in Ubuntu Breezy (5.10). I built it from source downloaded from [http://ekiga.org](http://ekiga.org). I had to download avahi-0.6.9 source and installed it as dependency ( I disabled mono and monodoc while installing avahi since backport is not available for latest version of monodoc). All other dependencied were met by the ubuntu repositories.

But the important point is I don't have anybody else to communicate with me through this tool... I don't have mic and camera.... wait..wait.. i can understand your point that what is the use of installing ekiga? Just for Fun!!!!!!!!!!!

Regards
T.KaruppuSwamy

---

### Post by kaamos on 2006-03-15
For those that don't wish to compile additional libraries, here is a simple way to install:

Applications->Accessories->Terminal
```
sudo su
echo "deb http://snapshots.gnomemeeting.net/ubuntu/ breezy main" >> /etc/apt/sources.list
apt-get update
apt-get install ekiga-cvs
exit

```
Applications->Internet->Ekiga

---

### Post by swamytk on 2006-03-15
That's it Kaamos! thanks for your shortcut technique!

---

### Post by damu on 2006-03-15
Thanks so much kaamos for that.  :) 

I am actually doing all my phone calls  with Voip (PC to Phone), and loads of them are from UK to France. 
I found way cheaper providers than Skype (free for phonecalls to landlines on my destinations!). On WinXP, I used VoipBuster. On Ubuntu, I intend to use [SIPDiscount]("http://www.sipdiscount.com/en/") which might be another name for the same SIP company...

I will try to configure Ekiga now to use it. ;) 

I also read about another very cheap uk Voip company in the forum.

I will still need Skype for a while as my contacts have my skype in phone number. It's a real pain in the b** as Skype doesn't work great at all for me on Breezy. After each phone call, I have to close and restart Skype, otherwise I can't either receive or give a phonecall (connection failed...) Did anyone of you experiment the same bug?

Anyway thanks again for this easy way to install Ekiga!

---

### Post by it.henrik on 2006-03-16
Anyone know how to install the stable version from [www.ekiga.org?](www.ekiga.org?)

---

### Post by damu on 2006-03-16
It seems I can't connect to  a SIP provider with the snapshot version of Ekiga, and it can't be debugged (I can't manage to edit the logs through terminal which could help to find out the issue...).

One has to use the last version of Ekiga....

I tried a synaptic, there is a new package available, but it doesn't find the sources to download it....would have be too easy  ... :neutral: 

So, I downloaded the latest package available for ubuntu breezy from Ekiga.net
But I can't manage to install them :
> damu@ubuntu:~$ sudo dpkg -i /home/damu/downloads/libpt-1.10.0_1.10.0-1.breezy.1404_i386.deb
Selecting previously deselected package libpt-1.10.0.
dpkg: considering removing libpt-1.8.3c2 in favour of libpt-1.10.0 ...
dpkg: no, cannot remove libpt-1.8.3c2 (--auto-deconfigure will help):
 libpt-plugins-v4l2 depends on libpt-1.8.3c2 (= 1.8.7-1ubuntu1)
  libpt-1.8.3c2 is to be removed.
dpkg: regarding .../libpt-1.10.0_1.10.0-1.breezy.1404_i386.deb containing libpt-1.10.0:
 libpt-1.10.0 conflicts with libpt-1.8.3c2
  libpt-1.8.3c2 (version 1.8.7-1ubuntu1) is installed.
dpkg: error processing /home/damu/downloads/libpt-1.10.0_1.10.0-1.breezy.1404_i386.deb (--install):
 conflicting packages - not installing libpt-1.10.0
Errors were encountered while processing:
 /home/damu/downloads/libpt-1.10.0_1.10.0-1.breezy.1404_i386.deb

I tried to install some other packages before this one, but there would always be some problems of dependencies with packages not yet installed, mostly this one....

---


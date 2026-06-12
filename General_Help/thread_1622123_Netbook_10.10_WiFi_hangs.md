---
title: "Netbook 10.10 WiFi hangs"
date: 2010-11-15
forum: General Help
---

### Post by rebrain on 2010-11-15
Hallo,

I am having a problem with the WiFi connection on a Netbook Edition of Ubuntu 10.10
The Netbook I am running is Asus Eeepc 1005HA.

I am connecting to the Hidden Wireless Network with WPA2 Personal.

The connection succeeds and it seems everything is working great for about 2 minutes. Then the internet stops working and the browser just keeps loading. To restore the connectivity I reconnect to the same network again which fixes the problem for the next 2 minutes. Then I have to reconnect again.

It is really annoying. Does anyone know how to fix this?

It is a practically fresh install. I always install Ubuntu and try new releases out but never use it because of such problems.

Sincerely,
Rebrain

---

### Post by rebrain on 2010-11-16
bump

---

### Post by rebrain on 2010-11-21
Still experiencing the issue!
Can noone help?

---

### Post by rebrain on 2010-11-25
Is the topic really going to go unanswered?

I am still having the issue.

---

### Post by davec64 on 2010-11-25
Not familiar with this machine but I did find this:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus Eee PC 1005HA]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus Eee PC 1005HA")

Karmic
> Wireless (Atheros AR9285) works out of the box, but connection is flaky. To fix, open a terminal and type 'sudo apt-get install linux-backports-modules-karmic'

And for Lucid it suggests:
> for wireless issue (see Karmic) Run 'sudo apt-get install linux-backports-modules-wireless-lucid-generic' instead.

So for Maverick you could try
```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

I don't know if that will fix it (the package exists), but if you're clutching at straws, its got to be worth a try!

Best of luck!  :)

---

### Post by infowars on 2010-11-27
davec is correct about Ubuntu.

I'm running 1000HA also

I am running eeepc 9.10 and everything is working out of the box including Wifi fulltime and FAN control. on Live CD.

the eeepc control app didn't work for the fan control on eeeMint 9 only Wifi, but didn't want to fry the board just to use the net so I am over here with Ubuntu 9.10 getting it to install in another partition..

EEEPC Ubunutu 10 more than likely wont be out of testing for a few more months, just hopefully sooner, event tho it is listed to be dnloaded and installed, it's beta mostly.

Search for "eeepc control" updated and see if the eeepc crowd updated the app for us....:P

Try this [http://ftp.riken.jp/Linux/simosnet-livecd/EeePC/eeeubuntu-10.10.iso](http://ftp.riken.jp/Linux/simosnet-livecd/EeePC/eeeubuntu-10.10.iso) 
Is this the one you installed???
Hope that helps!

---

### Post by rebrain on 2010-11-29
@davec64:

This happens when I try to execute what you suggested.
I actually tried that fix before an update. It did not fix the problem and after the update the error below appears and the package is also in the Update Manager but it is greyed out.

> The following packages have unmet dependencies:
 linux-backports-modules-wireless-maverick-generic : Depends: linux-backports-modules-wireless-2.6.35-23-generic but it is not installable



The previous versions of ubuntu seemed to work smoothly, how can it be that the new version is actually a step back. 10.10 does not even install on my Desktop. Installer crashes.

@infowars: I installed the standart Netbook Edition 10.10 from Ubuntu.com . I always try to upgrade to see what's new but the 2 most recent ubuntu releases just don't seem to meet expectations. Good idea with the side launcher but poor execution and so slow.
I guess I will try the eeebuntu. Or downgrade to 9.10.

It is sad though that I will need to customize grub and install few but important programs on the new system all over again. Thinking about trying openSuse or Mandriva, but I am used to Ubuntu.

---

### Post by infowars on 2010-11-30
> @infowars: I installed the standart Netbook Edition 10.10 from  Ubuntu.com . I always try to upgrade to see what's new but the 2 most  recent ubuntu releases just don't seem to meet expectations. Good idea  with the side launcher but poor execution and so slow.
I guess I will try the eeebuntu. Or downgrade to 9.10.eeeubuntu ALL the way..... I did the 10.4 under Wubi and had to add eeepc control 2. ?
to get fan working correctly. Fan is most important as is Wifi for me....
I have links to eeepc linux distros including Mint (which everything worked but me no "terminal type guy so apps didn't install as easy as the more advanced seem to think)

If you want the eeepc link I can get it to ya.

Im sticking with Ubuntu 10.4 and NOT touching 10.10 until the "they" get OUT all de bugs. And what Ive read on this forum, it has more bugs than windows (well maybe NOT!)


> It is sad though that I will need to customize grub and install few but  important programs on the new system all over again. Thinking about  trying openSuse or Mandriva, but I am used to Ubuntu.     Mandriva is a grand OS but I couldn't get wifi running even with netwrapper hoops and jumps, songs and dance.

With Sbackup, standard in Ubnutu 10.4 do a BKUP, and save to stick... than reinstall /home and /var etc....which is all our preferences,  and BINGO in a few minutes....UP and running... Hooray

I tried to get "remastersys" clone the entire distro to CD....to install but couldn't get repository to work in third party software, and I tied to install the remastersys app that I have, but Ubuntu would allow me to that either... out of date blah, blah, blah..... so I went with the Sbackup ... that is a shame also....I got "remastersys" working in MINT 8?????

Well if ya need the eeepc linux distros list..pm me and I send it to you as I don't know if I can place URLs of other distros???

Happy distroing! :D

---


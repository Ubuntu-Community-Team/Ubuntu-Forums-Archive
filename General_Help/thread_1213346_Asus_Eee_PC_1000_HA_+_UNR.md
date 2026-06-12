---
title: "Asus Eee PC 1000 HA + UNR"
date: 2009-07-14
forum: General Help
---

### Post by carloshiga on 2009-07-14
Does anybody here have installed the Ubuntu Netbook Remix on an Asus Eee PC 1000 HA? I've heard that there are some problems with the wireless connection and the update manager.
I am thinking about buying one, but if the UNR doesn't work fine maybe it is better to buy another model.

Thanks.

---

### Post by cuatl on 2009-07-15
you need install ndiswrapper (windows xp wifi driver) in 1000ha.

---

### Post by irishlyrucked on 2009-07-17
I have the 1000HA.  I'm currently on my 5th installation of UNR trying to get the wireless to work correctly.  I've been googling to no avail.  Connecting is fine, but it's slower than dialup speeds on surfing the web.

---

### Post by irishlyrucked on 2009-07-17
I can confirm the 1000ha works with a few issues.

Wireless does indeed work with ndiswrapper.
[http://ubuntuforums.org/showpost.php?p=7488814&postcount=2](http://ubuntuforums.org/showpost.php?p=7488814&postcount=2)

desktop-switcher needs to be upgraded.
[https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519/comments/28](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519/comments/28)

webcam does not work.
Turn on wireless in the bios.  Also might have to set the resolution in gconf.
$sudo apt-get install gconf-editor
$sudo gconf-editor
apps > cheese
set resolution to 640x480 or 800x600

---

### Post by gpw1 on 2009-07-25
Can you swap out the wireless card for na intel 3945 wireless card

---

### Post by cbraxton on 2009-07-25
> **carloshiga said:**
> Does anybody here have installed the Ubuntu Netbook Remix on an Asus Eee PC 1000 HA? I've heard that there are some problems with the wireless connection and the update manager.


What issues are there supposed to be? I have 9.04 Netbook Remix on my Eee 1000HA and the wireless and update manager seem to work OK. (Though granted I only make occasional use of the wireless.)

---

### Post by carloshiga on 2009-08-03
Hi, I bought the Asus Eee PC 1000 HA. I installed the UNR 9.04 and everything ALMOST worked out-of-the-box. The wireless card was recognized but the connection was really slow, even close to my wireless router. The wireless card is an Atheros AR242X. After two days I solved the problem and I'm posting here my solution.

Here is what I did to get my Atheros AR242X working on my Eee PC 1000 HA:

Create a directory to save the driver:

```
mkdir madwifi
```

Then, download the driver here (you'll need a wired connection or you can download it using another computer and copy it to the madwifi directory):

[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)

The madwifi-hal-0.10.5.6-current.tar.gz is the one that worked for me. Once you extracted the files in the .tar.gz file, enter in the directory extracted:

```
cd madwifi-hal-0.10.5.6-r4068-20090705/
```

Next, install the build-essential:

```
sudo apt-get install build-essential
```

Run the make script:

```
make
```

Install the driver:

```
sudo make install
```

Edit the file /etc/modules adding "ath_pci" (without the quotes) to its end. Finally, reboot your Eee PC.

---


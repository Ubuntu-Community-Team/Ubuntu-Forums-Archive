---
title: "my xubuntu is slow, but i don't want to change to another linux distro."
date: 2009-08-24
forum: General Help
---

### Post by kemedo on 2009-08-24
Hello, 
i know that this topic was already mentioned on this forum, but i don't feel totally clarified.
I made a fresh install of xubuntu on a Athlon 1000 mhz with 384 mb of RAM, with an hdd of 40gb, and i really feel the os slow, even opening menus, the response is really slow.
I don't want to compare of course, but my windows xp is much faster than my xubuntu.
There's nothing i can do? Do i really have do migrate to a lighter distro?
Should i try another desktop environment?
I think that my computer specs would be enough to run xubuntu, but seems not.
Sorry for my bad english.
I would appreciate some help.
Thanks for the great forum and support!

---

### Post by ibutho on 2009-08-24
Hi and welcome to forum. Your specs are good enough to run XFCE, but in my opinion other distros do a better job with XFCE than Xubuntu. The problem is that it includes many GNOME apps and tries to mimic GNOME. If you don't want to use another distro, you could do a base install of Ubuntu using the Ubuntu server cd and then install install the xfce4 metapackage using apt-get (after enabling the universe repository in /etc/apt/sources.list).

---

### Post by kemedo on 2009-08-24
thanks a lot for the fast reply.
I thought on making that, as i read in some places, but i have a doubt, i use wireless to connect to internet, when i make the cli installation, my wireless card will be recognized and configured? how should i connect to an Acess Point from the command line?
Thanks once more.

---

### Post by wojox on 2009-08-24
You may also want to have a look at 
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

I used it for pure gnome on one partition and pure kde on another partition.

---

### Post by kerry_s on 2009-08-24
just install a lighter setup:

in terminal:
**sudo apt-get install lxde**

in the gui:
just search & install lxde

log out, select lxde from the session menu & log back in.

---

### Post by kemedo on 2009-08-24
thanks a lot for the fast replies, i am already installing lxde to give it a try.
@wojox, what exactly do that commands, they remove every gnome package attached to xubuntu installation?

---

### Post by kemedo on 2009-08-24
i finished lxde installation, and logged out, after it gave me an error saying that couldn't start xorg, that the configuration was wrong, and to restart gdm when the configuration is good.
In the error it said something about vesa, the thing is  that now i'm on the command line, but i can't see the normal kemedo-desktop$> and it doesn't accept any commands, it doesn't make nothing...
someone can help me?

---

### Post by ibutho on 2009-08-24
Try using a different terminal by doing Ctrl-Alt-F2 (you can use F1 to F6 to go to different virtual terminals and F7 to go to virtual terminal 7 where a gui is run from).

---

### Post by kemedo on 2009-08-24
i already managed to enter the shell, i removed lxde, but still can't enter on X.
I looked at the log, and the problem is Nvidia driver, i remember in the installation, xubuntu asked if i wanted to use Nvidia driver, and i said yes.
Now cannot load the driver, someone can help me please, i'm a total noob, and now i can't make nothing...
I just installed lxde, nothing more!

---

### Post by kerry_s on 2009-08-24
if the nvidia driver was updated, try rebooting so the new kernel module can load.

thats-> **sudo reboot**
if your on the command line.

---

### Post by kemedo on 2009-08-24
that didn't worked kerry, i had to change the driver from nvidia to nv in xorg.conf file.
how can i repair my nvidia driver?

---

### Post by kerry_s on 2009-08-24
you could try using synaptic to uninstall & install it again.

---

### Post by kemedo on 2009-08-25
hello again,
so i made a fresh install of Ubuntu Server.
As i supposed, my wireless connection is not configured.
I want to connect to an wpa connection, ive executed this commands but without success.
sudo ifdown wlan0
sudo iwconfig wlan0 essid nameofessid
sudo iwconfig wlan0 channel 11
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 key password
sudo ifup wlan0

after it outputs some lines like:
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4

just changing the interval number.
and finishes like:
No working leases in persistent database - sleeping.

i really need help

---


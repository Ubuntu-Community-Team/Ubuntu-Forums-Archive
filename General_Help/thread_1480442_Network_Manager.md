---
title: "Network Manager"
date: 2010-05-11
forum: General Help
---

### Post by elys22 on 2010-05-11
So, in order to access the wireless network at school, I was told to install wicd. I did so, and as it was installing, noticed that the instructions said in small print that it would interfere with Network Manager, so I tried to cancel the install, but it was too late. Now I have no wireless on my laptop. It completely deleted Network Manager, so it's not just a matter of bringing the icon back up. Obviously I can't re-install it with no connection. So I'm on my brother's old computer, and I downloaded the .deb file for it in order to install it in Ubuntu. I transferred it via memory card, and got an error message saying that the architecture was wrong (i386), which as far as I can tell means I tried to install a 32-bit program on my 64-bit system. So I downloaded the amd64 version, and got the message:

error: dependency is not satisfiable: libnm-glib0 (=0.7~~svn20080908)

It won't open with synaptics either, it's just faded out when I try so I can't even select it. Please help, I'm lost without a wireless connection.

---

### Post by 2hot6ft2 on 2010-05-11
2 options

**[COLOR="DarkGreen"]Option 1[/COLOR]**

On the one without NM.
Make sure you can plug it into a wired connection

First purge wicd and nm
```
sudo apt-get purge network-manager-gnome wicd
```
then

Open a terminal
Applications > Accessories > Terminal
and run

```
gksu gedit /etc/network/interfaces
```
add 2 lines so it looks like this
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
save and close
shut down connect to a wired connection and boot up
then
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install network-manager-gnome
```
When it finishes
```
gksu gedit /etc/network/interfaces
```
remove the 2 lines so it looks like this
> auto lo
iface lo inet loopback
save and close
reboot

**[COLOR="DarkGreen"]Option 2[/COLOR]**

If you can't get it to a wired connection.
Purge wicd and NM as at the top of the post then

Go to Synaptic on the one needing the packages and marking all the packages you want to install then clicking on File > Generate package download script
Then move or save the script to a usb flash drive which you can take to any linux box that is online and double clicking on it and selecting "Run" or "Run in Terminal if you want to be able to see when it finishes" it will download the packages to the same location as where the script is.

Then you take the usb to the machine that created the script and open Synaptic and click on File > Add downloaded packages and point it to where the script and packages are to install them.

The machine that creates the script is the architecture it will download them for. Not for the one you run the script on to download them.

:guitar:

---

### Post by elys22 on 2010-05-11
> **2hot6ft2 said:**
> 2 options

**[COLOR=DarkGreen]Option 1[/COLOR]**

On the one without NM.
Make sure you can plug it into a wired connection

First purge wicd and nm
```
sudo apt-get purge network-manager-gnome wicd
```then

Open a terminal
Applications > Accessories > Terminal
and run

```
gksu gedit /etc/network/interfaces
```add 2 lines so it looks like this

save and close
shut down connect to a wired connection and boot up
then
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install network-manager-gnome
```When it finishes
```
gksu gedit /etc/network/interfaces
```remove the 2 lines so it looks like this

save and close
reboot

**[COLOR=DarkGreen]Option 2[/COLOR]**

If you can't get it to a wired connection.
Purge wicd and NM as at the top of the post then

Go to Synaptic on the one needing the packages and marking all the packages you want to install then clicking on File > Generate package download script
Then move or save the script to a usb flash drive which you can take to any linux box that is online and double clicking on it and selecting "Run" or "Run in Terminal if you want to be able to see when it finishes" it will download the packages to the same location as where the script is.

Then you take the usb to the machine that created the script and open Synaptic and click on File > Add downloaded packages and point it to where the script and packages are to install them.

The machine that creates the script is the architecture it will download them for. Not for the one you run the script on to download them.

:guitar:




Thank you! One of the problems I had was that Ubuntu didn't recognize the ethernet cable, so I assumed it wasn't working. After I purged wcid and nm and added the eth0 command, I was able to connect and simply re-download NM in the software center. 

You're a lifesaver. :KS

---

### Post by 2hot6ft2 on 2010-05-11
> **elys22 said:**
> Thank you! One of the problems I had was that Ubuntu didn't recognize the ethernet cable, so I assumed it wasn't working. After I purged wcid and nm and added the eth0 command, I was able to connect and simply re-download NM in the software center. 

You're a lifesaver. :KS
No problem. I don't know why people keep installing wicd when it's usually a driver issue which doesn't help. You should be able to set the connection up with NM anyway. Wicd has bugs too.
:popcorn:

---

### Post by dcstar on 2010-05-11
> **2hot6ft2 said:**
> No problem. I don't know why people keep installing wicd when it's usually a driver issue which doesn't help.
.......

Possibly because too many people had a bad experience with something long ago when a package was just being developed, and now their solution to every single mention of that package is **"don't use it!"** no matter how bogus that message now is.

You still see this with things such as 64-bit distros and apps like Evolution, some nuff-nuff had problems years ago but still tells people right now to use something else - it's a baffling attitude that seems to be prevalent in too many Linux users.

I used to tell people not to use Network Manager when it first came out because it was rubbish way back then and caused numerous problems, but now it has evolved into the useful tool it was always supposed to be and does the job.

Linux systems and apps just evolve and change too much for people to either keep parroting their prejudices based on outdated situations or to follow now outdated HOWTOs that really don't apply to their current systems.

---


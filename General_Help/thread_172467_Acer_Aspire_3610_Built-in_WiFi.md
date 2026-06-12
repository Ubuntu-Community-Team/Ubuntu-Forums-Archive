---
title: "Acer Aspire 3610 Built-in WiFi"
date: 2006-05-08
forum: General Help
---

### Post by Forgotten on 2006-05-08
Ok, plain and simple question.

I have an Acer Aspire 3610 Notebook (I live in Canada) that was built to run Windows (like most out-of-the-box notebooks). Now it has a built in Wireless b/g modem/card thing..

How do I get the wireless to work on linux?

I believe its a Broadcom Wireless 802.11bg 3.100.46.0

So... Help? :)

---

### Post by MrMojoRising on 2006-05-09
Boy are you in for a treat. 

Acer laptops take a bit of configuring to get the internal card working. The card doesn't start based on a hardware switch so Linux can't find it by default. 

You need to look into a program called acer_acpi whcih turns the card on.
Then you need to look into ndiswrapper to get the drivers recognised.

There are a bunch of guides to do this.
Just search the forums for "acer_acpi ndiswrapper" or something of that sort.

Good luck




Once i got all the stuff configured on my laptop i run this small script to start my wireless (since i don't want it on when i start the laptop, only when i wanna turn the card on):


```
rmmod bcm43xx
depmod -a
modprobe acer_acpi
ndiswrapper -e bcmwl5
ndiswrapper -i bcmwl5.inf
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe acer_acpi
cd /proc/acpi/acer
chmod 777 ./wireless
echo "enabled: 0">/proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless

```

I just put that in a file called startWireless.sh and do a 

$ sudo ./startWireless.sh

As you can see i had to setup acer_acpi and ndiswrapper....Let me know if you can't figure it out. However there are some excellent guides. That's how i figured it out.

p.s. i have an Acer Travelmate 4404

---

### Post by Forgotten on 2006-05-09
[QUOTE=MrMojoRising]Boy are you in for a treat. 

Acer laptops take a bit of configuring to get the internal card working. The card doesn't start based on a hardware switch so Linux can't find it by default. 

You need to look into a program called acer_acpi whcih turns the card on.
Then you need to look into ndiswrapper to get the drivers recognised.

There are a bunch of guides to do this.
Just search the forums for "acer_acpi ndiswrapper" or something of that sort.

Good luck




Once i got all the stuff configured on my laptop i run this small script to start my wireless (since i don't want it on when i start the laptop, only when i wanna turn the card on):


```
rmmod bcm43xx
depmod -a
modprobe acer_acpi
ndiswrapper -e bcmwl5
ndiswrapper -i bcmwl5.inf
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe acer_acpi
cd /proc/acpi/acer
chmod 777 ./wireless
echo "enabled: 0">/proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless

```

I just put that in a file called startWireless.sh and do a 

$ sudo ./startWireless.sh

As you can see i had to setup acer_acpi and ndiswrapper....Let me know if you can't figure it out. However there are some excellent guides. That's how i figured it out.

p.s. i have an Acer Travelmate 4404[/QUOTE]


Not sure if I found what I'm sopossed to by looking for..

[http://ubuntuforums.org/showthread.php?t=125150&highlight=%22acer_acpi%22+ndiswrapper](http://ubuntuforums.org/showthread.php?t=125150&highlight=%22acer_acpi%22+ndiswrapper)

But I just looked at my Windows Device Manager (running a dual-boot here :)) and I have a Broadcom 802.11g Network Adapter I heard some buzz about this on the wiki and search results...

Any advice? I'm a bit lost.

---

### Post by MrMojoRising on 2006-05-09
Okay i'll try to give you a quick little How-To here based on the work of a few others here on the forum:

[COLOR="Red"]first of all you gonna want to get your headers and any build tools[/COLOR]

```
sudo apt-get install linux-headers-$(uname-r)
sudo apt-get install build-essentials
```

[COLOR="Red"]Next i will refer to JShein's post:[/COLOR]

1: Check the outplut of lspci. If it has any "unknown" entries, the you should update your pci.ids file. This file is an index of sorts that the kernel references for installed hardware. An updated file can be downloaded from:
[http://pciids.sourceforge.net]("http://pciids.sourceforge.net")

To update it, First back up the old one

**#sudo cp /var/lib/misc/pci.ids /var/lib/misc/pci.ids.OLD**

Then copy the downloaded file over the existing one.
[B]
#sudo cp <path to downloaded file> /var/lib/misc/pci.ids[/B]

You will now need to reboot your pc if you have updated this file.

[COLOR="Red"]Next you need to get the acer_acpi package and compile it...[/COLOR]

```
wget http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz
tar zxvf acer_acpi-0.3.tar.gz
cd acer_acpi-0.3
make
sudo make install
```
Then check the output of dmesg for any errors
```
dmesg | grep acer_acpi
```
[COLOR="Red"]You then need to download and copile ndiswrapper (this part courtesy of RedSmoke)
[/COLOR]
```
wget http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.7.tar.gz
tar xvzf ndiswrapper-1.7.tar.gz
cd ndiswrapper-1.7
make
sudo make install
```
[COLOR="Red"]You then need to acquire your windows drivers for the card and initialize them[/COLOR]
```
wget https://www.synapsenow.com/synapse/data/7117/documents/3624_80211bg.zip
unzip 3624_80211bg.zip
cd 3624_80211bg/Broadcom/
ndiswrapper -i bcmwl5.inf
```
verify that it installedproperly, you should get the following output
```
ndiswrapper -l
Installed Drivers:
bcmwl5          driver present, hardware present
```
once you have done that your still not done. You need to load the ndiswrapper module.
```
modprobe ndiswrapper
```
check that it loaded...
```
dmesg | grep ndis
```
next initialize acer_acpi
```
sudo -s
modprobe acer_acpi
cd /proc/acpi/acer
chmod 777 wireless
echo "enabled: 1" >/proc/acpi/acer/wireless
```
check that it worked...
```
dmesg | grep acpi
```
now you should be able to scan for networks with a:

iwlist wlan0 scan

....wlan0 might not be your card, if it's not check for it with 'iwconfig'.

[COLOR="Red"]If everything worked up to here then great, you're done. However you'll have to make a startup script if you want your wireless on every time you start up your laptop. Check [here]("http://ubuntuforums.org/showthread.php?t=140007&highlight=acer_acpi+ndiswrapper") for an example....[/COLOR]

However i don't want it to start everytime i boot up so that i save battery and don't reveal myself unknowingly......therefore i made this script that i run whenever i wanna go online...

**First copy the bcmwl5.inf and bcmwl5.sys files from that driver folder that you unzipped (under the Broadcom subfolder) to your home directory**  then...
**gedit ~/startWireless.sh**

add this to the file:

rmmod bcm43xx
depmod -a
modprobe acer_acpi
ndiswrapper -e bcmwl5
ndiswrapper -i bcmwl5.inf
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe acer_acpi
cd /proc/acpi/acer
chmod 777 ./wireless
echo "enabled: 0">/proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless


save and exit gedit

then make it executable:  **chmod +x startWireless.sh**

Then whenever you want to go online you type:

**sudo .~/startWireless.sh**

i also have a file called stopWireless.sh which contains: 

echo "enabled: 0">/proc/acpi/acer/wireless
modprobe -r acer_acpi
modprobe -r ndiswrapper



[COLOR="Red"]I hope this helped. I am by no means an expert but this is what i did to get mine working. IF you're confused or some steps don't work then check out the origional guides at:
[http://ubuntuforums.org/showthread.php?t=110749&highlight=acer_acpi+ndiswrapper](http://ubuntuforums.org/showthread.php?t=110749&highlight=acer_acpi+ndiswrapper)
[http://ubuntuforums.org/showthread.php?t=140007&highlight=acer_acpi+ndiswrapper](http://ubuntuforums.org/showthread.php?t=140007&highlight=acer_acpi+ndiswrapper)
[http://ubuntuforums.org/showthread.php?t=153876&highlight=acer_acpi+ndiswrapper](http://ubuntuforums.org/showthread.php?t=153876&highlight=acer_acpi+ndiswrapper)

I had to use a comination of those 3 posts to get things working just right.[/COLOR]

---

### Post by MrMojoRising on 2006-05-10
*Bump*

Any updates yet?

---

### Post by bomanizer on 2006-05-23
I'll try this as soon as I get home from work. I've been looking for something Acer-spesific for some time now an stumbled on this thread. I'll post my results later.

---

### Post by MrMojoRising on 2006-05-23
Glad to hear i'm helping someone out. 
Please let me know how it goes and if you have any problems

btw - if you are following my guide make sure that you get the drivers specific to your laptop, don't follow the link in this guide (unless of course you have the same laptop as **Forgotten**), try to find them on the acer website or if you dual boot, search your windows drive for "bcmwl5.inf" and use that.

---

### Post by _linux_ on 2006-05-23
There aren't any Linux drivers for your wireless card, so you need to use ndiswrapper. Go to [this]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show") wiki page to set it up. You could also search ndiswrapper here in the forums. There are LOTS of threads about setting up ndiswrapper, including some about Broadcom cards.

---

### Post by j0nes on 2007-03-23
I also have an Acer Aspire 3610, and went through some trials and tribulations regarding the built in Wifi.  It's up and running now, but it took a lot of reading and some trial and error.

Not sure if this is the right place to ask, but i'm trying to reslove some audio/sound problems.  I can play music no problem through a variety of media players (mainly i use XMMS), but there is a lot of static and the quality is just not up to par.

I've recently added the GNOME ALSA Mixer, but tweaking it's various options doesn't seem to help.  Any advice or pointers would be greatly appreciated.

I've only been Linux'ing for about a year, so please answer in n00b-speak.

---


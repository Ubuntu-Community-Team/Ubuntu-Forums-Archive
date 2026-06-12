---
title: "aticonfig has replaced fglrx?!?!?(stuck)"
date: 2006-02-21
forum: General Help
---

### Post by Strike&gt;&gt; on 2006-02-21
hello

i was shocked about this, as i did a reinstall of my ubuntu and installed the latest ati driver, but seems that they have removed fglrx! instead they have this aticonfig, which i don't know why?

can you please tell me how to configure/customize it, cause i'm really stuck!

the most important settings that i need to configure that i need are 

Setting for the refresh rate, screen resolution and vertical/horizontal syncs.

and i would be happy to tweak the file manually:)

---

### Post by Strike&gt;&gt; on 2006-02-21
or if someone can send me a link or something to one so i could use it perhaps, if possible?

---

### Post by Ocxic on 2006-02-21
I got my fglrx drivers by doing this with hardware acceleration and direct rendering:
Note: if after this you may want to run sudo dpkg-reconfigure xserver.xorg  and chose to use the fglrx driver, the other options are up to you inculde syc rates, and resolutions.

[/code]
this removes current drivers from your system:

sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #Select the ATI driver

reboot to get the kernel modules out of memeory

then do this to install the drivers and have fglrx working:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup #backup current xorg.conf
sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper #installs brograms nessasary for building the module

wget -c --no-check-certificate [https://www2.ati.com/drivers/linux/ati-driver-installer-8.21.7-i386.run](https://www2.ati.com/drivers/linux/ati-driver-installer-8.21.7-i386.run) # downloads drivers from ati.
chmod +x ati-driver-installer-8.21.7-i386.run
fakeroot ./ati-driver-installer-8.21.7-i386.run --buildpkg Ubuntu/breezy #build driver package for breezy

#this installes the drivers
sudo dpkg -i fglrx-control_8.21.7-1_i386.deb fglrx-kernel-source_8.21.7-1_i386.deb fglrx-sources_8.21.7-1_i386.deb xorg-driver-fglrx_8.21.7-1_i386.deb xorg-driver-fglrx-dev_8.21.7-1_i386.deb

#installs the driver in the kernel

sudo module-assistant build,install fglrx-kernel

#adds the module to the running kernel

echo fglrx | sudo tee -a /etc/modules

#modify's the xorg.conf to use the fglrx driver

sudo sed -e 's/"ati"/"fglrx"/' -i /etc/X11/xorg.conf


#removes te created packages no longer needed but may be kept if you like.

rm ati-driver-installer-8.21.7-i386.run
rm -f fglrx-control_8.21.7-1_i386.deb fglrx-kernel-source_8.21.7-1_i386.deb fglrx-sources_8.21.7-1_i386.deb xorg-driver-fglrx_8.21.7-1_i386.deb xorg-driver-fglrx-dev_8.21.7-1_i386.deb

[/code]

instruction here were origonaly posted here as a script: [http://www.ubuntuforums.org/showthread.php?t=125974&highlight=ATI](http://www.ubuntuforums.org/showthread.php?t=125974&highlight=ATI)

---

### Post by Strike&gt;&gt; on 2006-02-21
LOL, true, true indeed.

i used the instructions on this website, but it was easy in my opinion.

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)


i will try your instructions and see how it goes, so thanx for the help!

it's just wierd that they don't have the fglrx included anymore:-k

---

### Post by Strike&gt;&gt; on 2006-02-22
Thnx a lot, it actually worked! 

but i do however sometimes come across weird problems......

---

### Post by Ocxic on 2006-02-22
what problems???

---

### Post by Strike&gt;&gt; on 2006-02-23
Nothing huge, bot sometimes when i start enemy territory, it game an error, and i found that fglrx wasn't working properly, or when i log off, my screen just freezes and shows these random line going through the scree. But thank god everything gets fixed after a reboot. 

and something strange happened to one my screen saver that i downloaded off the internet(kcometen), it worked before i installed the ati driver, but now it doesn't:-k ??

have you come across anything like that?

---


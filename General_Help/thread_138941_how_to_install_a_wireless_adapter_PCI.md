---
title: "how to install a wireless adapter PCI"
date: 2006-03-02
forum: General Help
---

### Post by maxpayne on 2006-03-02
How do I install Limewire for linux.  I downloaded the version for linux and it is saved as an .rpm file.  It has 3 main folders, bin, lib, and share.  How in the world do I install the program? please tell me in plain english because I am linux stupid.

Many thanks!

---

### Post by csevcik on 2006-03-02
You may try your MS Windows XP drives using ndiswrapper under Ubuntu 5.10 and other Linuxes. Make sure that the ndiswrapper-utils are installed in your system (they are not installed by default although the ndiswrapper support is). Then find the drivers in your MS Windows CD and fin a file *.inf (I do not know your driver's name, so I'll call it "asdfgh.inf") and copy this file and the other files in the same directory of the CD to some directory of your disk (say "MyCard"). Move into your MyCard directory using a Ubuntu command window (Konsole in Kubuntu, usuallly called console ot terminal in gnome) and now type the following commands with administaror priviledges:

sudo ndiswrapper -i asdfgh.inf
(give your passwd when asked to do so)
sudo ndiswrapper -m

(this creates an alias which is wlan0 by default, for your card to be used by your kernel)
sudo  ndiswrapper -l
(if everithing goes OK and your card is installed you will get a reply like

asgfgh driver present, hardware present)
sudo modprobe ndiswrapper
sudo modprobe -l ndiswrapper
(this command will answer with a long line ending in /ndiswrapper.ko to tell you that the kernel has the ndiswrapper module installed)

After that, you have to configure the settings of your card for the IP provider or your wireless router with iwconfig, I'll assume that you are connected to a dhcp provider which assigns IP numbers dynamically and that your connectio is encrypted with some key. So things will look something like this:

sudo ifup wlan0
sudo iwconfig

(your wlan configuration is the output)

now change the settings as needed:

sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 key 12f45a78cc98...  (your hex encryption key if needed)
sudo iwconfig wlan0 channel 11 (or whatever channel used by your router or IP provider if your card is able to negociate a channel with the router or provider set this to auto instead of 11)
sudo iwconfig wlan0 essid yourwifilanname ("sevcik" in my home, write it WITHOUT quotes)

now do
sudo iwlist scanning

and you will see if the system is working.

You may avoid all the sudo's by creating yourself a root password as:

sudo passwd root
it will ask your passwd first and the the root passwd twice (MAKE SURE THEY ARE DIFFERENT ANT THAT THE root PASSWD IS SOLID). Then at your terminal window prompt type
su
(an give your root passwd here)

Now you may follow the command above without the sudos.

Good luck, remember that man xxxxxxxxx will give you more information on the xxxxxxxxx command that I am able to give here. Also you can find help on al this seaching for ndiswrapper in Google.

Carlos

---


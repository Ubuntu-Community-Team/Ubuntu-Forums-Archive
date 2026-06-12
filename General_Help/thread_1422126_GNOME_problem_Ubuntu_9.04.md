---
title: "GNOME problem Ubuntu 9.04"
date: 2010-03-05
forum: General Help
---

### Post by karthick ayyapillai on 2010-03-05
Hi
I am using linix for a yr i lost my charger and didnt use the machine for few months when i turned on it didnt go in to GNOME mode it went in terminal mode with a message stating that
Starting up …
Loading, please wait…
kinit: name_to_dev_t(/dev/disk/by-uuid/bd656dcd-04b4-412f-a880-62a6553bd8b) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/bd656dcd-04b4-412f-a880-62a6553bd8b
kinit: No resume image, doing normal boot…
then i tried the following
sudo fdisk -l
sudo mkswap /dev/sda5 (where sda5 is my linux swap).
sudo update initramfs -u
sudo reboot 
after reboot i didnt have the message stating  no resume image doing normal boot but still then i didnt get my GNOME working.
then i tried to login the xserver it went in and from there i upgraded to the ubuntu 9.0 version 
it went fine after the upgrade also it went again to terminal mode boot not GNOME boot.
I have a Ubuntu DVD i tried a fresh install but is not booting from the DVD.
When i tried to format the hard drive using the following 
sudo mkdosfs -v F32 /dev/sda
sudo mkfs -t vFAT /dev/sda5
it is not allowing me to do it throws a message that file system is mounted in the part so cant format it.
I tried to install the desktop through terminal using 
sudo apt-get install ubuntu-desktop
it is reading the package and then asking for the permission when i allow the operation is not connecting to internet
all i get is failed to fetch from [http://archivies.ubuntu.com](http://archivies.ubuntu.com)....
then i tried to reconfigure the xserver by changing the following 
cd /etc/X11
sudo cp xorg.conf xorg.conf.704
sudo dpkg-reconfigure xserver-xorg
sudo reboot
after the reboot i was not able to login to xserver also when i type startx in terminal it get black screen and then freeze. I need to turn it off using the power buttton.
I typed to following lpsci -vga and i got 
ATI radeen 200M graphics card
my system config are
siemens AMILO 1718 
250 GB ,1GB RAM ,ATI RADEEN 200M graphics 
(i dont use any windows partition in my box the entire hard drive is linux formated for ubuntu)
If any one can tell me how to resume my laptop that would be of great help. For your info i dont mind about the data in it i have a copy so no problem with formatting.I even tried the machine in recovery mode and opted for the xfix and fix broken pakages all in vain .
please help thanks in advance...

---

### Post by mörgæs on 2010-03-05
> **karthick ayyapillai said:**
> For your info i dont mind about the data in it i have a copy so no problem with formatting.

Then I think that you should just do a clean install of 9.04. It takes an hour - problem solved.

---

### Post by karthick ayyapillai on 2010-03-06
thanks for your help and advice i have re install ubuntu 9.1 now the system is fine but 
i lost my wireless connectivity. if you have any suggestions welcome and thanks in advance

---

### Post by mcoleman44 on 2010-03-06
Go to system>admin>hardware drivers 
activate your wireless driver. 

If nothing is listed then go to system>admin>update manager. 
Install all updates. Restart and when you log back in go back to hardware drivers and your wireless driver should be there. Install it, reboot and it should work.

---

### Post by mörgæs on 2010-03-07
- or stick to 9.04, if everything else fails. It is the most bugfree version ever, and it is supported until october 2010. At that time you can go to 10.04, skipping 9.10 entirely.

---

### Post by karthick ayyapillai on 2010-03-08
> **mörgæs said:**
> - or stick to 9.04, if everything else fails. It is the most bugfree version ever, and it is supported until october 2010. At that time you can go to 10.04, skipping 9.10 entirely.

thanks for your advice and help i think your idea is best coz i tried countless hours in configuring the wifi using many ways since i use a atheros 5001 chipset athk5 drivers wont support so i tried using mad wifi also but no hope , even after a fresh install what i get is same trouble . All i seen in the harware repository is a software modem to activate when i did it not working so plannin to install 9.04 today ll let you guys know any hope...
thanks again for your time and hlep

---

### Post by karthick ayyapillai on 2010-03-08
> **mcoleman44 said:**
> Go to system>admin>hardware drivers 
activate your wireless driver. 

If nothing is listed then go to system>admin>update manager. 
Install all updates. Restart and when you log back in go back to hardware drivers and your wireless driver should be there. Install it, reboot and it should work.

I have done that and i didnt get any wifi drivers there in the hardware drivers. I found that my system uses the old athk5 drivers so i tried using mad wifi too still no luck ll let you know if anything done.thanks for the help

---

### Post by karthick ayyapillai on 2010-03-08
Hi
finally the problem is solved with my wify in 9.10 version. Here is the solution which i found
my system config 
siemens laptop AMILO 1718
atheros 5001 wireless controller the equivalent linux driver is athk5 
step :1 if you have the old athk5 version driver then you can follow this steps.
find your driver first using the lspci command in the terminal. In the end you will see two ethernet controller the first one is the wireless controller if you read it carefully you can find the linux driver equivalent for the atheros driver listed in the result.
step :2 Now connect your computer which is having a fresh install of ubuntu 9.10 with a ethernet cable to your router. in the terminal type sudo apt-get update and execute it 
after that open the synaptic package manager which is under system---> adminstaration ---> syanptic package manager.
NOTE : during all this process keep your wifi switch disabled.
get all the updates and install.
step 3: remove the ethernet cable from the computer and reboot it soon you reboot it try to switch on the wifi switch 
step 4 : note dont go to the hardware drivers and activate anything mentioned in the list.
step 5: if your wifi is not working restart it a couple of times . Switch on /off the wifi button.
you might get it 
alternative way: Even then if you dont get wifi working then perform a clean install of ubuntu 9.10 with the ethernet cable plugged in to your computer and then follow the procedure from step 1
After so much struggle still you cant get wifi then the back route is to install madwifi 
you can find the procedure to install madwifi in forums or click the link below
[http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/](http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/)
you can also follow the steps below
to carry out the install you need to have a ethernet cable plugged in 
step 1: download madwifi latest stable version of tar.gz file from their website ,then using archive manager extract it to your desktop.
step 2:open terminal and type 
sudo apt-get install build-essential (this will build the image for the kernel)
cd madwifi*
go to the directory where you have extracted the tar.gz file
sudo make
sudo make install
sudo gedit  etc/modules
this will open a new file in GNOME and the file looks like this
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
ath_pci
you need to add the last two lines to the file and save it then come back to terminal
then type 
sudo modprobe ath_pci
is done 
final step is sudo reboot
you have installed madwifi drivers to your kernel.
after the reboot you ll be able to go wireless
thanks for all the guys who helped me and gave me a swift reply for all the problems which i posted in forums
if you still have any problems please post in forum i ll try my level best to help you

---


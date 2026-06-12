---
title: "Ubuntu command guide/list"
date: 2011-12-14
forum: General Help
---

### Post by tech291083 on 2011-12-14
hi,

I am new to Ubuntu, but I have used Fedora before. I understand that certain commands are different compared to Fedora. Is there a good list of Ubuntu commands for learners like me? Thanks.

---

### Post by mikewhatever on 2011-12-14
I think most of the commands are same for both Ubuntu and Fedora, except when the package manager is concerned. A look through the the 'apt-get' man page should, however, cover the gap.

---

### Post by galvatron408 on 2011-12-14
ubuntu is debian, so it doesn't use yum or rpm but instead, it uses apt and aptitude...
 
 
it doesn't use chkconfig, i really forgot how debian does startups... ;)

---

### Post by ajgreeny on 2011-12-14
One big difference is that ubuntu does not have a root account enabled, so uses ```
sudo <command>
``` to carry out admin procedures.

See **Root-sudo** in my signature for more reasoning and help about this.

---

### Post by Habitual on 2011-12-14
These 2 tips may help you or another...

```
Alt+F2 > yelp man:<page>
```
for a GUI'fied (can't believe I just used that word) man page (printable too).

Terminal:
```
echo "export LESS='FiX'" >> ~/.bashrc
source ~/.bashrc
```

Now when you type "man somepage" in terminal and scroll around (up and down the document) **when you exit, it will stay on the screen**. Easier for review. :)

HTH.

---

### Post by Megaptera on 2011-12-14
I found this helpful:
From here - [https://launchpad.net/clicompanion](https://launchpad.net/clicompanion)
"CLI Companion is a tool to store and run Terminal commands from a GUI. People unfamiliar with the Terminal will find CLI Companion a useful way to become acquainted with the Terminal and unlock its potential. Experienced users can use CLI Companion to store their extensive list of commands in a searchable list."

---

### Post by x C0MMAND0 x on 2011-12-14
[http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/)

---

### Post by x C0MMAND0 x on 2011-12-14
Here's another list of useful commands (taken from [http://forums.linuxmint.com/viewtopic.php?f=42&t=4306](http://forums.linuxmint.com/viewtopic.php?f=42&t=4306))

cat /proc/cpuinfo=CPU info
cd=change directory
convert -resize 640x480 -colors 14 wallpaper.png splashimage.xpm && gzip splashimage.xpm=change picture into grub splash.
cp=copy
df -h=disk space usage
etc/gnome/default.list=file of default programs
fglrxinfo=graphics driver info
free -m=memoryusage
glxgears=check 3d graphics
glxinfo=opengl info
ifconfig=network configuration info
killall gnome-panel=kill,refresh panel
locate=find target
lsb_release -a=OS info
lshw=list hardware
ls=list contents
lspci=list pci devices
man command | col -b > file.txt=save man uotput to file
man -f=man title of target
man intro=user commands help
man -k=man file for target
man man=man manual
mkdir=make directory
mv=move
netstat -l --tcp --udp (and then) watch -n 1 netstat -an --tcp --udp=watch port activities
rmdir=remove directory
rm=remove
rm -r=remove all
sudo apt-cache=debian apt library
sudo apt-cache search (search subject)=Search debian repo for apps
sudo apt-get dist-upgrade=upgrade all
sudo apt-get update=update sources.list
sudo cp /<filename.backup>/<filename>=reset to backup file
sudo deborphan | xargs sudo apt-get -y remove –purge=remove orphans
sudo dmidecode | more=Detailed hardware info
sudo dpkg -l | cut -d " " -f 3=list installed packages
sudo dpkg-reconfigure menu sudo dpkg-reconfigure menu-xdg (reboot)=fix Debian menu
sudo dpkg-reconfigure xserver-xorg=Reconfigure periphials, graphics
sudo fdisk -l=View Hard drive partitions
sudo hdparm -l /dev/sda=hard drive settings
sudo hdparm -tT /dev/sda=hard drive speed
sudo ln -s ~/.themes /root/.themes sudo ln -s ~/.icons /root/.icons sudo ln -s ~/.fonts /root/.fonts=make root look like user
top=system,processes,resources,cpu,ram,etc. info
uname -a=kernel version
update-menu=update gnome menu
whereis program-name=location of program/man page
which <program name>=location of program

---

### Post by galvatron408 on 2011-12-14
> **ajgreeny said:**
> One big difference is that ubuntu does not have a root account enabled, so uses ```
sudo <command>
``` to carry out admin procedures.

See **Root-sudo** in my signature for more reasoning and help about this.

thats not true. "sudo su" will switch you to root

and there's other ways too... if it was disabled, "sudo su" wouldn't work. by the way, you can disable root using PAM.

---

### Post by crave-n on 2011-12-15
I found this site a bit useful:
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
but being myself a beginner i dunno if it is useful fr u  :D

---

### Post by tech291083 on 2011-12-15
> **x C0MMAND0 x said:**
> Here's another list of useful commands (taken from [http://forums.linuxmint.com/viewtopic.php?f=42&t=4306](http://forums.linuxmint.com/viewtopic.php?f=42&t=4306))



Thanks a lot.

---


---
title: "How to clean the system and make it faster"
date: 2012-02-20
forum: General Help
---

### Post by esbrinartot on 2012-02-20
After one year of using Ubuntu I noticed is getting a little bit slower.

MAinly is because all the software I've installed, and so on.

To solve the situation can anybody explain what I have to do in orer to find out the active daemons in my computer?

I guess I can improve speed of ubuntu by disabling the daemons that I don't use.

What else I could do to improve the speed of the system?
(erase old kernel, clean all packets, sudo apt-get autoclean, sudo apt-get autoremove, Use a software as Ubuntu Tweak and Bleach bit)

Please help to improve the speed of my ubuntu

---

### Post by muteXe on 2012-02-20
you can run 'top' from the command line to see what processes are currently running.

---

### Post by esbrinartot on 2012-02-20
I've done it and I've seen for example a process called gwibber erver that I should kill.

However notice that What I would like is find out all the active daemons. The command top only show you a few.

Is there any configuration archive that I can comment all the daemons that I don't want to use?

---

### Post by Thorsen V on 2012-02-20
if you open a terminal and go full screen you should see a lot more of "top"

(most of which will be stuff that appears to be inactive, if your system is anything like mine :))

---

### Post by esbrinartot on 2012-02-20
Yes I agree Thorsen

But in the list a lot of daemons are missing

apache2
mysqk
postgresqo
sshd
and so on....

Where I can find the list of all this process ??

---

### Post by HavarN on 2012-02-20
The nmap program can easily show you which ports are open on your localhost, which should give you a rough idéa about which daemons or servers are running on your computer.

This scans all ports from 1 to 65535 on your localhost.
```
nmap -p 1-65535 localhost
```

nmap is not default on Ubuntu and must be installed before you use it.
```
sudo apt-get install nmap
```

Edit:
This should show you which daemons you have installed
```
dpkg -l | grep ii | grep daemon | grep -v lib
```

---

### Post by esbrinartot on 2012-02-20
yes the command
dpkg -l | grep ii | grep daemon | grep -v lib
let me know the daemons I've installed.

The last question is:

I've installed the Boot-up manager to disable the daemons.

I've disabled some as the bluetooth but when I use the command "dpkg -l | grep ii | grep daemon | grep -v lib" Bluez is still there.

I guess the command only shows the installed daemons. Is there any command to check the active daemons?

---

### Post by Thorsen V on 2012-02-20
ps -A

There's usually a _lot :)_

maybe try filtering it :

ps -A | grep -i apache


Therre are lots of options to to ps but -l (long format) is a poprular one: ps -Al

---

### Post by Toz on 2012-02-20
See [this link]("http://ubuntuforums.org/showthread.php?t=1574977") for a previous thread discussion on the **service --status-all** and **initctl list** commands to show active daemon processes.

---

### Post by Cheesehead on 2012-02-20
Wandering through the system semi-randomly disabling processes is certainly fun (especially when you must re-enable them), but it may not make your system any faster. Most processes sleep most of the time, and use a tiny sliver of CPU and memory when awake.

A slow/sluggish system may be due to many possible bottlenecks (CPU, RAM, Disk I/O or capacity) and/or bugs.

Investigate: Use 'top' during periods of sluggishness to identify the offending processes, and where the symptomatic bottlenecks are. Narrow the range of problems.

---

### Post by esbrinartot on 2012-02-20
I've tried so many things. And with all of them I received different answers.


I've tried rcconf.
I've tried  chkconfig
I've tied service --status-all

And all of them says that zramswap is not enabled. And I know it's working.

Why the commands says is disabled??

ssh according to rcconf and chkconfig is not enabled and according to service --status-all is working. The truth is that I can establish ssh connection so I guess it's working

So now I'm so confused...  I have no idea what's running or not

---

### Post by oldos2er on 2012-02-20
> **esbrinartot said:**
> What else I could do to improve the speed of the system?
(erase old kernel, clean all packets, sudo apt-get autoclean, sudo apt-get autoremove, Use a software as Ubuntu Tweak and Bleach bit)


Doing those things will free up some hard disk space, but they're not going to speed up your system.

If it were my system, I would max out my motherboard's RAM, and upgrade my video card to something well-supported (e.g. Nvidia) with at least 512MB video RAM.

What are your hardware specs?

---

### Post by esbrinartot on 2012-02-20
Hi

My computer is not as bad as you think

Is a pentium D with 3 RAM Gb and a NVIDA Card of 512GB

The computer goes fast but slower than 1 year ago. I just was trying to optimize whatever I can. I want to keep ubuntu 11.04 until the support expires. Then I will see what I do... Because unity sucks.

Now I'm trying to don't use the daemons that I don't need. But as you can see in my last post different commands gave different information.

---

### Post by CivilizationII on 2012-02-20
> **esbrinartot said:**
> After one year of using Ubuntu I noticed is getting a little bit slower.

MAinly is because all the software I've installed, and so on.

To solve the situation can anybody explain what I have to do in orer to find out the active daemons in my computer?

I guess I can improve speed of ubuntu by disabling the daemons that I don't use.

What else I could do to improve the speed of the system?
(erase old kernel, clean all packets, sudo apt-get autoclean, sudo apt-get autoremove, Use a software as Ubuntu Tweak and Bleach bit)

Please help to improve the speed of my ubuntu



For Ubuntu 10.04 and 11.04:

1/ The first thing you have to do is to verify that you are using EXT4 as filesystem (if filesystem is EXT3, then you need to go on the noatime option, not very hard to do, but not that simple). This is really the biggest speed enhancer, EXT4 is a pure jewel regarding speed.


2/ Then you need to remove all "bad" programs:

> sudo apt-get autoremove --purge \
apport* python-apport kerneloops* \
ubuntu-mono mono-runtime libmono* libgdiplus cli-common \
libreoffice* ure \
evolution evolution-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal \
libevolution evolution-data-server \
totem* libtotem* brasero* libbrasero* rhythmbox* pitivi shotwell \
banshee* tomboy \
nautilus-sendto-empathy empathy* gwibber* transmission* \
ubuntuone* python-ubuntuone python-ubuntuone* popularity-contest \
libcompiz* compiz* compizconfig* \
gnome-mahjongg gnomine gnome-sudoku aisleriot quadrapassel3/ Install two little system tool, required for the following steps:

> sudo apt-get install \
sysv-rc-conf rcconf4/ Remove "bad" network manager:

( obviously you must replace the following 10.10.1.1, 255.0.0.0 and 10.10.1.250 by the  values suited for your network, use " ifconfig -a " to know them )

> sudo apt-get autoremove --purge network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome

sudo cat > /etc/network/interfaces <<EOF
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 10.10.1.1
netmask 255.0.0.0
gateway 10.10.1.250
EOF


5/ Remove useless daemons, using:

> rcconfremove:
bluetooth
blrtty
dns-clean
fancontrol
ondemand
pcmciautils
pppd-dns
rsync
saned

(you can also delete the corresponding rc.d files)

if you're using bluetooth,     don't remove bluetooth
                                     if you're using a scaner,       don't remove saned
                                     if you're using RTC modem, don't remove pppd-dns and dns-clean


5/ Reboot, you now have Ubuntu on steroïd :P

---

### Post by esbrinartot on 2012-02-20
thks for your good answer

I will work in next points

point 1: I'm already using ext4

point 2: I don't want to uninstall all the software you propose. I know evolution, gwibber and so on are slow but It's a lot of job and I think that evolution and some other software is strongly linked to ubuntu, I aslo don't want to remove mono. Without mono I couldn0't neither gnome-do nor cairo-dock. Next time I format my computer I will aboid all this software.

point 3: I've already done. what is the difference between

thks for your good answer

I will work in next points

point 1: I'm already using ext4

point 2: I don't want to uninstall all the software you propose. I know  evolution, gwibber and so on are slow but It's a lot of job and I think  that evolution and some other software is strongly linked to ubuntu, I  aslo don't want to remove mono. Without mono I couldn0't neither  gnome-do nor cairo-dock. Next time I format my computer I will aboid all  this software.

point 3: I've already done. what is the difference between
   	 	 	 	sysv-rc-conf and rcconf??

point 4: I won't do it. Simply because I use to connect to more than 1  router and different places. I don't want to connect any time editing a  text file

point 5: I will work in this point. But notice rcconf and sysc-rc-conf  do the same.In addition I'm running some daemon like zram or ssh and  rcconf says is not running

thks for your good advice

---

### Post by Toz on 2012-02-20
> **esbrinartot said:**
> ssh according to rcconf and chkconfig is not enabled and according to service --status-all is working. The truth is that I can establish ssh connection so I guess it's working

So now I'm so confused...  I have no idea what's running or not

Ubuntu uses both the traditional sysv init scripts (/etc/init.d) and the upstart scripts (/etc/init). I believe the **service** utility works with the new upstart init scripts and **chkconfig** and **rcconf** work with the older sysv type scripts. When you install the ssh server, it uses the upstart method if initialization which is why "service --status-all" shows that its working and the others don't.

> I've tried so many things. And with all of them I received different answers.


I've tried rcconf.
I've tried  chkconfig
I've tied service --status-all

And all of them says that zramswap is not enabled. And I know it's working.

Why the commands says is disabled??


As far as I can tell from looking at the zramswap .deb file, its setup as an upstart script, meaning that "service --status-all" should show it as running. What does:
```
sudo service zramswap status
```
...show?

---

### Post by CivilizationII on 2012-02-20
> **esbrinartot said:**
> thks for your good answer

(...)

point 2: I don't want to uninstall all the software you propose. 

(...)

point 3: I've already done. what is the difference between
                      sysv-rc-conf and rcconf??



Of course, the list of removed programs is not fixed, and depending of your taste/choice you will apply or not.

In fact sysv-rc-conf and rcconf are exactly the sames, but time to times i prefer sysv-rc-conf, only a matter of UI (and number of options) choice.

---

### Post by esbrinartot on 2012-02-20
> **Toz said:**
> Ubuntu uses both the traditional sysv init scripts (/etc/init.d) and the upstart scripts (/etc/init). I believe the **service** utility works with the new upstart init scripts and **chkconfig** and **rcconf** work with the older sysv type scripts. When you install the ssh server, it uses the upstart method if initialization which is why "service --status-all" shows that its working and the others don't.


As far as I can tell from looking at the zramswap .deb file, its setup as an upstart script, meaning that "service --status-all" should show it as running. What does:
```
sudo service zramswap status
```...show?


thks for your good explanation. I confirm all that you said.

service utility with ssh:
[ + ]  ssh
chkconfig, rcconf or sysv-rc-conf
ssh doesn't work

about zram:
accordinf to chkconfig, rcconf or sysv-rc-conf IS NOT WORKING

According to service utility
 [ ? ]  zramswap    I don't know the meaning of ?

if I type de command you propose:
zramswap start/running

another comment. I wanted to disable apache2 so I went to sudo sysv-rc-conf
and I disabled apache2. but if type service --status-all surprise
[ + ]  apache2
Is it because traditional and new upstart script were setup to init apache2 ?

Just one comment for everyone when  type sysv-rc-conf and then i close the terminal the process keep on working consuming 100% of the cpu. I have to kill it with the command killall.So avoid to use this command.

---

### Post by OrangeCrate on 2012-02-20
Adding...

A good maintence scheme, to help "clean the system" can be found here:

**HOWTO: Cleaning up all those unnecessary junk files...**

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

(Don't let the date of the thread fool you, those tips are as valid today, as when they were first posted.)

---

### Post by Toz on 2012-02-20
> **esbrinartot said:**
> thks for your good explanation. I confirm all that you said.

service utility with ssh:
[ + ]  ssh
chkconfig, rcconf or sysv-rc-conf
ssh doesn't work

about zram:
accordinf to chkconfig, rcconf or sysv-rc-conf IS NOT WORKING

According to service utility
 [ ? ]  zramswap    I don't know the meaning of ?
? means status unknown

> if I type de command you propose:
zramswap start/running
Which is really interesting based on the previous command. I'm not sure why this is happening. Perhaps you should create a bug report with the zramswap maintainers.

> another comment. I wanted to disable apache2 so I went to sudo sysv-rc-conf
and I disabled apache2. but if type service --status-all surprise
[ + ]  apache2
Is it because traditional and new upstart script were setup to init apache2 ?
According to deb files again, apache2 seems to use old style sysv scripts. Try this:
```
sudo /etc/init.d/apache2 stop
```
...then check again.

---

### Post by esbrinartot on 2012-02-21
> **Toz said:**
> ? means status unknown


Which is really interesting based on the previous command. I'm not sure why this is happening. Perhaps you should create a bug report with the zramswap maintainers.


According to deb files again, apache2 seems to use old style sysv scripts. Try this:
```
sudo /etc/init.d/apache2 stop
```...then check again.

thks for your replies and support me in my never ending problems.
when I type sudo /etc/init.d/apache2 stop I obtain:
No apache MPM package installed
I've checked the packages and I with MPM i found next:
apache2-mpm-itk
apache2-mpm-event
apache2-mpm-worker
apache2-mpm-prefork
"al lof them not installed"

i think it's weird. In addition the command service status all give me unknown

I copy the result (notice that for example fan control and firestarter are working. but with rcconf shows are working) SORRY mate for my never ending story

 [ ? ]  acpi-support
 [ ? ]  acpid
 [ ? ]  alsa-restore
 [ ? ]  alsa-store
 [ ? ]  anacron
 [ + ]  apache2
 [ - ]  apparmor
 [ ? ]  apport
 [ ? ]  atd
 [ ? ]  avahi-daemon
 [ ? ]  binfmt-support
 [ - ]  bluetooth
 [ - ]  bootlogd
 [ ? ]  console-setup
 [ ? ]  cron
 [ ? ]  cryptdisks
 [ ? ]  cryptdisks-early
 [ ? ]  cryptdisks-enable
 [ ? ]  cryptdisks-udev
 [ ? ]  cups
 [ ? ]  dbus
 [ ? ]  dmesg
 [ ? ]  dns-clean
 [ ? ]  ecryptfs-utils-restore
 [ ? ]  ecryptfs-utils-save
 [ - ]  fancontrol
 [ - ]  firestarter
 [ ? ]  friendly-recovery
 [ - ]  grub-common
 [ ? ]  hddtemp
 [ ? ]  hostname
 [ ? ]  hwclock
 [ ? ]  hwclock-save
 [ ? ]  irqbalance
 [ ? ]  killprocs
 [ - ]  lm-sensors
 [ ? ]  lxdm
 [ ? ]  modemmanager
 [ ? ]  module-init-tools
 [ ? ]  network-interface
 [ ? ]  network-interface-security
 [ ? ]  network-manager
 [ ? ]  networking
 [ - ]  nfs-kernel-server
 [ ? ]  nmbd
 [ + ]  ntp
 [ ? ]  ondemand
 [ ? ]  pcmciautils
 [ ? ]  plymouth
 [ ? ]  plymouth-log
 [ ? ]  plymouth-splash
 [ ? ]  plymouth-stop
 [ ? ]  plymouth-upstart-bridge
 [ ? ]  pppd-dns
 [ ? ]  preload
 [ ? ]  procps
 [ + ]  proftpd
 [ + ]  pulseaudio
 [ ? ]  rc.local
 [ - ]  rsync
 [ ? ]  rsyslog
 [ ? ]  sendsigs
 [ + ]  sensord
 [ ? ]  setvtrgb
 [ ? ]  smbd
 [ + ]  ssh
 [ - ]  stop-bootlogd
 [ - ]  stop-bootlogd-single
 [ ? ]  sudo
 [ ? ]  udev
 [ ? ]  udev-fallback-graphics
 [ ? ]  udev-finish
 [ ? ]  udevmonitor
 [ ? ]  udevtrigger
 [ ? ]  ufw
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ ? ]  unattended-upgrades
 [ - ]  urandom
 [ + ]  winbind
 [ - ]  x11-common
 [ ? ]  zramswap

---


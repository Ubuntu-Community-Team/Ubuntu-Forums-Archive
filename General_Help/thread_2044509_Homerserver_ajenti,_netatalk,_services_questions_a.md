---
title: "Homerserver: ajenti, netatalk, services questions and issues"
date: 2012-08-19
forum: General Help
---

### Post by alek66 on 2012-08-19
Hi everyone:

I am trying to get tighter my home server (again) I switched to Lubuntu since I wanted lightweight interface. I know its going to be a long post so I numbered it. I consider myself an intermediate user, and still got a lot to learn.

Here are the server specs:
-Computer-
Processor		: AMD Athlon(tm) 64 Processor 3200+
Memory		: 2061MB (243MB used)
Operating System		: Ubuntu 12.04.1 LTS
-Display-
Resolution		: 1024x768 pixels
OpenGL Renderer		: Unknown (I have an old 64mb nvidia, but I don't want any drivers loaded.
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: HDA-Intel - HDA VIA VT82xx
-SCSI Disks-
ATA WDC WD1200JD-22H
ATA WDC WD1600AABS-6
ATA ST380011A

Here are the apps installed:

[LIST]
[*]Transmission
[/LIST][LIST]
[*]Apache2 web server
[/LIST][LIST]
[*]PS3 mediaserver
[/LIST]
[LIST]
[*]avahi
[/LIST]
[LIST]
[*]netatalk
[/LIST]
[LIST]
[*]vino remote desktop
[/LIST]
[LIST]
[*]ajenti
[/LIST][LIST]
[*]ftp server
[/LIST]
[LIST]
[*]ssh server
[/LIST]
[LIST]
[*]Zoneminder
[/LIST]


**Ajenti issue:**
I installed this package this via apt-get (no problems here) it worked, until I installed a necessary python module (python-beautifulsoup, via apt-get, no problems also), after that ajenti stopped to work, when I tried to restart it, I got this:

> sudo service ajenti restart
Stopping Ajenti
pidfile /var/run/ajenti.pid does not exist. Daemon not running?
Starting Ajenti


I have been googling but can't find anything about this. Please let me know what logs can I post.

[COLOR="red"][B]Edited 20 Aug 2012:
[/B][/COLOR]After some work, I decided to re install ajenti, I got it work again, but as dino99 said: it is still a young app.

**Time machine issues:**
I configured this following this [site]("http://kremalicious.com/ubuntu-as-mac-file-server-and-time-machine-volume/") it works fine, I can get my backups done, but every time I get this messages:
[IMG]http://s16.postimage.org/hyzcsg1yd/time_machine_error.png[/IMG]

Heres my /etc/netatalk/afpd.conf (I only posted the important part, the first its all comments)
> #
# CONFIGURATION FOR AFPD
# default:
# - -tcp -noddp -uamlist uams_dhx.so,uams_dhx2.so -nosavepassword
#- -transall -uamlist uams_randnum.so,uams_dhx.so -nosavepassword -advertise_ssh
- -tcp -noddp -uamlist uams_randnum.so,uams_dhx.so,uams_dhx2.so -nosavepassword

Heres my /etc/default/netatalk
> # Netatalk configuration

#########################################################################
# Global configuration
#########################################################################

#### machine's AFPserver/AppleTalk name.
ATALK_NAME=`echo ${HOSTNAME}|cut -d. -f1`

#### server (unix) and legacy client (<= Mac OS 9) charsets
ATALK_UNIX_CHARSET='LOCALE'
ATALK_MAC_CHARSET='MAC_ROMAN'

#### Don't Edit. export the charsets, read form ENV by apps
export ATALK_UNIX_CHARSET
export ATALK_MAC_CHARSET

#########################################################################
# AFP specific configuration
#########################################################################

#### Set which daemons to run.
#### If you use AFP file server, run both cnid_metad and afpd.
ATALKD_RUN=no
PAPD_RUN=no
CNID_METAD_RUN=yes
AFPD_RUN=yes
TIMELORD_RUN=no
A2BOOT_RUN=no

#### maximum number of clients that can connect:
AFPD_MAX_CLIENTS=20

#### UAMs (User Authentication Modules)
#### available options: uams_dhx.so, uams_dhx2.so, uams_guest.so,
####                    uams_clrtxt.so(legacy), uams_randnum.so(legacy)
#AFPD_UAMLIST="-U uams_dhx2.so,uams_clrtxt.so"

#### Set the id of the guest user when using uams_guest.so
#AFPD_GUEST=nobody

#### config for cnid_metad. Default log config:
#CNID_CONFIG="-l log_note"

#########################################################################
# AppleTalk specific configuration (legacy)
#########################################################################

#### Set which legacy daemons to run.
#### If you need AppleTalk, run atalkd.
#### papd, timelord and a2boot are dependent upon atalkd.
#ATALKD_RUN=no
#PAPD_RUN=no
#TIMELORD_RUN=no
#A2BOOT_RUN=no

#### Control whether the daemons are started in the background.
#### If it is dissatisfied that legacy atalkd starts slowly, set "yes".
#### In case using systemd/systemctl, this is not so significant.
#ATALK_BGROUND=no

#### Set the AppleTalk Zone name.
#### NOTE: if your zone has spaces in it, you're better off specifying
####       it in atalkd.conf
#ATALK_ZONE=@zone

[COLOR="Red"]**Editted 22 aug 2012:**[/COLOR]
will check this link to see if I can get it fixed [http://forums.freebsd.org/showthread.php?t=20324](http://forums.freebsd.org/showthread.php?t=20324)

**General questions:**
[LIST=1]
I would like to get vino, transmission, and ps3media server to run as services (basically so I can monitor them via Ajenti (where I can see if the services are running, and stop/start/restart them))
Also to get the to start at boot time. I googled it, but could find a specific way to achieve this.[/LIST]
[LIST=2]As a matter of fact I want to see all the apps listed there as services, but I know some of them are already as services, how can I check this.[/LIST]
[LIST=3] I have 3 disks on the server:
-Mounted File Systems-
/dev/sda1	/	32.59 % (73.9 GiB of 109.6 GiB)	
/dev/sdc1	/media/TimeMachine	60.94 % (29.1 GiB of 74.4 GiB)	
/dev/sdb1	/media/160	6.56 % (139.1 GiB of 148.8 GiB)	

SDA1 is the disk where the OS is installed.
The other two, one is for time machine, the other as a general use. This two, are only mounted if I click on them on the GUI, I saw also they are not on the fstab:
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5e94c099-d34f-45fc-b9dc-6f859dabc626 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7f602713-1a85-4599-9767-c645ed77e978 none            swap    sw              0       0


I want those two disk to be mounted at boot time, automatically, Why don't they appear in the fstab?
[/LIST]

**Ps3 media server issue:**
This is the least of my issues. I can live without this, but I want to fix this kind of things.
At my ps3: I can see pictures and videos perfectly, but when I try to listen to some mp3s, I get "no tracks". There are actually tracks and I could play them via a media center attached to another tv.
At my VLC: I cant play mp3 also, movies are ok and working. 

I have already checked [this]("http://www.ps3mediaserver.org/forum/viewtopic.php?f=6&t=3507&p=15591#p15591") and the forum, but everybody points at not being in the right place on the ps3. I got mp3 playing a on media player, but could not get it on VLC and PS3.

I still don't have zone minder configured yet, since I want to try out this modules first, rest be assured I will make a post about it later.

---

### Post by dino99 on 2012-08-19
you does not said why you have chosen that "ajenti" app (which is not into ubuntu archives) which is very young, so expect some warnings/errors ;)

[https://bugs.launchpad.net/ajenti](https://bugs.launchpad.net/ajenti)

---

### Post by alek66 on 2012-08-19
> **dino99 said:**
> you does not said why you have chosen that "ajenti" app (which is not into ubuntu archives) which is very young, so expect some warnings/errors ;)

[https://bugs.launchpad.net/ajenti](https://bugs.launchpad.net/ajenti)

Hey thanks for replying: I choose ajenti, simply because its lightweight and I like the GUI. And yes, you are corrected I added the sources
> deb [http://repo.ajenti.org/debian](http://repo.ajenti.org/debian) main main
And the key as mentioned in [their]("http://ajenti.org") website.

Hope I can get it to run soon.

---

### Post by alek66 on 2012-08-29
> **alek66 said:**
> 
**Ps3 media server issue:**
This is the least of my issues. I can live without this, but I want to fix this kind of things.
At my ps3: I can see pictures and videos perfectly, but when I try to listen to some mp3s, I get "no tracks". There are actually tracks and I could play them via a media center attached to another tv.
At my VLC: I cant play mp3 also, movies are ok and working. 

I have already checked [this]("http://www.ps3mediaserver.org/forum/viewtopic.php?f=6&t=3507&p=15591#p15591") and the forum, but everybody points at not being in the right place on the ps3. I got mp3 playing a on media player, but could not get it on VLC and PS3.


Updates: the mp3 on a realtek compatible mediaplayer can reproduce everything, the ps3 I found that only plays certain mp3 (depends on the vibrate of the mp3). The funny thing is that a generic media player can play  everything and the ps3 not. will keep investigating.

> I have 3 disks on the server:
-Mounted File Systems-
/dev/sda1	/	32.59 % (73.9 GiB of 109.6 GiB)	
/dev/sdc1	/media/TimeMachine	60.94 % (29.1 GiB of 74.4 GiB)	
/dev/sdb1	/media/160	6.56 % (139.1 GiB of 148.8 GiB)	

SDA1 is the disk where the OS is installed.
The other two, one is for time machine, the other as a general use. This two, are only mounted if I click on them on the GUI, I saw also they are not on the fstab:
Quote:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=5e94c099-d34f-45fc-b9dc-6f859dabc626 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=7f602713-1a85-4599-9767-c645ed77e978 none swap sw 0 0
I want those two disk to be mounted at boot time, automatically, Why don't they appear in the fstab?

I updated the fstab, I added the disks to fstab with their mount point with the following options: defaults, users and got them mount at boot.


**More Solved items:** [COLOR="Red"]30 aug 2012[/COLOR]
> I would like to get vino, transmission, and ps3media server to run as services (basically so I can monitor them via Ajenti (where I can see if the services are running, and stop/start/restart them))
Also to get the to start at boot time. I googled it, but could find a specific way to achieve this.
As a matter of fact I want to see all the apps listed there as services, but I know some of them are already as services, how can I check this.
I got to run apps as services thanks to [this.]("http://greeennotebook.com/2010/06/run-your-program-as-a-service-with-upstart-in-ubuntu/")

---

### Post by alek66 on 2012-09-05
Netatalk time machine solved by using this:
[http://forums.freebsd.org/showthread.php?t=20324](http://forums.freebsd.org/showthread.php?t=20324)

---

### Post by herophil322 on 2013-01-24
Anyone a idea how i can configure an ssl encryption for ajenti?
It try ist but it doesn´t work:(

lg

---


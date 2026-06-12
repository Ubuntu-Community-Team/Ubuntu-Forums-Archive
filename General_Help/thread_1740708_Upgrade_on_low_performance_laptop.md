---
title: "Upgrade on low performance laptop"
date: 2011-04-27
forum: General Help
---

### Post by psargaco on 2011-04-27
Hi.

I'm reissuing a question because I now realise that maybe I had made it too long. 

I have a Dell D531 with 4 GB RAM although the performance is very bad. It has Kubuntu 9.10 installed but I'm using fluxbox as the window manager to make walk instead of crawling. So I was wondering: 


[LIST=1]
[*]Would it make sense to upgrade  to 10.10 or even wait a bit for 11.04? Please bear in mind the  performance issues I've described.
[*]Will Unity be heavy on the hardware?
[*]Is there any Ubuntu version which comes with fluxbox as the default window  manager? Mint was supposed to have a fluxbox version but if I understand  it correctly, that was back in 2008.
[*]Would there be any performance gains if I installed a 64 bits version?
[*]How is the 64 bits software offer these days? I looked into that one  some time ago and lot's of stuff simply wasn't available in 64 bits.
[/LIST]
Thanks,

Paulo

---

### Post by sanguinoso on 2011-04-27
> I have a Dell D531 with 4 GB RAM although the performance is very bad 4 Gigs is a lot for an ubuntu machine what is your processor? And what exactly do you mean by "performance is bad". 

>  2. Will Unity be heavy on the hardware?  My understanding is is that Unity will have higher system requirements than the current Ubuntus which have gnome 2 by default. 
>  3. Is there any Ubuntu version which comes with fluxbox as the default window manager?  No.
>  4. Would there be any performance gains if I installed a 64 bits version?  Do you have a 64 bit processor? You could see some performance gains if so.
>  5. How is the 64 bits software offer these days?  I run 64 bit Ubuntu with no problems; 64 bit machines can also run 32 bit programs.

---

### Post by Joe of loath on 2011-04-27
9.10 has been buggy for me on some machines (9.10 was actually incredibly slow on my Dell when I first installed it, however I reinstalled and the problem went away). Have you tried 10.04 or 10.10 from live USB to see how they fare?

---

### Post by psargaco on 2011-04-27
> **sanguinoso said:**
> 4 Gigs is a lot for an ubuntu machine what is  your processor? And what exactly do you mean by "performance is bad".  

Example 1: I'm watching a 20 minutes film on youtube. After 7 mins the film starts running frame by frame.

Example 2: I'm running XP in VirtualBox. The laptop freezes. I mean,  literally. Nothing happens, doesn't respond to keyboard or mouse.

>   My understanding is is that Unity will have higher system requirements than the current Ubuntus which have gnome 2 by default. 
 No.
 Do you have a 64 bit processor? You could see some performance gains if so.

Yeap. It's an AMD Turion 64 X2 TL-60 (2.00 Ghz). It came originally with an 80 GB hard drive and 2 GB RAM. I decided to go for Kubuntu because XP was really painfully slow. Later I got two upgrades: a 300 GB harddrive and replaced the 2 GB for 4 GB.

> 
 I run 64 bit Ubuntu with no problems; 64 bit machines can also run 32 bit programs.

Cool, that's a good one. So, the next Linux will be 64 bits. Oh, wait. How about wifi card compatibility in 64 bits? D531 comes with a Broadcom.

Thanks!

---

### Post by KegHead on 2011-04-27
Hi!

Wow!

4gb ram?

Have you installed Ubuntu tweak and beach bit?

Also, an update could help!

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

KegHead

---

### Post by trollger on 2011-04-27
> **psargaco said:**
> Hi.

Is there any Ubuntu version which comes with fluxbox as the default window  manager? Mint was supposed to have a fluxbox version but if I understand  it correctly, that was back in 2008.Thanks,

Paulo

No but there is somthing simular called lxde (which is built with fluxbox... I think) which comes with Lubuntu. The current release is built off of ubuntu 10 so you may need to wait a while for 11.

or you could just install fluxbox and unistall GNOME

---

### Post by psargaco on 2011-04-27
> **KegHead said:**
> Hi!

Wow!

4gb ram?



Yeap!

> 

Have you installed Ubuntu tweak and beach bit?

Uhhh... sorry, you lost me there. I installed Kubuntu, then, some months afterwards XFCE, and 2 weeks later, Fluxbox.

Now that I'm running fluxbox I have installed parts of gnome like the power manager and network manager. Plus, there is still some stuff running from KDE. Here's my running processes:

```

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    9 ?        00:00:00 events/0
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 netns
   14 ?        00:00:00 async/mgr
   15 ?        00:00:00 kintegrityd/0
   17 ?        00:00:00 kblockd/0
   19 ?        00:00:00 kacpid
   20 ?        00:00:00 kacpi_notify
   21 ?        00:00:00 kacpi_hotplug
   22 ?        00:00:00 ata/0
   24 ?        00:00:00 ata_aux
   25 ?        00:00:00 ksuspend_usbd
   26 ?        00:00:00 khubd
   27 ?        00:00:00 kseriod
   28 ?        00:00:00 kmmcd
   29 ?        00:00:00 bluetooth
   30 ?        00:00:00 khungtaskd
   31 ?        00:00:00 pdflush
   32 ?        00:00:00 pdflush
   33 ?        00:00:00 kswapd0
   34 ?        00:00:00 aio/0
   36 ?        00:00:00 ecryptfs-kthrea
   37 ?        00:00:00 crypto/0
   42 ?        00:00:00 scsi_eh_0
   43 ?        00:00:00 scsi_eh_1
   44 ?        00:00:00 scsi_eh_2
   45 ?        00:00:00 scsi_eh_3
   46 ?        00:00:00 scsi_eh_4
   48 ?        00:00:00 scsi_eh_5
   53 ?        00:00:00 kstriped
   54 ?        00:00:00 kmpathd/0
   56 ?        00:00:00 kmpath_handlerd
   57 ?        00:00:00 ksnapd
   58 ?        00:00:00 kondemand/0
   60 ?        00:00:00 kconservative/0
   62 ?        00:00:00 krfcommd
  451 ?        00:00:00 kjournald2
  452 ?        00:00:00 ext4-dio-unwrit
  493 ?        00:00:00 mountall
  505 ?        00:00:00 upstart-udev-br
  511 ?        00:00:00 udevd
  756 ?        00:00:00 kpsmoused
  801 ?        00:00:00 hd-audio0
  890 ?        00:00:00 dd
  892 ?        00:00:00 rsyslogd
  894 ?        00:00:01 dbus-daemon
  899 ?        00:00:01 hald
  901 ?        00:00:01 NetworkManager
  903 ?        00:00:00 avahi-daemon
  905 ?        00:00:00 modem-manager
  907 ?        00:00:00 avahi-daemon
  911 ?        00:00:00 console-kit-dae
  974 ?        00:00:00 hald-runner
 1029 ?        00:00:00 wpa_supplicant
 1045 ?        00:00:00 hald-addon-gene
 1047 ?        00:00:00 hald-addon-rfki
 1050 ?        00:00:00 hald-addon-cpuf
 1051 ?        00:00:00 hald-addon-acpi
 1065 ?        00:00:00 hald-addon-inpu
 1094 ?        00:00:00 kdm
 1110 tty7     00:01:59 Xorg
 1202 tty4     00:00:00 getty
 1204 tty5     00:00:00 getty
 1210 tty2     00:00:00 getty
 1212 tty3     00:00:00 getty
 1214 tty6     00:00:00 getty
 1220 ?        00:00:00 acpid
 1226 ?        00:00:00 atd
 1227 ?        00:00:00 cron
 1453 ?        00:00:00 hddtemp
 1499 ?        00:00:00 kdm
 1521 ?        00:00:00 winbindd
 1527 ?        00:00:00 winbindd
 1560 ?        00:00:00 cupsd
 1720 tty1     00:00:00 getty
 1723 ?        00:00:00 dbus-launch
 1724 ?        00:00:00 dbus-daemon
 1746 ?        00:00:03 fluxbox
 1797 ?        00:00:00 ssh-agent
 1798 ?        00:00:00 gpg-agent
 1801 ?        00:00:00 dbus-daemon
 1802 ?        00:00:00 dbus-launch
 1806 ?        00:00:58 launchy
 1807 ?        00:00:01 nm-applet
 1809 ?        00:00:00 gnome-power-man
 1814 ?        00:00:00 devkit-power-da
 1821 ?        00:00:58 conky
 1832 ?        00:00:03 dropbox
 1859 ?        00:00:00 gconfd-2
 1865 ?        00:00:00 gnome-keyring-d
 1875 ?        00:00:00 gvfs-gdu-volume
 1878 ?        00:00:00 gvfsd
 1892 ?        00:00:00 devkit-disks-da
 1893 ?        00:00:00 devkit-disks-da
 1912 ?        00:00:00 gvfs-gphoto2-vo
 2235 ?        00:00:01 notification-da
 2409 ?        00:00:00 bash
 2411 ?        00:05:57 firefox-bin
 2677 ?        00:04:28 plugin-containe
 9482 ?        00:00:00 polkitd
19519 ?        00:00:00 migration/1
19520 ?        00:00:00 ksoftirqd/1
19521 ?        00:00:00 watchdog/1
19522 ?        00:00:00 ext4-dio-unwrit
19523 ?        00:00:00 kconservative/1
19524 ?        00:00:00 kondemand/1
19525 ?        00:00:00 kmpathd/1
19526 ?        00:00:00 crypto/1
19527 ?        00:00:00 aio/1
19528 ?        00:00:00 ata/1
19529 ?        00:00:00 kblockd/1
19530 ?        00:00:00 kintegrityd/1
19531 ?        00:00:00 events/1
19536 ?        00:00:00 udevd
19537 ?        00:00:00 udevd
19610 ?        00:00:00 anacron
19844 ?        00:00:00 dhclient
22115 ?        00:00:00 sh
22117 ?        00:00:00 run-parts
22123 ?        00:00:00 apt
22183 ?        00:00:00 sleep
28785 ?        00:00:00 xterm
28786 pts/0    00:00:00 bash
30052 pts/0    00:00:00 ps

```

> Also, an update could help!

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

KegHead

Maybe I need an upgrade, but the system is up to date. I update it regularly with Synaptic. There are no outstanding updates ):P

---

### Post by psargaco on 2011-04-27
> **trollger said:**
> No but there is somthing simular called lxde (which is built with fluxbox... I think) which comes with Lubuntu. The current release is built off of ubuntu 10 so you may need to wait a while for 11.

or you could just install fluxbox and unistall GNOME

LXDE looks like a good alternative. That's another good tip. Thanks.

---

### Post by psargaco on 2011-04-27
> **Joe of loath said:**
> 9.10 has been buggy for me on some machines (9.10 was actually incredibly slow on my Dell when I first installed it, however I reinstalled and the problem went away). Have you tried 10.04 or 10.10 from live USB to see how they fare?

I never tried a live USB but my experience with Live CDs is that you can't really get a fair assessment of the performance gains. I tried several versions and they were always really slow. It only served the purpose of getting a feel of the interface.

I've seen some youtube flicks, though.

---

### Post by K_45 on 2011-04-27
You could install a windows manager instead of a desktop environment. Something like Openbox or Fluxbox. Ubuntu and its derivatives are also quite porky. If you want a lightweight distro try Crunchbang or a Debian net install.

---

### Post by -kg- on 2011-04-27
> It's an AMD Turion 64 X2 TL-60 (2.00 Ghz). It came originally with an 80 GB hard drive and 2 GB RAM. I decided to go for Kubuntu because XP was really painfully slow. Later I got two upgrades: a 300 GB harddrive and replaced the 2 GB for 4 GB.

With specs like that, and describing the problems you've been having with Linux (and even with XP...XP will run right on lower spec machines than that), I would suspect something other than the type of DM you're using!  You should be able to run any DM you desire, and it should work fine!

Have you done a test on your RAM?  Run a Benchmark on the computer?  There's something wrong somewhere when KDE or Gnome won't run right on a 2 GHz, 64 bit processor with 4 GB of RAM!  I have Ubuntu 10.04 running on a computer here with a 600 MHz Celeron with 364 MB of RAM, and while it's not a speed demon, it runs fairly respectably, and will play Youtube videos fine.

---

### Post by KegHead on 2011-04-27
hi!

You could try to update via the terminal..

Could clear up any files, etc.

KegHead

---

### Post by Joe of loath on 2011-04-27
I will reiterate - I've had major issues with 9.10, do a clean install of 10.04 or 11.04 and it should improve.

---

### Post by slooksterpsv on 2011-04-27
> **Joe of loath said:**
> I will reiterate - I've had major issues with 9.10, do a clean install of 10.04 or 11.04 and it should improve.

I'd recommend a clean install, if you don't want to have to install again in 6 months to have the latest, go with 10.04; otherwise 11.04 will have a better kernel version. I personally noticed a big speed bump from 9.10 to 10.04 and a lot of things were more stable.

---

### Post by KegHead on 2011-04-27
Hi!

Xubuntu looks cool.

It's my backup distro when 11.10 comes out!

KegHead

---

### Post by psargaco on 2011-04-29
> **-kg- said:**
> With specs like that, and describing the problems you've been having with Linux (and even with XP...XP will run right on lower spec machines than that), I would suspect something other than the type of DM you're using!  You should be able to run any DM you desire, and it should work fine!

Have you done a test on your RAM?  Run a Benchmark on the computer?  There's something wrong somewhere when KDE or Gnome won't run right on a 2 GHz, 64 bit processor with 4 GB of RAM!  I have Ubuntu 10.04 running on a computer here with a 600 MHz Celeron with 364 MB of RAM, and while it's not a speed demon, it runs fairly respectably, and will play Youtube videos fine.

I haven't run any benchmark. But I think we can rule out RAM because I had it replaced from 1 x 2 GB to 2 x 2 GB and the issues remained. But you may be on to something. Perhaps there's a problem with the graphics card or something. The Youtube issue is independent of the OS.

---

### Post by psargaco on 2011-04-29
> **slooksterpsv said:**
> I'd recommend a clean install, if you don't want to have to install again in 6 months to have the latest, go with 10.04; otherwise 11.04 will have a better kernel version. I personally noticed a big speed bump from 9.10 to 10.04 and a lot of things were more stable.

I'll do that, thanks. Meanwhile I had problems backing up files, but I'll investigate a bit first and will create a new thread on a later occasion.

---

### Post by psargaco on 2011-04-30
> **trollger said:**
> No but there is somthing simular called lxde (which is built with fluxbox... I think) which comes with Lubuntu. The current release is built off of ubuntu 10 so you may need to wait a while for 11.

or you could just install fluxbox and unistall GNOME

I'm downloading Lubuntu now and will give it a spin. If I still don't like the performance I'll try the 64 bit approach. I will close this thread now. Thank you all for your inputs.

---


---
title: "Can't get gdm nor X to work, please help"
date: 2011-09-19
forum: General Help
---

### Post by castawaybcn on 2011-09-19
Hi there, 

I am running Ubuntu 10.04.3, linux kernel 2.6.32-33-generic

When I start my desktop computer everything seems fine until gdm should appear. Instead, the screen flashes a few times and blacks out. I can log in through command line in tty2 to 6, but not tty1 and tty7.
```
dmesg | grep error
```
returns several errors like this one:
```
gdm-simple-slav[1644]: segfault at 2d140283 ip 00484a4f sp bfaf99ac error 4 in libc-2.11.1.so
```

I also tried to stop Xserver with:
```
sudo /etc/init.d/gdm stop
```

And reinstalled nvidia's graphics drivers from their website, then I tried starting it again with
```
sudo /etc/init.d/gdm start
```
and got this:
```
gdm-binary[2775]: WARNING: Unable to load file '/etc/gdm/custom.conf': no such file or directory
gdm-binary[2775]: WARNING: Unable to dinf users: no seat-id found
gdm-binary[2775]: WARNING: GdmDisplay: display lasted 0.02488 seconds
```

There were 4 GdmDisplay error lines and then it told me to check X server log for errors), so I did:
```
cat /var/log/Xorg.0.log | grep EE
```
with this result:
```
(EE) [drm] KMS not enabled
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
```

I also tried restarting in recovery mode, but failsafeX showed me the same two previous errors. Running in low graphics mode resulted in the same black screen...

I have been trying to fix this for hours, but I am at a complete loss and I don't know what else to do.

Please help, any ideas or suggestions are more than welcome.

---

### Post by seawolf167 on 2011-09-19
Take a look at [this thread ]("http://ubuntuforums.org/showthread.php?t=690760")and see if it helps answer your question.

---

### Post by castawaybcn on 2011-09-19
Thanks for your answer. I did check but it did not help at all, still in dire straits.

---

### Post by castawaybcn on 2011-09-20
Bump

---

### Post by garvinrick4 on 2011-09-20
> Please help, any ideas or suggestions are more than welcome.That is all this is then, idea's ( when you work in Alpha's you do this a lot, stick with it)
.> KMS not enabledI do not have a nvida  and this thread is just not in my skill sets but I did notice you are running
in nomodeset is that correct and that is how you intended?  Do you need to run in nomodeset? 
KMS is disabled on your machine: ( I really do not know if running with disabled has any effect on your machine just trying to throw something in and bump you)
This is just a thought since you were getting no action yet on your thread. This will bump you
up to front at worst. Hope you get your machine fixed up.
## [COLOR=Red]And you did try to chroot into your / and purge and reinstall gdm.[/COLOR] Or in a tty if still have internet.

```
nomodeset

Ubuntu 10.04 LTS enables the new kernel-mode-setting (KMS) technology by default on most common video chipsets. 
While this is a major step forward for the graphics architecture in 
Ubuntu, in some rare cases KMS will prevent your 
video output from working correctly, or from working at all. 
If you need to disable KMS, you can do so by booting with 
the nomodeset option. You can also save this setting so that 
it's applied at every boot by adding it to your grub config 
(for GRUB 2: edit /etc/default/grub and add nomodeset to 
GRUB_CMDLINE_LINUX, then run sudo update-grub
```

---

### Post by garvinrick4 on 2011-09-20
> gdm-binary[2775: WARNING: Unable to load file '/etc/gdm/custom.conf': no such file or directory
Here is my /etc/gdm/custom.conf in a Maverick which for some reason you do not seem to have.
Just looking for error message answers here.

---

### Post by garvinrick4 on 2011-09-20
If you are still around and did not give up the ghost and fresh install, let me know so I
am not kicking around a dead thread. 
> Failed to initialize GLX extension (NVIDIA X driver not found)
( I might have to buy a machine with NVIDIA
graphic's not fully understanding that issue irks me to know end.) Take care partner
and give a post if still working on this thread.  EDIT (heading back to oneiric now and out of maverick) See ya around.

---

### Post by castawaybcn on 2011-09-21
Well, first of all... wow, thanks a lot for all that stuff garvinrick4, I really appreciate it!

And no, the thread is not dead at all, it's just different time zones!

About nomodeset. Actually I have no idea why I set it up, probably because of a screen resolution/conflict with plymouth's login animation. Even though I did that ages ago I tried removing nomodeset from boot but still no love. Actually it was unlikely to work as I tried booting in safe mode and that does not have nomodeset option enabled. Well, one thing less to look at.

Thanks for providing your /etc/gdm/custom.conf file contents, but I don't know if this is the problem. Actually my laptop (from where I am writting this) does not have this file either (also 10.04) but then again it has an ATI graphics card. I will try creating the file manually, but I do not have autologin enabled as it is not possible with an encrypted home drive.

I did not try purging gdm, as it is my understanding that this actually removes the whole gnome desktop, am I right? I have to admit that this was actually one of the options in my list, but not one I was looking forward to...

Will let you know if I find anything else, and thanks again for your support.

---

### Post by garvinrick4 on 2011-09-21
Yes you mess with any gdm or xorg it will have to do with ubuntu-desktop.
```
sudo apt-get install --reinstall gdm
```
 Edit Run this code again above.

---

### Post by garvinrick4 on 2011-09-21
Did that do any good for you.
We got gdm we got xorg and we got your graphics driver.
sudo apt-get clean
sudo apt-get install --reinstall gdm
sudo apt-get install --reinstall xorg
and last we have your graphics driver
do you remember how to install your graphics driver?
Do one at a time and see if fixes.
I have run them on my machine before giving them to you before and now just to
make sure I am not putting you in a bad way.
You do get to a tty with internet correct if not we got to go to a Live cd and chroot.
After reinstall gdm there is.
sudo /etc/init.d/gdm restart

###Let me know what is going on when get a chance I have this thread suscribed so will be around.
[COLOR=Red]EDIT run code again[/COLOR]

---

### Post by castawaybcn on 2011-09-21
> **garvinrick4 said:**
> Yes you mess with any gdm or xorg it will have to do with ubuntu-desktop.
```
sudo apt-get install -reinstall gdm
```

strangely enough -reinstall is not an option:
```
E: Command line option 'r' [from -reinstall] is not known.
```

---

### Post by garvinrick4 on 2011-09-21
> **castawaybcn said:**
> strangely enough -reinstall is not an option:
```
E: Command line option 'r' [from -reinstall] is not known.
```
sudo apt-get install --reinstall gdm

---

### Post by castawaybcn on 2011-09-21
> **garvinrick4 said:**
> Did that do any good for you.
We got gdm we got xorg and we got your graphics driver.
sudo apt-get clean
sudo apt-get install --reinstall gdm
sudo apt-get install --reinstall xorg
and last we have your graphics driver
do you remember how to install your graphics driver?
Do one at a time and see if fixes.
I have run them on my machine before giving them to you before and now just to
make sure I am not putting you in a bad way.
You do get to a tty with internet correct if not we got to go to a Live cd and chroot.
After reinstall gdm there is.
sudo /etc/init.d/gdm restart

###Let me know what is going on when get a chance I have this thread suscribed so will be around.
[COLOR=Red]EDIT run code again[/COLOR]


Started normally, where gdm should appear switched to tty2 (ALT+F2)
```

sudo apt-get clean
sudo apt-get install --reinstall gdm
sudo /etc/init.d/gdm restart
```
went back to tty7 (ALT+F7) but no luck, restarting with
```
sudo shutdown -r 0
```
And back where I started. Reinstalled xorg as you suggested but no luck, flashing were gdm should be is a bit different, just as useless though.
In order to reinstall the nvidia graphics should I follow [this post]("http://ubuntuforums.org/showpost.php?p=9203671&postcount=1")?

---

### Post by garvinrick4 on 2011-09-21
I do not have a nvidia card so am in same as you, it was running do you remember at
install what driver you installed. I do not have a lucid install but I do have one Maverick
hanging around. Going to Google a bit myself and ask some other users with Nvidia graphics. 
I think we are getting it honed down to that problem anyway. Usually their
are a lot of Nvidia users that would step in and help. We will work on it. Keep in touch
will be here all day.
#what is your graphics card?

---

### Post by garvinrick4 on 2011-09-21
**  Installation of ATI and nVidia Graphics drivers **

 **  nVidia Driver **

 The current proprietary nVidia drivers are automatically installed using: 
 Menu -> System -> Administration -> Hardware Drivers  Look for the current drivers to activate there. 
 
[LIST]
[*]Here are alternate manual instructions.
[/LIST]
 
[LIST]
[*]Please make a backup of xorg.conf before following this method.
[/LIST]
  sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak  
[LIST]
[*]Install the nvidia-settings package:
[/LIST]
   sudo apt-get install nvidia-settings  
[LIST]
[*]Download the nVidia driver:
[/LIST]
  wget -O NVIDIA-Linux-x86-pkg1.run [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) sudo sh NVIDIA-Linux-x86-pkg1.run  
and choose yes to any verbose response. After you install the driver, reboot your computer. 
 **  ATI Driver **

 If you have problems with ATI drivers after upgrading, check [this link]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide") for solutions to common problems with ATI. 
 **  Monitors / Displays **

---

### Post by garvinrick4 on 2011-09-21
[LIST]
[*]Sometimes after a kernel upgrade a proprietary driver may stop  working. In such a case, try installing the new linux-headers that match  the newly upgraded kernel:
[/LIST]
 sudo apt-get install linux-headers-$(uname -r)

rick@rick-narwhal:~$ uname -a
Linux rick-narwhal 3.0.4-030004-generic #201108301138 SMP Tue Aug 30 11:42:30 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```
sudo apt-get install linux-headers-3.0.4-030004-generic
```This is for my headers. Use your own from uname -a

#Did you just get through with an upgrade when machine failed?

---

### Post by garvinrick4 on 2011-09-21
sudo sh -c "echo 'deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/Ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/Ubuntu) lucid main' >> /etc/apt/sources.list" 
sudo apt-get update 
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings 
 
Here is lucid ppa with nvidia lucid drivers:
Run them one at a time. I like the ppa's, 
Since I know nothing about nvidia graphics and no one hopped in I like this. Only question is do you have to run with nomodeset option as was set.

Hope I have helped you some in your Thread. I am going to get me a Nvidia card as to get a skill set with these graphics cards, I hope you and I have learned
a little here. This is like working in a Alpha when it falls apart on you. You find a solution by working on it. Keep in touch. If post 16 did not do it this will I believe.

---

### Post by castawaybcn on 2011-09-21
> **garvinrick4 said:**
> **  Installation of ATI and nVidia Graphics drivers **

 **  nVidia Driver **

 The current proprietary nVidia drivers are automatically installed using: 
 Menu -> System -> Administration -> Hardware Drivers  Look for the current drivers to activate there. 
 
[LIST]
[*]Here are alternate manual instructions.
[/LIST]
 
[LIST]
[*]Please make a backup of xorg.conf before following this method.
[/LIST]
  sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak  
[LIST]
[*]Install the nvidia-settings package:
[/LIST]
   sudo apt-get install nvidia-settings  
[LIST]
[*]Download the nVidia driver:
[/LIST]
  wget -O NVIDIA-Linux-x86-pkg1.run [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) sudo sh NVIDIA-Linux-x86-pkg1.run  
and choose yes to any verbose response. After you install the driver, reboot your computer. 
 **  ATI Driver **

 If you have problems with ATI drivers after upgrading, check [this link]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide") for solutions to common problems with ATI. 
 **  Monitors / Displays **

when I try to install nvidia graphics (downloaded from their website) it complains that there is an active X server, perhaps it is what I can't see on either tty2 or tty7, when I try stopping it (perhaps I am doing it wrong): 
```
sudo gdm-stop
```
I get this:
```
/var/run/gdm.pid doesn't exist, perhaps GDM isn't running
```
Which of the several further steps you kindly offered do you think I should try next?

---

### Post by garvinrick4 on 2011-09-21
#17
If this does not do the trick, remember to try nomodeset if it needed. I do have a buddy that is online
with nvidia in his machines. One way or another we will get you going.

tty7
ctrl/alt/F7 (is brings you back to X)
is
sudo stop gdm
sudo start gdm
or
sudo /etc/init.d/gdm restart

---

### Post by castawaybcn on 2011-09-21
> **garvinrick4 said:**
> sudo sh -c "echo 'deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/Ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/Ubuntu) lucid main' >> /etc/apt/sources.list" 
sudo apt-get update 
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings 
 
Here is lucid ppa with nvidia lucid drivers:
Run them one at a time. I like the ppa's, 
Since I know nothing about nvidia graphics and no one hopped in I like this. Only question is do you have to run with nomodeset option as was set.

Hope I have helped you some in your Thread. I am going to get me a Nvidia card as to get a skill set with these graphics cards, I hope you and I have learned
a little here. This is like working in a Alpha when it falls apart on you. You find a solution by working on it. Keep in touch. If post 16 did not do it this will I believe.

I tried, but added [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) lucid main instead since the one you suggested no longer has any packages for ubuntu. I installed the three nvidia packages but no luck.

I also tried removing the nomodeset option from the boot options, the only difference it made was an uglier plymouth screen and lower terminal resolution.

When I try running in safe mode I get this error:
```
(EE) Failed to load module "nouveau" (module does not exist, 0)
(EE) Failed to initialize GLX extension (Compatible NVIDI X driver not found)
```
Then I choose reconfigure to reconfigure graphics and "create new configuration for this hardware" and restart x, but I am sent back to the terminal and boot process gets stuck just after "checking battery state" 

I will leave it like this for a while and see if there is anything new.

Thanks a lot for your time, mate.

---

### Post by garvinrick4 on 2011-09-21
Ok if it is a graphics problem a user with your card hopefully knows what the heck he
is doing. I am lost with the nvidia graphics cards.
Get your nomodeset back in place if you removed it.
Does gdm stop and start? You are lucid version correct? We reinstalled xorg and gdm,
graphics card no go. So will keep an eye and hope my friend can get you straight.
wildemanne39 is on the way, nice guy will do his best and owns some nvidia cards.

---

### Post by castawaybcn on 2011-09-21
> **garvinrick4 said:**
> Ok if it is a graphics problem a user with your card hopefully knows what the heck he
is doing. I am lost with the nvidia graphics cards.
Get your nomodeset back in place if you removed it.
Does gdm stop and start? You are lucid version correct? We reinstalled xorg and gdm,
graphics card no go. So will keep an eye and hope my friend can get you straight.
wildemanne39 is on the way, nice guy will do his best and owns some nvidia cards.

Yep, on lucid and my graphics card is nVidia GeForce 9400Gt

Will call it a night for today though, will come back to this tomorrow in the afternoon. Thanks again.

---

### Post by garvinrick4 on 2011-09-21
> Will call it a night for today though, will come back to this tomorrow in the afternoon. Thanks again. Ok post back tomorrow this Thread has become
a quest. Enjoy your evening.

---

### Post by wildmanne39 on 2011-09-21
Hi, I have been reading the thread that is what took me so long there is a lot to read and I will have to look over it more most likely.

I want to get some information before I start posting possible solutions,

```
cat /etc/lsb-release; uname -a
```
```
lspci | grep VGA
```
```
sudo lshw
```
please post the outcome of these commands here by clicking on new reply and click # and paste the information between the brackets.

Also have you checked disk utility to see if you may have bad sectors on your hard drive that caused file corruption?

If I ask something that has already been posted please forgive me I may not remember everything I have read.

Is this a new install or having you been using ubuntu with no problems before now?
Thank you

---

### Post by castawaybcn on 2011-09-22
Hi wildmanne39, welcome and thanks a lot for giving a hand with this. Sorry for getting back so late, I have been rather busy with work.

Not a clean install, I have been running Ubuntu in this computer for 2+ years now. Originally I installed 9.10 and upgraded to 10.04 without any major troubles except for some minor sound card issues. Everything was going really fine until now.

```
cat /etc/lsb-release; uname -a
```
Returns
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 1004.03 LTS"
Linux cesc-desktop 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux
```
and
```
lspci | grep VGA
```
gives me:
```

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
```
As for
```
sudo lshw
```
Well, it produces a lot of stuff, and since I am typing this manually into my laptop... can you tell me what we are looking for?

I will check for bad sectors too. I will have to boot with a usb and use the disk utility though. Will get back when I have some results, but it may be a while, I have to run out in a few minutes.

I really appreciate what you guys are doing here. Even if we don't come to a successful outcome it is people like you that make me truly believe in what FLOSS means. Thanks a million.

---

### Post by wildmanne39 on 2011-09-22
Hi, I am reviewing the information you just posted, and what I was looking for is your computer specs, and how old it is.

If you do not have an internet connection on that computer you can paste it to a usb flash drive and put then use the computer that you are on the forum with the post the information here.
Thank you

---

### Post by wildmanne39 on 2011-09-22
Hi, I have a couple of idea's let's get the results of these commands first please.
```
lsmod | grep nvi
```
```
dmesg | egrep 'nvi|VGA'
```
```
tail -n100 /var/log/syslog
```
```
tail -n100 /var/log/kern.log
```
Thank you

---

### Post by castawaybcn on 2011-09-23
Ok, here is what I have done so far. First I checked for bad blocks in both my / and home partition:
```
sudo badblocks -v /dev/sda2
sudo badblocks -v /dev/sda6
```
Luckily there where no errors in either of them. Then I checked both partitions for inconsistencies
```
sudo fsck -t ext4 /dev/sda2
sudo fsck -t ext4 /dev/sda6
```
And no errors either. So, I carried on with your instructions:
```
lsmod | grep nvi
```
returns
```
nvidia	10382593 0
agpgart	31724 2 nvidia,intel_agp
```

```
dmesg | egrep 'nvi|VGA'
```
returns
```
[    1.197463] fb0: VESA VGA frame buffer device
[    1.805059] fb1: VESA VGA frame buffer device
[    8.693214] nvidia: module license 'NVIDIA' taints kernel.
[    9.825427] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.825435] nvidia 0000:01:00.0: setting latency timer to 64
```
```
tail -n100 /var/log/syslog
```
returns
```
Sep 23 21:23:10 cesc-desktop kernel: [   10.963427] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Sep 23 21:23:10 cesc-desktop kernel: [   10.963429] vboxdrv: Successfully loaded version 4.1.2 (interface 0x00190000).
Sep 23 21:23:10 cesc-desktop dhclient: DHCPACK of 192.168.1.36 from 192.168.1.1
Sep 23 21:23:10 cesc-desktop dhclient: bound to 192.168.1.36 -- renewal in 38085 seconds.
Sep 23 21:23:10 cesc-desktop NetworkManager: <info>  DHCP: device eth3 state changed preinit -> bound
Sep 23 21:23:10 cesc-desktop NetworkManager: <info>  Activation (eth3) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep 23 21:23:10 cesc-desktop NetworkManager: <info>  Activation (eth3) Stage 4 of 5 (IP4 Configure Get) started...
Sep 23 21:23:10 cesc-desktop NetworkManager: <info>    address 192.168.1.36
Sep 23 21:23:10 cesc-desktop NetworkManager: <info>    prefix 24 (255.255.255.0)
Sep 23 21:23:10 cesc-desktop NetworkManager: <info>    gateway 192.168.1.1
Sep 23 21:23:10 cesc-desktop NetworkManager: <info>    hostname 'cesc-desktop'
Sep 23 21:23:10 cesc-desktop NetworkManager: <info>    nameserver '192.168.1.1'
Sep 23 21:23:10 cesc-desktop NetworkManager: <info>  Activation (eth3) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep 23 21:23:10 cesc-desktop NetworkManager: <info>  Activation (eth3) Stage 4 of 5 (IP4 Configure Get) complete.
Sep 23 21:23:10 cesc-desktop NetworkManager: <info>  Activation (eth3) Stage 5 of 5 (IP Configure Commit) started...
Sep 23 21:23:10 cesc-desktop avahi-daemon[988]: Joining mDNS multicast group on interface eth3.IPv4 with address 192.168.1.36.
Sep 23 21:23:10 cesc-desktop avahi-daemon[988]: New relevant interface eth3.IPv4 for mDNS.
Sep 23 21:23:10 cesc-desktop avahi-daemon[988]: Registering new address record for 192.168.1.36 on eth3.IPv4.
Sep 23 21:23:10 cesc-desktop kernel: [   11.177320] vboxpci: IOMMU not found (not compiled)
Sep 23 21:23:10 cesc-desktop sm-mta[1633]: My unqualified host name (cesc-desktop) unknown; sleeping for retry
Sep 23 21:23:10 cesc-desktop /etc/mysql/debian-start[1643]: Upgrading MySQL tables if necessary.
Sep 23 21:23:10 cesc-desktop /etc/mysql/debian-start[1646]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Sep 23 21:23:10 cesc-desktop /etc/mysql/debian-start[1646]: Looking for 'mysql' as: /usr/bin/mysql
Sep 23 21:23:10 cesc-desktop /etc/mysql/debian-start[1646]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Sep 23 21:23:10 cesc-desktop /etc/mysql/debian-start[1646]: This installation of MySQL is already upgraded to 5.1.41, use --force if you still need to run mysql_upgrade
Sep 23 21:23:10 cesc-desktop /etc/mysql/debian-start[1653]: Checking for insecure root accounts.
Sep 23 21:23:10 cesc-desktop /etc/mysql/debian-start[1657]: Triggering myisam-recover for all MyISAM tables
Sep 23 21:23:11 cesc-desktop NetworkManager: <info>  (eth3): device state change: 7 -> 8 (reason 0)
Sep 23 21:23:11 cesc-desktop NetworkManager: <info>  Policy set 'Auto eth3' (eth3) as default for routing and DNS.
Sep 23 21:23:11 cesc-desktop NetworkManager: <info>  Activation (eth3) successful, device activated.
Sep 23 21:23:11 cesc-desktop NetworkManager: <info>  Activation (eth3) Stage 5 of 5 (IP Configure Commit) complete.
Sep 23 21:23:12 cesc-desktop gdm-simple-slave[1074]: CRITICAL: Error while compiling regular expression DBUS_SESSION_BUS_ADDRESS=(.+)#012DBUS_SESSION_BUS_PID=([0-9]+) at char 0: unknown option bit(s) set
Sep 23 21:23:12 cesc-desktop gdm-simple-slave[1074]: GLib-CRITICAL: g_regex_match_full: assertion `regex != NULL' failed
Sep 23 21:23:12 cesc-desktop gdm-binary[985]: WARNING: GdmDisplay: display lasted 2.758723 seconds
Sep 23 21:23:12 cesc-desktop gdm-simple-slave[1933]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 23 21:23:12 cesc-desktop sm-msp-queue[2007]: My unqualified host name (cesc-desktop) unknown; sleeping for retry
Sep 23 21:23:13 cesc-desktop acpid: client 1158[0:0] has disconnected
Sep 23 21:23:13 cesc-desktop acpid: client connected from 1945[0:0]
Sep 23 21:23:13 cesc-desktop acpid: 1 client rule loaded
Sep 23 21:23:14 cesc-desktop gdm-simple-slave[1933]: CRITICAL: Error while compiling regular expression DBUS_SESSION_BUS_ADDRESS=(.+)#012DBUS_SESSION_BUS_PID=([0-9]+) at char 0: unknown option bit(s) set
Sep 23 21:23:14 cesc-desktop gdm-simple-slave[1933]: GLib-CRITICAL: g_regex_match_full: assertion `regex != NULL' failed
Sep 23 21:23:14 cesc-desktop kernel: [   15.930879] __ratelimit: 22 callbacks suppressed
Sep 23 21:23:14 cesc-desktop kernel: [   15.930883] gdm-simple-slav[1933]: segfault at 2d1e0733 ip 00c17a4f sp bfb99e5c error 4 in libc-2.11.1.so[ba4000+153000]
Sep 23 21:23:14 cesc-desktop gdm-binary[985]: WARNING: GdmDisplay: display lasted 2.617187 seconds
Sep 23 21:23:15 cesc-desktop gdm-simple-slave[2063]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 23 21:23:15 cesc-desktop acpid: client 1945[0:0] has disconnected
Sep 23 21:23:15 cesc-desktop acpid: client connected from 2072[0:0]
Sep 23 21:23:15 cesc-desktop acpid: 1 client rule loaded
Sep 23 21:23:17 cesc-desktop ntpdate[1700]: step time server 91.189.94.4 offset 0.586109 sec
Sep 23 21:23:17 cesc-desktop gdm-simple-slave[2063]: CRITICAL: Error while compiling regular expression DBUS_SESSION_BUS_ADDRESS=(.+)#012DBUS_SESSION_BUS_PID=([0-9]+) at char 0: unknown option bit(s) set
Sep 23 21:23:17 cesc-desktop gdm-simple-slave[2063]: GLib-CRITICAL: g_regex_match_full: assertion `regex != NULL' failed
Sep 23 21:23:17 cesc-desktop gdm-binary[985]: WARNING: GdmDisplay: display lasted 2.372875 seconds
Sep 23 21:23:17 cesc-desktop kernel: [   18.304140] gdm-simple-slav[2063]: segfault at 2ce693a3 ip 00af9a4f sp bf822acc error 4 in libc-2.11.1.so[a86000+153000]
Sep 23 21:23:17 cesc-desktop gdm-simple-slave[2095]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 23 21:23:18 cesc-desktop acpid: client 2072[0:0] has disconnected
Sep 23 21:23:18 cesc-desktop acpid: client connected from 2104[0:0]
Sep 23 21:23:18 cesc-desktop acpid: 1 client rule loaded
Sep 23 21:23:20 cesc-desktop gdm-simple-slave[2095]: CRITICAL: Error while compiling regular expression DBUS_SESSION_BUS_ADDRESS=(.+)#012DBUS_SESSION_BUS_PID=([0-9]+) at char 0: unknown option bit(s) set
Sep 23 21:23:20 cesc-desktop gdm-simple-slave[2095]: GLib-CRITICAL: g_regex_match_full: assertion `regex != NULL' failed
Sep 23 21:23:20 cesc-desktop gdm-binary[985]: WARNING: GdmDisplay: display lasted 2.422301 seconds
Sep 23 21:23:20 cesc-desktop kernel: [   20.726814] gdm-simple-slav[2095]: segfault at 2d0f0263 ip 00577a4f sp bfaa998c error 4 in libc-2.11.1.so[504000+153000]
Sep 23 21:23:20 cesc-desktop gdm-simple-slave[2126]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 23 21:23:20 cesc-desktop kernel: [   20.736509] eth3: no IPv6 routers present
Sep 23 21:23:21 cesc-desktop acpid: client 2104[0:0] has disconnected
Sep 23 21:23:21 cesc-desktop acpid: client connected from 2135[0:0]
Sep 23 21:23:21 cesc-desktop acpid: 1 client rule loaded
Sep 23 21:23:22 cesc-desktop gdm-simple-slave[2126]: CRITICAL: Error while compiling regular expression DBUS_SESSION_BUS_ADDRESS=(.+)#012DBUS_SESSION_BUS_PID=([0-9]+) at char 0: unknown option bit(s) set
Sep 23 21:23:22 cesc-desktop gdm-simple-slave[2126]: GLib-CRITICAL: g_regex_match_full: assertion `regex != NULL' failed
Sep 23 21:23:22 cesc-desktop gdm-binary[985]: WARNING: GdmDisplay: display lasted 2.416039 seconds
Sep 23 21:23:22 cesc-desktop kernel: [   23.143179] gdm-simple-slav[2126]: segfault at 2cebf083 ip 00bc2a4f sp bf8787ac error 4 in libc-2.11.1.so[b4f000+153000]
Sep 23 21:23:22 cesc-desktop gdm-simple-slave[2157]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 23 21:23:23 cesc-desktop acpid: client 2135[0:0] has disconnected
Sep 23 21:23:23 cesc-desktop acpid: client connected from 2166[0:0]
Sep 23 21:23:23 cesc-desktop acpid: 1 client rule loaded
Sep 23 21:23:25 cesc-desktop gdm-simple-slave[2157]: CRITICAL: Error while compiling regular expression DBUS_SESSION_BUS_ADDRESS=(.+)#012DBUS_SESSION_BUS_PID=([0-9]+) at char 0: unknown option bit(s) set
Sep 23 21:23:25 cesc-desktop gdm-simple-slave[2157]: GLib-CRITICAL: g_regex_match_full: assertion `regex != NULL' failed
Sep 23 21:23:25 cesc-desktop gdm-binary[985]: WARNING: GdmDisplay: display lasted 2.427420 seconds
Sep 23 21:23:25 cesc-desktop gdm-binary[985]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
Sep 23 21:23:25 cesc-desktop kernel: [   25.570970] gdm-simple-slav[2157]: segfault at 2d3a1823 ip 00cb7a4f sp bfd5af4c error 4 in libc-2.11.1.so[c44000+153000]
Sep 23 21:23:25 cesc-desktop init: gdm main process (985) terminated with status 1
Sep 23 21:24:11 cesc-desktop sm-mta[1633]: unable to qualify my own domain name (cesc-desktop) -- using short name
Sep 23 21:24:11 cesc-desktop sm-mta[2213]: starting daemon (8.14.3): SMTP+queueing@00:10:00
Sep 23 21:24:13 cesc-desktop sm-msp-queue[2007]: unable to qualify my own domain name (cesc-desktop) -- using short name
Sep 23 21:24:13 cesc-desktop saned[2253]: saned (AF-indep+IPv6) from sane-backends 1.0.20 starting up
Sep 23 21:24:13 cesc-desktop saned[2253]: do_bindings: [0] bind failed: Address already in use
Sep 23 21:24:13 cesc-desktop saned[2254]: Now daemonized
Sep 23 21:24:13 cesc-desktop saned[2254]: Dropped privileges to uid 112 gid 118
Sep 23 21:24:13 cesc-desktop kernel: [   73.911482] CPU0 attaching NULL sched-domain.
Sep 23 21:24:13 cesc-desktop kernel: [   73.911487] CPU1 attaching NULL sched-domain.
Sep 23 21:24:13 cesc-desktop kernel: [   73.932588] CPU0 attaching sched-domain:
Sep 23 21:24:13 cesc-desktop kernel: [   73.932593]  domain 0: span 0-1 level MC
Sep 23 21:24:13 cesc-desktop kernel: [   73.932597]   groups: 0 1
Sep 23 21:24:13 cesc-desktop kernel: [   73.932605] CPU1 attaching sched-domain:
Sep 23 21:24:13 cesc-desktop kernel: [   73.932608]  domain 0: span 0-1 level MC
Sep 23 21:24:13 cesc-desktop kernel: [   73.932612]   groups: 1 0
Sep 23 21:24:13 cesc-desktop init: plymouth-stop pre-start process (2368) terminated with status 1
Sep 23 21:24:51 cesc-desktop kernel: [  111.698299] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
Sep 23 21:24:51 cesc-desktop kernel: [  111.703255] padlock: VIA PadLock not detected.
Sep 23 21:28:10 cesc-desktop anacron[1188]: Job `cron.daily' started
Sep 23 21:28:10 cesc-desktop anacron[2638]: Updated timestamp for job `cron.daily' to 2011-09-23
```
```
tail -n100 /var/log/kern.log
```
returns
```
Sep 23 21:23:09 cesc-desktop kernel: [    1.076522] usb 2-1: new low speed USB device using uhci_hcd and address 2
Sep 23 21:23:09 cesc-desktop kernel: [    1.122538] uvesafb: NVIDIA Corporation, G96 Board - 07290040, Chip Rev   , OEM: NVIDIA, VBE v3.0
Sep 23 21:23:09 cesc-desktop kernel: [    1.132741] uvesafb: protected mode interface info at c000:c520
Sep 23 21:23:09 cesc-desktop kernel: [    1.132744] uvesafb: pmi: set display start = c00cc583, set palette = c00cc5de
Sep 23 21:23:09 cesc-desktop kernel: [    1.132745] uvesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
Sep 23 21:23:09 cesc-desktop kernel: [    1.196556] uvesafb: VBIOS/hardware doesn't support DDC transfers
Sep 23 21:23:09 cesc-desktop kernel: [    1.196559] uvesafb: no monitor limits have been set, default refresh rate will be used
Sep 23 21:23:09 cesc-desktop kernel: [    1.196689] uvesafb: scrolling: ywrap using protected mode interface, yres_virtual=2867
Sep 23 21:23:09 cesc-desktop kernel: [    1.197460] uvesafb: framebuffer at 0xfb000000, mapped to 0xf8180000, using 14336k, total 14336k
Sep 23 21:23:09 cesc-desktop kernel: [    1.197463] fb0: VESA VGA frame buffer device
Sep 23 21:23:09 cesc-desktop kernel: [    1.336956] usb 2-1: configuration #1 chosen from 1 choice
Sep 23 21:23:09 cesc-desktop kernel: [    1.352338] usbcore: registered new interface driver hiddev
Sep 23 21:23:09 cesc-desktop kernel: [    1.396147] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
Sep 23 21:23:09 cesc-desktop kernel: [    1.396268] generic-usb 0003:04D9:1603.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.0-1/input0
Sep 23 21:23:09 cesc-desktop kernel: [    1.489084] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input4
Sep 23 21:23:09 cesc-desktop kernel: [    1.489195] generic-usb 0003:04D9:1603.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.0-1/input1
Sep 23 21:23:09 cesc-desktop kernel: [    1.489217] usbcore: registered new interface driver usbhid
Sep 23 21:23:09 cesc-desktop kernel: [    1.489285] usbhid: v2.6:USB HID core driver
Sep 23 21:23:09 cesc-desktop kernel: [    1.546967] Console: switching to colour frame buffer device 160x64
Sep 23 21:23:09 cesc-desktop kernel: [    1.584018] usb 2-2: new low speed USB device using uhci_hcd and address 3
Sep 23 21:23:09 cesc-desktop kernel: [    1.742913] usb 2-2: config 1 has an invalid interface number: 1 but max is 0
Sep 23 21:23:09 cesc-desktop kernel: [    1.742916] usb 2-2: config 1 has no interface number 0
Sep 23 21:23:09 cesc-desktop kernel: [    1.756997] usb 2-2: configuration #1 chosen from 1 choice
Sep 23 21:23:09 cesc-desktop kernel: [    1.791518] input: 2.4GHz 2way RF Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input5
Sep 23 21:23:09 cesc-desktop kernel: [    1.791707] generic-usb 0003:1BCF:053A.0003: input,hiddev96,hidraw2: USB HID v1.00 Mouse [2.4GHz 2way RF Receiver] on usb-0000:00:1d.0-2/input1
Sep 23 21:23:09 cesc-desktop kernel: [    1.804924] vesafb: cannot reserve video memory at 0xfb000000
Sep 23 21:23:09 cesc-desktop kernel: [    1.804940] vesafb: framebuffer at 0xfb000000, mapped to 0xf9000000, using 512k, total 512k
Sep 23 21:23:09 cesc-desktop kernel: [    1.804942] vesafb: mode is 800x600x8, linelength=800, pages=0
Sep 23 21:23:09 cesc-desktop kernel: [    1.804944] vesafb: scrolling: redraw
Sep 23 21:23:09 cesc-desktop kernel: [    1.804946] vesafb: Pseudocolor: size=0:8:8:8, shift=0:0:0:0
Sep 23 21:23:09 cesc-desktop kernel: [    1.805059] fb1: VESA VGA frame buffer device
Sep 23 21:23:09 cesc-desktop kernel: [    1.842455] EXT4-fs (sda2): mounted filesystem with ordered data mode
Sep 23 21:23:09 cesc-desktop kernel: [    5.840682] usb-storage: device scan complete
Sep 23 21:23:09 cesc-desktop kernel: [    5.841057] scsi 4:0:0:0: Direct-Access     PIXIKA   USB Flash Drive  5.00 PQ: 0 ANSI: 2
Sep 23 21:23:09 cesc-desktop kernel: [    5.841475] sd 4:0:0:0: Attached scsi generic sg2 type 0
Sep 23 21:23:09 cesc-desktop kernel: [    5.842032] sd 4:0:0:0: [sdb] 2009088 512-byte logical blocks: (1.02 GB/981 MiB)
Sep 23 21:23:09 cesc-desktop kernel: [    5.842525] sd 4:0:0:0: [sdb] Write Protect is off
Sep 23 21:23:09 cesc-desktop kernel: [    5.842530] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
Sep 23 21:23:09 cesc-desktop kernel: [    5.842534] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Sep 23 21:23:09 cesc-desktop kernel: [    5.844151] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Sep 23 21:23:09 cesc-desktop kernel: [    5.844156]  sdb: sdb1
Sep 23 21:23:09 cesc-desktop kernel: [    5.846150] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Sep 23 21:23:09 cesc-desktop kernel: [    5.846154] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Sep 23 21:23:09 cesc-desktop kernel: [    8.432286] udev: starting version 151
Sep 23 21:23:09 cesc-desktop kernel: [    8.443771] Adding 2096440k swap on /dev/sda5.  Priority:-1 extents:1 across:2096440k 
Sep 23 21:23:09 cesc-desktop kernel: [    8.485989] lp: driver loaded but no devices found
Sep 23 21:23:09 cesc-desktop kernel: [    8.538741] udev: renamed network interface eth0 to eth3
Sep 23 21:23:09 cesc-desktop kernel: [    8.693214] nvidia: module license 'NVIDIA' taints kernel.
Sep 23 21:23:09 cesc-desktop kernel: [    8.693216] Disabling lock debugging due to kernel taint
Sep 23 21:23:09 cesc-desktop kernel: [    8.714393] type=1505 audit(1316805787.777:2):  operation="profile_load" pid=731 name="/sbin/dhclient3"
Sep 23 21:23:09 cesc-desktop kernel: [    8.714963] type=1505 audit(1316805787.777:3):  operation="profile_load" pid=731 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 23 21:23:09 cesc-desktop kernel: [    8.715277] type=1505 audit(1316805787.777:4):  operation="profile_load" pid=731 name="/usr/lib/connman/scripts/dhclient-script"
Sep 23 21:23:09 cesc-desktop kernel: [    8.716442] type=1505 audit(1316805787.777:5):  operation="profile_replace" pid=722 name="/sbin/dhclient3"
Sep 23 21:23:09 cesc-desktop kernel: [    8.717021] type=1505 audit(1316805787.781:6):  operation="profile_replace" pid=722 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 23 21:23:09 cesc-desktop kernel: [    8.717337] type=1505 audit(1316805787.781:7):  operation="profile_replace" pid=722 name="/usr/lib/connman/scripts/dhclient-script"
Sep 23 21:23:09 cesc-desktop kernel: [    9.599828] parport_pc 00:06: reported by Plug and Play ACPI
Sep 23 21:23:09 cesc-desktop kernel: [    9.599870] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Sep 23 21:23:09 cesc-desktop kernel: [    9.614273] ppdev: user-space parallel port driver
Sep 23 21:23:09 cesc-desktop kernel: [    9.682145] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 23 21:23:09 cesc-desktop kernel: [    9.682169] HDA Intel 0000:00:1b.0: setting latency timer to 64
Sep 23 21:23:09 cesc-desktop kernel: [    9.824397] intel_rng: FWH not detected
Sep 23 21:23:09 cesc-desktop kernel: [    9.824560] lp0: using parport0 (interrupt-driven).
Sep 23 21:23:09 cesc-desktop kernel: [    9.825427] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 23 21:23:09 cesc-desktop kernel: [    9.825435] nvidia 0000:01:00.0: setting latency timer to 64
Sep 23 21:23:09 cesc-desktop kernel: [    9.825439] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Sep 23 21:23:09 cesc-desktop kernel: [    9.825856] NVRM: loading NVIDIA UNIX x86 Kernel Module  280.13  Wed Jul 27 16:55:43 PDT 2011
Sep 23 21:23:09 cesc-desktop kernel: [   10.341018] EXT4-fs (sda6): mounted filesystem with ordered data mode
Sep 23 21:23:09 cesc-desktop kernel: [   10.457582] EXT4-fs (sda7): mounted filesystem with ordered data mode
Sep 23 21:23:09 cesc-desktop kernel: [   10.542850] type=1505 audit(1316805789.604:8):  operation="profile_replace" pid=1066 name="/sbin/dhclient3"
Sep 23 21:23:09 cesc-desktop kernel: [   10.543358]   alloc irq_desc for 27 on node -1
Sep 23 21:23:09 cesc-desktop kernel: [   10.543361]   alloc kstat_irqs on node -1
Sep 23 21:23:09 cesc-desktop kernel: [   10.543374] ATL1E 0000:02:00.0: irq 27 for MSI/MSI-X
Sep 23 21:23:09 cesc-desktop kernel: [   10.543442] type=1505 audit(1316805789.604:9):  operation="profile_replace" pid=1066 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 23 21:23:09 cesc-desktop kernel: [   10.543559] ADDRCONF(NETDEV_UP): eth3: link is not ready
Sep 23 21:23:09 cesc-desktop kernel: [   10.543791] type=1505 audit(1316805789.604:10):  operation="profile_replace" pid=1066 name="/usr/lib/connman/scripts/dhclient-script"
Sep 23 21:23:09 cesc-desktop kernel: [   10.544563] ATL1E 0000:02:00.0: ATL1E: eth3 NIC Link is Up<100 Mbps Full Duplex>
Sep 23 21:23:09 cesc-desktop kernel: [   10.544650] ADDRCONF(NETDEV_CHANGE): eth3: link becomes ready
Sep 23 21:23:09 cesc-desktop kernel: [   10.546674] type=1505 audit(1316805789.608:11):  operation="profile_load" pid=1067 name="/usr/bin/evince"
Sep 23 21:23:10 cesc-desktop kernel: [   10.962078] vboxdrv: Found 2 processor cores.
Sep 23 21:23:10 cesc-desktop kernel: [   10.962776] vboxdrv: fAsync=0 offMin=0x1db offMax=0x76c
Sep 23 21:23:10 cesc-desktop kernel: [   10.963427] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Sep 23 21:23:10 cesc-desktop kernel: [   10.963429] vboxdrv: Successfully loaded version 4.1.2 (interface 0x00190000).
Sep 23 21:23:10 cesc-desktop kernel: [   11.177320] vboxpci: IOMMU not found (not compiled)
Sep 23 21:23:14 cesc-desktop kernel: [   15.930879] __ratelimit: 22 callbacks suppressed
Sep 23 21:23:14 cesc-desktop kernel: [   15.930883] gdm-simple-slav[1933]: segfault at 2d1e0733 ip 00c17a4f sp bfb99e5c error 4 in libc-2.11.1.so[ba4000+153000]
Sep 23 21:23:17 cesc-desktop kernel: [   18.304140] gdm-simple-slav[2063]: segfault at 2ce693a3 ip 00af9a4f sp bf822acc error 4 in libc-2.11.1.so[a86000+153000]
Sep 23 21:23:20 cesc-desktop kernel: [   20.726814] gdm-simple-slav[2095]: segfault at 2d0f0263 ip 00577a4f sp bfaa998c error 4 in libc-2.11.1.so[504000+153000]
Sep 23 21:23:20 cesc-desktop kernel: [   20.736509] eth3: no IPv6 routers present
Sep 23 21:23:22 cesc-desktop kernel: [   23.143179] gdm-simple-slav[2126]: segfault at 2cebf083 ip 00bc2a4f sp bf8787ac error 4 in libc-2.11.1.so[b4f000+153000]
Sep 23 21:23:25 cesc-desktop kernel: [   25.570970] gdm-simple-slav[2157]: segfault at 2d3a1823 ip 00cb7a4f sp bfd5af4c error 4 in libc-2.11.1.so[c44000+153000]
Sep 23 21:24:13 cesc-desktop kernel: [   73.911482] CPU0 attaching NULL sched-domain.
Sep 23 21:24:13 cesc-desktop kernel: [   73.911487] CPU1 attaching NULL sched-domain.
Sep 23 21:24:13 cesc-desktop kernel: [   73.932588] CPU0 attaching sched-domain:
Sep 23 21:24:13 cesc-desktop kernel: [   73.932593]  domain 0: span 0-1 level MC
Sep 23 21:24:13 cesc-desktop kernel: [   73.932597]   groups: 0 1
Sep 23 21:24:13 cesc-desktop kernel: [   73.932605] CPU1 attaching sched-domain:
Sep 23 21:24:13 cesc-desktop kernel: [   73.932608]  domain 0: span 0-1 level MC
Sep 23 21:24:13 cesc-desktop kernel: [   73.932612]   groups: 1 0
Sep 23 21:24:51 cesc-desktop kernel: [  111.698299] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
Sep 23 21:24:51 cesc-desktop kernel: [  111.703255] padlock: VIA PadLock not detected.
```
Oh, and I almost forgot about
```
sudo lshw
```
which returns
```
ubuntu                    
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=80C33299-8DFE-D511-AEB0-00248C72E0D9
  *-core
       description: Motherboard
       product: P5KPL-CM
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: x.xx
       serial: MS1C93B20102594
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0602 (02/24/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: Socket 775
          size: 1200MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 32
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM A1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM B1
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:fa000000-feafffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G96 [GeForce 9400 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff(prefetchable) memory:fa000000-fbffffff ioport:dc00(size=128) memory:fea80000-feafffff(prefetchable)
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:f9ffc000-f9ffffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:1000(size=4096) memory:80000000-801fffff memory:80200000-803fffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:e000(size=4096) memory:feb00000-febfffff memory:80400000-805fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth3
                version: b0
                serial: 00:24:8c:72:e0:d9
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.36 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:27 memory:febc0000-febfffff ioport:ec00(size=128)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c480(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c800(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c880(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:cc00(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f9ffbc00-f9ffbfff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:c400(size=8) ioport:c080(size=4) ioport:c000(size=8) ioport:bc00(size=4) ioport:b880(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GH22NS30
                vendor: HL-DT-ST
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: ST3500410AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sda
                version: CC34
                serial: 6VM02E1W
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000122ba
              *-volume:0
                   description: Extended partition
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sda1
                   size: 424GiB
                   capacity: 424GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2047MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 49GiB
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 249GiB
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 122GiB
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sda2
                   version: 1.0
                   serial: 62630659-c97f-4dd5-af77-fec8b769bc24
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-08-17 17:18:00 filesystem=ext4 lastmountpoint=/I&#65533;h&#448;&#65533;&#65533;xV&#65533;&#65533;&#65533;&#65533;t&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;/&#65533;h&#65533;&#65533;&#65533;~1!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;-&#65533; modified=2011-09-21 22:24:00 mounted=2011-09-23 20:33:23 state=clean
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@3:0.0.0,3
                   logical name: /dev/sda3
                   version: 1.0
                   serial: caf9192d-b3af-405d-b0eb-88cefa4caf68
                   size: 20GiB
                   capacity: 20GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2009-07-04 11:59:02 filesystem=ext4 modified=2011-09-16 09:56:05 mounted=2011-09-16 08:23:05 state=clean
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi
          physical id: 2
          bus info: usb@1:5
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 981MiB (1028MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=000049e8
           *-volume
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /cdrom
                logical name: /casper-rw-backing
                version: FAT32
                serial: 9aa8-65f7
                size: 980MiB
                capacity: 980MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted


```

---

### Post by wildmanne39 on 2011-09-23
Hi, I see 2 video card drivers loaded, do you have an intel video card? I did not see an intel card in the information you posted but there is an intel driver loaded and it may be causing issues.

I recommend black listing it if you do not have an intel card, and we can go from there.
```
sudo su
echo "blacklist intel_agp" >> /etc/modprobe.d/blacklist.conf
exit
```then restart your computer.
Thank you

---

### Post by WayKoolJr on 2011-09-23
I can't remember where I stumbled on to the error that gave me the clue,  but have you tried bumping vmalloc in grub?  I had this exact same  symptom with nvidia and I added vmalloc=256M at the end of  GRUB_CMDLINE_LINUX_DEFAULT and it came right up.


GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=256M"
update-grub
reboot

---

### Post by castawaybcn on 2011-09-24
hi wildmanne39. I don't think I have an intel card, but I blacklisted it anyway as you suggested, but I still have the same issue after reboot.
Thanks

---

### Post by castawaybcn on 2011-09-24
Hi WayKoolJr,
my grub line is:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap"
```
I changed it to what you suggested and the only difference it made was an uglier booting animation. GDM is still not showing

Thanks.

---

### Post by realzippy on 2011-09-24
A few 2 cents to this interesting thread:
1.
Your grub command line is correct.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap"
```

However,if you edited it for testing purposes in the past,have you run
```
sudo update-grub
``` afterwards?
......................................................................
2.
```
Unable to load file '/etc/gdm/custom.conf'
```
..appears pretty often in your logs...

What about creating this missed file (eg. with "nano" ) ?
It should contain eg:
```
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=false
TimedLogin=yourusername
AutomaticLogin=yourusername
TimedLoginDelay=30
DefaultSession=gnome
```

(edit yourusername)
If still no success,you may create another user,to get a "vanilla" gdm:
```
sudo adduser test
```

..............................................

Sorry if I over-read it,but are you able to log in in recovery mode ?

---

### Post by castawaybcn on 2011-09-24
Hi realzippy,

Welcome to this thread, and thanks for giving a hand.

1.Yep, I did run ```
sudo uptdate-grub
``` after editing my /etc/default/grub

2. I am pretty sure /etc/gdm/custom.conf should not be necessary as I don't have it in the computer I am using at the moment (not the one with the problem) and I believe all the automatic login stuff is rather incompatible with an encrypted home partition, which is my case.
But hey, I tried generating the file manually as you suggested and... still no gdm.

I also added a new user. Same result: no gdm, no tty1 nor tty7.

What puzzles me (among other things) is that when I try stopping gdm ```
sudo gdm-stop
``` but it may not be running as I get:```
/var/run/gdm.pid doesn't exist, perhaps GDM isn't running
```
and then when try ```
sudo gdm start
``` it gives me the no seat-id found and 4 GDMDisplay warnings/errors like those explained in the [1st]("http://ubuntuforums.org/showpost.php?p=11279159&postcount=1") post of this thread and that also show up in the logs posted in [#28]("http://ubuntuforums.org/showpost.php?p=11279159&postcount=28")

When I boot in recovery I am presented with the Recovery Menu, from which I pick failsafeX just to be shown the error:
```
(EE) Failed to load module "nouveau" (module does not exist, 0)
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
```

Do you think I should install any nouveau related packages?

Then from the next set of options I have tried:
Run Ubuntu in low-graphics mode for just one session, which takes me back to the flashing screen where gdm should be, then manually back to tty2 with the failsafe menu options again.
Reconfigure graphics, with Use default (generic) configuration. Which does not seem to do anything, and Create new configuration which seems to do nothing either.

---

### Post by realzippy on 2011-09-24
Sorry,
I didn't notice your /home is encrypted.
Agree,creating file makes no sense then.

Not sure about reinstallling nouveau,but might do no harm:
```
sudo nvidia-settings --uninstall
sudo apt-get remove --purge nvidia*
sudo apt-get remove --purge xserver-xorg-video-nv xserver-xorg-video-nouveau
sudo apt-get install nvidia-common
sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```
source:
[https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching)


Edit:
Btw,isn't the command to stop/start gdm:

```
sudo service gdm stop
```
instead of
```
sudo gdm stop
``` ?

---

### Post by wildmanne39 on 2011-09-24
Hi realzippy, thank you for helping out, you know more about nvidia issues and xorg then I do these days, I spend most of my time in networking these days.

---

### Post by realzippy on 2011-09-24
Hi wildmanne39,
hope that does not mean you are out of this thread,
I have no idea what's wrong here,also I missed totally that OP uses encrypted home,better I lay back and observe thread ...

---

### Post by castawaybcn on 2011-09-24
> **realzippy said:**
> Sorry,
I didn't notice your /home is encrypted.
Agree,creating file makes no sense then.

Not sure about reinstallling nouveau,but might do no harm:
```
sudo nvidia-settings --uninstall
sudo apt-get remove --purge nvidia*
sudo apt-get remove --purge xserver-xorg-video-nv xserver-xorg-video-nouveau
sudo apt-get install nvidia-common
sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```
source:
[https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching)


Edit:
Btw,isn't the command to stop/start gdm:

```
sudo service gdm stop
```
instead of
```
sudo gdm stop
``` ?

Reinstall as suggested except for ```
sudo nvidia-settings --uninstall
``` as --uninstall does not seem to be a recognized option.

Still no gdm, flashing is slightly different now though: a few random lines show up, but without forming any recognizable shape. On the other hand, restarting in recovery mode no longer works and, while in recovery, I can't even switch to a different terminal.

Aaaaaaaaaaaahhrgh! Sorry about that, I just had to say it...

btw```
sudo service gdm stop
``` returns ```
stop: Unknow instance: 
```

Side note: easystroke looks amazing, I'll try it out as soon as I get my system back

---

### Post by realzippy on 2011-09-24
..what does /var/log/Xorg.0.log say?

......................................

```
stop: Unknown instance:
```

..because it was never started?

guess

```
sudo service gdm start
```

gives the known errors....?

---

### Post by castawaybcn on 2011-09-24
/var/log/Xorg.0.log says a lot of things, but I couldn't see anything video or gdm related, here it is:
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux cesc-desktop 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=62630659-c97f-4dd5-af77-fec8b769bc24 ro quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap
Build Date: 08 March 2011  08:22:50AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 24 17:45:34 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f1e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0641:1043:82d4 nVidia Corporation G96 [GeForce 9400 GT] rev 161, Mem @ 0xfd000000/16777216, 0xe0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched nouveau as autoconfigured driver 0
(==) Matched nv as autoconfigured driver 1
(==) Matched vesa as autoconfigured driver 2
(==) Matched fbdev as autoconfigured driver 3
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.15
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "nv"
(WW) Warning, couldn't open module nv
(II) UnloadModule: "nv"
(EE) Failed to load module "nv" (module does not exist, 0)
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
	RIVA TNT    (NV04)
	RIVA TNT2   (NV05)
	GeForce 256 (NV10)
	GeForce 2   (NV11, NV15)
	GeForce 4MX (NV17, NV18)
	GeForce 3   (NV20)
	GeForce 4Ti (NV25, NV28)
	GeForce FX  (NV3x)
	GeForce 6   (NV4x)
	GeForce 7   (G7x)
	GeForce 8   (G8x)
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] nouveau interface version: 0.0.15
(EE) [drm] KMS not enabled
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 14336 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 98.148
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G96 Board - 07290040
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): VESA VBE PanelID read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x33f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x33f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x33f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 10e (320x200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10f (320x200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 111 (640x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 112 (640x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 114 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 115 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 117 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 118 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 11a (1280x1024)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 11b (1280x1024)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 62
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 62
	LinNumberOfImagePages: 62
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 132 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 133 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 135 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 136 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 13d (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 13e (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 145 (1600x1200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 146 (1600x1200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 14a (1600x1200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009280
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 224 64KB banks (14336kB)
(II) VESA(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): <default monitor>: Using hsync range of 31.50-37.90 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1600x1200" (hsync out of range)
(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 14336 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 98.148
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G96 Board - 07290040
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(II) VESA(0): virtual address = 0xb6925000,
	physical address = 0xfb000000, size = 14680064
(II) VESA(0): Setting up VESA Mode 0x115 (800x600)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "es"
(**) Option "xkb_variant" "cat"
(II) XKB: reuse xkmfile /var/lib/xkb/server-0AFA66265020E293BF499122FFE9AD8C16A17D3B.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "es"
(**) Option "xkb_variant" "cat"
(II) config/udev: Adding input device   USB Keyboard (/dev/input/event3)
(**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event3"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "es"
(**) Option "xkb_variant" "cat"
(II) config/udev: Adding input device   USB Keyboard (/dev/input/event4)
(**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event4"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "es"
(**) Option "xkb_variant" "cat"
(II) config/udev: Adding input device 2.4GHz 2way RF Receiver (/dev/input/event5)
(**) 2.4GHz 2way RF Receiver: Applying InputClass "evdev pointer catchall"
(**) 2.4GHz 2way RF Receiver: Applying InputClass "evdev keyboard catchall"
(**) 2.4GHz 2way RF Receiver: always reports core events
(**) 2.4GHz 2way RF Receiver: Device: "/dev/input/event5"
(II) 2.4GHz 2way RF Receiver: Found 12 mouse buttons
(II) 2.4GHz 2way RF Receiver: Found scroll wheel(s)
(II) 2.4GHz 2way RF Receiver: Found relative axes
(II) 2.4GHz 2way RF Receiver: Found x and y relative axes
(II) 2.4GHz 2way RF Receiver: Found absolute axes
(II) 2.4GHz 2way RF Receiver: Found keys
(II) 2.4GHz 2way RF Receiver: Configuring as mouse
(II) 2.4GHz 2way RF Receiver: Configuring as keyboard
(**) 2.4GHz 2way RF Receiver: YAxisMapping: buttons 4 and 5
(**) 2.4GHz 2way RF Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "2.4GHz 2way RF Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "es"
(**) Option "xkb_variant" "cat"
(II) 2.4GHz 2way RF Receiver: initialized for relative axes.
(WW) 2.4GHz 2way RF Receiver: ignoring absolute axes.
(II) config/udev: Adding input device 2.4GHz 2way RF Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) Open ACPI successful (/var/run/acpid.socket)
(II) VESA(0): Setting up VESA Mode 0x115 (800x600)
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II)   USB Keyboard: Device reopened after 1 attempts.
(II)   USB Keyboard: Device reopened after 1 attempts.
(II) 2.4GHz 2way RF Receiver: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
```
On the other hand
```
sudo service gdm start
```
says
```
gdm start/running, process 3495
```
and going back to tty7 or tty1 brings no gdm but same old black screen instead, am I missing something?

---

### Post by realzippy on 2011-09-24
```
(II) [drm] nouveau interface version: 0.0.15
(EE) [drm] KMS not enabled
(WW) Falling back to old probe method for fbdev
```

according to log you have still "nomodeset" activated,
so this might cause the fallback to fbdev/VESA .....
You should undo this.
On the other hand,VESA also cannot start gdm.....

Btw,what happens when running
```
startx
```   at tty ?

---

### Post by wildmanne39 on 2011-09-24
Hi, I just finished reading the x.org log and I noticed the same thing as realzippy, but I do not know what to do about it if you can not boot into recovery mode.

Do you have an older kernel that you can boot into?
Thank you

---

### Post by castawaybcn on 2011-09-25
I removed nomodeset, the result is no flashing but some random coloured lines where gdm should be and no access to any other terminals.
```
startx
```
brings me this:
```
xauth: /home/francesc/.Xauthority not writable, changes will be ignored
xauth: error in locking authority file /home/francesc/.Xauthority
xauth: error in locking authority file /home/francesc/.Xauthority
xauth: error in locking authority file /home/francesc/.Xauthority

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again

Please consult the The X.Org Foundation support at http://wiki.x.org for help.

ddxSigGiveUp: Closing log
No protocol specidifed
giving up.
xinit:  Resource temporarily unavailable (errnno 11): unable to connect to X server
xinit: No such process (errno 3): Server error.
xauth: error in locking authority file /home/francesc/.Xauthority
```

And if I remove the lock file and try starting x again:

```

xauth: error in locking authority file /home/francesc/.Xauthority
xauth: error in locking authority file /home/francesc/.Xauthority
xauth: error in locking authority file /home/francesc/.Xauthority
xauth: error in locking authority file /home/francesc/.Xauthority

_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the The X.Org Foundation support at http://wiki.x.org for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

ddxSigGiveUp: Closing log
No protocol specidifed
giving up.
xinit:  Resource temporarily unavailable (errnno 11): unable to connect to X server
xinit: No such process (errno 3): Server error.
xauth: error in locking authority file /home/francesc/.Xauthority
```

How can I make sure no x server is running? I tried running
```
sudo init 1
```
which seems to do the trick and brings me to the recovery menu, but I can't get any either to get failsafeX or to reconfigure graphics card to work. Actually, after reconfiguring I click on resume normal boot but it gets stuck just after the message "Checking battery state"

Here's /var/log/Xorg.0.log btw:
```
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
```

I have also tried running with older kernels, but that didn't seem to make any difference. Will try some more just to be sure.

Thanks to both of you for your time.

---

### Post by wildmanne39 on 2011-09-25
Hi, I believe you have tried a version of this already but I would still try with all the changes you have made and if it does not work I am afraid I am at a loss.
```
sudo rm /etc/X11/xorg.conf
```
```
sudo dpkg-reconfigure xserver-xorg
```
Thank you

---

### Post by realzippy on 2011-09-26
Hm,according to Xorg.0.log there is no xorg.conf in the moment.
If *dpkg-reconfigure xserver-xorg* doesn't help either,I
would like to come back to that "nomodeset"....
I mean,where does it come from?
Did you ever run a NVIDIA-linux-driver.run script attempting to install their driver manually?
If so,you might try to run same  .run script with the --uninstall option.
........................................................................

You could try a basic xorg.conf calling the VESA driver (nomodeset does not disturb):

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

..that should normally bring you to login,reduced resolution....

---

### Post by castawaybcn on 2011-09-27
*dpkg-reconfigure xserver-xorg* did not work, manually recreating the file did not work either, and adding the *--uninstall* parameter to the nvidia script did produce a bunch of errors probably because I had already uninstalled the driver manually. I fear the only solution right now is a reinstall, probably tomorrow.

Thanks a lot for your help guys, I really mean it. Even though we did not seem to find out what was going on I have learned quite a fair deal with the whole process.

---

### Post by wildmanne39 on 2011-09-27
Hi, I to suspect that is probably the best option a this time.

---


---
title: "Ubuntu will not start after attempt upgrade to  11.10"
date: 2011-10-14
forum: General Help
---

### Post by Del64 on 2011-10-14
I left system downloading the files for Ubuntu 11.10 from 11.04. The system said it required a reboot, so I did so. I am dual booting when it restarted I used windows for a bit figuring the updates will continue next time I am on Ubuntu. I go back to Ubuntu and I receive this screen attached (with a nice reflection of my self). It stays on the screen. 

I do have access to the root in recovery but I cannot update, upgrade, or repair broken packages in repair mode. It states it has cant connect to the sources. 

Any help will be greatly appreciated!

---

### Post by henslok on 2011-10-14
Same problem here, first it shows there is a problem with network connection then it says it will wait another 60sec finally screen goes blank... and nothing... I managed to go on tty1 and remove ~/.gnome, ~./gnome2, ~/.compiz and ~/.config and still no joy. :( Now I'm getting desperate as it (was) my server!

---

### Post by chickenSandwich on 2011-10-14
Greetings,
   I am having a problem similar to that described by Henslock.  After the upgrade from 11.04 to 11.10 had finally completed, I restarted.  The first boot up took longer than normal, and during the ubuntu loading splash screen I received the same message that Henslock stated:  Waiting for network configuration.  Followed by about a minute wait and a second message: Waiting another 60 seconds for network configuration.
   The first boot finally brought me to a login screen, and I logged in successfully.  After installing adobe flash for firefox I rebooted.   I received the same messages described above, but this time a blank screen followed and then nothing.  I rebooted into the recovery console.  Ran fsck and attempted to repair broken packages.  I dropped to a network root prompt, but could neither connect to the internet nor get any information about my network adapter.
   I ran apt-get autoremove to let the system clean itself up. 
I will advise on my progress.  If anyone has any information, we would be grateful. 

ubuntu 11.10 32 bit
Thanks,
chickenSandwich

---

### Post by effenberg0x0 on 2011-10-14
Hi, I would like to understand what exactly happened there. Maybe we can fix things.


[LIST]
[*]What was the method you used to upgrade from 11.04 to 11.10? (cd, usb, apt-get, dist-upgrade, do-release-upgrade, update-manager, etc)
[*]Did you get any different message/warning/error during the upgrade?
[*]Were you connected via ethernet cable, WIfi, other method (3G, etc)?
[/LIST]

Can you post your log files? I'm specially interested in /var/log/Xorg.0.log, /var/log/syslog and /var/log/dmesg right after a reboot.
**EDIT: add /etc/apt/sources.list too.**

You can run something like this at a VT (Ctrl+Alt+F2):

```
cd
mkdir logs && cd logs
sudo cat /var/log/dmesg > ~/logs/dmesg.txt
sudo cat /var/log/syslog > ~/logs/syslog.txt
sudo cat /var/log/Xorg.0.log > ~/logs/xorg.txt
sudo cat /etc/apt/sources.list > ~/logs/sources.txt
sudo -s
cd /etc/apt/ 
for SOURCE in `ls`; do echo $SOURCE >> ~/logs/sources.list.d.txt && cat $SOURCE >> ~/logs/sources.list.d.txt; done
tar -cvzf your_nickname.tar.gz dmesg.txt syslog.txt xorg.txt sources.txt sources.list.d.txt
```Then if you have no Internet, you could save it to a USB

Maybe the USB wont automount (check if it does on /media and /mnt). In this case, to manually mount a USB:
```
sudo fdisk -l (check the Device (/dev/sdb1, etc) and if your USB is FAT32 or ntfs)
sudo mkdir /media/myusb
```For FAT
```
sudo mount -t vfat /dev/sdb1 /media/myusb -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
```For NTFS
```
sudo mount -t ntfs-3g /dev/sdb1 /media/myusb
```Then copy the files to usb:
```
sudo cp ~/logs/your_nickname.tar.gz /media/myusb

```You can also use a LiveCD / LiveUSB, an older/other Distro, Windows (if its set to see the Linux partition), any other method, etc to access the your_nickname.tar.gz file in your home folder and post it here as an attachment. 

Thanks in advance.

Effenberg

---

### Post by bartman789 on 2011-10-14
I'm having a similar problem here.

I was on Ubuntu Studio 11.04, upgraded to 11.10 via the upgrade prompt. Went through the upgrade process without any issues - only warnings were about overwriting .conf files that I had modified (for cups).

On restarting after the upgrade, the system displays the Ubuntu studio splash screen and... stops. No login prompt, no HDD activity.

The system is responsive - pressing the power button causes a normal shutdown, and Ctrl+Alt+Del reboots (thought that was a Windows only thing, but anyway).

So it looks like the login handler (LightDM?) is not kicking in or something of that sort. Unfortunately, I can't get to a console (tried Ctrl+Alt+F1, but no luck), so I can't see what's going on.

Any suggestions, folks? Thanks all!

B.

---

### Post by Gossamer2 on 2011-10-14
Same boat here.

I logged in to the desktop and was prompted to upgrade to 11.10.

I was also prompted for a few configuration files like Samba etc.

The system actually rebooted properly a couple of times, but always got stuck on the boot logo. If you wait long enough, you can get a terminal on Ctrl-Alt-F1, but there was no networking or anything. Found the command "dhclient eth0" which brought that up, but I'm still seriously stuck.

There are all kinds of errors in DMESG like:

init: modemanager: main process (###) terminating with status 255
Then it respawns and fails again.

Also,
init: network-manager main process (###) killed by ABRT signal

Please help! Starting to lose hair again. ](*,)

---

### Post by effenberg0x0 on 2011-10-14
At this point there are just too many possibilities. 

If you have Internet in the console prompt and know your VGA you can try to reinstall your video driver.

Sometimes all it takes is removing xorg.conf
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup && sudo service lightdm start

```

In others, you have to reinstall compiz, unity, xorg.
Others need to fix TCP/IP setup manually and try to fix broken dependencies.

Without looking at proper logs, everything is a wild guess.

Effenberg

---

### Post by effenberg0x0 on 2011-10-14
Guys, I need your help to check if you fit into a bug that has been reported. If so, we can easily fix your problem.

At a VT, try the following command:

```
sudo nano /etc/X11/default-display-manager

```

It must have only one line like this:
```
/usr/sbin/lightdm
```

If it says only "lightdm", adjust to match the line above, press Ctrl+X, Y, <enter> to save the file and reboot.

If you get again to console, run
```

sudo killall -s KILL /usb/bin/X
sudo service gdm stop
sudo service lightdm stop
sudo service lightdm start

```

Effenberg

---

### Post by Gossamer2 on 2011-10-14
Nope. Mind had /usr/sbin/lightdm

Tried the commands and just get a black screen, shortly followed by the monitor powering off. Had to do a Ctrl-Alt-Del.

---

### Post by effenberg0x0 on 2011-10-14
> **Gossamer2 said:**
> Nope. Mind had /usr/sbin/lightdm

Tried the commands and just get a black screen, shortly followed by the monitor powering off. Had to do a Ctrl-Alt-Del.

If your monitor went out of sync, this may be good for us. It means you have the conditions to start a GUI session, but probably have wrong display settings. 

Tell me what is the output of:
```
cat /etc/default/grub | grep CMDLINE

```

And try this:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.con.backup
sudo lightdm stop
sudo lightdm start


```Effenberg

---

### Post by Gossamer2 on 2011-10-15
There was no xorg.conf file there.

I've managed to get the logs on to a USB stick. I can send those if you like.

BTW: I have checked my package status with aptitude, and everything is ok. Also, another thing I noticed is that when I log in to the terminal, there is a message saying "*** System restart required ***", but I'm restarted numerous times now.

---

### Post by effenberg0x0 on 2011-10-15
Great,, attach the logs. Then we can finally see whats happening.

Thanks

---

### Post by Gossamer2 on 2011-10-15
Oops... Forgot to add the output to your query.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX = ""

I have sent a private message with the link to the logs.

---

### Post by Gossamer2 on 2011-10-15
effenberg0x0, thank you so much for your help. You fixed my problem and I'm back up and running. You're a lifesaver!

---

### Post by CPUUnlimited on 2011-10-15
OK, fine and dandy, can you share what he did to help you with the rest of us that can no longer boot since trying to update to 11.10?

I have to select "previous version" from my boot menu then pick the top one which is 11.10.  If I try to just select 11.10 from the first menu I get the same hang issue that the rest of you are having.


ERRG!

---

### Post by bartman789 on 2011-10-15
Nope. Same as Gossamer2 - mine had /usr/sbin/lightdm too.

One thing I'm noticing though - for all of the stop service and mv commands, I get the following error - "Can't open /var/lib/sudo/bart/console: Read-only file system.

Heads up - I'm booting in Recovery Mode, dropping to a root console, and then logging in with my primary ID (not running as root).

Also, the grub details you requested are:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Thanks for the help!

---

### Post by Del64 on 2011-10-16
Is there an easier way to uninstall those components like compiz or whatever? Rather than going through the files and manually uninstalling them? I already uninstalled avira.

I am fairly new to linux, I just started this summer and I have not had much time to learn about the terminal and its potential.

---

### Post by effenberg0x0 on 2011-10-16
@bartman

You have to start your PC in recovery mode. To do that, hold shift while it boots until you see Grub menu. The first option in Grub is the default one. The second is the recovery. It will eventually ask what you want in recovery and you want to drop to a root shell prompt.

In the recovery, run these commands:

```
lspci | grep -i vga
```Take note if it answers you nvidia, ati or intel.

Run the command "mount" and see if your linux unit is market as RW or RO.

Run these commands now, they're to make sure the unit is read-write. Otherwise, fixes are impossible.
```
if [ $(mount | grep `sudo fdisk -l | grep -i linux$ | awk '{print $1}'` | grep "(rw" | wc -l) -eq 1 ]; then FSSTATUS=rw; else FSSTATUS=ro; fi

FSTYPE=$(mount | grep `sudo fdisk -l | grep -i linux$ | awk '{print $1}'` | grep "(rw" | awk '{print $5}')

if [ $FSSTATUS == "ro" ]; then 
ROOTSDA=$(mount | grep `sudo fdisk -l | grep -i linux$ | awk '{print $1}'` | awk '{ print $1}')
sudo mount -f -o remount,rw -t $FSTYPE $ROOTSDA

```Run the command "mount" and see if your linux unit is market as RW or RO. It should be Read-Write at this point.

Check for Internet access. Take note if it is OK or Not.```

if [ `ping -c 1 www.ubuntu.com | grep -i "1 received" | wc -l` -ne 1 ]; then echo "No Internet"; else echo "Internet OK"; fi

```Now the fixes:
```
sudo killall -s KILL /usr/bin/X
sudo service lightdm stop
sudo service gdm stop
sudo killall -s KILL /usr/sbin/lightdm
sudo mkdir /run
sudo mkdir /run/lock
sudo  mv /var/run/* /run
sudo  mv /var/lock/* /run/lock
sudo rm -rf /var/run
sudo rm -rf /var/lock
sudo ln -s /run /var/run
sudo ln -s /run/lock /var/lock
sudo apt-get remove --purge --force-yes gdm
sudo apt-get update && sudo apt-get install --reinstall lightdm
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo gconftool-2 --recursive-unset /apps/compiz-1
sudo gconftool-2 --recursive-unset /apps/compizconfig-1
sudo mv ~/.config/compiz-1/compizconfig ~/.config/compiz-1/compizconfig.old
sudo mv ~/.config/compiz-1 ~/.config/compiz.old
sudo mv ~/.compiz-1 ~/.compiz-1.old
sudo mv ~/.cache/compizconfig-1 ~/.cache/compizconfig-1.old
if [ ! -f /etc/lightdm/lightdm.conf ]; then sudo touch /etc/lightdm/lightdm.conf
echo -e "[SeatDefaults]\r\nuser-session=ubuntu\r\ngreeter-session=unity-greeter" | sudo tee /etc/lightdm/lightdm.conf
if [ ! -f /etc/X11/default-display-manager ]; then sudo touch /etc/X11/default-display-manager
echo -e "/usr/sbin/lightdm" | sudo tee /etc/X11/default-display-manager
sudo sed -i s'/quiet//g' /etc/default/grub
sudo sed -i s'/splash//g' /etc/default/grub
sudo update-grub
sudo reboot now

```The PC will boot, let it do it. If still you're stuck at console (no lightdm), you might have to reinstall video drivers.

If you have Intel VGA, it should be simple:
```
sudo apt-get update
sudo apt-get install --reinstall --fix-broken --allow-unauthenticated xserver-xorg-video-intel
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo reboot now

```For Nvidia, complete instructions are here:
[http://ubuntuforums.org/showthread.php?t=1857588&highlight=effenberg+nvidia](http://ubuntuforums.org/showthread.php?t=1857588&highlight=effenberg+nvidia) Post #5

For ATI, see instructions here:
[http://ubuntuforums.org/showthread.php?p=11293922#post11293922](http://ubuntuforums.org/showthread.php?p=11293922#post11293922) Post #27

Regards,
Effenberg

---

### Post by killerbng on 2011-10-16
I just got this problem too. upgraded from 11.04 to 11.10 and got the network config crap and then it booted but very slowly and teh system was sliggish. 3 reboots later now its just a black screen...I have the logged in a tar.gz but I dont have a usb stick as I have no need for 1 so im trying to figure out a way to upload em :/ this sucks so much, never going to upgrade this comp to 11.10 lol

---

### Post by Del64 on 2011-10-17
I have tried the fix from effenbeg0x0 and only half the code ran successfully  everything with compiz and remaking the directories did not work. I received a different loading screen but it still stopped at "checking battery state.." After rebooting and updating it again I received the same screen as shown in the attachment.

---

### Post by pablomo on 2011-10-19
I had a very similar problem (nvidia + 11.10 upgrade + twinview), Unity crashing on login:

 [   70.739741] compiz[2658]: segfault at 0 ip b59c40e0 sp bfa37b3c error 4 in libnvidia-glcore.so.280.13[b4719000+18a0000]
[2503]: WARNING: App 'compiz.desktop' respawning too quickly
[2503]: WARNING: Application 'compiz.desktop' killed by signal
[2503]: WARNING: App 'compiz.desktop' respawning too quickly

I see several people are having the same issue on Ubuntu and others

The fixes above from [effenberg]("http://ubuntuforums.org/member.php?u=260143") seem to have cured it for the moment. Does this mean it is not a good idea to have any compiz advanced settings (e.g. wobbly windows)?

---

### Post by sublimeowl on 2011-10-19
I can start X bu issuing ctrl-alt-F1 and logging on the console. then type startx and the desktop will load. But this is not a solution. Just something to unstuck.

I also have a dependency problem that I'm trying to fix. I think it's related since it just do a partial upgrade. I'll update this thread once I get more info

---

### Post by Del64 on 2011-10-19
I just reformatted the pc and installed 10.10 and now I get a black screen on boot up with just my backlight on.

---

### Post by killerbng on 2011-10-19
could some1 link to the real ATI reconfig the 1 posted for post 27 on that ink is for nvidia....also..how teh hell do u apt0get when the network is screwed up from the update as well....not sure how effen expects us to apt-get with this bugged upgrade :(


edit...BTW I tried the startx way through crtl alt f1 and I get errors so I guess that would fix that but what do I do to fix the net? :/ I really wish I didnt upgrade yet :( forced to use windows lol

---

### Post by killerbng on 2011-10-21
where is the offical bug fix for this :/ major freakign bug and its still there? :( come on now ubuntu even shitsoft would of fixxed a major bug liek this by now lol

---

### Post by techvish81 on 2011-10-21
[http://ubuntuforums.org/showthread.php?t=1866512](http://ubuntuforums.org/showthread.php?t=1866512)

---

### Post by itsing on 2011-12-01
Anyone has any solution for this problem yet?? Please share :D

---

### Post by Vipsu on 2012-02-25
> **effenberg0x0 said:**
> @bartman

===
In the recovery, run these commands:

===
sudo mount -f -o remount,rw -t $FSTYPE $ROOTSDA
====
sudo sed -i s'/quiet//g' /etc/default/grub
sudo sed -i s'/splash//g' /etc/default/grub
sudo update-grub
sudo reboot now

The PC will boot, let it do it. If still you're stuck at console (no lightdm), you might have to reinstall video drivers.
===
Regards,
Effenberg

It Works :D 
 I replaced "-f" with "-n" etc in the mount command, and used a bit different sed syntax. No video driver reinstallation needed this time.

Regards,
Vipsu

---


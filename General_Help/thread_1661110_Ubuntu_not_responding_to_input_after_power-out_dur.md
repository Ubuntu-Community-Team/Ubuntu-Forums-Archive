---
title: "Ubuntu not responding to input after power-out during update"
date: 2011-01-06
forum: General Help
---

### Post by mahela007 on 2011-01-06
Hi.. I was running and update on my Ubuntu laptop (dual booted with windows). I download my updates via a local repository using apt-cacher ng so the download itself doesn't take very long. However, at some point during the update process, the laptops battery ran out and now, Ubuntu won't respond to any input from the mouse or the keyboard. What can I do? Is there any way to salvage the system and if so, is it possible to repair any damage?

---

### Post by ianmillington on 2011-01-06
First the moral - it's not a good idea to upgrade while running on battery but of course you know that!

Try this -Connect the computer to a wired connection. Boot your machine and immediately the BIOS has run hit the shift key to show the grub menu (if you are dual-booting you don't need to as the grub menu is visible anyway).

Select the recovery option

You will be presented with a list of options. Select "command prompt with networking". When you see the prompt type

sudo dpkg --configure -a

Then when that is done select normal boot.

HTH

---

### Post by mahela007 on 2011-01-06
thanks.. I'll try that and post back. Actually, I forgot that the thing was on battery power because I hadn't intended to do an update when I turned the laptop on. .. oh well. ;-)
EDIT: I booted up and got to the GRUB screen. What do you mean by the "recovery option" ? Is it the "recovery mode" kernel versions? There is also a tip which reads "press C for command line".

---

### Post by lrgmmc on 2011-01-06
yes recovery mode with highest kernal number

---

### Post by mahela007 on 2011-01-07
nope.. that doesn't seem to work. I tried selecting each "recovery mode" option (I have about 4) and every time, a list of messages flashes across the screen and after about 10 seconds, it seems to halt / pause. At this stage, the PC doesn't respond to the keyboard. The hard drive usage light does not light up either.
Is it just that I'm not waiting long enough for things to proceed? (I waited about a minute but since the screen and the hard drive light didn't show any activity, I thought the thing had crashed.)
Also, could you please tell me what to expect just in case one of the recovery kernels DOES load up properly?

EDIT: I dunno if it's important but like I said before, the updates for this laptop come of my LAN.. so it's package management settings direct it to look for new packages on my desktop which is also connected to the LAN. I did have the desktop on and connected to the LAN when I was booting up the recovery kernels in the laptop.

---

### Post by ianmillington on 2011-01-07
Do any of the last few messages make any sense, for example the system is trying to find something but failing?

---

### Post by Elfy on 2011-01-07
> Is it just that I'm not waiting long enough for things to proceed? (I waited about a minute but since the screen and the hard drive light didn't show any activity, I thought the thing had crashed.) I'd probably wait longer than a minute - it's possibly trying to do an fsck

> Also, could you please tell me what to expect just in case one of the recovery kernels DOES load up properly?A small menu from which you can pick the option for netroot

---

### Post by mahela007 on 2011-01-07
@ianmillington
The last line reads 
"Begin: Running scripts/init-bottom
DONE"

Sometimes with other kernel version, it says something like "creating SWAP" on a particular partition

I tried waiting for more than a minute.. It seems like it really is stuck.

---

### Post by ianmillington on 2011-01-07
I think at this point if it were me I would be thinking in terms of a possible reinstall. 

Do you have a live cd? If so, when you run the CD can you see your /home directory? If so, I think a forerunner to whetever else you do now will be to back up your /home directory.

---

### Post by mahela007 on 2011-01-07
Yeah.. I agree. I do have a live CD but not the latest version. I might as well download that and install it. The laptop didn't have any critical documents on it..
Still open to any suggestion on how to fix this though........

---

### Post by oldfred on 2011-01-07
If you have good liveCD, you can chroot into your system and update it from that. But if you cannot get network it may not work.

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Or, but you probably do not need the grub uninstall:
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Once chrooted run these commands:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by ianmillington on 2011-01-07
If you can't get to the command line in recovery mode (especially using the oldest kernel) then I'm asking myself what other options you have, to be honest. 

My suspicion is that it was doing something critical when the power went and as a result some key files got trashed, meaning that your only option might be to reinstall. Before you do this though, wait a while and see if someone else has any alternative thoughts/ideas.


Obviously give oldfred's advice a go

---

### Post by ianmillington on 2011-01-07
Deleted due to duplication

---

### Post by ianmillington on 2011-01-07
Deleted due to duplication

---

### Post by ianmillington on 2011-01-07
Deleted due to duplication

---

### Post by mahela007 on 2011-01-07
> **oldfred said:**
> If you have good liveCD, you can chroot into your system and update it from that. But if you cannot get network it may not work.

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Or, but you probably do not need the grub uninstall:
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Once chrooted run these commands:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

Sorry.. I don't really understand most of that. Are there any more noob friendly posts?

---

### Post by mahela007 on 2011-01-08
Ok,.,. after a bit of reading, I feel confident enough to give those instructions a go.. Does the version of the Live CD I use matter? Is it compulsory to use a live CD of the same Ubuntu version as the installed version?

---

### Post by oldfred on 2011-01-08
Not really, it can even be any of the other linux repair CDs. You just use the liveCD as the kernel to boot and once chrooted into your install everything you do is to that install including reinstalling a kernel or virtually any other applications. 

Just make sure you use the correct partition for the one line chroot instructions (with & joining commands) as those are a lot easier just to copy & paste. If the one line version does not work then you need to use the line by line one and find what does not work.

Then once in the chroot enviroment, you are in your system, try running each update command. If any errors post back with what the message is.

---

### Post by mahela007 on 2011-01-08
Does chroot refer to the command line command which changes the root directory? (I apologize if that seems to be a dumb question).

---

### Post by oldfred on 2011-01-08
Not sure of your answer, so I did this, which you can run for more info:
man chroot

chroot - run command or interactive shell with special root directory

---

### Post by mahela007 on 2011-01-08
This is what I read.. 
[http://manpages.ubuntu.com/manpages/jaunty/man2/chroot.2.html](http://manpages.ubuntu.com/manpages/jaunty/man2/chroot.2.html)

SO anyway.. I tried "chrooting" using an 8.10 live CD and guess what.. It game me an "unknown file system type: ext4 " error. I suppose this means I'll have to use the live CD of a newer Ubuntu version?

Also , I don't know if its relevant but when I started up partition editor in the live CD, it game me a message saying "The kernel is unable to re-read the partitiontables on the following devices:
- /dev/sda"
My linux installation is on /dev/sda6

---

### Post by gauravnarra on 2011-06-02
i too have the same problem ....exactly the same .
should i reboot ubuntu or is there any other way..
:(

---

### Post by lrgmmc on 2011-06-02
Have you given post #11 a try?

---

### Post by mahela007 on 2011-06-02
Hang in there.. don't panic. I managed to correct this problem so there's hope for you Ubuntu as well. (However, my Ubuntu does have some flaws after the incident so I'm waiting to upgrade it to a newer version.. but all the files are still there and it is USABLE for day to day tasks.)

Unfortunately, I can't remember exactly how I got round to fixing it ](*,).. I'll post back as soon as I figure it out. For the moment, I think you should check up on the chroot thing. (I think that's what I did). 
From what I understand, it allows you to boot from a live CD and make the Ubuntu on the CD work with all the files and folder on the hard drive in order to re-update your system.

---

### Post by mahela007 on 2011-06-02
@Guaravnara Please took at my other thread here. I used TinyCore linux (10MB ) download to chroot into Ubuntu and fix it. Hope you find this useful.

---


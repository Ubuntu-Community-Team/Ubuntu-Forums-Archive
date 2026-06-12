---
title: "Linux Newbie here.  I need help with Wireless Problems"
date: 2012-01-12
forum: General Help
---

### Post by ljrobison on 2012-01-12
Hello all, I have recently tried installing both Linux distro's Ubuntu and Mint (if I shouldn't be talking about MINT here let me know, I just think its relative to solving the problem I'm having) over the past 3 days. Each time was on a fresh partition. Both times I noticed the updates for the installation would have ETAs of 44455 hours or more and nothing would happen. As soon as I would switch to a wired connection they would install in under an hour. First I installed Ubuntu and reasearched the problem, tried a few fixes I found, nothing worked. So I decided to remove Ubuntu and try Mint 12, the exact same thing happened. So from the information I have gathered there might be an issue with the kernel? I'm not really sure, I'm a linux newbie. 

Does anyone know how I can fix this issue? I have removed Mint so I have no linux partitions on my HDD now. I really wanna play around with Linux but I can't hard wire my laptop 24/7. Please help me out =D

Thank you!

edit: Forgot to mention my wireless is fine in Windows 7

---

### Post by adityamagadi on 2012-01-13
go to system settings select additional drivers and activate your wireless driver(hoping yours is a broadcomm) and do this
on your terminal.
sudo apt-get update
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer

---

### Post by ljrobison on 2012-01-13
The Wireless Card in my computer is Intel WiFi Link 1000 BGN according to Windows Device Manager.  I dunno if that helps.  Also when I looked at the module it was using (I think Im using the right term) it says it was 

```
iwlagn
```

I tried some various code fixes googling that, but no avail.

---

### Post by carl4926 on 2012-01-13
You should post the result of

```
lspci -nnk
```

---

### Post by xyzzyman on 2012-01-13
Did you disable Wireless N in any of the fixed you tried? Usually forcing these cards to G takes care of the issue. Not ideal if you need N for a weird connection issue, or you use N for local file transfers, but usually G is faster than your internet connection. Mint is a fork of Ubuntu so the fix will wind up being the same for both.

Also, your card was folded into the iwlwifi driver in kernel 3.2. So if you have a spare blank DVD or thumb drive you can try the latest Ubuntu 12.04 daily live-cd [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) as I have no more wireless N issues since moving to a 3.2 kernel. If that works for you from the live CD, I can link to the PPA that has the version 3.2 kernel "backported" to 11.10. (If 12.04 works you could always install it, but being early in testing it could be working fine and then break through updates. Which could be good for learning but not as fun as breaking a regular release on your own and having to fix it if you're just starting out. :guitar:)

---

### Post by ljrobison on 2012-01-13
> **xyzzyman said:**
> Did you disable Wireless N in any of the fixed you tried? Usually forcing these cards to G takes care of the issue. Not ideal if you need N for a weird connection issue, or you use N for local file transfers, but usually G is faster than your internet connection. Mint is a fork of Ubuntu so the fix will wind up being the same for both.

Also, your card was folded into the iwlwifi driver in kernel 3.2. So if you have a spare blank DVD or thumb drive you can try the latest Ubuntu 12.04 daily live-cd [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) as I have no more wireless N issues since moving to a 3.2 kernel. If that works for you from the live CD, I can link to the PPA that has the version 3.2 kernel "backported" to 11.10. (If 12.04 works you could always install it, but being early in testing it could be working fine and then break through updates. Which could be good for learning but not as fun as breaking a regular release on your own and having to fix it if you're just starting out. :guitar:)

I tried doing this with some commands I found (disable_11n=1 or something like that IIRC)  but I would get an error message, I'll try again when I get home. 

Carl ill also post the results of what you suggested. 

Thanks guys

---

### Post by varunendra on 2012-01-13
> **ljrobison said:**
> I tried doing this with some commands I found (disable_11n=1 or something like that IIRC)  but I would get an error message,
Hi, and welcome to the forums :)

The proper method to disable N channel (if required) on your driver is here: [http://ubuntuforums.org/showpost.php?p=11360822&postcount=6](http://ubuntuforums.org/showpost.php?p=11360822&postcount=6)

If that doesn't work, please post outputs of:
```
uname -rm
lsb_release -a
sudo lshw -C network
lsmod
iwconfig
rfkill list all
```

---

### Post by ljrobison on 2012-01-13
That's what I tried. The first command ran fine, but the second one had some error I can't remember. I'll try again when I get off work and post the results here

---

### Post by ljrobison on 2012-01-13
I ended up trying:
sudo rmmod iwlagn sudo modprobe iwlagn 11n_disable=1
and it worked this time, so I opened firefox and my Internet seems to be running fine. The last time I got a few errors, I don't know what happened. So I am going to try another clean install and make the change permanent. 

Thank you very much everyone.  I cant wait to mess around with Linux.  

On a side note, do you guys have any tips on some things I should do first as a Linux newbie? :p

---

### Post by carl4926 on 2012-01-14
> On a side note, do you guys have any tips on some things I should do first as a Linux newbie?

Get yourself a machine that you can use without concern.
Install and Install and Install.....etc....

Don't limit it to just Ubuntu. Try different Distros, get familiar with multi-booting and the different Grub versions.

If you can't do it on a real machine. The next best thing if your machine is up to it, is to use a VM like Virtual Box.

---

### Post by varunendra on 2012-01-14
> **ljrobison said:**
> I ended up trying:
sudo rmmod iwlagn sudo modprobe iwlagn 11n_disable=1
and it worked this time
Great! Best of luck with the fresh installation.

> **ljrobison said:**
> On a side note, do you guys have any tips on some things I should do first as a Linux newbie? :razz:
Yeah, I'd like to share a few (and I may be missing a few major ones!):

First,  I'll point to some backup options, since it gives you full freedom to  fiddle with your system if you have a reliable backup:-

[LIST]
[*]Since  you seem to be dual booting, make sure to create backup DVDs of your  windows installation before you screw it up during your experiments.
[*]Check  out a clonezilla live cd - a great tool for creating compressed backups  of all kinds of partitions or entire hard drive. (maybe a substitute to  Win backup DVDs if used wisely)
[*]Try out [Remastersys]("http://www.geekconnection.org/remastersys/") - a great tool for creating a live backup of your linux installation.
[/LIST]
Now something about installation:-

[LIST]
[*]Although you seem to have successfully installed Ubuntu on its own partition, it's always good to know that **Gparted **is  one of the most friendly and most reliable tools for  creating/manipulating partitions. It is safer to create partitions with  gparted, then only choosing them during installation (creating them with  default partitioner may sometimes be confusing)
[*]It is a good idea to assign relevant labels to existing partitions in Windows to be able to easily recognize them in linux.
[*]During  installation process, you can safely skip downloads of language packs  if you are not going to use custom languages. You can install them later  anyway, so skipping speeds up installation time. I even disconnect from  internet to speed up the installation, as anything that is downloaded  at that time, can also be downloaded later (the system will  automatically suggest you when and if required)
[/LIST]
Something after installation:-



[LIST]
[*]By  default, Linux tends to reserve 5% of space on linux partitions for  root-level maintenance tasks and to avoid fragmentation as much as  possible. On partitions larger than 20GB, it is usually a wastage of  space. So some of us think it should be set to 200 MB to 1% (whichever  is larger). Even some others like to completely turn it off for  partitions other than '/' itself (1% on root, 0 for others). The command  to set its percentage on a particular partition (only linux partitions)  is: *sudo tune2fs -m <number of required %> <device>*.  For example, if Ubuntu is installed on sda2, then in order to set the  reserve space on it to 1%, the command will be - ```
sudo tune2fs -m 1  /dev/sda2
``` For more info on the command, try *tune2fs --help* or *man tune2fs*.
[*]Knowledge  of various Desktop Environments may be interesting for you. A great  post on DEs (courtesy - our dear friend late Robin):  [http://ubuntuforums.org/showpost.php?p=10653379&postcount=11](http://ubuntuforums.org/showpost.php?p=10653379&postcount=11)
[/LIST]
Some "must-have" apps:

[LIST]
[*]Gparted: partitioning tool
[*]Virtualbox: for trying different OSes safely and easily
[*]Clamav: Antivirus for saving your windows friends.
[*]Remastersys: for creating live backup DVDs
[*]VLC or "Restricted Extras" from repository: to allow you play all existing formats of audio-video files.
[*]k3b:  best cd burning application for Linux (Be warned: if you are not using  KDE, it will bring with it a lot of KDE-specific packages that will  cause a huge download of 200+ MB) (..and if you are using KDE, it'll be  installed by default ;))
[*]Flash-Aid (to be installed from within firefox as a plugin): to automatically optimize performance of flash videos
[*]Startup manager: for easily setting/changing boot preferences
[/LIST]
Due  to risk of turning the post into a novel, I'll stop at this point.  Depending on your specific needs, just ask a question here (in a new  topic-specific thread), and you'll most often get the best suggestions  available.


Hope you enjoy Ubuntu (and oh, we do have an  entire section for 'other distro talk' in the forums. You can even  discuss about Macs and Windows if it is somehow related with Linux  issues).


Cheers!:popcorn:

---


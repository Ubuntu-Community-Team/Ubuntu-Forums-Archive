---
title: "No GUI on startup?"
date: 2010-12-12
forum: General Help
---

### Post by Nissan_350Z on 2010-12-12
Okay.. i let the update manager do it's thing and update to 10.10.. well. it asked to restart.. and i let it. Now ubuntu will NOT boot up, it shows the purple ubuntu screen with the dots and then a black screen flashes: 
Ubuntu 10.10 cody-A0751h ttyl
cody-A0751h login:
3 times then it stays steady. and i log in and it takes me to a command prompt.
I try the Ctrl+Alt+F7.. it shows where it TRIED to start up.. but its just stopped. and i tried startx into the command prompt.. and it errors out.. any ideas? thanks!

---

### Post by Atamisk on 2010-12-12
So, when you say "It Errors Out", what does it actually tell you?

---

### Post by oldfred on 2010-12-12
Perhaps the update manager did not finish or did you change some video or video related settings?

If you can get to command line. This is what I recommend from a chroot so I do not have sudo, I believe the sudo -i is the preferred way.

in not chroot use:
sudo -i
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

Not sure if you need to do some more updates to video drivers.
If able to boot to recovery mode & netroot
#list of recommended drivers:
jockey-text -l
#Install a driver:
sudo jockey-text -e <driver>

---

### Post by cgroza on 2010-12-12
If the above does not work, backup your xorg.conf file and then delete it. I had success on bringging a dead display to life like this with debian.

---

### Post by Nissan_350Z on 2010-12-12
well.. there's a LOT there.. but from what i see under Fatal server error:
AddScreen/ScreenInit failed for driver 0
and then under that is
ddxSigGiveUp: Closing log
giving up
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.

---

### Post by Nissan_350Z on 2010-12-12
> **oldfred said:**
> Perhaps the update manager did not finish or did you change some video or video related settings?

If you can get to command line. This is what I recommend from a chroot so I do not have sudo, I believe the sudo -i is the preferred way.

in not chroot use:
sudo -i
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

Not sure if you need to do some more updates to video drivers.
If able to boot to recovery mode & netroot
#list of recommended drivers:
jockey-text -l
#Install a driver:
sudo jockey-text -e <driver>

im stuck at apt-get update #resync package index
my wifi isnt working for some reason either.. it worked when i was able to login but not at the terminal.. any other ideas? 
i appreciate this!

---

### Post by oldfred on 2010-12-12
Are you using a Ethernet connect, not the wifi for updates?

You did not paste any of the info after the hash/pound sign? That is only for comments.

Otherwise if you do not have a network connection you will have to use chroot and see if that will give you a connection.

drs305 chroot to reinstall grub2 (just that you do not uninstall/reinstall grub)
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)eat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

---

### Post by Nissan_350Z on 2010-12-12
> **oldfred said:**
> Are you using a Ethernet connect, not the wifi for updates?

You did not paste any of the info after the hash/pound sign? That is only for comments.

Otherwise if you do not have a network connection you will have to use chroot and see if that will give you a connection.

drs305 chroot to reinstall grub2 (just that you do not uninstall/reinstall grub)
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)eat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Okay so i connect it into an ethernet cable and it went through everything just fine except the last bit.. im stuck at:Not sure if you need to do some more updates to video drivers.
If able to boot to recovery mode & netroot
#list of recommended drivers:
jockey-text -l
#Install a driver:
sudo jockey-text -e <driver>
 
When i did that i got:
root@cody-A0751h:~# sudo jockey-text -e
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__initinit__.py:57: GtkWarning: could not open display warnings/warn(stre(e), _gtk.Warning)

Thanks!

---

### Post by oldfred on 2010-12-12
I might try uninstalling & reinstalling the desktop.

From your chroot:

# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

What video card do your have? It may be related to cgroza's suggestion on xorg.

---

### Post by Nissan_350Z on 2010-12-12
interesting.. i type in apt-get remove ubuntu-desktop
and it says 
Package ubuntu-desktop is not installed, so not removed.

but i type 
apt-get install ubuntu-desktop
and it shows about 25MB that can be downloaded.. which might possibly be whats wrong? it's downloading and my graphics card is (in linux) considered Poulsbo?
but it's intel GMA 500
Thanks1 I'll let you know something soon.

---

### Post by Nissan_350Z on 2010-12-12
> **oldfred said:**
> I might try uninstalling & reinstalling the desktop.

From your chroot:

# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

What video card do your have? It may be related to cgroza's suggestion on xorg.

and what i just posted. it went through successfully, i restarted.. and it's still back at the ttyl login..

---

### Post by oldfred on 2010-12-12
Was it not Ubuntu that you were running? The packages are different for Kubuntu and all the other versions.

Does this run now?
```
jockey-text -l
```

Beyond that you are into some specific configuration of video drivers which I do not know much about.

Have you tried editing grub with e at the menu and replace quiet splash with either the Intel or generic settings?

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Nissan_350Z on 2010-12-13
> **oldfred said:**
> Was it not Ubuntu that you were running? The packages are different for Kubuntu and all the other versions.

Does this run now?
```
jockey-text -l
```

Beyond that you are into some specific configuration of video drivers which I do not know much about.

Have you tried editing grub with e at the menu and replace quiet splash with either the Intel or generic settings?

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

Nope.. i still get the:
root@cody-A0751h:~# sudo jockey-text -l
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__initinit__.py:57: GtkWarning: could not open display warnings/warn(stre(e), _gtk.Warning)

Yes, i was running Ubuntu Netbook remix 10.10. when it last worked correctly..
i tried the setting the grub with quiet splash only option.. and still no luck..
i could try setting the graphic settings.. those are in the grub bootloader settings, right?
I tried adding the i915.modeset=1
and changing the 1 to a zero.. but no luuck with either.. still at square one.. any other ideas? i really do appreciate this..

---

### Post by oldfred on 2010-12-13
I am running out of ideas. Back in post #4 was the idea of renaming your xorg. I have not had to edit or do anything with xorg file for at least a couple of years.

You can also try the xforcevesa setting.

I think we just installed the standard desktop which may confuse you. But I do not know command line to install/reinstall netbook remix. I have installed both Ubuntu and Kubuntu desktops on my system, but it was not what I wanted. If I try Kubuntu again I will just do a full install to another partition.

What system do you have. I can look for similar issues. 

I will be back on tomorrow AM. Its late.

---

### Post by Nissan_350Z on 2010-12-13
> **oldfred said:**
> I am running out of ideas. Back in post #4 was the idea of renaming your xorg. I have not had to edit or do anything with xorg file for at least a couple of years.

You can also try the xforcevesa setting.

I think we just installed the standard desktop which may confuse you. But I do not know command line to install/reinstall netbook remix. I have installed both Ubuntu and Kubuntu desktops on my system, but it was not what I wanted. If I try Kubuntu again I will just do a full install to another partition.

What system do you have. I can look for similar issues. 

I will be back on tomorrow AM. Its late.

I'll try post #4 tomorrow.. it's late here too, almost 2am.. but i have an Acer A0751h.
and the desktop always looked like that of regular ubuntu.. it never looked any different than anything else..
but thanks for your help and have a good night.

---

### Post by oldfred on 2010-12-13
I did find this link that covers some things.

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Installing:
[http://www.askdavetaylor.com/how_to_install_ubuntu_linux_on_asus_netbook_winxp.html](http://www.askdavetaylor.com/how_to_install_ubuntu_linux_on_asus_netbook_winxp.html)

---

### Post by Nissan_350Z on 2010-12-13
> **oldfred said:**
> I did find this link that covers some things.

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Installing:
[http://www.askdavetaylor.com/how_to_install_ubuntu_linux_on_asus_netbook_winxp.html](http://www.askdavetaylor.com/how_to_install_ubuntu_linux_on_asus_netbook_winxp.html)

hmm.. you think it would just be best to completely reinstall ubuntu? i went through windows 7 and saved some files from it.. its just a pain to get the graphics and everything back going again.. but to keep this from happening.. do you think i should update it anymore or.. what?

Thanks for the help and i really appreciate it. I guess i'll just reinstall the Ubuntu OS.

---

### Post by Nissan_350Z on 2010-12-13
yeah i just redid it and everything is perfect! marking as solved... thanks for your help!!

---

### Post by oldfred on 2010-12-14
Sometimes reinstall is the quickest and easiest solution.

Glad you have it working.:)

---


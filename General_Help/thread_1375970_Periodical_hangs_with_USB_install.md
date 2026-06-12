---
title: "Periodical hangs with USB install"
date: 2010-01-08
forum: General Help
---

### Post by xeross on 2010-01-08
Hey, 

I've recently installed Ubuntu to my USB stick (Installed from CD so not Live Persistent). 

But it hangs every few seconds, I think this is because of the low read/write speed of the usb stick. However when using the Live version booting/shutting down takes a long while, I basically need it to be able to boot fast, run fast, and shutdown fast.

Any ideas how I can solve this ?

Thanks for your time, Xeross

---

### Post by xeross on 2010-01-09
Bump.

---

### Post by xeross on 2010-01-10
Bump. No one can help me ?

---

### Post by dannyboy79 on 2010-01-12
i recently installed karmic to a 16gb verbatim store-n-go usb stick. i used a windows .exe program which creates a 4gb casper-rw image and puts it on the usb stick to be able to boot to and run a live session that is persistent. i do notice some freezing once in awhile but then again i am doing tons at once when this happens. the nice thing about teh pendrivelinux  windows .exe program is that it sets everything up for you. it basically makes a tmpfs for your /tmp directory and other optimizations. i did however notice that i was using the live session user named ubuntu and i didn't want that, i wanted to create my own user since this would pretty much always be instaled into this hardware. well, after creating my own user adn copying over tons of stuff from the real hdd install i haev for this hardware, and making updates to fstab, hostname and plenty other things, i rebooted and none of those things were saved for my user. VERY WEIRD. so i am not sure if persistent mode will onyl work if you make all the changes to the live session only and not by creating your own user, logging out, then logging in under the user you create. i haev to play around some more. there are tons of websites out there for optimizing install to SSD, so you could apply those same optimizations because a solid state drive is very similar to flash drive. GOOD LUCK

---

### Post by xeross on 2010-01-12
Ye I also switched back to the windows installer.

And on your matter with your user, there's a script in the boot that recreates the ubuntu user and makes it autologin. Your user is still there it's just not logged in.

You can remove the autologon instructions can be found in [http://ubuntuforums.org/showthread.php?t=1309554](http://ubuntuforums.org/showthread.php?t=1309554)

---

### Post by dannyboy79 on 2010-01-13
> **xeross said:**
> Ye I also switched back to the windows installer.

And on your matter with your user, there's a script in the boot that recreates the ubuntu user and makes it autologin. Your user is still there it's just not logged in.

You can remove the autologon instructions can be found in [http://ubuntuforums.org/showthread.php?t=1309554](http://ubuntuforums.org/showthread.php?t=1309554)

i figured that about auto logging in as a the live session user. my question still remains, why are simple changes to fstab, /etc/network/interfaces and /etc/hostname not being saved? What I do after the live session user is logged in, is logout, chose my login account. make all my changes, then after I reboot, none of the things i just changed were saved. it's very irritating. any thoughts?

---

### Post by xeross on 2010-01-14
My network interfaces get saved just fine, try using the network connections panel in the user interface.

And I believe the hostname is also reset by one of the init scripts.

---

### Post by dannyboy79 on 2010-01-14
network manager is just plain pathetic which is why i always use the /etc/network/interfaces file. also, what about your /etc/resolv.conf file defining your dns nameservers? what about fstab, haev you tried to edit it to add some network shares or other computer hdd's to get auto-mounted on boot? if could inform me of a script that resets all these things, i'll rename it to test it out. thanks

---


---
title: "how to edit in a command prompt?"
date: 2010-12-18
forum: General Help
---

### Post by ionbasa on 2010-12-18
okay, so i somehow managed to mess up my install of 10.10

I used the alternate AMD 64 install

so now when I login it is only a text prompt. This leads me to believe that I am running in Ubuntu Server. I read this article:
[http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)
but my network is not setup!!
So I tried to do this:
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

but when I get to:
```
sudo vi /etc/network/interfaces
```
I dont realy know how to edit the file.
I basicaly see 
```

# The loopback network interface
auto lo
iface lo inet loopback
~
~

```
so I want to replace that with:
```

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

how would i save the file and how would i edit it from the Command line?

---

### Post by cherva on 2010-12-18
Don't use vi it is not for very user friendly ...
try ```
sudo nano /etc/network/interfaces
```
Then you can start editing right away and to save just hit
Ctrl+X it will ask you for a file name just leave it as is and hit enter again... All other commands of nano are at the bottom of the screen.
Don't replace it ... just append it beneath the other stuff in the file.

---

### Post by nothingspecial on 2010-12-18
I would try nano

```
sudo nano /etc/network/interfaces
```

Ctrl - O to save

Ctrl - X to exit

However, maybe you could try
```

sudo ifconfig eth0 up
sudo dhclient
```

I`m assuming you have a wired internet connection.

---

### Post by hwychld on 2010-12-18
vi is not the most friendly editor, but with a little luck you can make those changes.

Make a backup of the file first
```
cp interfaces interfaces.bak
```

When you get the file open, you can use the h,j,k,l keys to move around in the file.  When you are ready to edit, press the i key (puts you into insert mode).  Make the changes you need, then press esc.  Now to save and exit type 

```
:wq
```

If at any point you get weird characters and just need to quit without saving type
```
:q!
```

Good luck

---

### Post by ionbasa on 2010-12-18
okay so i ran 

sudo ifconfig eth0 up
sudo dhclient

how do i know if it worked/ now allows network access. and yes eth0 is an wired connection.

---

### Post by hwychld on 2010-12-18
One more thing, and perhaps this will help prevent the weird characters that sometimes show up when using the arrrow keys and backspace keys.

Ubuntu actually ships with vim, but runs it in compatibility mode.  To use vim, once you launch vi type

```
:set nocp<Enter>
```

If you wish to make this permanent you can edit your .vimrc file in your home directory and place the set nocp command in there.

---

### Post by hwychld on 2010-12-18
just run ifconfig and see if the adapter was assigned a IP address.

---

### Post by ionbasa on 2010-12-18
okay it was assigned an IP address and I successfully ran

sudo apt-get update

from there I can follow the instructions here to get the GUI right?
[http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)

---

### Post by oldfred on 2010-12-18
A lot of users are having issues with the graphical interface starting.

Have you tried this?

sudo service gdm start
or
sudo /etc/init.d/gdm restart

Have you tried a few options on the kernel boot line?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

#If able to boot to recovery mode & netroot
#list of recommended drivers:
jockey-text -l
#Install a driver:
sudo jockey-text -e <driver>

---

### Post by nothingspecial on 2010-12-18
Yes,

```
sudo apt-get install ubuntu-desktop
```

or many many other options. ;)

Go ahead.:D

---

### Post by nothingspecial on 2010-12-18
> **oldfred said:**
> A lot of users are having issues with the graphical interface starting.

Have you tried this?

sudo service gdm start
or
sudo /etc/init.d/gdm restart

Have you tried a few options on the kernel boot line?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

#If able to boot to recovery mode & netroot
#list of recommended drivers:
jockey-text -l
#Install a driver:
sudo jockey-text -e <driver>


I`m guessing OP did alternate install without selecting a DE.

---


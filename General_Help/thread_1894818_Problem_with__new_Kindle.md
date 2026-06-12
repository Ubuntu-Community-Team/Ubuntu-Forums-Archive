---
title: "Problem with  new Kindle"
date: 2011-12-13
forum: General Help
---

### Post by sallymc on 2011-12-13
Hi hi,
I have a problem with my new Kindle.  It mounts onto Ubuntu 10.04 beautifully, but when I press eject , the box says :
Volume is busy
One or more applications are keeping the volume busy.
vlc/media/Kindle
When I press "unmount anyway" the message reappears again and again..

When I press  Safely Remove Drive, the box says :
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

Hoping someone can HELP ?
Sallymc

---

### Post by sallymc on 2011-12-13
Hi hi,
I have a problem with my new Kindle.  It mounts onto Ubuntu 10.04 beautifully, but when I press eject , the box says :
Volume is busy
One or more applications are keeping the volume busy.
vlc/media/Kindle
When I press "unmount anyway" the message reappears again and again..

When I press  Safely Remove Drive, the box says :
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

Hoping someone can HELP ?
Sallymc

---

### Post by oldos2er on 2011-12-13
Do you have a file manager window opened to the Kindle folder? Or a terminal? If so you need to close them first before 'Safely Remove'.

---

### Post by kgarbutt on 2011-12-13
From the terminal type exactly this:

sudo eject Kindle

Ken

---

### Post by oldos2er on 2011-12-13
Posts merged.

---

### Post by oldtimer7777 on 2011-12-13
Use Calibre instead of Kindle.  Calibre is linux native, and works better than Kindle and does all the same functions too. It is about 3/4 the way down the new user checklist:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Always use native linux apps instead of windows app whenever possible on a Linux OS.

> **sallymc said:**
> Hi hi,
I have a problem with my new Kindle.  It mounts onto Ubuntu 10.04 beautifully, but when I press eject , the box says :
Volume is busy
One or more applications are keeping the volume busy.
vlc/media/Kindle
When I press "unmount anyway" the message reappears again and again..

When I press  Safely Remove Drive, the box says :
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

Hoping someone can HELP ?
Sallymc

---

### Post by oldos2er on 2011-12-13
> **oldtimer7777 said:**
> Use Calibre instead of Kindle. 

Calibre is software, Kindle is hardware.

---

### Post by oldtimer7777 on 2011-12-13
> **oldos2er said:**
> Calibre is software, Kindle is hardware.

Do you have a Kindle?  I do.

You can migrate your ebooks directly from the cloud to Calibre instead of mounting a Kindle device to Ubuntu.  That's why I suggested it.  That is the underlying reason why they are having this issue.  They want to migrate data from the Kindle, or vicaversa and Calibre is the recommended way to accomplish that. What other reason would they have?

---

### Post by oldos2er on 2011-12-13
> **oldtimer7777 said:**
> Do you have a Kindle?  I do.

You can migrate your ebooks directly from the cloud to Calibre instead of mounting a Kindle device to Ubuntu.  That's why I suggested it.  That is the underlying reason why they are having this issue. 

Looks as though the underlying reason is a dbus error.

>  They want to migrate data from the Kindle, or vicaversa and alibre is the recommended way to accomplish that. What other reason would they have?

Why make assumptions about what the OP is wanting to do? Let's see what the OP's answers to the questions put to her are first.

---

### Post by sallymc on 2011-12-14
> **oldos2er said:**
> Looks as though the underlying reason is a dbus error.



Why make assumptions about what the OP is wanting to do? Let's see what the OP's answers to the questions put to her are first.

Thanks everyone for your concern.  I figured out how to stop ubuntu from  thinking the kindle is a digital audio device by default. Instead, it  will just think it's a removable disk drive. .

Here's what I did:

    * open a terminal window (applications/accessories/terminal)
    * type: cd /lib/udev/rules.d <press enter>
    * cp 40-usb-media-players.rules 40-usb-media-players.save <press enter>
    * sudo gedit 40-usb-media-players.rules <press enter>
    * search for "kindle" - you should get a line that looks like this:

ATTRS{idVendor}=="1949" , ATTRS{idProduct}=="0001|0002|0003|0004" , ENV{ID_MEDIA_PLAYER}="amazon_kindle"

    * just go to the beginning of that line and insert # and a space, so the line is:

# ATTRS{idVendor}=="1949" , ATTRS{idProduct}=="0001|0002|0003|0004" , ENV{ID_MEDIA_PLAYER}="amazon_kindle"

    * save the file
    * exit the editor
    * exit the terminal
    * reboot

Now when you plug in your Kindle it should mount it so it looks like a disk drive.

---

### Post by dandnsmith on 2011-12-14
Thanks for that solution.
I haven't needed it yet, but was going to try Kindle mounting soon.

---

### Post by deepclutch on 2011-12-14
I faced the same problem, albeit on Debian Testing. BTW, I have a Kindle Touch.

My Solution was to purge HAL(which was obsolete),usbmount from the system. It is few days, since I plugged Kindle to the system. but IIRC, this solved the issue as I can safely eject the Device.  
I am aware that usb drives needs to be "sync" before eject/unmounted. In case, you need to remove a drive forcedly, try "sync" command, later umount/eject the drive as I read somewhere it helps with usb drive's life.

I may update this post with lsusb -vvv for kindle touch, in case it helps update udev rules :)

---


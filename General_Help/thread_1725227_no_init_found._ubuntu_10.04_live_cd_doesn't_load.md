---
title: "no init found. ubuntu 10.04 live cd doesn't load"
date: 2011-04-09
forum: General Help
---

### Post by leptep on 2011-04-09
I can no longer access my desktop!!!

my ubuntu 10.04 acted weird today, i could no longer erase files in the downloads folder, i wanted to restart and the restart window as well opened with no text in the box window.

I pressed enter and managed to turn off my machine.

turning back on I get this message:

not init found: try passing init=bootarg
Busy Box V1.13.13 ......

enter 'help'
(initramfs)_


Please HELP


Ido

---

### Post by linuxuser12345 on 2011-04-09
Okay, in your 10.04 installation, go to:
*Places... Home Folder... (right click)Downloads... Properties... Permissions*
_**Edit your folder permissions from there.**_

I would recommend using a program called UNetbootin to create a live USB for Ubuntu 10.04.02. Go to:
*Applications... Ubuntu Software Center... (type)UNetbootin... Install*
_**Then:**_
*Applications... System Tools... UNetbootin*

---

### Post by leptep on 2011-04-09
thanks for your quick answer.

I tried loading 9.10 from live cd,,, didn't load as well.

i downloaded and mounted a usb with ubuntu 10.04 following the instructions.

i put the usb in my machine and tell it to load from usb,
after about 30 min when nothing happened ( i only see the dots advance ) i pressed the esc key.

i see the following on screen:(after a few loading and running messages)

stdin: error 0
/init: line 7: can't open /dev/sr0:no medium found
/init: line 7: can't open /dev/sr0:no medium found
unable to open '/dev/sda'

---

### Post by leptep on 2011-04-10
i managed to load xubuntu 10.10 from live cd.
is this good sign?

---

### Post by leptep on 2011-04-10
I see in other posts i should run this comand after live cd loads:


sudo e2fsck -C0 -p -f -v /dev/sda1

because the error i got was:
stdin:error 0
init: line 7 can't open /dev/sr0: no medium found

i though running this:

sudo e2fsck -C0 -p -f -v /dev/sr0

makes sense?
i get a message saying it is mounted and if i continue i will cause severe filesystem damage

---

### Post by linuxuser12345 on 2011-04-10
Have you tried to load Ubuntu 10.10 from the live CD? Sometimes one version of Ubuntu and the liveCD  is more compatible than the other. I would try loading up Ubuntu 10.10 on a USB or CD and booting it from there. It sounds promising, as Xubuntu 10.10 would load, *also*.

---

### Post by leptep on 2011-04-10
ubuntu 10.10 did load!

now what?

i've opened gparted, i see /dev/sda1 (file system - ext4)
trying to check it but it says filesystem mounted or opened exclusively by another program?
the unmount option on sda1 is greyed out.

i try e2fsck -C0 -p -f -v /dev/sda1
i get the same error - it is mounted or opened by other program.

i tried this as well:
sudo fsck /dev/sr0

it waited for about 20 seconds and then output : 
No medium found while trying to open /dev/sr0

---

### Post by leptep on 2011-04-11
i meant only the live cd loaded,
Ubuntu still doesn't load,,,
funeral?

---

### Post by leptep on 2011-04-11
Disk utility,
I try to mount the main hard disk, it turns for a long time going nowhere

---

### Post by leptep on 2011-04-12
hello!!!

can anyone help?
is my hard disk dead?

---

### Post by linuxuser12345 on 2011-04-13
I am so sorry for not getting back to you in time! :(
I am just a little busy, but for now on I will help you until I can't any more with this issue! :)

Anyways,
Just click the Install button on the desktop. Go through the guided process and choose the installation to remove your old data and completely use your hard drive for Ubuntu 10.10. That is what I would do.

---

### Post by leptep on 2011-04-14
But I want to recover my data,
how can i do that?

---

### Post by linuxuser12345 on 2011-04-14
I am not too sure. *Somebody* on these forums can help you out with that, though! :)
At least we got 1/2 of the problem fixed already.

---


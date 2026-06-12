---
title: "BASH script keeps looping infinitely"
date: 2011-05-27
forum: General Help
---

### Post by th1rt3en on 2011-05-27
I have a simple .bashrc backup script I've been working on, but my external hard drive needs to be plugged in for it to work. So I set up a while loop, that exits after the hard drive has been plugged in and backed up. Here it is:

```

#/bin/bash

pluggedin=1

while [ $pluggedin==1 ]; do
   if [ -e "/media/files" ]; then
      rm /media/files/docs-archive/settings-backup/bashrc-backup
      cp /home/th1rt3en/.bashrc /media/files/docs-archive/settings-backup/bashrc-backup
      pluggedin=0
   else
      mplayer /home/th1rt3en/bin/audio/blip.wav & #This is just a notification noise
      /usr/bin/zenity --display :0 --warning --text="Please plug in external hard drive for backup"
   fi
done

/usr/bin/zenity --display :0 --warning --text="Backup complete"

```For some reason this keeps looping and doesn't seem to be changing the variable to 0. Can anybody please tell me what I've done wrong?

---

### Post by th1rt3en on 2011-05-27
Huh, I fixed it. I guess I needed to put the while loop variable in quotes:

```
while [ "$pluggedin" == "1" ]; do
```instead of

```
while [ $pluggedin==1 ]; do
```Sorry for the pointless post! 
I've been hitting my head against a wall trying to solve this for an hour, then I figure it out right after I throw in the towel.

---

### Post by mobilediesel on 2011-05-27
There also had to be space around all the operators. It would probably work without the quotes as long as there was space between the == and the variable.
```
while [ $pluggedin == 1 ]; do
```
but it could also be done like this:
```
#/bin/bash

while true; do
   if [ -e "/media/files" ]; then
      rm /media/files/docs-archive/settings-backup/bashrc-backup
      cp /home/th1rt3en/.bashrc /media/files/docs-archive/settings-backup/bashrc-backup
      break
   else
      mplayer /home/th1rt3en/bin/audio/blip.wav & #This is just a notification noise
      /usr/bin/zenity --display :0 --warning --text="Please plug in external hard drive for backup"
   fi
done

/usr/bin/zenity --display :0 --warning --text="Backup complete"
```

---

### Post by th1rt3en on 2011-05-28
Thanks for the advice mobile! I like that method a lot better, a tad bit cleaner I think.
And your avatar is rather clever too by the way, putting your name into a QR code.

---

### Post by mobilediesel on 2011-05-30
> **th1rt3en said:**
> Thanks for the advice mobile! I like that method a lot better, a tad bit cleaner I think.
And your avatar is rather clever too by the way, putting your name into a QR code.

I first programmed on a TI 99/4A and then a Commodore 64. Limited memory forces you into the habit of cutting code down to the smallest possible size that still works. That fits in with an idea I found on catb.org about perfection being found not when there's nothing left to add but when there's nothing left to take away.

and the avatar isn't an actual QR code but I can't remember the exact type of 2D code it is.

---


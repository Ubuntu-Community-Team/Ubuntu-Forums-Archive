---
title: "can't  change ownership of usb drive"
date: 2011-12-31
forum: General Help
---

### Post by NickyRuggs on 2011-12-31
well something has changed on my system and I can't figure this out.

I had a usb drive for my wifes car that had her music that I was syncing with Rhythmbox.  

I just plugged it in my laptop and its owned by root and I cant change it.  I tried changing all the entries in the /media directory but as soon as I plugin the usb drive ownership reverts to root.  if I try changing ownership i get an error.

before plugging:

root@pearl:/media# ls -ltra
total 84
drwx------  4 knic knic 16384 1969-12-31 19:00 3132-6462
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb7
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb6
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb5
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb4
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb3
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb2
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb1
drwx------  1 knic knic  8192 2011-10-27 18:04 OS
drwxr-xr-x 27 root root  4096 2011-12-10 09:54 ..
drwxr-xr-x  2 knic knic  4096 2011-12-28 17:06 usbstick
drwxr-xr-x  2 knic knic  4096 2011-12-31 17:40 usb0
lrwxrwxrwx  1 root root     4 2011-12-31 17:41 usb -> usb0
drwxr-xr-x 13 knic knic  4096 2011-12-31 17:41 .


after plugging:

root@pearl:/media# ls -ltra
total 84
drwxr-xr-x  3 root root  4096 1969-12-31 19:00 usb0
drwx------  4 knic knic 16384 1969-12-31 19:00 3132-6462
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb7
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb6
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb5
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb4
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb3
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb2
drwxr-xr-x  2 knic knic  4096 2010-10-06 20:51 usb1
drwx------  1 knic knic  8192 2011-10-27 18:04 OS
drwxr-xr-x 27 root root  4096 2011-12-10 09:54 ..
drwxr-xr-x  2 knic knic  4096 2011-12-28 17:06 usbstick
lrwxrwxrwx  1 root root     4 2011-12-31 17:41 usb -> usb0
drwxr-xr-x 13 knic knic  4096 2011-12-31 17:41 .

changing owner....


root@pearl:/media/usb# ls -ltra
total 28
drwxr-xr-x  3 root root  4096 1969-12-31 19:00 .
-rwxr-xr-x  1 root root    34 2011-10-23 20:00 .is_audio_player
-rwxr-xr-x  1 root root   552 2011-10-23 21:06 Marcy-car.pls
drwxr-xr-x  2 root root 12288 2011-12-27 23:18 mp3
drwxr-xr-x 13 knic knic  4096 2011-12-31 17:41 ..
root@pearl:/media/usb# chown knic.knic *
chown: changing ownership of `Marcy-car.pls': Operation not permitted
chown: changing ownership of `mp3': Operation not permitted
root@pearl:/media/usb# ls -ltra
total 28
drwxr-xr-x  3 root root  4096 1969-12-31 19:00 .
-rwxr-xr-x  1 root root    34 2011-10-23 20:00 .is_audio_player
-rwxr-xr-x  1 root root   552 2011-10-23 21:06 Marcy-car.pls
drwxr-xr-x  2 root root 12288 2011-12-27 23:18 mp3
drwxr-xr-x 13 knic knic  4096 2011-12-31 17:41 ..

---

### Post by Paddy Landau on 2012-01-01
*Please post code between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags to make it easier to read (or highlight the code and press the # button in the toolbar).*

Which entry is your wife's USB -- is it /media/usb?

It belongs to root, so *you* cannot change its owner. But you can, as the administrator, change it using sudo.
```
sudo chown knic:knic /media/usb
```However, what intrigues me is all the folders in /media. Normally, when you plug in a USB, it automatically creates a new folder in /media, assigns it to you, and lets you access it (so you don't have to fiddle with ownership). When you "safely remove" the device, it automatically unmounts it and deletes the folder. You shouldn't have a whole bunch of folders belonging to you in /media.

May I suggest you unplug all your USB devices (safely remove them); and delete all the entries in /media -- it is normally empty!

Then log out, log in, and try again.

---

### Post by coffeecat on 2012-01-01
@NickyRuggs, the mountpoints /media/usb* suggest that you have installed the app usbmount. If you have, that is your problem. Uninstall it. Usbmount is designed for GUI-less systems (usually servers). It interferes with the USB automounting functionality of the GUI desktop and causes the root permission issue you are seeing.

---

### Post by NickyRuggs on 2012-01-01
Thank you Coffeecat... you were spot on.

I removed usbmount and now things are back to normal.

<code>


/dev/mmcblk0p1         1983360    405984   1577376  21% /media/3132-6462
/dev/sdb1              3914252        24   3914228   1% /media/USB DISK
root@pearl:/media# cd USB\ DISK/
root@pearl:/media/USB DISK# ls
Marcy-car.pls  mp3
root@pearl:/media/USB DISK# ls -ltra
total 28
drwx------ 3 knic knic  4096 1969-12-31 19:00 .
-rw-r--r-- 1 knic knic    34 2011-10-23 20:00 .is_audio_player
-rw-r--r-- 1 knic knic   552 2011-10-23 21:06 Marcy-car.pls
drwx------ 2 knic knic 12288 2011-12-27 23:18 mp3
drwxr-xr-x 7 knic knic  4096 2012-01-01 14:06 ..
root@pearl:/media/USB DISK# 

</code>

---

### Post by redlinethecar on 2012-01-01
This might help..

[IMG]http://ubuntuforums.org/i2.grvcdn.com/uploads/images/1/21/00/21//47679270_512.jpeg[/IMG][http://www.convo.io/funnypages/283/make-me-a-sandwich](http://www.convo.io/funnypages/283/make-me-a-sandwich)

lol this thread made me think of that.

---

### Post by Paddy Landau on 2012-01-02
> **NickyRuggs said:**
> I removed usbmount and now things are back to normal.
Excellent. I would not have thought of that.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others with the same problem.

---


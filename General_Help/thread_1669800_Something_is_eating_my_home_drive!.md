---
title: "Something is eating my home drive!"
date: 2011-01-18
forum: General Help
---

### Post by politenessman on 2011-01-18
I am using 10.10 64 bit.
Just to sanity check I looked at system > About Ubuntu, and it tells me that "*You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012.*"

Anyway, I have a 7.5GB home drive. Currently its usage is up to 7GB and rising, to the point where I keep getting message telling me I only have 128MB of space left etc.

Here is where it gets interesting. I used Baobab 2.31.1 to check my drive usage and it looks like I have about 4.5GB used (if I add up all of the figures it gives me), but it is also telling me that the drive is at 6.9GB.

If I go to my user folder / view hidden items / right click > properties it tells me I have ~ 13.7GB of data.

What am I missing and why is my data growing??? :???:

---

### Post by mastablasta on 2011-01-18
have you installed any programmes. perhaps something under WINE?
 
also a better way to check disk space is in terminal.
 
Free space in terminal
```
df -h
```
 
[http://webtools.live2support.com/linux/df.php](http://webtools.live2support.com/linux/df.php)
 
Partitions.
```
fdisk -l
```

---

### Post by politenessman on 2011-01-18
I don't have all that much installed and other than the updates via the update manager I've not installed anything recently.
I also checked the system monitor to see if there was anything running that I'm not familiar with and there doesn't appear to be.

df -h gives me this:

> tony@Acer1810TZ:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             7.6G  3.4G  3.9G  47% /
none                  1.5G  320K  1.5G   1% /dev
none                  1.5G  516K  1.5G   1% /dev/shm
none                  1.5G  368K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  7.6G  3.4G  3.9G  47% /var/lib/ureadahead/debugfs
**/dev/sda7             7.6G  7.0G  223M  97% /home**
/dev/sda4             232G   76G  156G  33% /media/Data
**/home/tony/.Private   7.6G  7.0G  223M  97% /home/tony**
/dev/sr0              7.8G  7.8G     0 100% /media/floppy0
/dev/sdb1             1.9G   90M  1.9G   5% /media/CANON_DC

I've bolded the relevant part of this.
Could it be ecryptfs eating the space?

---

### Post by lithopsian on 2011-01-18
Well you've shown what is taking up the space, but what do you keep in there?  Did you know you have an encrypted file system?  Are you deliberately using it for something?  Is it your entire home directory?

Home directories often fill up with things like trash, icon thumbnails, browser cache, email, local icon themes, and all the other trash.  You need to look at the storage within .Private to see which bit is chewing so much space.  Normally I'd suggest using the du command to see where the space is gone but I'm not sure how that would work on an encrypted volume.

---

### Post by politenessman on 2011-01-18
I've cleared all the various caches and so forth, and I know that I have ~4.3GB of data so I should have a couple of gigs free space, and I did yesterday (I think). Its only today that I started to get low space messages.

Yes the entire home drive is encrypted - I'm paranoid :)
I guess I need to dig more, but I'll be damned if I can find where the space went.

---

### Post by reobedr on 2011-01-18
Could be that your xsessions.errors file is filling up with errors

---

### Post by politenessman on 2011-01-18
You sir, are awesome!

Yup. I rebooted, logged back in and still got messages about my diminishing space. Saw your message and checked the size of my .xsession-errors file and I see this:

.xsession-errors                 21.6kb (and climbing every few seconds)
.xsession-errors.old             2.4GB

The majority of the errors seem to be this repeating:


> (nm-applet:1900): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed

(nm-applet:1900): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nm-applet:1900): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

Guess I need to figure out what this is.

---

### Post by sydbat on 2011-01-18
> **politenessman said:**
> You sir, are awesome!

Yup. I rebooted, logged back in and still got messages about my diminishing space. Saw your message and checked the size of my .xsession-errors file and I see this:

.xsession-errors                 21.6kb (and climbing every few seconds)
.xsession-errors.old             2.4GB

The majority of the errors seem to be this repeating:




Guess I need to figure out what this is.I have a feeling it has to do with your encryption. Is there a way to unencrypt your /home folder to find out for sure (as I do not use encryption, I do not know if this is possible)?

---

### Post by reobedr on 2011-01-18
Most google hits of the first error point to a network manager memory leak....
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/684599](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/684599)

not sure there's a solution yet

---

### Post by reobedr on 2011-01-18
sorry double post...

---


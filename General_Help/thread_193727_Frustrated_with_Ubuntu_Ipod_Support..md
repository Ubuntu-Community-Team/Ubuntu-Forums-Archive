---
title: "Frustrated with Ubuntu Ipod Support."
date: 2006-06-10
forum: General Help
---

### Post by sauceboy23 on 2006-06-10
Hey guys:

I am having some serious trouble 'ejecting' my ipod from amarok. How can this be done? I am able to transfer files, but after transferring to my Ipod (Color/Photo 20gig) I can't seem to eject/unmount it. Later today out of frustration I just pulled the plug and lost at least two gigs worth of songs on my Ipod... ](*,) I have tried gtkpod (wont even let me transfer files, crashes several times), and am really desperate. All I want is to be able to transfer songs to my ipod! Is that too much to ask? Oh and yes, I have used the search on ubuntuforums and read almost every thread regarding Ipods and Ubuntu. :-| Amarok seems like a great player, it recognizes my Ipod and its songs, transfers, but wont let me unmount...Please help!

---

### Post by grsing on 2006-06-10
Have you tried ejecting it with sudo from the command line:

sudo umount [insert the location of the ipod here, without the brackets]

In some situations you have to have root permissions to eject it, this should cover that.

---

### Post by !nkubus on 2006-06-10
[QUOTE=grsing]Have you tried ejecting it with sudo from the command line:

sudo umount [insert the location of the ipod here, without the brackets]

In some situations you have to have root permissions to eject it, this should cover that.[/QUOTE]

I have 2 suggestion from amarok, you need the command 
(if on gnome)
gksu eject /dev/sda2

(if on kde)
kdesu eject /dev/sda2

or 

You can go on the Gonme desktop right click on the beautiful Ipod Icon and click eject and it works #1 without any configuration at all.


Hope it Helps

---

### Post by brainkilla on 2006-06-10
If you transfer large chunks of data to your iPod, when you try to unmount it the actual copying takes place, so you'll have to wait for a (long) while to get the device available - then and only then it's safe to unplug it...

---

### Post by grsing on 2006-06-10
The problem with ejecting/unmounting from the desktop is that it's without root permission.  It should work, but doesn't always.

---

### Post by sauceboy23 on 2006-06-10
raghu@mars:~$ sudo -s
Password:
root@mars:~# gksu eject /dev/sda2
umount: /: device is busy
umount: /: device is busy
eject: unmount of `/dev/sda1' failed
root@mars:~#

thats what happens when i enter the command into the terminal.

I've tried to unmount it from the desktop, and on my Ipod it still says "Do not Disconnect" Is it okay to disconnect safely now? I was expecting it to go back to the main screen (on the ipod) after I unmounted it...Thanks for the help.

---

### Post by grsing on 2006-06-10
If it still says "Do not Disconnect", it's not necessarily safe, though I've done it with no ill effects.  YMMV.

---

### Post by charnov on 2006-06-10
Neither Rhythymbox nor Amarok worked for me. I switched to Banshee, but the right-click eject option seems to work fine from within Gnome. It does take a while to finish though when I moved a ton of files around.

---

### Post by MGStreak on 2007-06-30
> **!nkubus said:**
> 
(if on gnome)
gksu eject /dev/sda2


I have been trying for *months* to get my iPod to unmount properly... with various commands/scripts/smashing of computer with hammer/etc.  Finally, I found a method that works, and works reliably!!!

Thank you.

---


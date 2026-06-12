---
title: "Using Ubuntu To Save My Files"
date: 2006-04-26
forum: General Help
---

### Post by tris203 on 2006-04-26
I decided i had had enough of windows and was going to back up my files and reformat, and install a dual-boot between Ubuntu and Windows.
BEFORE i had done anything i turned on my PC and got an error, saying "There is a hardisk error please restart" restarting produced the same error. So i put in my knoppix live cd (although i can also do the same using Ubuntu) and was able to save some files to my 256mb memory key. But i have no where to put them, so 200mb is all i can save using this method.

I tried resizing my partitions to move my data onto the new partition and re-install windows, then install Linux to another partition. But that didn't work as my "NTSF filetable is corrupt" ALTHOUGH I CAN STILL READ AND VIEW, MOVE AND COPY THE FILES THROUGH LINUX.

Next i tried connecting my iPod (4gb Mini - Windows formatted - With iPod Linux Installed) to the computer but it came up with the "Do Not Disconnect" Message but Ubuntu never recognised the iPod.

Next i tried networking my computer (running a live CD) to my friends windows box, but they failed to recognise each other.

SO.......

How can I:

a) Connect my iPod to my computer
 or
b)Network my friends and I's computer together using 1 windows computer and 1 Ubuntu LIVE computer

ALSO

Is there a function in Ubuntu i can use to find files, accessed or modified after a cetain date, as these are the ones i need to back up (as these are the files that have changed since my last back-up)

Many Thanks

tris203

---

### Post by nanotube on 2006-04-26
well, first the easy part - to find files modified after a certain date, use command "find" from a terminal. (type "man find" to get details on the options for the find command that will enable you to perform this search).

now, for networking - what do you mean by 'failed to recognize each other' ? if you mean using the "windows networking" type thing, that's because that is not installed by default on ubuntu. easiest way would be i think to go through an ssh server (ssh server is just a quick 
```
sudo apt-get install ssh-server
```
away.

or, if your friends comp is like in the next room, just use the usb key to move the files from one comp to the other :)

oh, and you can also of course try burning your files to CD, if you have a cdrw drive...

---

### Post by tris203 on 2006-04-27
By failed to regognize each other i mean, my linux live did nothing and his windows option said "Limited or No Connectivity"


Any ideas about connecting the iPod because with about 4gb of updated stuff that i need to move, moving it on a 256mb stick will take a while.

Thanks

tris203

---

### Post by Sef on 2006-04-27
If you can, download and burn Trinity Rescue Disk.

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by tris203 on 2006-04-27
So run (8) (SSH server) then the windows computer should be able to recognise my Linux Live box, or will the iPod work with that??

---

### Post by nanotube on 2006-04-27
the ssh server is so the windows box can connect to your linux box.

---

### Post by tris203 on 2006-04-29
When I try when i try the command
```
sudo apt-get install ssh-server
```

It can't do it as i currently have no internet connection on my computer. (Thats using ubuntu.

When I use the Trintity Rescue Disk (3.1) it is unable to resolve an IP adress, therefore i cannot connect to the windows box, soooo im stuck.

I think connecting the iPod is my best bet, does anyone have any ideas for that??

Thanks alot

tris203

---


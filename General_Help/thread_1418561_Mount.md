---
title: "Mount"
date: 2010-02-28
forum: General Help
---

### Post by tom henderson on 2010-02-28
Hello,

I have a new Dell Inspiron Mini 10, and I installed Ubuntu Netbook Remix 9.10 on it. I am trying to sort out my badly organized data, and I'm a bit confused on how file systems differ from one machine to another.

**Here's what I've got:**

160GB of hard drive space on the netbook
One USB drive (320 gig capacity) containing 220GB of stuff, with filesystem type msdos according to the ubuntu gui
One Macbook with a home directory containing 75GB of stuff
A very shaky understanding of what it means to 'mount' a drive

**Here's what I want:**

All the data from the Macbook rescued onto the USB drive
Some of that data moved onto the netbook
The USB drive formatted to work with both computers, so I can store music and video there

**Here's what's wrong:**

When I plug in the USB drive to the Macbook, it won't mount, apparently. I can see the contents of the drive using 

ls /Volumes/Untitled

but when I've tried to make modifications to it, it says it is read-only.

I don't know if you'll be able to help because there seem to be differences in how Mac OS is Unix-like and how Ubuntu is Unix-like, but I hope you can give me an idea on what to try next. Thanks!

---

### Post by garvinrick4 on 2010-02-28
Are you trying to mount the drive in Ubuntu?

Plug in USB port go to gparted in Admin. Go to gparted drop down on upper left.
choose devices go to the USB drive. It will open its partition table up. Right click on
it and choose label. Lets say you call it backup. type backup in for label. Ok now see
what it says sba1 or something like that. Close gparted.

Now open a terminal.
Make a directory:  sudo mkdir /media/backup
Now mount: " sudo mount /dev/sba1 /media/backup"   without qoutes            space after sba1 
To unmount: " sudo umount /media/backup"  without quotes,                                      not a typo umount is right

Get it now, it is always called /media/backup from now on. 
All drives or partitions have there own sda5 or sba1 or sda7. Use the one
it is in gparted or can run "sudo fdisk -l"  without quotes small L that is also.
Once you label something it is always that to mount or unmount. /media/backup
or whatever you name it. 
Must make a directory (folder) for any new device. /dev is always followed by its partition # /sda1 for example.
Always be careful in gparted and stay focused, it is your drive you are fooling with, but must be used now and aqain.

---


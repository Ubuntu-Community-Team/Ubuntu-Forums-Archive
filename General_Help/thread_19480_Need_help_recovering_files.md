---
title: "Need help recovering files"
date: 2005-03-12
forum: General Help
---

### Post by taitanojt0 on 2005-03-12
I am way newbie at linux or anything non-windows... kinda... well

My laptop running win xp home edition just crashed... and i need to either recover my files via home network but do not know how to get samba to work... or i need to burn a cd or dvd but cannot use my onboard cd drive cause im using the live cd... i have a usb cd-rw drive but ubuntu wont let me use it... another option i have is to rename files on my hard drive in order to replace the config files that wont let win xp boot..., but 1) i dont know how to rename files, ive tried everything... and 2) i dont think i have write access and using the terminal i can get root priv but then dont know how to proceed...   

i think my syntax is just messed up and dont know how to fix it...

is this the right syntax for renaming a file:
-----
rename -v /mnt/hda1/folder/file.ext newfilename.ext
-----
also how can i get samba to work.. i cant edit the conf file and i dont know what else to do cause configuring my network cards, ip and network info doesnt seem to work...

is there anyway i can recover my files! any help will be greatly appreciated! :)

if anyone can help please respond...

---

### Post by az on 2005-03-12
If your partitions are ntfs with windows xp, forget about writing to those partitions.  Why can't your usb cd burner work?

What netowrk cards do you have?  If they are wireless cards, try ndiswrapper to load the windows drivers.

---

### Post by taitanojt0 on 2005-03-12
my cd burner shows up in the 'computer -> disks' folder, but i cant seem to work it. my usb smart media card reader also acts this way...

it gives the error message 'Unable to mount the selected volume.'

it cant find /dev/cdrom1 in /etc/fstab or /etc/mtab

i have an emachines m6809 with the following wireless network card:

802.11g Built-in Wireless (up to 54Mbps)
10/100Mbps built-in Ethernet 

i think it is made by broadcom

and how would i set up my sabma, ive tried and it says that i need to install it, but im running the live cd and i dont know how to do this...

---

### Post by taitanojt0 on 2005-03-12
ok, i got the cd burder to work, but now it wont write my files...

---

### Post by bored2k on 2005-03-12
[QUOTE=taitanojt0]ok, i got the cd burder to work, but now it wont write my files...[/QUOTE]
 a. Install [http://www.ubuntulinux.org/wiki/GnomeBaker](http://www.ubuntulinux.org/wiki/GnomeBaker)
b. Get a System independant recovery disc/tool like Hiren's boot cd, and use its tools to recover your files.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) is a good one.
Hiren's is better but we want to to stay in the right side of the law here.

---


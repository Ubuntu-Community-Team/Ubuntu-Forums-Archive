---
title: "Windows prompts to format existing formatted drive"
date: 2009-08-18
forum: General Help
---

### Post by charonred on 2009-08-18
I know this is a Windoze problem, but thought Ubuntu users might have a better idea how to rescue the data on a Windows disk.

A friend just phoned and said his XP install (drive C: ) today started prompting him to format his WD 1.0TB drive (drive G: ), and it won't allow him to access the drive.

The drive was formatted when installed, and has been in use since Oct '08 as his main storage drive ... everything he has downloaded/collected since is on that drive, along with stuff he collected over previous 2 years on his other 500GB drive.

I haven't been over to his place yet, but would running a Live Ubuntu CD allow me to access the drive and backup to another disk? Or can I repair the drive so it works in Windows without losing the data on it - ie would re-initialising the drive trash the data?

---

### Post by damis648 on 2009-08-18
It will probably be fine, but if Ubuntu fails to mount the drive then the filesystem or drive may be damaged.

---

### Post by charonred on 2009-08-18
Thanks, I'm fearing that it may be what you suggested, but hoping not - are their any Linux tools that would allow me to recover the drive if it's corrupt file system.

---

### Post by philinux on 2009-08-18
Could be a virus or a bad disk. Either way livecd is the way to go.

---

### Post by nikhilk on 2009-08-18
> **charonred said:**
> Thanks, I'm fearing that it may be what you suggested, but hoping not - are their any Linux tools that would allow me to recover the drive if it's corrupt file system.

I have only heard about testdisk and photorec but never used them myself. From what I have heard they are good and many people got their files/filesystems back.

I suggest using a specialized rescue disk if there is a corrupt partition.

---

### Post by charonred on 2009-08-18
Thanks, 
just I remembered I have a copy of Parted Magic 4.3 so I'll give that a shot too as I see it has TestDisk on it.

If necessary I may bring the 1.0TB drive back to my place and drop it in one of my other PCs to work on it - easier than stuffing around at friends place.

---

### Post by charonred on 2009-08-20
**_Linux to the rescue_** - I went over my friends place last night, and sure enough Windows wouldn't recognise the drive as being formatted and was prompting to format the drive.

I wonder how many people get this, and subsequently click OK, and then lose everything they had on that drive - what a piece of  ****

All I did was boot from a Jaunty Live CD, mount the 1.0 TB drive in question, explore the contents, unmount, then reboot to Windows - and guess what, Windows could now see the drive as formatted and explore it as it previously did. 

My friend was most impressed; he couldn't understand why Windows wanted to nuke his drive, and after Ubuntu 'fixed' the drive, he said to me "You've proved Linux to me".

Now he wants a Linux install, and gave me the money to buy another 1.0 TB drive to install 9.04 on - he still wants access to the Windows install while he gets used to Ubuntu, so I suggested installing to a separate drive, he canthen choose which one to boot from. And so, before I go back there next week to do a proper install, I did a 'Wubi' install of Jaunty for him to 'play around with'; and again he was impressed with what he saw.

Another Linux convert =D>

Another friend was there watching the proceedings, and said he was sick of Windows messing his laptop, and asked if Ubuntu would  work on it? It was almost midnight, so I left him the Live CD to test on his laptop and said if he's happy with the Live CD test, then we'll look into installing it properly next week as well.

2 more people coming in from the 'dark side' ...

---

